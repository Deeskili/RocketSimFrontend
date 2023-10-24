---
comments: True
layout: notebook
title: Second Iteration Edited Recipe
description: 
type: hacks
courses: {'compsci': {'week': 1}}
categories: ['C4.1']
---


<html>
<head>
    <title>Recipe List</title>
</head>
<body>
    <h1>Add a Recipe</h1>
    <form id="recipeForm">
        <label for="title">Title:</label>
        <input type="text" id="title" name="title" required><br><br>

        <label for="recipe">Recipe:</label>
        <textarea id="recipe" name="recipe" required></textarea><br><br>

        <input type="submit" value="Submit">
    </form>

    <h1>Recipe List</h1>
    <div id="recipeList">
        <!-- Content will be dynamically generated here -->
    </div>

    <button id="fetchRecipes">Fetch Recipes</button>

    <script>
        const recipeForm = document.getElementById("recipeForm");
        const recipeList = document.getElementById("recipeList");
        const fetchRecipesButton = document.getElementById("fetchRecipes");

        const apiUrl = "https://backendrocketmain.stu.nighthawkcodingsociety.com/api/edited_recipe";

        // Function to create the recipe details page
        function createRecipeDetailsPage(recipe) {
            // Redirect to the recipe details page when the button is clicked
            window.location.href = `https://deeskili.github.io/RocketSimFrontend/c4.1/2023/10/21/recipedetails.html?recipeId=${recipe.id}`;
        }

        // Function to fetch and display all recipes
        function fetchRecipes() {
            fetch(apiUrl)
                .then(response => {
                    if (!response.ok) {
                        throw new Error(`Network response was not ok: ${response.status}`);
                    }
                    return response.json();
                })
                .then(data => {
                    recipeList.innerHTML = ""; // Clear existing content
                    data.forEach(recipe => {
                        const recipeCard = document.createElement("div");
                        recipeCard.textContent = `${recipe.title}: ${recipe.recipe}`;
                        recipeList.appendChild(recipeCard);
                    });
                })
                .catch(error => {
                    console.error("There was a problem fetching the data:", error);
                });
        }

        // Add an event listener to the "Submit" button
        recipeForm.addEventListener("submit", event => {
            event.preventDefault();
            const title = document.getElementById("title").value;
            const recipe = document.getElementById("recipe").value;

            if (title && recipe) {
                const data = { title, recipe };

                fetch("https://backendrocketmain.stu.nighthawkcodingsociety.com/api/edited_recipe/add_recipe", {
                    method: "POST",
                    headers: {
                        "Content-Type": "application/json"
                    },
                    body: JSON.stringify(data)
                })
                .then(response => {
                    if (!response.ok) {
                        throw new Error(`Network response was not ok: ${response.status}`);
                    }
                    return response.json();
                })
                .then(() => {
                    // After successfully adding the recipe, fetch and display all recipes
                    fetchRecipes();
                })
                .catch(error => {
                    console.error("There was a problem adding the recipe:", error);
                });
            }
        });

        // Add an event listener to the "Fetch Recipes" button
        fetchRecipesButton.addEventListener("click", fetchRecipes);
    </script>
</body>
</html>
