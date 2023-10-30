---
comments: True
layout: post
title: Live Project Plans and Summary
description: 
type: plans
courses: {'compsci': {'week': 0}}
categories: ['C4.1']
---

<h3>Overview</h3>

The main goal for our recipe search database was to create a search bar where people can input recipe name and get an output card where the recipe details including the title, ingredients as well as the step to make the dish are all listed out in detail. Our goal was to create something that helps people in real life, and not just using an API that really has no function in someone's day to day life.

<h3>Initial Concepts</h3>

1. Cayden Shi (Scrum Master)
   - Proposed idea for the recipe search bar after a rocket sim idea
   - Inspired from Saathvik's previous recipe code which allowed user to edits recipes
   - Spilt team into frontend and backend

2. Saathik (Backend)
   - Propsed to work on API
   - Had an idea for the the parrralax scrolling effect
   - Scrolling must have pictures that felt like they were moving
   -  Proposed idea for recipe cards which were to be displayed with a more info button. 

<h3>Advance Concepts</h3>

1. Saathvik
   - Propsed and created a double URL API for the same recipe database which was then going to be used by the fronted team, one for the overall and the other of each one
   - Propsed recipes to be linked by ID, whcih helps the search be easier
   - Each recipe is linked to its unique id, which when the more info button is clicked, the user is directed to a new page with the details of the recipe listed out. 

- Recipe list page
  - Linked with recipe Api URL
  - Each recipe is displyed with teh recipe card
  - Search bar searches across the cards
  - More info button
    - More info button link to recipe details page
    - More details page contains deatils
      - Instructions
      - Steps for dish
 
- Index Page
 - Parrallax scrollign effect
   - Parralx effect with images
   - Images scroll down with ther user giving an effect
   - Each image has text describing the page


<h3>Figma Plans</h3>

Figma was used to plan our layout for each page including the basic index page as well as the recipe detials and list page. 

<br>
<h4>Index Page</h4>
<iframe style="border: 1px solid rgba(0, 0, 0, 0.1);" width="1000" height="500" src="https://www.figma.com/embed?embed_host=share&url=https%3A%2F%2Fwww.figma.com%2Fproto%2F3nvtE8kJLdDL6zx4ho8bp8%2FRecipe-Book-Manager%3Fnode-id%3D23-30%26starting-point-node-id%3D23%253A30%26mode%3Ddesign%26t%3Di7odREAwLJqj0Ys4-1" allowfullscreen></iframe>
<br>
<h4>Recipe List and Details Page</h4>
<iframe style="border: 1px solid rgba(0, 0, 0, 0.1);" width="1000" height="500" src="https://www.figma.com/embed?embed_host=share&url=https%3A%2F%2Fwww.figma.com%2Ffile%2FcODpACkBAMJFpxXwB25EES%2FUntitled%3Ftype%3Ddesign%26node-id%3D0%253A1%26mode%3Ddesign%26t%3DLQy7vjhWWfw2cR2L-1" allowfullscreen></iframe>

<br>
<h3> User Ideology</h3>

Our basic idea for how the expirence for the user should be was very simple. The user should be able to understnad and easily navigate through the page without assitance, the webpage should be user freindly and look pretty cool. The user must have an overall postive experience using the page

We hoped the code would work this way:
- The user loads the webapge and is first led to the frontpage with the parralax effect
  - The user is impressed with teh parralx effect and wants to know more about the webpage 
- The user then move into the recipe list page and is impressed by how quickly 4000+ recipes are loaded
  - The user scrolls down and down into the never ending abyss of recipes and is in awe of the number of recipe cards in the page
- The user then uses the search bar to search for any of their favorite recipe
  - The outputs impress the user and thy continue to click into the more info button which then leads them into the recipe details page
    - In the reipe details page, the user is again in awe of the organization of the recipes as well as the number of steps and inrgedients
     - The user then takes a print out of the recipe informtion to try it out at home
- The user leaves with a smile :)

<h3>DevOPS</h3>

1. Cayden Shi: Scrum Master and is to work on the backend site and API
2. Saathvik Gampa: Backend and is to work on the backend API
3. Ryan Liu: Frontend Tester: Is to test API and the code to fetch data from the backend server
4. Sri Vaidya S: Frontend developer and is to work on the frontend stuff including the main API fetch and display


<h3> Anatomy of Recipe Book Manager</h3>

1. Github Repo(s): One for the backend servers and one for the main frontend website
2. Notebooks and Posts for testing and final product
3. Index.md file for the frontend homepage
4. Recipe details and the recipe lists for the main recipe search and details.
   - 2023-10-21-recipelist.md
   - 2023-10-21-recipedetails.md


<h3> Project Links</h3>
[Backend Repo](https://github.com/SGTech08/backendrocketmain)
[Frontend Repo](https://github.com/Deeskili/RocketSimFrontend)
[API URL - All recipes](https://backendrocketmain.stu.nighthawkcodingsociety.com/api/recipe/recipes)
[API URL - Induvidual ID](https://backendrocketmain.stu.nighthawkcodingsociety.com/api/recipe/recipedetails?id=1)
[Published Site-Frontend](https://deeskili.github.io/RocketSimFrontend/)