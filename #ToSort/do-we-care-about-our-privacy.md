# Do We Care About Our Privacy?

_Captured: 2017-06-24 at 03:59 from [dzone.com](https://dzone.com/articles/do-we-care-about-our-privacy?edition=305134&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-23)_

The single app analytics solutions to [take your web and mobile apps to the next level.](https://dzone.com/go?i=208121&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11232955.150143155%3Bdc_trk_aid%3D322361301%3Bdc_trk_cid%3D81513735%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) Try today! Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=208121&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11232955.150143155%3Bdc_trk_aid%3D321036346%3Bdc_trk_cid%3D81513735%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

We all are using private methods in our classes. There are two different ways to use them - one is good and valid while the second one is a hint that something can be wrong with our design.

First of all, we should consider why we are using these private methods. The main reason is breaking our code on smaller problems. We want to create more readable code - from our complicated method, we can create two smaller and consistent private methods. So instead of doing all the work in one method, we break up our code:
    
    
    public class Pagination {
    
      private final Integer page;
      private final Integer itemsPerPage;
    
      public Pagination(final Integer page, final Integer itemsPerPage) {
        this.page = page;
        this.itemsPerPage = itemsPerPage;
      }
    
      public Pageable pageable() {
        return new PageRequest(page(), itemsPerPage());
      }
    
      private Integer page() {
        return Optional.ofNullable(page)
          .filter(p -> p >= 0)
          .orElse(0);
      }
    
      private Integer itemsPerPage() {
        return Optional.ofNullable(itemsPerPage)
          .filter(ipp -> ipp >= 1)
          .orElse(10);
      }
    
    }

Another reason is avoiding code duplication in our class. We separate our code not only to get it more readable but to reuse the same block of code more than once:
    
    
    public class PersonOffice {
    
    private final List<Person> people;
    
      public PersonOffice() {
        this.people = new LinkedList<>();
      }
    
      public BigDecimal sumOfMonthlyPayment() {
        throwExceptionWhenOfficeIsEmpty();
        //CODE
      }
    
      public Optional<BigDecimal> getMonthlyPaymentForName(final String name) {
        throwExceptionWhenOfficeIsEmpty();
        //CODE
      }
    
      private void throwExceptionWhenOfficeIsEmpty() {
        if(people.isEmpty()) {
          throw new EmptyOfficeException("Office is empty!");
        }
      }
    
    // CODE
    }

Above we have the first type of a private method - as I wrote in beginning this type is helpful. It prevents creating spaghetti code, helps to avoid duplication, and breaks our problem into smaller things. As you can see, all of these private methods use fields of the class in which they were implemented.

Now we can talk about private methods which are not using anything from a class. We declare them as static.

Private static method is a method inside of class, which is not connected with the state of the object it is in. This method for sure will not change the object itself because it is not using any of its fields.
    
    
    public class Bank {
    
      private final TaxMinistry taxMinistry;
    
      public Bank(final TaxMinistry taxMinistry) {
        this.taxMinistry = taxMinistry;
      }
    
      public BigDecimal getGrossPrice(final BigDecimal netPrice) {
        final BigDecimal tax = taxMinistry.getCurrentTax();
        return calculateGross(netPrice, tax);
      }
    
      private static BigDecimal calculateGross(final BigDecimal netPrice, final BigDecimal tax) {
        final BigDecimal taxValue = calculateTaxValue(netPrice, tax);
        return netPrice.add(taxValue);
      }
    
      private static BigDecimal calculateTaxValue(final BigDecimal netPrice, final BigDecimal tax) {
        return netPrice.multiply(tax);
      }
    
    }

We should decide to move our calculation logic into a separate method. In this situation, we do not need taxMinistry because we are only operating on two values passed by parameter - netPrice and tax. Because of that, we can mark our private methods as static. Of course, we do not have to put a static modifier if we don't want to and the method will work as before. The compiler will not raise any problems and the application will not throw any exceptions if we do not make it static.

The main difference here is that static indicates that our class is probably doing more than it should. In our Bank class, we do two things: ask TaxMinistry for current taxes and calculate the gross price. Instead, we can create a separate class which will do this for us:
    
    
    public class PriceWithTax {
    
      private final BigDecimal value;
      private final BigDecimal tax;
    
      public PriceWithTax(final BigDecimal value, final BigDecimal tax) {
        this.value = value;
        this.tax = tax;
      }
    
      public BigDecimal grossPrice() {
        return value.add(getVatAmount());
      }
    
      public BigDecimal getVatAmount() {
        return value.multiply(tax);
      }
    
    }

Here, the calculations are delegated to the`PriceWithTax` class, which is easier to read and maintain, simply because it is smaller. The behavior of this class is clear for the API/code reader. Unit tests are so much easier too.

In your IDE, you can turn on an info message that will tell us which method can be private or static. This information (and also an existing static modifier on a private method) will remind you, that you should think more about your class design. A new class will probably better fit into your codebase.

CA App Experience Analytics, a whole new level of visibility. [Learn more.](https://dzone.com/go?i=208122&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11232955.150143157%3Bdc_trk_aid%3D322361143%3Bdc_trk_cid%3D81513735%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=208122&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11232955.150143157%3Bdc_trk_aid%3D322361143%3Bdc_trk_cid%3D81513735%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).
