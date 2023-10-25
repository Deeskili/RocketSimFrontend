---
comments: True
layout: notebook
title: Recipe Search
description: 
type: hacks
courses: {'compsci': {'week': 1}}
categories: ['C4.1']
---

<html>
<head>
    <title>Recipe List</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f2f2f2;
            margin: 0;
            padding: 0;
        }
        .recipe-container {
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
            margin: 10px;
        }
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
        .more-info-button:hover {
            background-color: #45a049;
        }
        .search-container {
            display: flex;
            justify-content: center;
            align-items: center;
            margin: 20px;
        }
        #searchInput {
            padding: 10px;
            width: 300px;
            border: 2px solid #ccc;
            border-radius: 5px;
            font-size: 16px;
        }
        #searchButton {
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 5px;
            padding: 10px 20px;
            cursor: pointer;
            font-size: 16px;
            margin-left: 10px;
        }
        #searchButton:hover {
            background-color: #45a049;
        }
    </style>
</head>
<body>
    <div class="search-container">
        <input type="text" id="searchInput" placeholder="Search for recipes...">
        <button id="searchButton">Search</button>
    </div>

    <div id="recipeList" class="recipe-container">
        <!-- Content will be dynamically generated here -->
    </div>

    <script>
        document.addEventListener("DOMContentLoaded", () => { // the event listener in this case for this code would basicallly be the loading of the page and thus the function "DOMContentLoaded" is used as the event listener
            const recipeList = document.getElementById("recipeList");  // data is being fetched from the backend servers through elements id's which are also used to fetch all sorts of data from API, these charectorizations help organize the code more evenly
            const searchInput = document.getElementById("searchInput"); // the element her for example is for the search bar which searches across recipe cards.

            // Function to create the recipe details page
            function createRecipeDetailsPage(recipe) {
                // Redirect to the recipe details page when the button is clicked
                window.location.href = `https://deeskili.github.io/RocketSimFrontend/c4.1/2023/10/21/recipedetails.html?recipeId=${recipe.id}`; // this is the commited site for the recipe details page. What this does its that it acts as a sort of linker between the main recipe lists and the recipe details page.
                    // with the "{recipe.id}" the recipe id is extract from the 2nd API and outputed into the url

            }

            // Function to fetch and display the recipes from the API
            function fetchAndDisplayRecipes() {
                const apiUrl = "https://backendrocketmain.stu.nighthawkcodingsociety.com/api/recipe/recipes";
                // this is our main API from which all the recipe cards are formatted. 
                // This is one of the two major API that we will be using for our NATM projec , the first is our main API conatining all the recipes, the second the same API but this time fromatted with the API ID, recipe 1 has the ID of 1 and so on....
                fetch(apiUrl)
                    .then(response => {
                        if (!response.ok) {
                            throw new Error(`Network response was not ok: ${response.status}`);
                        }
                        return response.json();
                    })
                    .then(data => {
                        // Generate recipe cards for each recipe
                        // Generate recipe cards for each recipe. Each of the 4000+ recipes have their own recipe cards as formatted above with the css code
                        data.forEach(recipe => {
                            const recipeCard = createRecipeCard(recipe); // creates a recipe card for each of the recipe title extracted and links to each div section and thus the term "dynamically generated cards".
                            recipeList.appendChild(recipeCard);
                        });
                    })
                    .catch(error => {
                        console.error("There was a problem fetching the data:", error); // for corrupted data the program outputs a 404 error notification
                    });
            }

            // Function to create a recipe card
            // Function to create a recipe card. Each recipe has its induvidual recipe card, each card is the data fetched from the API URL customixed with the title and more info button realting to that recipe specifically.
            function createRecipeCard(recipe) {
                const recipeCard = document.createElement("div");
                recipeCard.classList.add("recipe-card");

                // Display recipe title
                const titleElement = document.createElement("div"); // as mentioned above each recipe is fetch from teh database through the induvidual "getrecipebyID" code. The first element fetched here is the title, subbed into the titleElement
                titleElement.classList.add("recipe-title");
                titleElement.textContent = recipe.title;
                recipeCard.appendChild(titleElement);

                // More info button
                const moreInfoButton = document.createElement("button"); // The more info button is the second element, not extrasct from the API but a linker to the API.
                moreInfoButton.classList.add("more-info-button");
                moreInfoButton.textContent = "More Info";
                moreInfoButton.addEventListener("click", () => { // Event listeners listen to a call from the user, link a click or the enter bar. Here the event listener for the more info button is clicking on the button defined by the "click".
                    createRecipeDetailsPage(recipe);
                });
                recipeCard.appendChild(moreInfoButton);
                return recipeCard;
            }

             // Function to filter recipes based on search input. We also create a search bar which helps to sort our the different recipe cards.
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

            // Add event listener for the search input
            searchInput.addEventListener("input", performSearch);
            // Again another event listener is used to link the two sites, here the event listener is for the search and the event listener input is basically any input from the user realating ot the recipe name.

            // Fetch and display recipes when the page loads
            fetchAndDisplayRecipes();
        });
    </script>
</body>
</html>
