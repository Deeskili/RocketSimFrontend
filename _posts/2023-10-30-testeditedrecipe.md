---
comments: True
layout: post
title: Editedapitest SQLITE
description: 
type: plans
courses: {'compsci': {'week': 3}}
categories: ['C4.1']
---


<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Recipe Manager</title>
    <style>
        /* Add some basic styling */
        .container {
            max-width: 600px;
            margin: auto;
        }
    </style>
</head>
<body>

    <div class="container">
        <h1>Recipe Manager</h1>

        <!-- Form to Add a Recipe -->
        <form id="addRecipeForm">
            <h2>Add a Recipe</h2>
            <label for="title">Title:</label>
            <input type="text" id="title" name="title" required>
            <label for="ingredients">Ingredients:</label>
            <textarea id="ingredients" name="ingredients" required></textarea>
            <label for="instructions">Instructions:</label>
            <textarea id="instructions" name="instructions"></textarea>
            <button type="submit">Add Recipe</button>
        </form>

        <!-- Display Recipes -->
        <div id="recipes">
            <h2>Recipes</h2>
        </div>
    </div>

    <script>
        document.getElementById('addRecipeForm').addEventListener('submit', function (e) {
            e.preventDefault();

            const title = document.getElementById('title').value;
            const ingredients = document.getElementById('ingredients').value;
            const instructions = document.getElementById('instructions').value;

            fetch('http://127.0.0.1:5000/recipes', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json',
                },
                body: JSON.stringify({
                    title,
                    ingredients,
                    instructions,
                }),
            })
            .then(response => response.json())
            .then(data => {
                console.log('Success:', data);
                loadRecipes();
            })
            .catch((error) => {
                console.error('Error:', error);
            });
        });

        function loadRecipes() {
            fetch('http://127.0.0.1:5000/recipes')
                .then(response => response.json())
                .then(data => {
                    displayRecipes(data);
                })
                .catch((error) => {
                    console.error('Error:', error);
                });
        }

        function displayRecipes(recipes) {
            const recipesContainer = document.getElementById('recipes');
            recipesContainer.innerHTML = '<h2>Recipes</h2>'; // Reset

            recipes.forEach(recipe => {
                const div = document.createElement('div');
                div.innerHTML = `
                    <h3>${recipe.title}</h3>
                    <p>Ingredients: ${recipe.ingredients}</p>
                    <p>Instructions: ${recipe.instructions}</p>
                    <button onclick="deleteRecipe(${recipe.id})">Delete</button>
                `;
                recipesContainer.appendChild(div);
            });
        }

        function deleteRecipe(id) {
            fetch(`http://127.0.0.1:5000/recipes/${id}`, {
                method: 'DELETE',
            })
            .then(response => {
                if (response.status === 204) {
                    loadRecipes();
                }
            })
            .catch((error) => {
                console.error('Error:', error);
            });
        }

        // Load recipes when the page loads
        loadRecipes();
    </script>

</body>
</html>
