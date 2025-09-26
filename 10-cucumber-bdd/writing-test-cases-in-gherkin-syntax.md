# Writing Test Cases in Gherkin Syntax

Gherkin is a language used to write test cases for Cucumber, a tool for Behavior-Driven Development (BDD). Gherkin's syntax is simple and designed to be understandable by both non-technical stakeholders and developers.

## The Structure of Gherkin

### 1. Feature

A feature is a high-level description of a software feature and contains one or more scenarios. It is defined using the `Feature` keyword.

**Example:**

```gherkin
Feature: User login functionality
  This feature allows users to log into the application.
```

### 2. Scenario

A scenario represents a specific user interaction or behavior. It consists of steps that describe the user actions and expected outcomes. Each scenario is defined using the `Scenario` keyword.

**Example:**

```gherkin
Scenario: Successful login with valid credentials
```

### 3. Steps

Steps are the building blocks of a scenario. Each step starts with one of the keywords: `Given`, `When`, `Then`, `And`, or `But`.

- `Given` describes the initial context or setup.
- `When` describes the action or event.
- `Then` describes the expected outcome.
- `And` and `But` are used to add more conditions to any of the previous steps.

**Example:**

```gherkin
Given the user is on the login page
When the user enters valid credentials
Then the user should be redirected to the dashboard
```

## Writing a Gherkin Test Case

Let's create an original and unique Gherkin test case for a simple e-commerce website where users can search for products.

### Feature: Product Search

```gherkin
Feature: Product Search
  As a user,
  I want to search for products
  So that I can find the items I want to buy.
```

### Scenario: Searching for a product by name

```gherkin
Scenario: Searching for a product by name
  Given the user is on the home page
  When the user enters "laptop" in the search bar
  And the user clicks the search button
  Then the user should see a list of laptops in the search results
```

- ✅ Feature describes the overall functionality.
- ✅ Scenario describes one concrete behavior.
- ✅ Steps break down the actions and outcomes.

### Detailed Explanation

#### Step 1: Define the Feature

```gherkin
Feature: Shopping Cart
  As a user,
  I want to add products to my shopping cart
  So that I can purchase them later.
```

- This feature describes the shopping cart functionality.

#### Step 2: Define the Scenario

```gherkin
Scenario: Adding a product to the cart
```

- This scenario describes the process of adding a product to the cart.

#### Step 3: Write the Steps

```gherkin
Given the user is on the product page for "laptop"
```

- Sets up the initial context where the user is on the product page.

```gherkin
When the user clicks the "Add to cart" button
```

- Describes the action of clicking the "Add to cart" button.

```gherkin
Then the product should be added to the shopping cart
And the shopping cart should show "1 item"
```
- Describes the expected outcome, ensuring the product is added to the cart and the cart updates correctly.

By following these steps, you can write clear and effective Gherkin test cases for their applications.

### Example 1: SauceDemo Login

Let’s apply this to SauceDemo, the practice website we’ve been using.
```gherkin
Feature: Login Feature
  In order to access the store
  As a registered user
  I want to be able to log in with valid credentials

  Scenario: Successful Login
    Given the user is on the login page
    When the user enters "standard_user" and "secret_sauce"
    Then the user should be redirected to the products page

  Scenario: Failed Login
    Given the user is on the login page
    When the user enters "locked_out_user" and "secret_sauce"
    Then the user should see an error message
```
> Notice how both successful and failed logins are grouped under the same `Feature:`.

### Example 2: Adding a Product to Cart
```gherkin
Feature: Shopping Cart
  As a user,
  I want to add products to my shopping cart
  So that I can purchase them later.

  Scenario: Adding a product to the cart
    Given the user is on the product page for "Sauce Labs Backpack"
    When the user clicks the "Add to cart" button
    Then the product should be added to the shopping cart
    And the shopping cart should show "1 item"
```
## 📝 Hands-on Exercise

👉 Try this with **SauceDemo**:  

Write a `.feature` file for the **checkout process** with at least two scenarios:  

1. ✅ Successful checkout with valid details  
2. ❌ Unsuccessful checkout with missing details  

💡 Hint: Use **Given**, **When**, **Then** steps like we did for Login and Cart.  

## ⚡ Key Takeaways

- **Feature** → describes what functionality you are testing.  
- **Scenario** → describes one concrete example or use case.  
- **Steps** (`Given`, `When`, `Then`) → break the behavior into actions and results.  
- **SauceDemo** is a great playground to practice writing `.feature` files.  

<div style="width: 100%">
<a href='intro-to-cucumber-for-bdd.md'><-- Previous Section: Behaviour-Driven Development (BDD)</a>
<div align="right"><a href='setting-up-cucumber-with-selenium.md'> Next Section: Setting Up Cucumber with Selenium --></a></div>
</div>

