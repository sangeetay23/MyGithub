## Github Profiles App Documentation

This documentation outlines the files and functionalities of a simple Github profile search application.

**Project Structure:**

* **git.html:**  This is the main HTML file for the application. It contains the basic HTML structure and links to the external CSS and Javascript files. 
* **git.js:**  This file contains all the Javascript logic for the application. It fetches user data from Github API, displays it in a user card, and lists repositories. 
* **git.css:** This file provides the styling for the application's user interface.

**Detailed Breakdown:**

**1. git.html**

* **DOCTYPE declaration:** Specifies the document type as HTML5.
* **HTML elements:**
    * **Head:**
        * **Meta charset:** Sets the character encoding for the document.
        * **Meta viewport:** Configures the viewport for optimal display on different devices.
        * **Link rel="stylesheet":**  Links the external CSS file `git.css` to style the HTML elements.
        * **Title:** Sets the title of the HTML document, which appears in the browser tab.
    * **Body:**
        * **Form (user-form):**
            * **Input type="text":** Provides a text input field for users to enter a Github username.
        * **Main (id="main"):**  An empty `<main>` element where the user card and repository information will be dynamically displayed.
        * **Script src:** Includes the axios library for making HTTP requests.
        * **Script src:** Includes the `git.js` file containing the Javascript logic.

**2. git.js:**

* **Constants:**
    * **APIURL:**  Defines the base URL for the Github API.
    * **main:**  Selects the `<main>` element from the HTML using the `id` attribute.
    * **form:**  Selects the `<form>` element from the HTML using the `id` attribute.
    * **search:**  Selects the `<input>` element from the HTML using the `id` attribute.
* **getUser(username):**
    * **Asynchronous function:**  Uses `async` to handle asynchronous operations, such as fetching data from the API.
    * **try...catch block:**  Handles potential errors during API requests.
        * **axios(APIURL + username):**  Sends a GET request to the Github API to retrieve user data.
        * **createUserCard(data):**  Calls the function to display the fetched user data in a card.
        * **getRepos(username):**  Calls the function to fetch and display repositories associated with the user.
        * **Error handling:**  If the response status is 404 (not found), displays an error card with a relevant message.
* **getRepos(username):**
    * **Asynchronous function:**  Uses `async` to handle asynchronous operations, such as fetching data from the API.
    * **try...catch block:**  Handles potential errors during API requests.
        * **axios(APIURL + username + '/repos?sort=created'):**  Sends a GET request to the Github API to retrieve the user's repositories.
        * **addReposToCard(data):**  Calls the function to display the fetched repositories in the user card.
        * **Error handling:**  If there is an error fetching repositories, displays an error card.
* **createUserCard(user):**
    * **Creates HTML for the user card:**  
        * Displays the user's avatar, name, bio (if available), location (if available), email (if available), followers count, following count, and public repositories count.
        * Adds an empty `<div>` with `id="repos"` to hold the repository list.
    * **Sets main.innerHTML:**  Inserts the generated HTML into the `<main>` element, replacing any previous content.
* **createErrorCard(msg):**
    * **Creates a simple error card:**  Displays a message indicating an error, for example, when a user profile is not found.
    * **Sets main.innerHTML:**  Inserts the generated HTML into the `<main>` element.
* **addReposToCard(repos):**
    * **Selects the "repos" element:**  Retrieves the `<div>` with `id="repos"` from the user card.
    * **Iterates over repositories:**  Loops through the fetched repositories and creates a link for each repository.
        * **repoEl.href:**  Sets the link to the repository's URL.
        * **repoEl.innerText:**  Sets the link text to the repository name.
        * **Appends repoEl:**  Adds each repository link to the "repos" element.
* **Event listener (form submit):**
    * **Event handling:**  Listens for the submission of the form.
    * **e.preventDefault():**  Prevents the default form submission behavior, which would reload the page.
    * **getUser(user):**  Calls the `getUser` function with the username entered in the search input field.
    * **Clears search input:**  Resets the search input field after submitting the form.

**3. git.css:**

* **General styling:**
    * **Font:** Sets the default font to "Poppins."
    * **Background color:** Sets the body background color to a dark blue.
    * **Color:**  Sets the text color to white.
    * **Display:**  Sets the `flex` properties for the body to center the content.
    * **Overflow:**  Hides the scrollbar.
* **User form styling:**
    * **Width:** Sets the maximum width of the form.
    * **Input:**  Styles the search input field with a dark background, border radius, padding, and box shadow.
* **Card styling:**
    * **Max-width:** Sets the maximum width of the user card.
    * **Background color:**  Sets the background color of the user card.
    * **Border radius:** Rounds the corners of the user card.
    * **Box shadow:**  Adds a box shadow to the user card for a 3D effect.
    * **Display:**  Sets the `flex` properties for the user card.
    * **Padding:**  Adds padding to the user card for spacing around content.
* **Avatar styling:**
    * **Border radius:**  Makes the avatar image circular.
    * **Border:**  Adds a border to the avatar image.
    * **Height and width:**  Sets the height and width of the avatar image.
* **User information styling:**
    * **Color:**  Sets the text color of the user information to light gray.
    * **Margin left:**  Adds margin to the left for spacing between the avatar and information.
    * **h2:**  Styles the user's name.
    * **ul:**  Styles the list of user information (followers, following, repos).
    * **li:**  Styles individual items in the user information list.
* **Repository link styling:**
    * **Text decoration:**  Removes the default underline from the repository links.
    * **Background color:**  Sets the background color of the repository links.
    * **Font size:**  Sets the font size of the repository links.
    * **Padding:**  Adds padding to the repository links.
    * **Margin:**  Adds margin to the repository links for spacing.
    * **Display:**  Sets the display property to `inline-block` to allow horizontal layout of links.

**Responsive Design:**

The CSS includes a media query for screens smaller than 500px. When the screen width is less than 500px, the user card will be displayed vertically instead of horizontally, and the user form will have a reduced maximum width.

**Functionality:**

* The application allows users to search for Github profiles by entering a username in the search input field.
* When the search form is submitted, the application makes an API call to fetch the user's profile information.
* The fetched user data is displayed in a visually appealing card, including the user's avatar, name, bio, location, email, followers count, following count, and public repositories count.
* The application fetches and displays up to 5 of the user's repositories, providing links to each repository on Github.
* Error handling is implemented to display informative messages to the user in cases where a user profile is not found or if there are problems fetching repositories.


**Overall, this project is a basic implementation of a Github profile search application that demonstrates fundamental web development concepts like HTML, CSS, Javascript, API calls, DOM manipulation, and responsive design.** 
