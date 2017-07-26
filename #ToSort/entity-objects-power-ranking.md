# Entity Objects Power Ranking

_Captured: 2017-03-27 at 22:51 from [dzone.com](https://dzone.com/articles/entity-objects-power-ranking?edition=286926&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-27)_

Learn how to troubleshoot and diagnose some of [the most common performance issues in Java today](https://www.appdynamics.com/lp/ebook-top-10-java-performance-problems/?utm_source=sponsorship&utm_medium=sponsorship&utm_campaign=java%25252520zone&utm_content=ebook-top-10-java-performance-problems&utm_term=dzone-content-syn&utm_budget=digital). Brought to you in partnership with [AppDynamics](https://www.appdynamics.com/lp/ebook-top-10-java-performance-problems/?utm_source=sponsorship&utm_medium=sponsorship&utm_campaign=java%25252520zone&utm_content=ebook-top-10-java-performance-problems&utm_term=dzone-content-syn&utm_budget=digital).

There seems to be an ever-ongoing discussion about how powerful an _entity_ object should be. That's indeed a very valid discussion, as the choice that we make (often unconsciously) will have a huge impact on the final shape of our application. Let's see what options do we have and try to analyze the consequences of each.

## **Anemic Objects**

Anemic objects contain just data and nothing else. To be precise, we shouldn't even call them objects. These are simply data structures. All logic related to these objects lies somewhere else, most likely in some "service" or "util" class, close to its usage.
    
    
    public class Order {
        private List<OrderPosition> positions = new ArrayList<OrderPosition>();
    
        // getters and setters
    }
    
    
    public class OrderPosition {
        private Long productId;
        private BigDecimal quantity;
    
        // getters and setters
    }
    
    
    public class OrderService {
        // repository, c-tor
    
        public void addPosition(Long orderId, Long productId, BigDecimal quantity) {
            if (quantity.compareTo(BigDecimal.ZERO) <= 0) { // I protect invariants!
                throw new IllegalArgumentException("Quantity has to be positive");
            }
    
            Order order = orderRepository.findById(orderId);
            Optional<OrderPosition> positionForProduct = findPosition(order, productId); // I do database stuff!
    
            if (positionForProduct.isPresent()) { // I do domain logic!
                OrderPosition orderPosition = positionForProduct.get();
                orderPosition.setQuantity(orderPosition.getQuantity().add(quantity));
            } else {
                OrderPosition orderPosition = toOrderPosition(productId, quantity);
                order.getPositions().add(orderPosition);
            }
    
            gui.display(order); // I decide what's displayed and when!
        }
    
        private Optional<OrderPosition> findPosition(Order order, Long productId) {
            return order.getPositions()
                    .stream()
                    .filter(position -> position.getProductId().equals(productId))
                    .findAny();
        }
    
        private OrderPosition toOrderPosition(Long productId, BigDecimal quantity) {
            OrderPosition orderPosition = new OrderPosition();
            orderPosition.setProductId(product.getId());
            orderPosition.setQuantity(quantity);
            return orderPosition;
        }
    }

Anemic objects are, at least from my experience, pretty ubiquitous, and I think that the reason for this is that creating such "objects" is just easy. People first think about the data they need to implement a feature, bash it into a class, and then use it as they need without changing it again until some field with data is missing. This is scary, especially considering all the cons of anemic objects:

  * The logic is spread all over the codebase, far from the data is operates on
  * If you want to reuse, you have to search for "common" places, that both parties can depend on (and that's only when you actually find the usage)
  * In a bigger codebase, there's a huge chance that you won't find some common logic and duplication will arise
  * Just data and nothing else, these are basically data structures
  * A single, small change to the class' internals can spread all over the codebase, which would make you reluctant to change anything (code rigidity)

## **Domain Objects**

Domain objects contain only domain-related data and operations. They are meant to represent the domain model, it's relationships and invariants as accurately as possible. No application-specific logic should reside in the domain objects. It should reside in the application layer or its equivalent in the architecture.
    
    
    public class Order {
        private List<OrderPosition> positions = new ArrayList<OrderPosition>();
    
        public void addPosition(Long productId, BigDecimal quantity) {
            Optional<OrderPosition> positionForProduct = findPosition(productId);
    
            if (positionForProduct.isPresent()) { // I do domain logic!
                OrderPosition orderPosition = positionForProduct.get();
                orderPosition.increaseQuantity(quantity);
            } else {
                positions.add(new OrderPosition(productId, quantity));
            }
        }
    
        private Optional<OrderPosition> findPosition(Long productId) {
            return positions
                    .stream()
                    .filter(position -> position.forProduct(productId))
                    .findAny();
        }
    
        public List<OrderPosition> getPositions() {
            return Collections.unmodifiableList(positions);
        }
    }
    
    
    public class OrderPosition {
        private Long productId;
        private BigDecimal quantity;
    
        OrderPosition(Long productId, BigDecimal quantity) {
            if (quantity.compareTo(BigDecimal.ZERO) <= 0) { // I protect invariants!
                throw new IllegalArgumentException("Quantity has to be positive");
            }
            this.productId = productId;
            this.quantity = quantity;
        }
    
        boolean forProduct(Long productId) {
            return this.productId.equals(productId);
        }
    
        void increaseQuantity(BigDecimal amount) {
            if (quantity.compareTo(BigDecimal.ZERO) <= 0) {
                throw new IllegalArgumentException("Quantity has to be positive");
            }
            this.quantity = quantity.add(amount);
        }
    
        public Long getProductId() {
            return productId;
        }
    
        public BigDecimal getQuantity() {
            return quantity;
        }
    }
    
    
    public class OrderService {
        // fields, c-tor
    
        public void addPosition(Long orderId, Long productId, BigDecimal quantity) {
            Order order = orderRepository.findById(orderId); // I do database stuff!
            order.addPosition(productId, quantity);
            gui.display(extractDetails(order)); // I decide what's displayed and when!
        }
    
        private OrderDetails extractDetails(Order order) {
            OrderDetails orderDetails = new OrderDetails();
            for (OrderPosition orderPosition : order.getPositions()) {
                orderDetails.addPosition(new Position(
                        orderPosition.getProductId(),
                        orderPosition.getQuantity()));
            }
            return orderDetails;
        }
    }

Domain objects really shine when you work with a domain model as they're the clearest way to express it. They are more maintainable than anemic objects, as they provide separation of concerns between the domain and the rest of the application. Domain changes are clearly localized, code reuse is easier, and the classes remain relatively small. On the downside, some people denote their limited encapsulation as they still need to share their internals, e.g. for presentation purposes and that you can't tell the object's actual business function (use cases) just by looking at the object itself.

## **Fat/Business Objects**

Fat objects, which some may call business objects provide full encapsulation of the underlying data and are tasked with actual application-specific business tasks. They are not some domain concepts that you orchestrate to carry out a use case. Fat objects take matters into their own hands and communicate with each other to carry out the use case themselves.
    
    
    public class Order {
        private List<OrderPosition> positions = new ArrayList<>();
    
        public void addPosition(Long productId, BigDecimal quantity, OrderView orderView) {
            Optional<OrderPosition> positionForProduct = findPosition(productId);
    
            if (positionForProduct.isPresent()) { // I do domain logic!
                OrderPosition orderPosition = positionForProduct.get();
                orderPosition.increaseQuantity(quantity);
            } else {
                positions.add(new OrderPosition(productId, quantity));
            }
    
            orderView.display(extractDetails()); // I decide what's displayed and when!
        }
    
        private Optional<OrderPosition> findPosition(Long productId) {
            return positions
                    .stream()
                    .filter(position -> position.forProduct(productId))
                    .findAny();
        }
    
        private OrderDetails extractDetails() {
            OrderDetails orderDetails = new OrderDetails();
            for (OrderPosition orderPosition : positions) {
                orderDetails.addPosition(orderPosition.getDetails());
            }
            return orderDetails;
        }
    
        public static class OrderView {
            void display(OrderDetails details);
        }
    
        public static class OrderDetails {
            // stuff
        }
    }
    
    
    class OrderPosition {
        private Long productId;
        private BigDecimal quantity;
    
        OrderPosition(Long productId, BigDecimal quantity) {
            if (quantity.compareTo(BigDecimal.ZERO) <= 0) { // I protect invariants
                throw new IllegalArgumentException("Quantity has to be positive");
            }
            this.productId = productId;
            this.quantity = quantity;
        }
    
        boolean forProduct(Long productId) {
            return this.productId.equals(productId);
        }
    
        void increaseQuantity(BigDecimal amount) {
            if (quantity.compareTo(BigDecimal.ZERO) <= 0) {
                throw new IllegalArgumentException("Quantity has to be positive");
            }
            this.quantity = quantity.add(amount);
        }
    
        Position getDetails() {
            return new Position(productId, quantity);
        }
    }
    
    
    public class OrderService {
        // fields, c-tor
    
        public void addPosition(Long orderId, Long productId, BigDecimal quantity) {
            Order order = orderRepository.findById(orderId); // I do database stuff!
            order.addPosition(productId, quantity, gui);
        }
    }

The so-called "OO purists" are happy when they see fat objects, as they provide maximum encapsulation and maximum power. All the changes in the business logic are easily localized within this objects whether it's a domain change or just a change of an application feature. A problem that might arise with fat objects is that they can get really fat; you need to constantly watch and control the class size so that it doesn't get out of hand. These objects also never tend to get stable. As new features come along, they keep changing to adapt to new requirements. As the domain model gets mixed with application logic, I'd expect it to be easier for the programmer to make a mistake to break object's invariants.

## **God Objects**

God objects are the second extreme in my little power ranking. They do domain logic, contain business features and handle a ton of other unrelated stuff. The more godly your objects become, the less necessary other objects are.
    
    
    public class Order {
    
        public static void addPosition(Long orderId, Long productId, BigDecimal quantity) {
            // I'm doing it all!!
            // I protect invariants!
            // I do database stuff!
            // I do domain logic!
            // I decide what's displayed an when!
            // I AM THE KING OF THE WORLD!!
        }
    }

I'd like to say something good about god objects, but nothing comes to my mind. Maybe the fact that you don't have to switch files or that you always know what file to change when you want to change something in the system. But on the other side, god classes are way too fat, unstable and ultimately unmaintainable. In a project that contains one or more god classes, you don't learn the business by reading the code. You learn about the ways to survive in the codebase instead.

## Which Ones (Should) You Use?

I suppose that all of us worked at one point with all of the approaches and that most people would argue that either the second or third option is the best. I strongly believe in a dichotomy between the application's domain and use cases -- i.e. they are related, but a piece of logic belongs to either one or the other, so I'd opt for the second option. But that's just my view of the case. I'm really curious, what approach do you work with on a daily basis and which one do you believe is the best? Please, let me know in the comments!

Understand the needs and benefits around implementing [the right monitoring solution for a growing containerized market](https://www.appdynamics.com/lp/the-importance-of-monitoring-containers/?utm_source=sponsorship&utm_medium=dzone&utm_campaign=java%20zone&utm_content=importance-of-monitoring-containers&utm_term=dzone-content-syn&utm_budget=digital). Brought to you in partnership with [AppDynamics.](https://www.appdynamics.com/lp/the-importance-of-monitoring-containers/?utm_source=sponsorship&utm_medium=dzone&utm_campaign=java%20zone&utm_content=importance-of-monitoring-containers&utm_term=dzone-content-syn&utm_budget=digital)

### Like This Article? Read More From DZone
