# Introduction to CI/CD (Contd.)  

Now that you know why CI/CD matters, let’s break it down into its main components:  

## What is CI/CD?  

**CI/CD** stands for:  
- **Continuous Integration (CI)**  
- **Continuous Delivery (CD)**  
- **Continuous Deployment (CD)**  

It’s all about delivering apps to users faster by **automating every step of the process** — from coding, to testing, to deploying.  


## Continuous Integration (CI)  
Continuous Integration is a development practice where developers integrate code into a shared repository frequently, preferably several times a day. Each integration can then be verified by an automated build and automated tests. CI aims to provide rapid feedback so that if a defect is introduced into the codebase, it can be identified and corrected as soon as possible.

- Developers integrate (merge) their code changes into a shared repository frequently (several times a day).  
- Each integration triggers **automated builds and tests**.  
- Goal: **Catch bugs early** and keep the project stable.  

👉 Example: Imagine a team of 5 people editing a shared Google Doc. Instead of waiting until the end of the week to merge all changes (which would cause conflicts), everyone updates the document frequently.  


## Continuous Delivery (CD)  
Continuous Delivery is the practice of ensuring that the codebase is always in a state that can be deployed to production at any time. It involves rigorous automated testing to provide assurance that the application will work as expected in production.

- Ensures the code is always in a **deployable state.**  
- Code passes automated tests and is packaged so it **could be deployed at any moment.**  
- Deployment to production still requires a **manual approval step.**  

👉 Example: Think of baking bread — after mixing and baking, your bread is ready to eat, but you may decide when to actually serve it.  

## Continuous Deployment (CD)  
Continuous Deployment is the practice of automatically deploying every code change that passes the automated tests to a production environment. This ensures that the software is always in a deployable state and can be released to users at any time.

- Goes one step further: every change that passes the automated pipeline is **deployed automatically to production**.  
- No manual approval — truly hands-off.  

👉 Example: Like a vending machine — once you insert money and make a selection, the item is **automatically delivered** without needing someone to hand it to you.  

## Benefits of CI/CD  

- **Faster Time to Market** → Features and fixes reach users quickly.  
- **Improved Quality** → Automated tests reduce bugs in production.  
- **Reduced Risk** → Small, frequent updates are easier to manage.  
- **Better Collaboration** → Developers integrate and share work more often.  


<div style="width: 100%">
<a href='overview.md'><-- Previous Section: CI/CD Overview</a>
<div align="right"><a href='setting-up-ci-with-github-actions.md'> Next Section: Setting Up CI with GitHub Actions --></a></div>
</div>
