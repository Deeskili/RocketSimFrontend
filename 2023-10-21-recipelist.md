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
    <div class="search-container">
    <input type="text" id="searchInput" placeholder="Search for recipes here">
    <button id="searchButton">Search</button>
</div>
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
        .recipe-card img {
            width: 100%;
            max-height: 200px;
            object-fit: cover;
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
            width: 300px; /* Adjust the width as needed */
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
    <div id="recipeList" class="recipe-container">
        <!-- Content will be dynamically generated here -->
    </div>

    <script>
    document.addEventListener("DOMContentLoaded", () => {
        const recipeList = document.getElementById("recipeList");
        const apiUrl = "https://backendrocketmain.stu.nighthawkcodingsociety.com/api/recipe/recipes";

        // Add event listener for the search button
        const searchButton = document.getElementById("searchButton");
        searchButton.addEventListener("click", performSearch);

        // Function to create the recipe details page
        function createRecipeDetailsPage(recipe) {
            // Redirect to the recipe details page when the button is clicked
            window.location.href = `https://deeskili.github.io/RocketSimFrontend/c4.1/2023/10/21/recipedetails.html?recipeId=${recipe.id}`;
        }

        // Fetch data from the API for all recipes
        fetch(apiUrl)
            .then(response => {
                if (!response.ok) {
                    throw new Error(`Network response was not ok: ${response.status}`);
                }
                return response.json();
            })
            .then(data => {
                // Store the data in a variable for filtering
                let recipesData = data;

                // Generate recipe cards for each recipe
                data.forEach(recipe => {
                    const recipeCard = createRecipeCard(recipe);
                    recipeList.appendChild(recipeCard);
                });

                // Function to create a recipe card
                function createRecipeCard(recipe) {
                    const recipeCard = document.createElement("div");
                    recipeCard.classList.add("recipe-card");

                    // Display image (you may need to adjust this)
                    const imgElement = document.createElement("img");
                    imgElement.src = findMatchingImageFilename(recipe.title);
                    recipeCard.appendChild(imgElement);

                    // Display recipe title
                    const titleElement = document.createElement("div");
                    titleElement.classList.add("recipe-title");
                    titleElement.textContent = recipe.title;
                    recipeCard.appendChild(titleElement);

                    // More info button
                    const moreInfoButton = document.createElement("button");
                    moreInfoButton.classList.add("more-info-button");
                    moreInfoButton.textContent = "More Info";

                    // Add an event listener to the "More Info" button
                    moreInfoButton.addEventListener("click", () => {
                        createRecipeDetailsPage(recipe);
                    });

                    recipeCard.appendChild(moreInfoButton);
                    return recipeCard;
                }

                // Function to filter recipes based on search input
                function performSearch() {
                    const searchInput = document.getElementById("searchInput").value.toLowerCase();
                    const filteredRecipes = recipesData.filter(recipe => recipe.title.toLowerCase().includes(searchInput));

                    // Clear the recipe list
                    recipeList.innerHTML = "";

                    // Generate recipe cards for filtered recipes
                    filteredRecipes.forEach(recipe => {
                        const recipeCard = createRecipeCard(recipe);
                        recipeList.appendChild(recipeCard);
                    });
                }
            })
            .catch(error => {
                console.error("There was a problem fetching the data:", error);
            });
    });
</script>
</body>
</html>