---
comments: True
layout: notebook
title: Search Bar JS Code+
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
        }
        h1 {
            text-align: center;
        }
        .search-container {
            text-align: center;
        }
        .search-input {
            padding: 10px;
            border: 2px solid #ccc;
            border-radius: 5px;
            width: 250px;
            font-size: 16px;
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
            text-align: center;
        }
    </style>
</head>
<body>
    <h1>Recipe Search</h1>

    <div class="search-container">
        <input type="text" id="searchInput" class="search-input" placeholder="Enter a keyword">
        <button id="searchButton" class="search-button">Search</button>
    </div>

    <div id="searchResults"></div>

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
                        // Create HTML elements to display each result (e.g., recipe name)
                        const resultElement = document.createElement("div");
                        resultElement.textContent = recipe.name;

                        // Add the result to the search results container
                        searchResults.appendChild(resultElement);
                    });
                }
            }
        });
    </script>
</body>
</html>