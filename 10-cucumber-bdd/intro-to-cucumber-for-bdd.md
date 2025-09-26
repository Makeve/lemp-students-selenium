# What is Behaviour-Driven Development (BDD)?

Behaviour-Driven Development (BDD) is a software development approach that enhances collaboration between developers, testers, and business stakeholders.  
It encourages writing test cases in a natural language that non-technical stakeholders can understand.

## Real-World Analogy: Ordering at a Restaurant 🍽️

Imagine you are ordering food at a restaurant.  
You don’t tell the chef how to cook, you just say:

- ✅ **Given** I want a pizza  
- ✅ **When** I place an order  
- ✅ **Then** I should receive a pizza  

This is exactly how BDD works! 🎯


## 📌 BDD Scenario Flow

- **Given** (the context) → Setup the situation  
- **When** (the action) → Perform an event  
- **Then** (the outcome) → Verify the result  

👉 BDD is about writing test cases in a natural, readable language (English-like format).  
This helps **business analysts, testers, and developers** collaborate easily.

## Key Concepts

- **User Stories**: Describe the desired behaviour of an application.  
- **Gherkin Syntax**: A structured format for writing stories in a way everyone can understand.  

## Benefits of BDD

- **Enhanced Collaboration**: Encourages communication between all stakeholders.  
- **Improved Requirements**: Helps in understanding and defining clear requirements.  
- **Early Bug Detection**: Identifies issues early in the development cycle.  

## Why Use Cucumber for BDD?

BDD is just a practice — but to make it real, we need tools.  
That’s where **Cucumber** comes in. 🥒

✅ **Readable Tests**: Written in plain English (Gherkin syntax)  
✅ **Improved Collaboration**: Bridges the gap between business & developers  
✅ **Reusability**: Scenarios can be reused for multiple test cases  
✅ **Supports Automation**: Works with Selenium, REST APIs, Mobile Testing, etc.  

## Example of a User Story

Consider a user story for a login feature:

```gherkin
Feature: Login Feature
  Scenario: Successful Login with Valid Credentials
    Given the user is on the login page
    When the user enters valid credentials
    Then the user should be redirected to the home page
```

## Hands-on Exercise

### Task
1. Write a user story for a registration feature using Gherkin syntax.
2. Include scenarios for both successful and unsuccessful registrations.

💡 Pro Tip: Always think of both positive and negative paths.
For example, what happens if a required field is left blank?

### Sample User Story
```
Feature: Registration Feature
  Scenario: Successful Registration
    Given the user is on the registration page
    When the user enters valid details
    Then the user should see a registration success message

  Scenario: Unsuccessful Registration
    Given the user is on the registration page
    When the user enters invalid details
    Then the user should see an error message
```

---

<div style="width: 100%">
<a href='index.md'><-- Previous Section: Cucumber for BDD</a>
<div align="right"><a href='writing-test-cases-in-gherkin-syntax.md'> Next Section: Writing Test Cases in Gherkin Syntax --></a></div>
</div>
