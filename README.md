# Exbanking

## Banking Application

---

### 1. CI/CD Integration for GitHub Actions

This repository integrates Continuous Integration and Continuous Deployment (CI/CD) using GitHub Actions. The provided YAML file automates the testing of both functional and non-functional requirements every time code is pushed to the main branch or a pull request is made against it. It also allows manual triggers of the workflow.

#### Workflow Overview

The CI/CD pipeline includes the following steps:
1. **Checkout Code:** Retrieves the repository code.
2. **Set Up Node.js:** Sets up Node.js version 14.
3. **Install Dependencies:** Installs necessary npm packages.
4. **Start Server:** Starts the server in the background.
5. **Run Cypress Tests:** Executes the functional tests using Cypress.
6. **Install k6:** Installs the k6 load testing tool.
7. **Run k6 Load Test:** Executes the non-functional load tests using k6.
8. **Upload k6 Results:** Uploads the k6 test results.
9. **Stop Server:** Stops the running server.
10. **Upload Test Report:** Uploads the test report generated by Mochawesome.

---

### 2. Functional and Non-Functional Test Cases

All functional and non-functional test cases are documented in the Excel file included in this repository. This file provides detailed descriptions of each test case, including the steps to reproduce, expected results, and other relevant information.

---

### 3. Mock APIs Functional Test Cases

This project implements a mock banking API using Express.js in Node.js. It provides endpoints for 
- creating users (create_user).
- depositing funds (deposit).
- withdrawing funds (withdraw).
- checking balances (get_balance)
- transferring funds between users(send).

This project contains a collection of functional test cases for testing mock APIs of the Exbanking application using a Node.js server using express. The requests can be of the following types and more. However, the collection includes only GET and POST requests as these are only required.

- **GET test:** Tests the GET endpoint of the mock API by sending a GET request and validating the response code and the response data.
- **POST test:** Tests the POST endpoint of the mock API by sending a POST request with a JSON payload and validating the response code and the response data.
- **PUT test:** Tests the PUT endpoint of the mock API by sending a PUT request with a JSON payload and validating the response code and the response data.
- **DELETE test:** Tests the DELETE endpoint of the mock API by sending a DELETE request and validating the response code.

---

### 4. API Automation Testing Framework

This repository contains an automation testing framework for APIs using Cypress, Mochawesome, Express, and Concurrently.

#### Cypress

Cypress is a front-end testing tool built for the modern web. It enables fast, easy, and reliable testing for anything that runs in a browser. We are using Cypress for automating our API tests.

- **Installation:** Cypress is installed via npm and configured in the `cypress.config.js` file.
- **Usage:** Test files are located in the `cypress/e2e/` directory.

#### Mochawesome

Mochawesome is a custom reporter for use with the JavaScript testing framework, Mocha. It generates a visually appealing HTML report along with a JSON report of the test results.

- **Installation:** Mochawesome is included in the `package.json` and configured in the `cypress.config.js` file.
- **Usage:** Reports are generated in the `reports` directory after running tests with `npm run test:server`.

#### Express

Express is a minimal and flexible Node.js web application framework that provides a robust set of features for web and mobile applications. In this framework, Express is used to create a **mock server** to simulate API endpoints for testing purposes.

- **Installation:** Express is included in the `package.json` and used to set up the server in `/server.js`.
- **Usage:** start the server with `npm run server.js`.

#### Concurrently

Concurrently is a utility that allows you to run multiple commands concurrently. It is used here to run the mock server and the Cypress tests at the same time.

- **Installation:** Concurrently is included in the `package.json`.
- **Usage:** Run both the server and tests concurrently with `npm start`.


---
#### Folder Structure:


---
    Exbanking/
    -.github
        -workflows
            - build.yml
    -cypress
        -e2e
            -integration
                -create_user.cy.js
                -deposit.cy.js
                -get_balance.cy.js
                -send.cy.js
                -withdraw.cy.js
        -fixtures
            -testdata.json
        -support
            -command.js
            -e2e.js
    -Functional and Non Functional testcases
        -api_testcases.xlsx
    -node_modules
    -cypress.config.js
    -nonFunctionalCases.js
    -package-lock.json
    -package.json
    -README.md
    -server.js


---

### Running API Automation Project Using GitHub Actions:

This project uses Cypress for API automation. You can run the tests directly using GitHub Actions in two ways: manually triggering the workflow or by pushing code to the repository. Here are the detailed steps for both methods.

#### Running Tests via GitHub Actions
1. **Method 1: Manually Triggering the Workflow**
    - **Fork the Repository**

        * Navigate to the GitHub repository containing the ExBanking project.
        * Click the Fork button at the top right corner of the repository page to create a copy of the repository under your own GitHub account.

    - **Navigate to Your GitHub Repository**
        Open your web browser and go to the GitHub repository containing the project.
        
    - **Navigate to GitHub Actions**
        - Click on the Actions tab located at the top of your repository page.
        
    - **Select the Workflow "Automation for Func and Non-Func Test"**
    
    - **Trigger the Workflow Manually**
            - Click on the Run workflow button.
            - This button is located at the right corner of the screen in the GitHub Actions tab.
            - The workflow is configured with workflow_dispatch, so a form will appear when you click on "Run workflow".
            - The "main" branch will be selected by default. You can choose a different branch if necessary.
            - Click on the "Run workflow" button at the bottom of the form to start the workflow.
            
    - **Monitor the Workflow**
        - **Monitor in Real-Time**
            * Once triggered, the workflow will start running. You can monitor its progress in real-time.  
            * Click on the running workflow to see detailed logs and the status of each step.
            
    - **Wait for Completion**
    
        * Wait for the workflow to complete. It will take around 2-4 minutes.
        
    - **View Reports**
    
        * Upon completion, two reports will be generated for Functional and Non-Functional Test cases.
        * To view these reports, go to the summary section present in the top left corner of the workflow run page.
        * After clicking on "Summary", you will find two files at the bottom: **"Mochawesome HTML Report"** and **"k6LoadTesting result"**.
        
    - **Download and Extract Reports**
        * Download these zip files.
        * Extract the zip files to access the reports of functional and non-functional test cases.
        
    **Sample Images of Mochawesome Report and K6 Load Testing Report:**
    
    - **k6 Load Testing Report**
    ![K6 Load Testing Report](https://raw.githubusercontent.com/vikramsingh62/Exbanking/main/sample%20reports/K6_LoadTesting.png)
    
    - **Mochawesome Report**
    ![Mochawesome](https://raw.githubusercontent.com/vikramsingh62/Exbanking/main/sample%20reports/MochawesomeReport.png)
    
    
        
