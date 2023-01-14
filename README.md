# Playwright_PageObjectModel
Based on WebdriverIO Tutorials by Raghav Pal 

https://youtu.be/rAec3mZFhF0
***
This project was created by [Raghav Pal](https://automationstepbystep.com/about-me/) while doing a DEMO tutorial on How to create Page Object Model framework in Playwright
This is done on a Node project with JavaScript

### Tools & Technologies
* Node JS
* VS Code
* JavaScript

### To use this project

Step 1 - Download the folder or clone the repository

Step 2 - Check node.js is installed on your system  **`node -v`**

Step 3 - Open terminal/cmd > Goto project folder > Run command 

**`npm ci`**	

// this will download and install all required libraries mentioned in package.json file (ci is used to install all exact version dependencies or devDependencies from a package-lock. json file)

**`npx playwright test`**		

// this will run the tests

### Tutorial Steps - Playwright Page Object Model Project

* Step 1 - Create a new folder and open in IDE or Editor (like VS Code)
* Step 2 - Initialize a new Node.js project by running **`npm init -y`** to create a package.json file
* Step 3 - Install & Setup Playwright by running **`npm init playwright@latest`**
* Step 4 - Create a demo login test, can use Test Generator to record **`npx playwright codegen`**
* Step 5 - Run tests and check results - **`npx playwright test`**  & **`npx playwright show-report`**
* Step 6 - Create new folder "pages" in your project, this will contain all page objects
* Step 7 - Create a new file and class for each page e.g. login.js and LoginPage
* Step 8 - In the class create element locators & action methods for login page
* Step 9 - In test file, import the page class, create instance of it, & use methods from LoginPage class
* Step 10 - Run the test **`npx playwright test`** and check results

***
login.spec.js

```
import { test, expect } from '@playwright/test';
import { LoginPage } from '../../pages/login'

test('test', async ({ page }) => {

  const Login = new LoginPage(page)

  await Login.gotoLoginPage()
  await Login.login('tomsmith', 'SuperSecretPassword!')

  // await page.goto('https://the-internet.herokuapp.com/login');
  // await page.getByLabel('Username').click();
  // await page.getByLabel('Username').fill('tomsmith');
  // await page.getByLabel('Password').click();
  // await page.getByLabel('Password').fill('SuperSecretPassword!');
  // await page.getByRole('button', { name: ' Login' }).click();
});
```



***
login.js
```
exports.LoginPage = class LoginPage {

    constructor(page) {

        this.page = page
        this.username_textbox = page.getByLabel('Username')
        this.password_textbox = page.getByLabel('Password')
        this.login_button = page.getByRole('button', { name: 'Login' })
    }

    async gotoLoginPage(){
        await this.page.goto('https://the-internet.herokuapp.com/login');
    }

    async login(username, password){
        await this.username_textbox.fill(username)
        await this.password_textbox.fill(password)
        await this.login_button.click()
    }

}
```
__________________________

#### Never Stop Learning
***Raghav Pal***

***https://automationstepbystep.com/***
