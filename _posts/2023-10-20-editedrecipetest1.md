---
comments: True
layout: notebook
title: Edited Recipe Storage Test 
description: 
type: hacks
courses: {'compsci': {'week': 1}}
categories: ['C4.1']
---

<html>
<head>
    <title>Recipe Input</title>
</head>
<body>
    <h1>Enter Recipe</h1>
    <form>
        <label for="recipeName">Recipe Title:</label>
        <input type="text" id="recipeName" name="recipeName"><br>

        <label for="recipeText">Recipe:</label>
        <textarea id="recipeText" name="recipeText" rows="10" cols="40"></textarea><br>

        <button onclick="submitRecipe()">Submit Recipe</button>
    </form>

    <script>
        function submitRecipe() {
            const recipeName = document.getElementById("recipeName").value;
            const recipeText = document.getElementById("recipeText").value;

            if (recipeName && recipeText) {
                // Send the data to the backend for storage
                fetch('/api/editedrecipe/addrecipe', {  // Specify the correct Flask API endpoint
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json'
                    },
                    body: JSON.stringify({
                        title: recipeName,
                        ingredients: recipeText,
                        instructions: '',  // You can add more fields as needed
                        image_name: '',    // You can add more fields as needed
                        cleaned_ingredients: '',  // You can add more fields as needed
                        edited_by: 'User'  // Assuming the user's name or identifier
                    })
                })
                .then(response => response.json())
                .then(data => {
                    alert(data.message);
                })
                .catch(error => console.error('Error submitting recipe:', error));
            } else {
                alert('Please fill in both the title and the recipe text.');
            }
        }
    </script>
</body>
</html>
