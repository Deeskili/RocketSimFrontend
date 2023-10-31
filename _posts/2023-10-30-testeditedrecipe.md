---
comments: True
layout: post
title: Editedapitest SQLITE
description: Please work!!!
type: Tangibles
courses: {'compsci': {'week': 3}}
categories: ['C4.1']
---


<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Recipe Manager</title>
    <style>
        #recipe-form, #delete-recipe {
            margin-bottom: 20px;
        }

        input[type="text"], textarea {
            width: 100%;
            margin-bottom: 10px;
        }

        button {
            padding: 5px 15px;
            font-size: 16px;
        }
    </style>
</head>
<body>

    <div id="recipe-form">
        <h2>Add Recipe</h2>
        <input type="text" id="title" placeholder="Title">
        <textarea id="ingredients" placeholder="Ingredients"></textarea>
        <textarea id="instructions" placeholder="Instructions"></textarea>
        <button onclick="addRecipe()">Submit</button>
    </div>

    <button onclick="viewRecipes()">View Recipes</button>

    <div id="recipe-list"></div>

    <div id="delete-recipe">
        <h2>Delete Recipe</h2>
        <input type="text" id="delete-id" placeholder="Recipe ID">
        <button onclick="deleteRecipe()">Delete</button>
    </div>

    <script>
        function addRecipe() {
            const title = document.getElementById('title').value;
            const ingredients = document.getElementById('ingredients').value;
            const instructions = document.getElementById('instructions').value;

            fetch('http://127.0.0.1:5000/recipes', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify({
                    title,
                    ingredients,
                    instructions
                })
            });
        }

        function viewRecipes() {
            fetch('http://127.0.0.1:5000/recipes')
                .then(response => response.json())
                .then(data => {
                    const list = document.getElementById('recipe-list');
                    list.innerHTML = "";
                    data.forEach(recipe => {
                        list.innerHTML += `<div>
                            <h3>${recipe.title} (ID: ${recipe.id})</h3>
                            <p>${recipe.ingredients}</p>
                            <p>${recipe.instructions}</p>
                        </div>`;
                    });
                });
        }

        function deleteRecipe() {
            const id = document.getElementById('delete-id').value;

            fetch(`http://127.0.0.1:5000/recipes/${id}`, {
                method: 'DELETE'
            }).then(() => viewRecipes());
        }
    </script>

</body>
</html>
