![logo_ironhack_blue 7](https://user-images.githubusercontent.com/23629340/40541063-a07a0a8a-601a-11e8-91b5-2f13e4e6b441.png)

# LAB | React Stack Tracker

<details>
  <summary>
    <h2>Learning Goals</h2>
  </summary>

This exercise allows you to practice and apply the concepts and techniques taught in class.

Upon completion of this exercise, you will be able to:

- Install and set up React Router

- Use React Router to create a React application that contains multiple pages

- Use React Router hook `useParams` to access URL parameters.

- Create page components that dynamically render content based on URL parameter values.

- Use React Router hook `useSearchParams` to access URL query strings.

  <br>

  <hr>

</details>

## Introduction

Have you ever wondered which tech stacks power your favorite apps and what programming languages are used by the top tech companies? Needless to ask, being a developer, you must have! Now, it's time to turn that curiosity into action.

Welcome to Stack Tracker, the app for exploring the technology landscape and tech stacks of top tech companies, ready to be built by you!

<br>

<p align="center">
  <img src="https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/m3/lab-wikicountries/lab-react-wiki-countries-countries-react-router-setup.gif" alt="Example - Finished LAB" />
</p>
<br>

## Setup

- Fork this repo
- Clone this repo
- Open the LAB and start:

```bash
cd lab-react-stack-tracker
npm install
npm run dev
```

<br>

## Submission

- Upon completion, run the following commands:

  ```bash
  git add .
  git commit -m "done"
  git push origin master
  ```

- Create a Pull Request and submit your assignment.

<br>

## Test Your Code

This lab is equipped with unit tests to provide automated feedback on your progress and help you understand whether your code is working as expected. If you want to check the tests, they are located in the `src/test` folder.

### Iterations and Test Results

During an iteration, if your code seems to work as expected but some tests don't pass, feel free to move on to the next iteration. Once you've completed all the mandatory iterations, you can go back and resolve any remaining failed test

<br>

### Run the Tests

1. To execute the tests, run the following command in the terminal:

```shell
npm run test
```

2. The above command will execute the tests and open the `@vitest/ui` Test Reporter in the browser.

3. To see the test results, **open** [http://127.0.0.1:51204/\_\_vitest\_\_](http://127.0.0.1:51204/__vitest__) in your browser.

<br>

## Instructions

### Iteration 0 | Getting Started

#### Install Dependencies

The application you will use React Router for setting up multiple pages and handling navigation.

To begin, install React Router package:

```shell
npm install react-router-dom
```

<br>

#### JSON Datasets

The data that you will use in this exercise is located in the files `src/companies.json` and `src/technologies.json`. We suggest you also take a moment and go over the files and get familiar with the structure of the objects. The data (objects) stored in these files have the following structure:

**Example:** **`companies.json` objects**

```json
{
  "id": "7a735bb6-cfaa-4616-9a68-cbd243e0bb82",
  "companyName": "Google",
  "website": "www.google.com",
  "logo": "https://www.example.com/company-logo.png",
  "techStack": [
    {
      "name": "Go",
      "slug": "go",
      "image": "https://example.com/go-logo.png"
    },
    {
      "name": "JavaScript",
      "slug": "javascript",
      "image": "https://example.com/javascript-logo.png"
    }
  ]
}
```

<br>

**Example:** **`technologies.json` objects**

```json
{
  "id": "0c13d729-b0e1-4f75-81e6-446e07b019a6",
  "slug": "react",
  "name": "React",
  "description": "A JavaScript library for building user interfaces...",
  "image": "https://example.com/react-logo.png"
}
```

<br>

<br>

---

### Iteration 1 | Import Data

In this iteration, we will do the initial setup and use the state to store the data that we will use in the app.

In the `App` component, import the json datasets from the files `src/companies.json` and `src/technologies.json` and save them in the state as separate variables.

---

### Iteration 2 | Create Components

Inside the `src` folder, we have two separate folders named `components` and `pages`, one used for storing all the individual components and the other for storing the complete pages.

Create the following components in their respective folders:

**Components Folder:**

- **`src/components/Navbar.jsx`**: The `Navbar` component should display a `nav` element with the text **"StackTracker"**.

<br>

**Pages Folder:**

- **`src/pages/HomePage.jsx`**: The `HomePage` component should display a headline with the text:

  **"StackTracker: Discover Tech Stacks Used by Top Companies"**
  <br>

- **`src/pages/CompanyPage.jsx`**: The `CompanyPage` component should display a headline with the text:

  **"Company Profile**"

- **`src/pages/TechnologyPage.jsx`**: The `TechnologyPage.jsx` component should display a headline with the text:

  **"Technology Details**"

<br>

<details>

  <summary><b>See Expected Result</b></summary>

<br>

**`HomePage`**:

![styled homepage component](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/m3/lab-wikicountries/lab-react-wiki-countries-home-page-static.png)

<br>

**`CompanyDetailsPage`**:

![styled country details page component](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/m3/lab-wikicountries/lab-react-wiki-countries-country-details-page-static.png)
<sub> Note: Structure and content copied from the "examples" folder</sub>
<br>

</details>

<br>

---

### Iteration 2 | Setup React Router and Create Routes

After creating the components, it is time to take the next step and set up React Router to handle navigation and create multiple pages in your app.

1. Set up React Router in your `src/main.jsx` file:

```jsx
// src/main.jsx
import ReactDOM from "react-dom/client";
import "./index.css";
import App from "./App";

import { BrowserRouter as Router } from "react-router-dom";

ReactDOM.createRoot(document.getElementById("root")).render(
  <React.StrictMode>
    <Router>
      <App />
    </Router>
  </React.StrictMode>
);
```

<br>

2. In your `App.jsx` set up three routes that render the following pages:

- Route `/`, which renders the `HomePage` component
- Route `/company/:companySlug`, which renders the `CompanyPage` component
- Route `/tech/:slug`, which renders the `TechnologyPage` component

<br>

Once you set up the routes, your app should render two pages as shown in the expected result below.

<details>

  <summary><b>See Expected Result</b></summary>

![navigating to country details page from home page](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/m3/lab-wikicountries/lab-react-wiki-countries-countries-react-router-setup.gif)

  <br>

</details>

<br>

---

### Iteration 3 | Display Companies as a List

In the `HomePage` component, render the list of companies.

Each list item should be a React Router [`Link`](https://reactrouter.com/en/main/components/link) showing the company **name** and **logo**.

The component should take 1 prop:

- `companies`: The array of companies coming from the `App`. This is the data from `companies.json` that you stored in the state of `App` in [Iteration 1](#iteration-1-|-import-data).

<br>

To allow users to navigate to a specific company's details page, embed the company's `slug` in the URL for each `Link`. When any of the company name on the `HomePage` are clicked, the company `slug` should show up in the URL, and the user should be navigated to the company details page (`CompanyPage`).

<br>

<details>

  <summary><b>See Expected Result</b></summary>

![home page showing list of country names](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/m3/lab-wikicountries/lab-react-wiki-countries-countries-list-names-only.gif)

  <br>

</details>

<br>

---

### Iteration 4 | Show Company Details

In this iteration, you will work on the `CompanyPage` component to display the information of a specific company.

The component should take 1 prop:

- `companies`: The array of companies coming from the `App`.

<br>

#### 4.1 | Access URL Parameters

When a company name link on the `HomePage` is clicked, the user should be navigated to the `CompanyPage`, and the company `slug` should be available as a URL parameter.

To access the URL parameters from the browser's URL bar, use the React Router hook `useParams`.

If you need a reminder on how to set up the useParams hook and access the URL parameters, check [this example](https://reactrouter.com/en/6.10.0/hooks/use-params).

<br>

#### 4.2 | Show Company Details

To retrieve the data for a specific company, you should iterate over the array of companies that is passed as a prop and find the company with a matching `slug` property.

Once you have the company data render the company _name_, _website_, _description_, and _logo_.

<br>

<details>

  <summary><b>See Expected Result</b></summary>

![dynamic country details page loading](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/m3/lab-wikicountries/lab-react-wiki-countries-country-details-page-dynamic-loading.gif)

  <br>

</details>

<br>

#### 4.3 | Show Company's Tech Stack

Next, render the tech stack of the company as a list of links.

For each technology, display its `name` and `image`, and wrap them in a React Router `Link` component to make them clickable links. To allow users to navigate to a technology details page, embed the technology `slug` in the URL of the `Link`.

<br>

<details>

  <summary><b>See Expected Result</b></summary>

![dynamic country details page and borders](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/m3/lab-wikicountries/lab-react-wiki-countries-country-details-page-dynamic.gif)

  <br>

</details>

<br>

---

### Iteration 5 | Technology Details

In this iteration, you will work on the `TechologyPage` component to display the information of a specific technology.

The component should take 1 prop:

- `technologies`: The array coming from the `App`. This is the data from `technologies.json` that you stored in the state of `App` in [Iteration 1](#iteration-1-|-import-data).

<br>

#### 5.1 | Access URL Parameters

When a technology link on the `CompanyPage` is clicked, the user should be navigated to the `TechologyPage`, and the technology `slug` (name) should be available as a URL parameter.

To access the URL parameters from the browser's URL bar, use the React Router hook `useParams`.

If you need a reminder on how to set up the useParams hook and access the URL parameters, check [this example](https://reactrouter.com/en/6.10.0/hooks/use-params).

<br>

#### 5.2 | Show Technology Details

To retrieve the info of a specific technology, you should iterate over the array of technologies that is passed as a prop, and find the one with a matching `slug` property.

Once you have it, render the technology _name_, _image_, and _description_.

<br>

<details>

  <summary><b>See Expected Result</b></summary>

![dynamic country details page loading](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/m3/lab-wikicountries/lab-react-wiki-countries-country-details-page-dynamic-loading.gif)

  <br>

</details>

<br>

#### 5.3 | Render the Back Button

Next, render the tech stack of the company as a list of links.

For each technology, display its `name` and `image`, and wrap them in a React Router `Link` component to make them clickable links. To allow users to navigate to a technology details page, embed the technology `slug` in the URL of the `Link`.

<br>

<details>

  <summary><b>See Expected Result</b></summary>

![dynamic country details page and borders](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/m3/lab-wikicountries/lab-react-wiki-countries-country-details-page-dynamic.gif)

  <br>

</details>

<br>



### Bonus: Iteration 6 | Back to Visited Company

Create a button that in the `TechnologyPage` component that when clicked, navigates the user back to the page of the last visited company.



When navigating from a `CompanyPage` to a `TechnologyPage`, include a query string in the URL named with a slug of the current company. 

Next, on the `TechnologyPage`, retrieve the slug from the query string using `useSearchParams()` and create a **<kbd>Back</kbd>** button. This back button, when clicked, should navigate the user back to the `CompanyPage` of the last visited company using the route `/company/:companySlug`.

<br>



### Bonus: Iteration 7 | Styling

Now that your application is fully functional, it could use a bit of aesthetic touch. This is your chance to get creative, start adding some styles to make your app "pop"!

<br>

**Happy coding!** :blue_heart:

<br>

## FAQs

<details>
  <summary>I am stuck and don't know how to solve the problem or where to start. What should I do?</summary>

  <br>

If you are stuck in your code and don't know how to solve the problem or where to start, you should take a step back and try to form a clear question about the specific issue you are facing. This will help you narrow down the problem and come up with potential solutions.

For example, is it a concept that you don't understand, or are you receiving an error message that you don't know how to fix? It is usually helpful to try to state the problem as clearly as possible, including any error messages you are receiving. This can help you communicate the issue to others and potentially get help from classmates or online resources.

Once you have a clear understanding of the problem, you will be able to start working toward the solution.

  <br>

[Back to top](#faqs)

</details>

<br>

<details>
  <summary>How do I update a state variable in my React component? How do I use the useState hook in my React component?</summary>

  <br>

To update a state variable in a React component, you should use the `useState` hook. This hook returns an array with two elements: the **current value** of the state variable and a **function to update it**. Here is an example of how to use `useState` to update the `count` state variable:

```jsx
import { useState } from "react";

function MyComponent() {
  const [count, setCount] = useState(0);

  const handleClick = () => {
    setCount(count + 1);
  };

  return (
    <div>
      <button onClick={handleClick}> Increment </button>
      <p>Count: {count}</p>
    </div>
  );
}
```

In the above example, the `handleClick` function is called when the button is clicked, and it updates the `count` state variable by calling the `setCount` function with the new value: `setCount(count + 1)`.
The component will re-render every time a state variable gets updated.

  <br>

[Back to top](#faqs)

</details>

<br>

<details>
  <summary>I am getting an error: "not defined". How do I fix it?</summary>

  <br>

The "ReferenceError: variable is not defined" error in JavaScript occurs when you try to access a variable or a function that has not been defined yet or is out of scope.

To fix the issue, check that you have defined the variable or function that you are trying to use and double-check the spelling to make sure you are using the correct name.

In case the variable or a function is defined in another file, make sure that the file has been imported or loaded correctly.

  <br>

[Back to top](#faqs)

</details>

<br>

<details>
  <summary>I am unable to push changes to the repository. What should I do?</summary>

  <br>

There are a couple of possible reasons why you may be unable to _push_ changes to a Git repository:

1. **You have not committed your changes:** Before you can push your changes to the repository, you need to commit them using the `git commit` command. Make sure you have committed your changes and try pushing again. To do this, run the following terminal commands from the project folder:

   ```shell
   git add .
   git commit -m "Your commit message"
   git push
   ```

<br>

2. **You do not have permission to push to the repository:** If you have cloned the repository directly from the main Ironhack repository without making a _Fork_ first, you do not have write access to the repository.
   To check which remote repository you have cloned, run the following terminal command from the project folder:

   ```shell
   git remote -v
   ```

   <br>

   If the link shown is the same as the main Ironhack repository, you will need to fork the repository to your GitHub account first, and then clone your fork to your local machine to be able to push the changes.

   **Note**: You may want to make a copy of the code you have locally, to avoid losing it in the process.

  <br>

[Back to top](#faqs)

</details>
