---
title: Recipe Book Manager
layout: base
---


<html>
<head>
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <style>
        body, html {
            height: 100%;
            margin: 0;
            font: 400 15px/1.8 "Lato", sans-serif;
            color: #777;
        }
        /* Background images for different sections */
        .bgimg-1, .bgimg-2, .bgimg-3, .bgimg-4, .bgimg-5 {
            position: relative;
            opacity: 0.65;
            background-attachment: fixed;
            background-position: center;
            background-repeat: no-repeat;
            background-size: cover;
        }
        .bgimg-1 {
            background-image: url("https://images.unsplash.com/photo-1553025934-296397db4010?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8OHx8ZGFyayUyMGZvb2QlMjBwaG90b2dyYXBoeXxlbnwwfHwwfHx8MA%3D%3D&auto=format&fit=crop&w=800&q=60");
            min-height: 100%;
        }
        .bgimg-2 {
            background-image: url("https://images.unsplash.com/photo-1534604973900-c43ab4c2e0ab?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2888&q=80");
            min-height: 400px;
        }
        .bgimg-3 {
            background-image: url("https://images.unsplash.com/photo-1560910615-9eaa2e704e63?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2825&q=80");
            min-height: 400px;
        }
        .bgimg-4 {
            background-image: url("https://plus.unsplash.com/premium_photo-1695822018668-72355fc4ee7c?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1pYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto.format&fit=crop&w=3024&q=80");
            min-height: 400px;
        }
        .bgimg-5 {
            background-image: url("https://images.unsplash.com/photo-1625604087024-7fb428fc4626?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1pYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2940&q=80");
            min-height: 400px;
        }
        /* Caption style */
        .caption {
            position: absolute;
            left: 0;
            top: 50%;
            width: 100%;
            text-align: center;
            color: #000;
        }
        .caption span.border {
            background-color: #111;
            color: #fff;
            padding: 18px;
            font-size: 25px;
            letter-spacing: 10px;
        }
        h3 {
            letter-spacing: 5px;
            text-transform: uppercase;
            font: 20px "Lato", sans-serif;
            color: #111;
        }
        /* Turn off parallax for tablets and phones */
        @media only screen and (max-device-width: 1024px) {
            .bgimg-1, .bgimg-2, .bgimg-3, .bgimg-4, .bgimg-5 {
                background-attachment: scroll;
            }
        }
    </style>
</head>
<body>
    <div class="bgimg-1">
        <div class="caption">
            <span class="border">Recipe Book</span>
        </div>
    </div>
    <div style="color: #777;background-color:white;text-align:center;padding:50px 80px;text-align: justify;">
        <h3>Recipe Book Manager</h3>
        <p>Welcome to your own recipe book manager where you can create, store, edit all your favorite recipes. Everything you love to eat all in one place!</p>
    </div>
    <div class="bgimg-2">
        <div class="caption">
            <span class="border">Over 4000 Recipes!!</span>
        </div>
    </div>
    <div style="color: #777;background-color:white;text-align:center;padding:50px 80px;text-align: justify;">
        <h3>Over 4000 Recipe!!</h3>
        <p>Our recipe book contains over 4000 recipe from which you can choose!</p>
    </div>
    <div class="bgimg-3">
    <a href="https://deeskili.github.io/RocketSimFrontend/2023-10-21-recipelist.html" style="text-decoration: none; display: block;">
        <div class="caption">
            <span class="border">Search Recipes!</span>
        </div>
    </a>
    </div>
    <div style="color: #777;background-color:white;text-align:center;padding:50px 80px;text-align: justify;">
        <h3>Search Recipes!</h3>
        <p>Our unique search bar allows you to search across the wide array of recipes to find that one you savour.</p>
    </div>
    <div class="bgimg-4">
    <a href="https://deeskili.github.io/RocketSimFrontend/2023-10-21-recipelist.html" style="text-decoration: none; display: block;">
        <div class="caption">
            <span class="border">Try New Recipes!</span>
        </div>
    </a>
    </div>
    <div style="color: #777;background-color:white;text-align:center;padding:50px 80px;text-align: justify;">
        <h3>Try New Recipes!</h3>
        <p>In a creative frenzy? No worries, our recipe manager can help you find something new to try our everyday!</p>
    </div>
    <div class="bgimg-5">
    <a href="https://deeskili.github.io/RocketSimFrontend/c4.1/2023/10/30/testeditedrecipe.html">
        <div class="caption">
            <span class="border">Input Recipe/Delete Recipe</span>
        </div>
    </a> 
    </div>
    <div style="color: #777;background-color:white;text-align:center;padding:50px 80px;text-align: justify;">
        <h3>Add Your Own Recipe!</h3>
        <p>Add, Search, or Delete recipes from our own database!</p>
    </div>
</body>
</html>
