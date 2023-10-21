---
comments: True
layout: notebook
title: Recipe details
description: 
type: hacks
courses: {'compsci': {'week': 1}}
categories: ['C4.1']
---


<!DOCTYPE html>
<html>
<head>
    <title>Recipe Details</title>
</head>
<body>
    <h1 id="recipe-title"></h1>
    <h2>Ingredients</h2>
    <ul id="recipe-ingredients"></ul>
    <h2>Instructions</h2>
    <ol id="recipe-instructions"></ol>

    <script>
        document.addEventListener("DOMContentLoaded", () => {
            // Get the recipeId from the URL
            const urlParams = new URLSearchParams(window.location.search);
            const recipeId = urlParams.get("recipeId");

            // Fetch the recipe details based on the recipeId from the API
            fetch(`https://backendrocketmain.stu.nighthawkcodingsociety.com/api/recipe/recipedetails?id=${recipeId}`)
                .then(response => {
                    if (!response.ok) {
                        throw new Error(`Network response was not ok: ${response.status}`);
                    }
                    return response.json();
                })
                .then(recipe => {
                    // Display recipe details on the page
                    const titleElement = document.getElementById("recipe-title");
                    const ingredientsElement = document.getElementById("recipe-ingredients");
                    const instructionsElement = document.getElementById("recipe-instructions");

                    titleElement.textContent = recipe.title;

                    // Split ingredients by commas and create a bulleted list
                    const ingredients = recipe.cleaned_ingredients.split(',');
                    ingredients.forEach(ingredient => {
                        if (ingredient.trim() !== '') {
                            const listItem = document.createElement("li");
                            listItem.textContent = ingredient.trim();
                            ingredientsElement.appendChild(listItem);
                        }
                    });

                    // Split instructions by periods and create a numbered list
                    const instructions = recipe.instructions.split('.');
                    instructions.forEach(instruction => {
                        if (instruction.trim() !== '') {
                            const listItem = document.createElement("li");
                            listItem.textContent = instruction.trim();
                            instructionsElement.appendChild(listItem);
                        }
                    });
                })
                .catch(error => {
                    console.error("There was a problem fetching the recipe details:", error);
                });
        });
    </script>
</body>
</html>
