---
comments: True
layout: notebook
title: Recipe with images test
description: 
type: hacks
courses: {'compsci': {'week': 1}}
categories: ['C4.1']
---


<!DOCTYPE html>
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
            border-radius: 15px; /* Rounded corners */
            padding: 10px;
            margin: 10px;
            background-color: white;
        }
        .recipe-card h2 {
            font-weight: bold;
            color: black; /* Text color */
            font-size: 18px; /* Font size */
            font-family: Arial, sans-serif; /* Font family */
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
    </style>
</head>
<body>
    <div id="recipeList" class="recipe-container">
        <!-- Content will be dynamically generated here -->
    </div>

    <script>
        const recipeList = document.getElementById("recipeList");
        const apiUrl = "https://backendrocketmain.stu.nighthawkcodingsociety.com/api/recipe/recipes";

        // Function to create recipe cards
        function createRecipeCard(recipe) {
            const recipeCard = document.createElement("div");
            recipeCard.classList.add("recipe-card");

            // Recipe title
            const titleElement = document.createElement("h2");
            titleElement.textContent = recipe.title;

            // More Info button
            const moreInfoButton = document.createElement("button");
            moreInfoButton.classList.add("more-info-button");
            moreInfoButton.textContent = "More Info";
            moreInfoButton.addEventListener("click", () => showRecipeDetails(recipe));

            // Append elements to the recipe card
            recipeCard.appendChild(titleElement);
            recipeCard.appendChild(moreInfoButton);

            recipeList.appendChild(recipeCard);
        }

        // Function to show recipe details
        function showRecipeDetails(recipe) {
            const detailsUrl = `recipe_details.html?title=${encodeURIComponent(recipe.title)}&ingredients=${encodeURIComponent(recipe.ingredients)}&steps=${encodeURIComponent(recipe.steps)}`;
            window.location.href = detailsUrl;
        }

        // Fetch data from the API
        fetch(apiUrl)
            .then(response => response.json())
            .then(data => {
                data.forEach(recipe => createRecipeCard(recipe));
            })
            .catch(error => console.error("Error fetching data:", error));
    </script>
</body>
</html>
