---
comments: True
layout: post
title: Add, View or Delete Recipes
description: Our unique database allows you to add, delete and also view your own recipes!
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
        /* Reset some default styles for consistency */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
    body {
    font-family: Arial, sans-serif;
    background-color: #f2f2f2;
    margin: 0;
    padding: 0;
}
/* Header Styles */
header {
    background-color: #333;
    color: #fff;
    text-align: center;
    padding: 20px 0;
    font-size: 24px;
}
/* Recipe Form Styles */
#recipe-form {
    background-color: #fff;
    border: 1px solid #ddd;
    padding: 20px;
    margin: 20px;
    border-radius: 5px;
}
#recipe-form h2 {
    color: #333;
    font-size: 24px;
    margin-bottom: 15px;
}
input[type="text"], textarea {
    width: 100%;
    padding: 10px;
    margin-bottom: 15px;
    border: 1px solid #ccc;
    border-radius: 5px;
}
button {
    background-color: #333;
    color: #fff;
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    font-size: 18px;
    cursor: pointer;
}
button:hover {
    background-color: #555;
}
/* View Recipes Button Styles */
button#view-recipes {
    background-color: #4285f4;
    color: #fff;
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    font-size: 18px;
    cursor: pointer;
}
button#view-recipes:hover {
    background-color: #2b4b91;
}
/* Recipe List Styles */
#recipe-list {
    background-color: #fff;
    border: 1px solid #ddd;
    padding: 20px;
    margin: 20px;
    border-radius: 5px;
}
#recipe-list div {
    border: 1px solid #ccc;
    border-radius: 5px;
    padding: 15px;
    margin-bottom: 15px;
}
#recipe-list h3 {
    color: #333;
    font-size: 20px;
}
/* Delete Recipe Styles */
#delete-recipe {
    background-color: #fff;
    border: 1px solid #ddd;
    padding: 20px;
    margin: 20px;
    border-radius: 5px;
}
#delete-recipe h2 {
    color: #333;
    font-size: 24px;
    margin-bottom: 15px;
}
#delete-id {
    width: 100%;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
}
/* Unique Styles */
h2 {
    background-color: #4285f4;
    color: #fff;
    padding: 10px 0;
    font-size: 22px;
    border-radius: 5px 5px 0 0;
}
p {
    font-size: 16px;
    line-height: 1.4;
}
/* Responsive Design */
@media (max-width: 768px) {
    #recipe-form, #recipe-list, #delete-recipe {
        margin: 10px;
        padding: 10px;
    }
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
