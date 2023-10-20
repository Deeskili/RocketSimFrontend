---
comments: True
layout: notebook
title: Edited Recipe Fetch Test 
description: 
type: hacks
courses: {'compsci': {'week': 1}}
categories: ['C4.1']
---
<html>
<head>
    <title>View Recipes</title>
</head>
<body>
    <h1>View Recipes</h1>

    <!-- Add a button to fetch and display recipes -->
    <button onclick="fetchRecipes()">Fetch Recipes</button>

    <!-- Add a container to display recipes -->
    <div id="recipeContainer"></div>

    <script>
        function fetchRecipes() {
            // Send a request to the backend to fetch recipes
            fetch('/api/editedrecipe/recipes')  // Specify the correct Flask API endpoint
                .then(response => response.json())
                .then(data => {
                    const recipeContainer = document.getElementById('recipeContainer');
                    recipeContainer.innerHTML = ''; // Clear the container
                    data.forEach(recipe => {
                        const recipeDiv = document.createElement('div');
                        recipeDiv.innerHTML = `<h2>${recipe.title}</h2><p>${recipe.ingredients}</p>`;
                        recipeContainer.appendChild(recipeDiv);
                    });
                })
                .catch(error => console.error('Error fetching recipes:', error));
        }
    </script>
</body>
</html>