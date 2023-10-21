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
            border-radius: 5px;
            padding: 10px;
            margin: 10px;
            background-color: white;
        }
        .recipe-card img {
            width: 100%;
            max-height: 200px;
            object-fit: cover;
        }
        .recipe-name {
            font-weight: bold;
            margin-top: 10px;
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
        document.addEventListener("DOMContentLoaded", () => {
            const recipeList = document.getElementById("recipeList");
            const apiUrl = "https://backendrocketmain.stu.nighthawkcodingsociety.com/api/recipe/recipes";

            // Fetch data from the API
            fetch(apiUrl)
                .then(response => {
                    if (!response.ok) {
                        throw new Error(`Network response was not ok: ${response.status}`);
                    }
                    return response.json();
                })
                .then(data => {
                    // Generate recipe cards
                    data.forEach(recipe => {
                        const recipeCard = document.createElement("div");
                        recipeCard.classList.add("recipe-card");

                        // Display image
                        const imgElement = document.createElement("img");
                        imgElement.src = `_images/${recipe.image}`;
                        recipeCard.appendChild(imgElement);

                        // Display recipe name
                        const nameElement = document.createElement("div");
                        nameElement.classList.add("recipe-name");
                        nameElement.textContent = recipe.name;
                        recipeCard.appendChild(nameElement);

                        // More info button
                        const moreInfoButton = document.createElement("button");
                        moreInfoButton.classList.add("more-info-button");
                        moreInfoButton.textContent = "More Info";
                        recipeCard.appendChild(moreInfoButton);

                        // Append the recipe card to the container
                        recipeList.appendChild(recipeCard);
                    });
                })
                .catch(error => {
                    console.error("There was a problem fetching the data:", error);
                });
        });
    </script>
</body>
</html>
