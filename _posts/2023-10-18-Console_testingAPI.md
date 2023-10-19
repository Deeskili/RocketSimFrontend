---
comments: True
layout: notebook
title: Console Log Test
description: 
type: hacks
courses: {'compsci': {'week': 1}}
categories: ['C4.1']
---

%%js
const apiUrl = "https://backendrocketmain.stu.nighthawkcodingsociety.com/api/recipe/recipes";
fetch(apiUrl)
    .then(response => {
        if (!response.ok) {
            throw new Error(`Network response was not ok: ${response.status}`);
        }
        return response.json();
    })
    .then(data => {
        console.log("Data from the API:", data);
    })
    .catch(error => {
        console.error("There was a problem fetching the data:", error);
    });

