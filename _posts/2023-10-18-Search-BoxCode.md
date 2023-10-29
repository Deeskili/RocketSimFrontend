---
comments: True
layout: notebook
title: Search Bar CSS and HTMl Code
description: 
type: tangibles
courses: {'compsci': {'week': 2}}
categories: ['C4.1']
---

%%html
<html>
    <head>
        <title>Recipe API Search</title>
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
</html>

