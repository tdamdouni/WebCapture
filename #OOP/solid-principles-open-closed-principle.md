# Solid Principles: Open/closed principle

_Captured: 2018-04-01 at 19:39 from [egkatzioura.com](https://egkatzioura.com/2018/02/23/solid-principles-open-closed-principle/)_

Previously we talked about the [single responsibility](https://egkatzioura.com/2018/02/23/solid-principles-single-responsibility-principle/) principle. The [open/closed](https://en.wikipedia.org/wiki/Open/closed_principle) principle is the second principle in the row regarding the solid principles acronym.

"Software entities (classes, modules, functions, etc.) should be open for extension, but closed for modification"

By employing that principle the goal is to extend a module's behaviour without modifying its source code.

Imagine a scenario of applying a discount to one of our products. A discount service will apply the discount specified and give back the discounted price.

Currently our system has only one kind of discount which applies to all adults.

1234567891011121314
`package` `com.gkatzioura.solid.ocp;``import` `java.math.BigDecimal;``import` `java.math.RoundingMode;``public` `class` `Discount {``public` `BigDecimal apply(BigDecimal price) {``BigDecimal percent = ``new` `BigDecimal(``"0.10"``);``BigDecimal discount = price.multiply(percent);``return` `price.subtract(discount.setScale(``2``, RoundingMode.HALF_UP));``}``}`

And the discount service shall apply this discount to the price given.

12345678910111213
`package` `com.gkatzioura.solid.ocp;``import` `java.math.BigDecimal;``public` `class` `DiscountService {``public` `BigDecimal applyDiscounts(BigDecimal price,Discount discount) {``BigDecimal discountPrice = price.add(BigDecimal.ZERO);``discountPrice = discount.apply(discountPrice);``return` `discountPrice;``}``}`

However our company wants to offer a discount to seniors, thus we have the senior Discount.

1234567891011121314
`package` `com.gkatzioura.solid.ocp;``import` `java.math.BigDecimal;``import` `java.math.RoundingMode;``public` `class` `SeniorDiscount {``public` `BigDecimal apply(BigDecimal price) {``BigDecimal percent = ``new` `BigDecimal(``"0.20"``);``BigDecimal discount = price.multiply(percent);``return` `price.subtract(discount.setScale(``2``, RoundingMode.HALF_UP));``}``}`

This makes things a little more complicated for the discount service since the service has to apply both the discount for adult and both the discount for seniors.

123456789101112131415161718192021
`package` `com.gkatzioura.solid.ocp;``import` `java.math.BigDecimal;``public` `class` `DiscountService {``public` `BigDecimal applyDiscounts(BigDecimal price,Discount discount) {``BigDecimal discountPrice = price.add(BigDecimal.ZERO);``discountPrice = discount.apply(discountPrice);``return` `discountPrice;``}``public` `BigDecimal applySeniorDiscount(BigDecimal price,SeniorDiscount discount) {``BigDecimal discountPrice = price.add(BigDecimal.ZERO);``discountPrice = discount.apply(discountPrice);``return` `discountPrice;``}``}`

By doing so we modified the discount service sourcecode to extend its behaviour. Also for every different discount that the sales department might come up with, the discount service will get extra methods.

In order to follow the open/closed principle we will create a discount interface.

12345678
`package` `com.gkatzioura.solid.ocp;``import` `java.math.BigDecimal;``public` `interface` `Discount {``BigDecimal apply(BigDecimal price);``}`

The default discount will be renamed to the AdultDiscount and implement the discount interface.

123456789101112131415
`package` `com.gkatzioura.solid.ocp;``import` `java.math.BigDecimal;``import` `java.math.RoundingMode;``public` `class` `AdultDiscount ``implements` `Discount {``@Override``public` `BigDecimal apply(BigDecimal price) {``BigDecimal percent = ``new` `BigDecimal(``"0.10"``);``BigDecimal discount = price.multiply(percent);``return` `price.subtract(discount.setScale(``2``, RoundingMode.HALF_UP));``}``}`

The SeniorDiscount will also implement the Discount interface.

123456789101112131415
`package` `com.gkatzioura.solid.ocp;``import` `java.math.BigDecimal;``import` `java.math.RoundingMode;``public` `class` `SeniorDiscount ``implements` `Discount {``@Override``public` `BigDecimal apply(BigDecimal price) {``BigDecimal percent = ``new` `BigDecimal(``"0.20"``);``BigDecimal discount = price.multiply(percent);``return` `price.subtract(discount.setScale(``2``, RoundingMode.HALF_UP));``}``}`

Last but not least our DiscountService will be refactored in order to apply discounts based on the Discount interface.

123456789101112131415161718
`package` `com.gkatzioura.solid.ocp;``import` `java.math.BigDecimal;``public` `class` `DiscountService {``public` `BigDecimal applyDiscounts(BigDecimal price,Discount[] discounts) {``BigDecimal discountPrice = price.add(BigDecimal.ZERO);``for``(Discount discount:discounts) {``discountPrice = discount.apply(discountPrice);``}``return` `discountPrice;``}``}`

By this way the discount service will be able to apply different discounts without altering its source code.

The same principle can be applied to the Discount.  
Supposing we want to have a basic discount to be applied extra when a discount is applied.

123456789101112131415
`package` `com.gkatzioura.solid.ocp;``import` `java.math.BigDecimal;``import` `java.math.RoundingMode;``public` `abstract` `class` `BasicDiscount ``implements` `Discount {``@Override``public` `BigDecimal apply(BigDecimal price) {``BigDecimal percent = ``new` `BigDecimal(``"0.01"``);``BigDecimal discount = price.multiply(percent);``return` `price.subtract(discount.setScale(``2``, RoundingMode.HALF_UP));``}``}`

By extending the BasicDiscount class we are able to have more discounts with the behaviour of the BasicDiscount and also extend this behaviour without modifying the BasicDiscount sourcecode.

You can find the source code on [github](https://github.com/gkatzioura/SolidPrinciples/tree/master/src/main/java/com/gkatzioura/solid/ocp). The next principle is the [liskov substitution](https://egkatzioura.com/2018/02/19/solid-principles-liskov-substitution-principle/) principle.

Also I have compiled a cheat sheet containing a summary of the solid principles.  
Sign up in the [link](https://s3-eu-west-1.amazonaws.com/egkatzioura/subscriptions/solidprinciples.html) to receive it.
