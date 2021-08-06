---
layout: post
title:  "1st Week of Coding"
date:   2021-06-13 20:00:00 +0530
categories: jekyll update
---
Hi everyone,

This week (7 June - 13 June), I began my coding period for the GSoC program. We had two meetings this week, first meeting on 7th June and the other meeting on 10th June.

&nbsp;

### Meeting 1 (7th June)

During the first meeting, we discussed the work we did during the Community Bonding period. During that period I researched for the APIs through which we can access datasets. During the meeting I proposed to create a document on the research of these APIs and share it with my mentor, Henry. Later in the meeting, we setup the debugger in VS Code and tested it.

Until the next meeting, I shortlisted the APIs which I think were more general in terms of dataset and not narrowed down for only a few datasets. These shortlisted APIs were then added to the document with the specific details.

Using the debugger, I understood the workflow of the `download_from_kaggle()` function, and how it was called by retriever.

&nbsp;

### Meeting 2 (10th June)

During the second meeting, I presented the document, and my mentor suggested me to create an issue with the contents of the document. Later we discussed where to call the function for downloading datasets using Socrata API.

The issue created is [#1593 API research for API integration in Data Retriever (GSoC '21)](https://github.com/weecology/retriever/issues/1593).

Until the next meeting, I would be writing a function which uses the Socrata API to access the datasets. And create a script to check the functionality.

See you guys next week!!
