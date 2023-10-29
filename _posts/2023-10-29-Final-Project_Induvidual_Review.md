---
comments: True
layout: post
title: Induvidual Review Sri S
description: Recap of key events and learnings
type: tangibles
courses: {'compsci': {'week': 3}}
categories: ['C4.1']
---

<h3>Overview of Final Project</h3>
 
Our final project is a recipe manager book that extracts details from a backend API and outputs results in the frontend webpage. There are over 4000 recipes in the backend server whcih the code extracts and displays as recipe cards from which the user can search and choose any particular recipe of their liking. As I was working with the frontend side of the project, I'll be recaping my entire journey up until this point of project completion.

<h3>Project Planning</h3>

Week 0 started of with us planning you recipe manager site. Our original goal was a rocket simulator but we then switched up to a recipe manager owing to the difficulties of making and running a rocket simulator. Week 0's main goal for the frontend team was planning out and exicuting the frontedn home page, which we first planned out in figma and developed a code based on that. Our goal was to make a parralax effect for scrolling which we felt would be pretty cool to scroll through.

<h3>Link to Fimga Animation</h3>

[Link to Fima Animation](https://www.figma.com/proto/3nvtE8kJLdDL6zx4ho8bp8/Recipe-Book-Manager?node-id=23-30&starting-point-node-id=23%3A30
)

<h3>Continuation of making the frontend homepage</h3>

We understood that extracting code from figma would be an impossible task and thus we taught ourselved with the help of W3 schools. This parrallax animation contains images as the background with text in the front and when the user scrolls down it give an effec tof the image going down with the as well.

<h3>Code Samples</h3>
Each of our background images was defined and displayed with the .bgimg-x funtion withe its url own below. the images we then divided into division and their identifiers were called apon with HTML and text was inserted with text boxes as well and paragraphs.


```python
 }
        .bgimg-2 {
            background-image: url("https://images.unsplash.com/photo-1534604973900-c43ab4c2e0ab?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2888&q=80");
            min-height: 400px;
        }


</div>
    <div class="bgimg-2">
        <div class="caption">
            <span class="border">Create Recipes!</span>
        </div>
    </div>
    <div style="color: #777;background-color:white;text-align:center;padding:50px 80px;text-align: justify;">
        <h3>Create recipes!</h3>
        <p>Create new recipes for you to store and access anytime in the future</p>
    </div>
```

<h3>Link to Home page</h3>
[Homepage](https://deeskili.github.io/RocketSimFrontend/)

Thus as you can see the code above, the parralax effect work and the scrolling down the user can see the images also seem to move along with the cursor and it moves through the text. This was a pretty cool effect that we worked on using HTML and CSS.

<h3>Overview of Backend to Frontend Data Pull</h3>
The backend servers were created by Saathvik of the backend team. The servers include a URL link that contains over 4000 recipes to search for and find, these recipes also have recipe details such as instruciton as to how the recipe can be recreated as well as the ingredients required to make the dish. We used two API overall, both belonging to the same recipes but on with the entirely of all the recipes and the other which is ID linked where one can change the id of the url of have a new recipe. Both of these URL API are used to make this recipe manager search work.

<h3>Recipe List</h3>
The recipe list page is our main work. This page contains all the 4000+ recipes inside recipe card. These cards are formtatted previously and all the data within them is dynamically generated. The CSS and HTML for the card acts as a templete onto which all the recipes are extracted from and displayed on. The HTML and CSS element is then linked with the JS elemnt down below which then extracts data from the URL API and outputs them into the recipes own card.


```python
.recipe-card {
            flex: 0 0 calc(33.33% - 20px);
            box-sizing: border-box;
            border: 1px solid #ccc;
            border-radius: 15px;
            padding: 10px;
            margin: 10px;
            background-color: white;
        }
        .recipe-title {
            font-weight: bold;
            margin-top: 10px;
            color: black;
            font-size: 18px;
            font-family: Arial, sans-serif;
        }
        .more-info-button {
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 5px;
            padding: 10px 20px;
            cursor: pointer;
            font-size: 16px;
            margin-top: 10px;
        }
```


```python
const recipeCard = document.createElement("div");
                recipeCard.classList.add("recipe-card");

const titleElement = document.createElement("div");
titleElement.classList.add("recipe-title");
                titleElement.textContent = recipe.title;
                recipeCard.appendChild(titleElement);

const moreInfoButton = document.createElement("button");
 moreInfoButton.classList.add("more-info-button");
                moreInfoButton.textContent = "More Info";
                moreInfoButton.addEventListener("click", () => {
```

<h3>Code Segments</h3>
Each recipe card is formatted with the HTML and CSS elements up above. These recipes then display information from the API URL after extraction through the JS elements down below. Each chnaracteristic of the API such as the title, instuctions, images and the detials are all characterized and pull from API as elements whcih I'll come back to in a second. Each recipe card displays the title of the recipe and the more info button whcih links the user to a recipe details page from which more details about the recipe are displayed.

<h3>Data Extraction</h3>

The basic command to extract data from the backend server since this is a URL API would be through definingh the apiUrl and then using the fetch commands by defining the variables to be extracted. IN this code the recipe title, the ingredients, the steps are all assigned to be elements, and each of that data is extracted through defining the element name and with previous HTML and CSS templete formatting the data is formatted and outputted.

The recipe list and the recipe details are connected through a commited link of the details page. This was somehting that took me time to figure out and after commited the details page, the linkage between the two was really easy. The code are displayed below.


```python
 document.addEventListener("DOMContentLoaded", () => { // the event listener in this case for this code would basicallly be the loading of the page and thus the function "DOMContentLoaded" is used as the event listener
            const recipeList = document.getElementById("recipeList"); 

 // Redirect to the recipe details page when the button is clicked
                window.location.href = `https://deeskili.github.io/RocketSimFrontend/c4.1/2023/10/21/recipedetails.html?recipeId=${recipe.id}`;

const apiUrl = "https://backendrocketmain.stu.nighthawkcodingsociety.com/api/recipe/recipes";

data.forEach(recipe => {
                            const recipeCard = createRecipeCard(recipe);

```

<h3>Search Input</h3>

I then added a search input to the overall recipe search cards. The search input allows the user to search through the recipe card by inputting any work and letter which searches acroos the 4000+ recipe card for similarities and outputs the resulting cards. The code for this search bar is pretty simple, the CSS and HTMl elment for the look of the seach bar, the recipes are fileterd through the function performSearch () key. Then the recipe card are sorted by name and through the recipeCard.querySelector("Recipe-title") function the outputs are porvided



```python
function performSearch() { // function is labelled as a performSearch

const searchTerm = searchInput.value.trim().toLowerCase(); // the input value is linked to the bar formatted above
                const recipeCards = recipeList.getElementsByClassName("recipe-card");

Array.from(recipeCards).forEach(recipeCard => {
                    const titleElement = recipeCard.querySelector(".recipe-title");
                    const title = titleElement.textContent.toLowerCase();




if (title.includes(searchTerm)) {
                        recipeCard.style.display = "block"; // shows the recipe card by blocking it from all teh others and outputting it as the only value
                    } else {
                        recipeCard.style.display = "none"; // hides all the recipe cards if the input does not match any, an if else fucntion is used to compare both values as you can see above.
                    }
                });
            }
```

<h3>Recipe Details Page</h3>

As I specified above, the recipe details page is the one linked above with the commited link. The commited details page acts as a tempplate and with the {recipeID} input, when the more info button of the recipe card is clicked the URL is change and the data from the 2nd API is extracted. Since all the details about the recipe is formatted and extracted as elements, the ingredients and the step as well as the titles are extracted as elements from the API


```python
 // Fetch the recipe details based on the recipeId from the API
            fetch(`https://backendrocketmain.stu.nighthawkcodingsociety.com/api/recipe/recipedetails?id=${recipeId}`)

const titleElement = document.getElementById("recipe-title");
const instructionsElement = document.getElementById("recipe-instructions")
const ingredientsElement = document.getElementById("recipe-ingredients")
```

<h3>Trimming</h3>

The recipe details and the recipe instruction all are extracted in a bluck of a paragraph. With the help of a little HTML and JS elements, these can be seperated to make the page look more organized and better to read with teh ingredients and the instructions in the from of a list (ordered and ordered)


```python
const ingredients = recipe.cleaned_ingredients.split(',');
                    ingredients.forEach(ingredient => {
                        if (ingredient.trim() !== '') {
                            const listItem = document.createElement("li");
                            listItem.textContent = ingredient.trim();
                            ingredientsElement.appendChild(listItem);


const instructions = recipe.instructions.split('.');
                    instructions.forEach(instruction => {
                        if (instruction.trim() !== '') {
                            const listItem = document.createElement("li"); // goes up to the html code written above "li"
                            listItem.textContent = instruction.trim();
                            instructionsElement.appendChild(listItem);
                        }
```

<h3>Issues & Fixes</h3>

- The first issue we faced was trying to copy the code from the figma design into vscode, but we then realized that that was not going to be possible as figma is just a site that helps create stuff and outline stuff and not for code. & thus as outlined above with the help of w3 school we built of webpage as it is today.



```python
Issue #1

.bgimg-4 {
            background-image: url("https://plus.unsplash.com/premium_photo-1695822018668-72355fc4ee7c?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1pYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto.format&fit=crop&w=3024&q=80");
            min-height: 400px;
<div class="bgimg-4">
        <div class="caption">
            <span class="border">View Recipes!</span>
        </div>
    </div>
    <div style="color: #777;background-color:white;text-align:center;padding:50px 80px;text-align: justify;">
        <h3>View Recipes!</h3>
        <p>Have a bad memory? No worries, you can always access them anytime your want to!!</p>
    </div>


```

- The second issue we faced was trying to extract data from the backend API URL into the frontend website. With a little help from ChatGPT we fixed the issue with the cont apiUrl function as well as the element fetch solution provided by the AI tool.



```python
Issue 2
function fetchAndDisplayRecipes() {
                const apiUrl = "https://backendrocketmain.stu.nighthawkcodingsociety.com/api/recipe/recipes";
```

- The third issue we faced was linking the recipe details and the recipe list pages or in API tems linking the first and second API and displaying the correct data for the correct recipe all the while the entire website is API controlled

- We fixed this error by first commiting the recipe details page and copying that link into the recipe list page. This helped link both pages together no matter if it was a localhost or a commited site. with the {recipeID} fucntion, the code could dynamically generate the correct ID and display the correct recipe by details.



```python
Issue 3
function createRecipeDetailsPage(recipe) {
     window.location.href = `https://deeskili.github.io/RocketSimFrontend/c4.1/2023/10/21/recipedetails.html?recipeId=${recipe.id}`;
```

- The fourth issue we faced was making a search bar for the recipe list page. Making the bar was an easy task with CSS but then linking the CSS to the JS and making the site work was something we had to ponder ourslelves over. We finally fixed this issue by using the recipeCard.querySelector fucntion which enables us to short list each the recipe card by name.



```python
Issue 4
 Array.from(recipeCards).forEach(recipeCard => {
                    const titleElement = recipeCard.querySelector(".recipe-title");
                    const title = titleElement.textContent.toLowerCase();


```

- The fifth and only unresolved issue was with our images. Our images are downlaoded into the images/Food Images file. Our main issue with these image is with linking them onto the wbesite. No matter what we try they dont seem to come into the site Our trial fixes included

    - Trying to link the images through the API itself
    - Trying to link the image using an external API
    - Trying to link the image by librares from google
    - Trying to use another API to link the images 

- No matter what we did the images dont seem to link into the website and thus our main goal before NATM would be to try and link the images in any way possible.

<h3>Event Listeners</h3>

For each API fetch event listeners we used, these listeners as the name suggest listen to the user and after the spicific "event" occus like a click or enter the code operates and runs what it's supposed to do.

1. Recipe List: Two event listeners were used in this page, one to load all the recipe card, and the other for the search bar input.
2. Recipe Details: Event listener to load the recipe details.


```python
Event Listener #1
document.addEventListener("DOMContentLoaded", () => {

Event Listener #2
 searchInput.addEventListener("input", performSearch);

Event Listener #3
 document.addEventListener("DOMContentLoaded", () =>
```

<h3>Plans for NATM week</h3>

1. Our main goal for NATM week as mentioned above is to fix the images error. We plan to use an external API for only images to try and display a few with the recipes. With the help of Mr. Mortensen and Mr. Lopez we hope to link these images into the wbesite some way or the other as without images the website looks really bland

2. Our second goal before NATM is to reformat the site, remove stuff and add stuff to make it more like our own webiste and not just like that of a forked website from the teach.

3. If our qualification remains our hope is to contiue working to better the site and give an overall good presentation at night at the museum!
