# Exercise 1: Buy the Backpack and Assert it Has Been Ordered

## Scenario

The following scenario describes how to automate the process of buying a backpack from the Sauce Demo website and asserting that it has been ordered successfully.

### Steps

1. **Open Browser**: Start by opening a new browser instance.
2. **Navigate to Main Page**: Go to the main page of the Sauce Demo website.
3. **Login**: Enter the username and password, then click the login button.
4. **Select Item**: Choose the backpack item from the inventory.
5. **Add to Cart**: Add the selected item to the shopping cart.
6. **Proceed to Checkout**: Navigate to the shopping cart and proceed to checkout.
7. **Enter Checkout Information**: Provide the first name, last name, and postal code.
8. **Complete Purchase**: Continue and finish the purchase process.

## Step-by-Step Implementation

### Feature File

Create a feature file for this scenario.

````markdown name=features/BuyBackpack.feature
```gherkin
Feature: Buy the Backpack

  Scenario: User buys a backpack and completes the order
    Given browser is open
    When user is on the main page "https://www.saucedemo.com/inventory.html"
    And user enters the username
    And user enters the password
    And user clicks the login button
    Then user selects item "backpack"
    Then user selects shopping cart
    Then user selects checkout
    And user enters First Name "Joe"
    And user enters Last Name "Bloggs"
    And user enters Postal Code "OL7 9AP"
    And user clicks continue
    And user clicks finish

````

## Summary
By following these steps, you will have written and executed test cases for buying a backpack on the Sauce Demo website. This hands-on exercise will help you apply the concepts learned throughout the course and gain practical experience in automating web application tests.


<div style="width: 100%">
<a href='intro-to-the-final-project.md'><-- Previous Section: Introduction to the Final Project</a>
<div align="right"><a href='exercise-2.md'> Next Section: Exercise 2 --></a></div>
</div>
