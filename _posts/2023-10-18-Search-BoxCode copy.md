---
comments: True
layout: notebook
title: Search Bar JS Code+ Test Fetching Data
description: 
type: hacks
courses: {'compsci': {'week': 1}}
categories: ['C4.1']
---


<html>
<head>
    <title>Recipe Search</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f2f2f2;
        }
        .container {
            text-align: center;
            margin-top: 50px;
        }
        .search-box {
            display: flex;
            justify-content: center;
        }
        .search-input {
            padding: 10px;
            border: 2px solid #ccc;
            border-radius: 5px;
            width: 250px;
            font-size: 16px;
            margin-right: 10px;
        }
        .search-button {
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 5px;
            padding: 10px 20px;
            cursor: pointer;
            font-size: 16px;
        }
        .search-button:hover {
            background-color: #45a049;
        }
        #searchResults {
            margin-top: 20px;
            text-align: left;
        }
        .recipe {
            border: 2px solid #ccc;
            border-radius: 5px;
            padding: 10px;
            margin: 10px;
        }
        .recipe img {
            display: block;
            margin: 0 auto;
        }
        .recipe h2 {
            color: #FF5733; /* Change the color as desired */
        }
        .recipe ul {
            list-style-type: disc;
            padding-left: 20px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Recipe Search</h1>
        <div class="search-box">
            <input type="text" id="searchInput" class="search-input" placeholder="Enter a keyword">
            <button id="searchButton" class="search-button">Search</button>
        </div>
        <div id="searchResults"></div>
    </div>

    <script>
        document.addEventListener("DOMContentLoaded", () => {
            const searchInput = document.getElementById("searchInput");
            const searchButton = document.getElementById("searchButton");
            const searchResults = document.getElementById("searchResults");

            // API URL
            const apiUrl = "https://backendrocketmain.stu.nighthawkcodingsociety.com/api/recipe/recipes";

            // Event listener for the search button
            searchButton.addEventListener("click", () => {
                const searchTerm = searchInput.value;
                if (searchTerm) {
                    // Clear previous search results
                    searchResults.innerHTML = "Searching...";

                    // Fetch data from the API based on the user's input
                    fetch(`${apiUrl}?q=${searchTerm}`)
                        .then(response => {
                            if (!response.ok) {
                                throw new Error(`Network response was not ok: ${response.status}`);
                            }
                            return response.json();
                        })
                        .then(data => {
                            // Display search results
                            displaySearchResults(data);
                        })
                        .catch(error => {
                            console.error("There was a problem fetching the data:", error);
                        });
                }
            });

            // Function to display search results
            function displaySearchResults(data) {
                searchResults.innerHTML = ""; // Clear previous results

                if (data.length === 0) {
                    searchResults.innerHTML = "No results found.";
                } else {
                    data.forEach(recipe => {
                        // Create an HTML element for each recipe
                        const recipeElement = document.createElement("div");
                        recipeElement.classList.add("recipe");

                        // Display picture
                        const imgElement = document.createElement("img");
                        imgElement.src = recipe.image;
                        imgElement.alt = recipe.name;
                        recipeElement.appendChild(imgElement);

                        // Display name
                        const nameElement = document.createElement("h2");
                        nameElement.textContent = recipe.name;
                        recipeElement.appendChild(nameElement);

                        // Display ingredients as an unordered list
                        const ingredientsElement = document.createElement("ul");
                        const ingredients = recipe.ingredients.split("\n");
                        ingredients.forEach(ingredient => {
                            const li = document.createElement("li");
                            li.textContent = ingredient;
                            ingredientsElement.appendChild(li);
                        });
                        recipeElement.appendChild(ingredientsElement);

                        // Display instructions as an unordered list
                        const instructionsElement = document.createElement("ul");
                        const instructions = recipe.instructions.split("\n");
                        instructions.forEach(instruction => {
                            const li = document.createElement("li");
                            li.textContent = instruction;
                            instructionsElement.appendChild(li);
                        });
                        recipeElement.appendChild(instructionsElement);

                        // Add the recipe to the search results container
                        searchResults.appendChild(recipeElement);
                    });
                }
            }
        });
    </script>
</body>
</html>
