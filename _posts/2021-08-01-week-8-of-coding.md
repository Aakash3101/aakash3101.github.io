---
layout: post
title:  "8th Week of Coding"
date:   2021-08-01 18:00:00 +0530
categories: jekyll update
---
Hello everyone,

This week (26 July - 1 Aug), This week, I worked on the `RDatasets` prototype and made some changes in the Socrata API pull request, and had my weekly standup meetings.

&nbsp;

### Meeting 1 (26th July)

So last week, I completed making a prototype for the `RDatasets`. My mentor was satisfied with the design as it was simple and it met the requirements. Then we discussed to make a command that would list all the rdatasets and it can also display all the rdatasets present in the specified packages.

So I created the functionality, and it is as follows:

- to display all rdatasets
  
  ```text
  retriever ls rdataset
  ```

- to display rdatasets present in the specified package(s)

  ```text
  retriever ls rdataset -p PACKAGE [PACKAGE ...]
  ```

&nbsp;

### Meeting 2 (30th July)

During the meeting, we discussed the design of `RDatasets`, to see if we can change any other thing or if it lacks some functionalities. Later we discussed the status of my Socrata API [PR #1600](https://github.com/weecology/retriever/pull/1600). So my mentor advised me to include some examples for the python interface of the Socrata API in the PR comments. And discussed a few other minor design changes which can be accommodated to simplify things for the user.

Later I created some interface examples in my PR and made the required changes.

See you guys next week!!
