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

</head>

    <style>
    /* Reset some default styles for consistency */
    * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
    }

    body {
        font-family: 'Poppins', sans-serif;
        background-color: #f7f7f7;
        margin: 0;
        padding: 0;
    }
   
    /* Recipe Form Styles */
    #recipe-form {
        background-color: #fff;
        border: 1px solid #6497b1;
        padding: 20px;
        margin: 20px;
        border-radius: 10px;
        box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
    }

    #recipe-form h2 {
        color: #355070;
        font-size: 24px;
        margin-bottom: 20px;
    }

    input[type="text"], textarea {
        width: 100%;
        padding: 10px;
        margin-bottom: 20px;
        border: 1px solid #ccc;
        border-radius: 10px;
        font-family: 'Poppins', sans-serif;
        font-size: 16px;
    }

    input[type="text"] {
        background-color: #f5f5f5;
    }

    textarea {
        background-color: #f8f8f8;
    }

    button {
        background-color: #6497b1;
        color: #fff;
        padding: 12px 25px;
        border: none;
        border-radius: 10px;
        font-size: 18px;
        cursor: pointer;
        transition: background-color 0.3s;
    }

    button:hover {
        background-color: #355070;
    }

    /* View Recipes Button Styles */
    button#view-recipes {
    background-color: #355070;
    color: #000; /* Updated to black */
    padding: 12px 25px;
    border: none;
    border-radius: 10px;
    font-size: 18px;
    cursor: pointer;
    transition: background-color 0.3s;
    }

    button#view-recipes:hover {
    background-color: #6497b1;
    color: #000; /* Updated to black */
    }


    /* Recipe List Styles */
    #recipe-list {
        background-color: #fff;
        border: 1px solid #6497b1;
        padding: 20px;
        margin: 20px;
        border-radius: 10px;
        box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
    }

    #recipe-list div {
        border: 1px solid #ccc;
        border-radius: 10px;
        padding: 20px;
        margin-bottom: 20px;
    }

    #recipe-list h3 {
    color: #000; /* Updated to black */
    font-size: 24px;
}


    /* Delete Recipe Styles */
    #delete-recipe {
        background-color: #fff;
        border: 1px solid #6497b1;
        padding: 20px;
        margin: 20px;
        border-radius: 10px;
        box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
    }

    #delete-recipe h2 {
        color: #355070;
        font-size: 24px;
        margin-bottom: 20px;
    }

    #delete-id {
        width: 100%;
        padding: 10px;
        border: 1px solid #ccc;
        border-radius: 10px;
        font-family: 'Poppins', sans-serif;
        font-size: 16px;
    }

    /* Unique Styles */
    h2 {
        background-color: #6497b1;
        color: #fff;
        padding: 15px 0;
        font-size: 32px;
        border-radius: 10px 10px 0 0;
        text-align: center;
    }

    p {
        font-size: 18px;
        line-height: 1.5;
    }

    /* Responsive Design */
    @media (max-width: 768px) {
        #recipe-form, #recipe-list, #delete-recipe {
            margin: 10px;
            padding: 10px;
        }
    }
</style>


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
