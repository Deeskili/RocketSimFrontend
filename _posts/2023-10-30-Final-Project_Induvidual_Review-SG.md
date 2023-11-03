---
comments: True
layout: post
title: Induvidual Review SG
description: Recap of key events and learnings
type: tangibles
courses: {'compsci': {'week': 3}}
categories: ['C4.1']
---

<h3>Overview of Final Project</h3>
 
Our final project is a recipe manager book that extracts details from a backend API and outputs results in the frontend webpage. There are over 4000 recipes in the backend server whcih the code extracts and displays as recipe cards from which the user can search and choose any particular recipe of their liking. As I was working with the frontend side of the project, I'll be recaping my entire journey up until this point of project completion.

<h3>Project Planning</h3>

Week 0 started of with us planning you recipe manager site. Our original goal was a rocket simulator but we then switched up to a recipe manager owing to the difficulties of making and running a rocket simulator. Week 0's main goal for the frontend team was planning out and exicuting the frontedn home page, which we first planned out in figma and developed a code based on that. Our goal was to make a parralax effect for scrolling which we felt would be pretty cool to scroll through.


<h3>Continuation of making the frontend homepage</h3>

We understood that extracting code from figma would be an impossible task and thus we taught ourselved with the help of W3 schools. This parrallax animation contains images as the background with text in the front and when the user scrolls down it give an effec tof the image going down with the as well. This animation is also called the parralelx affect. As the week goes on the front end team will begin improving it and making it look more apparent.

<h2>My Contributions </h2>
<h3>Code Samples</h3>
During the duration of making the backend api we figured it would help us very much by making the api using a database. We found a csv file online and made sure it was mapped with IDs so it can be used flawlessly on frontend. Here is a example of the database.

[CSV](https://ray.so/#theme=candy&background=true&darkMode=true&padding=64&code=U2V0IHJlc2VydmVkIHNraWxsZXQgd2l0aCBjaGlja2VuIGRyaXBwaW5ncyBvdmVyIG1lZGl1bSBoZWF0LiBZb3Ugc2hvdWxkIGhhdmUgYWJvdXQgwrwgY3VwLCBidXQgYSBsaXR0bGUgb3ZlciBvciB1bmRlciBpcyBhbGwgZ29vZC4gKElmIHlvdSBoYXZlIHNpZ25pZmljYW50bHkgbW9yZSwgZHJhaW4gb2ZmIGFuZCBzZXQgZXhjZXNzIGFzaWRlLikgQWRkIHdpbmUgYW5kIGNvb2ssIHN0aXJyaW5nIG9mdGVuIGFuZCBzY3JhcGluZyB1cCBhbnkgYnJvd25lZCBiaXRzIHdpdGggYSB3b29kZW4gc3Bvb24sIHVudGlsIGJpdHMgYXJlIGxvb3NlbmVkIGFuZCB3aW5lIGlzIHJlZHVjZWQgYnkgYWJvdXQgaGFsZiAoeW91IHNob3VsZCBiZSBhYmxlIHRvIHNtZWxsIHRoZSB3aW5lKSwgYWJvdXQgMiBtaW51dGVzLiBBZGQgYnV0dGVyIG1peHR1cmU7IGNvb2ssIHN0aXJyaW5nIG9mdGVuLCB1bnRpbCBhIHNtb290aCBwYXN0ZSBmb3JtcywgYWJvdXQgMiBtaW51dGVzLiBBZGQgYnJvdGggYW5kIGFueSByZXNlcnZlZCBkcmlwcGluZ3MgYW5kIGNvb2ssIHN0aXJyaW5nIGNvbnN0YW50bHksIHVudGlsIGNvbWJpbmVkIGFuZCB0aGlja2VuZWQsIDbigJM4IG1pbnV0ZXMuIFJlbW92ZSBmcm9tIGhlYXQgYW5kIHN0aXIgaW4gbWlzby4gVGFzdGUgYW5kIHNlYXNvbiB3aXRoIHNhbHQgYW5kIGJsYWNrIHBlcHBlci4K)

<h3>Link to Home page</h3>
[Homepage](https://deeskili.github.io/RocketSimFrontend/)

Thus as you can see the code above, the parralax effect work and the scrolling down the user can see the images also seem to move along with the cursor and it moves through the text. This was a pretty cool effect that we worked on using HTML and CSS. This was made by the front end team consisting of Ryan Liu and Sri Vaidyas

<h3>Overview of Backend to Frontend Data Pull</h3>
The backend servers were created by me of the backend team. The servers include a URL link that contains over 4000 recipes to search for and find, these recipes also have recipe details such as instruciton as to how the recipe can be recreated as well as the ingredients required to make the dish. We used two API overall, both belonging to the same recipes but on with the entirely of all the recipes and the other which is ID linked where one can change the id of the url of have a new recipe. Both of these URL API are used to make this recipe manager search work.

This api was made using examples given to us by the teacher like jokes and covid. First we tried to make the api via a external api but that did not work out. Therefor we used a csv file in order to grab and export the data using a backend url hosted by aws. 
[Backend with All](https://backendrocketmain.stu.nighthawkcodingsociety.com/api/recipe/recipes)
[Backend with id](https://backendrocketmain.stu.nighthawkcodingsociety.com/api/recipe/recipedetails?id=1)

<h3>Mapping Values</h3>
In order to use the data we found online otherwise called a database we will have to map the data. The mapping of the data will allow us to use data in a organized matter to make it easier for the frontend team to pull. I had many collumns which I mapped to values and made it a json file which the frontend team can pull and format for the user to read easily. 

[Values Mapped](https://ray.so/#theme=candy&background=true&darkMode=true&padding=32&code=Y2xhc3MgUmVjaXBlKGRiLk1vZGVsLCBVc2VyTWl4aW4pOgogICAgX190YWJsZW5hbWVfXyA9ICdyZWNpcGVzJwoKICAgIGlkID0gZGIuQ29sdW1uKGRiLkludGVnZXIsIHByaW1hcnlfa2V5PVRydWUpCiAgICB0aXRsZSA9IGRiLkNvbHVtbihkYi5TdHJpbmcoMTI4KSwgdW5pcXVlPVRydWUsIG51bGxhYmxlPUZhbHNlKQogICAgaW5ncmVkaWVudHMgPSBkYi5Db2x1bW4oZGIuU3RyaW5nKDI1NiksIG51bGxhYmxlPUZhbHNlKQogICAgaW5zdHJ1Y3Rpb25zID0gZGIuQ29sdW1uKGRiLlN0cmluZygyNTYpLCBudWxsYWJsZT1UcnVlKSAgIyBBc3N1bWluZyBpbnN0cnVjdGlvbnMgY2FuIGJlIG51bGxhYmxlCiAgICBpbWFnZV9uYW1lID0gZGIuQ29sdW1uKGRiLlN0cmluZyg2NCksIG51bGxhYmxlPVRydWUpICAjIEFzc3VtaW5nIGltYWdlX25hbWUgY2FuIGJlIG51bGxhYmxlCiAgICBjbGVhbmVkX2luZ3JlZGllbnRzID0gZGIuQ29sdW1uKGRiLlN0cmluZygyNTYpLCBudWxsYWJsZT1UcnVlKSAgIyBBc3N1bWluZyBjbGVhbmVkX2luZ3JlZGllbnRzIGNhbiBiZSBudWxsYWJsZQoKICAgIGRlZiBfX2luaXRfXyhzZWxmLCB0aXRsZSwgaW5ncmVkaWVudHMsIGluc3RydWN0aW9ucywgaW1hZ2VfbmFtZSwgY2xlYW5lZF9pbmdyZWRpZW50cyk6CiAgICAgICAgc2VsZi50aXRsZSA9IHRpdGxlCiAgICAgICAgc2VsZi5pbmdyZWRpZW50cyA9IGluZ3JlZGllbnRzCiAgICAgICAgc2VsZi5pbnN0cnVjdGlvbnMgPSBpbnN0cnVjdGlvbnMKICAgICAgICBzZWxmLmltYWdlX25hbWUgPSBpbWFnZV9uYW1lCiAgICAgICAgc2VsZi5jbGVhbmVkX2luZ3JlZGllbnRzID0gY2xlYW5lZF9pbmdyZWRpZW50cwoKICAgIGRlZiBhbGxkZXRhaWxzKHNlbGYpOgogICAgICAgIHJldHVybiB7CiAgICAgICAgICAgICJpZCI6IHNlbGYuaWQsCiAgICAgICAgICAgICJ0aXRsZSI6IHNlbGYudGl0bGUsCiAgICAgICAgICAgICJpbmdyZWRpZW50cyI6IHNlbGYuaW5ncmVkaWVudHMsCiAgICAgICAgICAgICJpbnN0cnVjdGlvbnMiOiBzZWxmLmluc3RydWN0aW9ucywgICMgQWRkZWQgaW5zdHJ1Y3Rpb25zCiAgICAgICAgICAgICJpbWFnZV9uYW1lIjogc2VsZi5pbWFnZV9uYW1lLAogICAgICAgICAgICAiY2xlYW5lZF9pbmdyZWRpZW50cyI6IHNlbGYuY2xlYW5lZF9pbmdyZWRpZW50cwogICAgICAgIH0K)

<h3>Function</h3>
Next we made a function so the frontend can ut a query on the end of the backend url like the id in order to obtain the data they were hoping to get. This was created by using functions. In the function we instructed the program to use the query that was provided and go through the csv until it could find the value that it needed. 

[Function](https://ray.so/#theme=candy&background=true&darkMode=true&padding=64&code=ZGVmIGluaXRSZWNpcGVzKCk6CiAgICB3aXRoIGFwcC5hcHBfY29udGV4dCgpOgogICAgICAgIHByaW50KCJDcmVhdGluZyByZWNpcGUgdGFibGVzIikKICAgICAgICBkYi5jcmVhdGVfYWxsKCkKICAgICAgICBpZiBkYi5zZXNzaW9uLnF1ZXJ5KFJlY2lwZSkuY291bnQoKSA-IDA6CiAgICAgICAgICAgIHJldHVybgoKICAgICAgICBiYXNlZGlyID0gb3MucGF0aC5hYnNwYXRoKG9zLnBhdGguZGlybmFtZShfX2ZpbGVfXykpCiAgICAgICAgZmlsZV9wYXRoID0gb3MucGF0aC5qb2luKGJhc2VkaXIsICIuLi9zdGF0aWMvZGF0YS9yZWNpcGVzLmNzdiIpICAjIENoYW5nZWQgdG8gdXNlIG9zLnBhdGguam9pbiBmb3IgYmV0dGVyIGNvbXBhdGliaWxpdHkKICAgICAgICBkZiA9IHBkLnJlYWRfY3N2KGZpbGVfcGF0aCkKCiAgICAgICAgZm9yIGluZGV4LCByb3cgaW4gZGYuaXRlcnJvd3MoKToKICAgICAgICAgICAgcmVjaXBlID0gUmVjaXBlKAogICAgICAgICAgICAgICAgdGl0bGU9cm93WydUaXRsZSddLAogICAgICAgICAgICAgICAgaW5ncmVkaWVudHM9cm93WydJbmdyZWRpZW50cyddLAogICAgICAgICAgICAgICAgaW5zdHJ1Y3Rpb25zPXJvdy5nZXQoJ0luc3RydWN0aW9ucycsIE5vbmUpLCAgIyBBZGRlZCBhIGdldCBtZXRob2QgdG8gaGFuZGxlIHRoZSBwb3NzaWJpbGl0eSBvZiB0aGUga2V5IG5vdCBleGlzdGluZwogICAgICAgICAgICAgICAgaW1hZ2VfbmFtZT1yb3cuZ2V0KCdJbWFnZV9OYW1lJywgTm9uZSksCiAgICAgICAgICAgICAgICBjbGVhbmVkX2luZ3JlZGllbnRzPXJvdy5nZXQoJ0NsZWFuZWRfSW5ncmVkaWVudHMnLCBOb25lKQogICAgICAgICAgICApCgogICAgICAgICAgICBkYi5zZXNzaW9uLmFkZChyZWNpcGUpCiAgICAgICAgICAgIHRyeToKICAgICAgICAgICAgICAgIGRiLnNlc3Npb24uY29tbWl0KCkKICAgICAgICAgICAgZXhjZXB0IEludGVncml0eUVycm9yOgogICAgICAgICAgICAgICAgZGIuc2Vzc2lvbi5yb2xsYmFjaygpCiAgICAgICAgICAgICAgICBwcmludChmIkR1cGxpY2F0ZSByZWNpcGUgb3IgZXJyb3I6IHtyZWNpcGUudGl0bGV9IikKICAgICAgICAgICAgZXhjZXB0IEV4Y2VwdGlvbiBhcyBlOgogICAgICAgICAgICAgICAgZGIuc2Vzc2lvbi5yb2xsYmFjaygpCiAgICAgICAgICAgICAgICBwcmludChmIkVycm9yIGFkZGluZyByZWNpcGUgYXQgaW5kZXgge2luZGV4fToge3N0cihlKX0iKQ)

<h3>Calling the Function</h3>
In a different file we imported the function from the file used above. In addition I defined the end of the url for instructions to the program when a certain function should be hit. 
[Function Calling Image](https://ray.so/#theme=candy&background=true&darkMode=true&padding=64&code=CmFwaSA9IEFwaShyZWNpcGVfYXBpKQpjbGFzcyByZWNpcGVzOgogICAgY2xhc3MgX2dldFJlY2lwZXMoUmVzb3VyY2UpOgogICAgICAgIGRlZiBnZXQoc2VsZik6CiAgICAgICAgICAgIHJlY2lwZXMgPSBkYi5zZXNzaW9uLnF1ZXJ5KFJlY2lwZSkuYWxsKCkKICAgICAgICAgICAgcmV0dXJuIGpzb25pZnkoW3JlY2lwZS5hbGxkZXRhaWxzKCkgZm9yIHJlY2lwZSBpbiByZWNpcGVzXSkKICAgICAgICAKICAgIGNsYXNzIF9nZXRyZWNpcGVkZXRhaWxzKFJlc291cmNlKToKICAgICAgICBkZWYgZ2V0KHNlbGYpOgogICAgICAgICAgICByZWNpcGUgPSBkYi5zZXNzaW9uLnF1ZXJ5KFJlY2lwZSkuZmlsdGVyKFJlY2lwZS5pZCA9PSBpbnQocmVxdWVzdC5hcmdzLmdldCgiaWQiKSkpLmZpcnN0KCkKICAgICAgICAgICAgcmV0dXJuIGpzb25pZnkocmVjaXBlLmFsbGRldGFpbHMoKSkKICAgIAogICAgYXBpLmFkZF9yZXNvdXJjZShfZ2V0UmVjaXBlcywgIi9yZWNpcGVzIikKICAgIGFwaS5hZGRfcmVzb3VyY2UoX2dldHJlY2lwZWRldGFpbHMsICIvcmVjaXBlZGV0YWlscyIp)


<h3>Overall</h3>
Overall the backend was created with many additions ot the backend. We used functions and aws deployment techniques to deploy the backend. I really liked the technical aspect of the backend and I would 100% do it again!

<h3>Github Analytics</h3>
Over the repositories I have been contributing to I have been constantly commiting to show my contributions. These commits can be seen from my github profile. 
[Github Analytics](https://github.com/SGTech08)

<h3>Individual Projects</h3>
One of my individual projects I made during the is my Dominos Monitor. With this monitor it fetches the API of dominos to check stock of a coupon. Then it keeps it in a loop until it finds a coupon that is successful. It allows me to get free pizza :) and who doesn't love free pizza. 

<h3>Trimester One Review</h3>

<h3>Plans for NATM week</h3>

1. Our main goal for NATM week as mentioned above is to fix the images error. We plan to use an external API for only images to try and display a few with the recipes. With the help of Mr. Mortensen and Mr. Lopez we hope to link these images into the wbesite some way or the other as without images the website looks really bland

2. Our second goal before NATM is to reformat the site, remove stuff and add stuff to make it more like our own webiste and not just like that of a forked website from the teach.

3. If our qualification remains our hope is to contiue working to better the site and give an overall good presentation at night at the museum!
