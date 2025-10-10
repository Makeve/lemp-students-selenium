# Exercise 2: Order and Remove Items

## Scenario

The following scenario describes how to automate the process of ordering and removing items from the shopping cart on the Sauce Demo website.

### Steps

1. **Open Browser**: Start by opening a new browser instance.
2. **Navigate to Main Page**: Go to the main page of the Sauce Demo website.
3. **Login**: Enter the username and password, then click the login button.
4. **Sort Items**: Select "Price (low to high)" from the dropdown.
5. **Add Items to Cart**: Add the bike light and fleece jacket to the shopping cart.
6. **Remove Item**: Remove the fleece jacket from the shopping cart.
7. **Navigation**: Select "All Items" from the menu and navigate back to the shopping cart.
8. **Proceed to Checkout**: Navigate to the shopping cart and proceed to checkout.
9. **Enter Checkout Information**: Provide the first name, last name, and postal code.
10. **Complete Purchase**: Continue and finish the purchase process.
11. **Check Tax**: Verify that the tax is "$0.80".

## Step-by-Step Implementation

### Feature File

Create a feature file for this scenario.

````markdown name=features/OrderAndRemoveItems.feature
```gherkin
@Exercise2
Feature: Order and Remove Items

  Scenario: User orders and removes items from the cart
    Given browser is open
    When user is on the main page "https://www.saucedemo.com/inventory.html"
    And user enters the username
    And user enters the password
    And user clicks the login button
    And user selects "Price (low to high)" from the dropdown
    Then user selects item "bike-light"
    Then user selects item "fleece-jacket"
    Then user selects shopping cart
    Then remove item "fleece-jacket"
    Then user selects menu item "All Items"
    Then user selects shopping cart
    Then user selects checkout
    And user enters First Name "Joe"
    And user enters Last Name "Bloggs"
    And user enters Postal Code "OL7 9AP"
    And user clicks continue
    And user checks tax is "$0.80"
    And user clicks finish
````
## Summary
By following these steps, you will have written and executed test cases for ordering and removing items on the Sauce Demo website. This hands-on exercise will help you apply the concepts learned throughout the course and gain practical experience in automating web application tests.

<div style="width: 100%">
<a href='exercise-1.md'><-- Previous Section: Exercise 1</a>
<div align="right"><a href='../12-final-project-career-readiness/index.md'> Proceed to Week 12 Session: Final Project & Career Readiness --></a></div>
</div>
