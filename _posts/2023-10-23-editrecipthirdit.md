---
comments: True
layout: notebook
title: Third Iteration Edited Recipe
description: 
type: hacks
courses: {'compsci': {'week': 1}}
categories: ['C4.1']
---


<html>
<head>
    <title>Recipe Manager</title>
</head>
<body>
    <h1>Add a Recipe</h1>
    <form id="add-recipe-form">
        <label for="recipe-name">Recipe Title:</label>
        <input type="text" id="recipe-name" required>
        
        <label for="recipe-ingredients">Ingredients:</label>
        <textarea id="recipe-ingredients" required></textarea>
        
        <label for="recipe-instructions">Instructions:</label>
        <textarea id="recipe-instructions" required></textarea>
        
        <button type="submit">Add Recipe</button>
    </form>

    <h1>Recipes</h1>
    <div id="recipe-list"></div>

    <script>
        // Function to fetch and display recipes
        function fetchRecipes() {
            fetch('http://localhost:5000/recipes')
                .then(response => response.json())
                .then(data => {
                    const recipeList = document.getElementById('recipe-list');
                    recipeList.innerHTML = '';

                    data.forEach(recipe => {
                        const recipeDiv = document.createElement('div');
                        recipeDiv.innerHTML = `
                            <h2>${recipe.name}</h2>
                            <p><strong>Ingredients:</strong> ${recipe.ingredients}</p>
                            <p><strong>Instructions:</strong> ${recipe.instructions}</p>
                        `;
                        recipeList.appendChild(recipeDiv);
                    });
                })
                .catch(error => {
                    console.error('Error fetching recipes:', error);
                });
        }

        // Function to add a recipe
        document.getElementById('add-recipe-form').addEventListener('submit', function (event) {
            event.preventDefault();

            const name = document.getElementById('recipe-name').value;
            const ingredients = document.getElementById('recipe-ingredients').value;
            const instructions = document.getElementById('recipe-instructions').value;

            const newRecipe = {
                name: name,
                ingredients: ingredients,
                instructions: instructions,
            };

            fetch('http://localhost:5000/recipes', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json',
                },
                body: JSON.stringify(newRecipe),
            })
                .then(response => {
                    if (response.status === 201) {
                        // Recipe added successfully, clear form and update recipe list
                        document.getElementById('add-recipe-form').reset();
                        fetchRecipes();
                    } else {
                        // Handle errors (e.g., validation errors)
                        console.error('Recipe not added. Check the data provided.');
                    }
                })
                .catch(error => {
                    console.error('Error adding a recipe:', error);
                });
        });

        // Fetch and display recipes when the page loads
        fetchRecipes();
    </script>
</body>
</html>
