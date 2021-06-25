---
layout: post
title:  "Second Week of Coding"
date:   2021-06-22 20:00:00 +0530
categories: jekyll update
---
Hi everyone,

This week (14 June - 21 June), This week, I debugged a error in the tests of retriever and created prototype scripts for the Socrata API, and had my weekly standup meetings.

&nbsp;

### Meeting 1 (14th June)

During the meeting, I presented the function which would be using the Socrata API to download the raw dataset. Created a test script to show the working of the function. The function correctly did its job. Later I would present an issue which was occuring while running the tests. We solved the issue during the meeting itself, and then I made a PR [#1594 Remove nuclear power plants](https://github.com/weecology/retriever/pull/1594) , which would resolve the error.

My task until the next meeting, was to find if we can automate the process of downloading datasets from Socrata, and then create a script from them like any other retriever script. The other task was to find the type of datasets hosted on Socrata, was information we can retrieve from the metadata of the datasets.

So I created some scripts which would be fetch me the number of datasets hosted on Socrata. That number turned out to be around 213k datasets. This could become a huge contribution from my side to the Data Retriever organization, if I could devise an efficient method to fetch datasets and create scripts for them automatically.

My next days went by creating python scripts, which would fetch me the details of the datasets, and how many domains are there which support the Socrata API, the number of datasets each domain hosts. Also I wrote a test function for the function which would download raw datasets using the Socrata API.

&nbsp;

### Meeting 2 (17th June)

During the second meeting, I presented the information I have collected for the past 3 days. This information actually eased my work a bit, since I have all the things related to the API, and their responses. My mentor told me that it would be great if I could integrate those datasets into Data Retriever as this would be a huge number of datasets. My mentor gave me the freedom to select a design for the process of automating the downloading and creation of scripts for the Socrata datasets.

Until the next meeting, my task is to completely identify the number of datasets that are feasible, and create a prototype of the how the design will be implemented. So I created a python script which prompted the user to provide a name of the dataset they would like to install, and then we use autocomplete feature of the Socrata API, and return the autocomplete suggestions to the user. Then the user would select the name, and then the script would return information like the ID, name, domain, description and the link of the dataset the user selected.

Below is the output of the script:

```text
retriever ls -socrata fishing

Autocomplete suggestions : Total 34 results

1. Recommended Fishing Rivers And Streams
2. Recommended Fishing Rivers And Streams API
3. Iowa Fishing Report
4. Recommended Fishing Rivers, Streams, Lakes and Ponds Map
5. Fishing Atlas
6. Public Fishing Rights Parking Areas Map
7. [ARCHIVED] Fishing License Sellers
8. Cook County - Fishing Lakes
9. Recommended Fishing Lakes and Ponds
10. Recommended Fishing Lakes and Ponds Map
11. Public Fishing Rights Parking Areas
12. Delaware Fishing Licenses and Trout Stamps
13. Cook County - Fishing Lakes - KML
14. General Fishing and Salmon Licence Sales
15. Hunting and Fishing License Sellers
16. Older Adult Hunting/Fishing Licenses
17. Fishing in Colorado State Parks
18. Historical - ccgisdata - FPDCC fishing lakes in Cook County
19. Major Contracts - Agriculture, Fishing, etc
20. MD iMAP: Maryland Finfish - Fishing Grounds
21. Seattle Parks and Recreation GIS Map Layer Shapefile - Fishing Piers
22. Fishing by Specialization Level
23. MD iMAP: Maryland Sport Venues - Fishing
24. MD iMAP: Maryland Recreational Uses - Charter Fishing Large Vessel
25. Seattle Parks and Recreation GIS Map Layer Web Services URL - Fishing Piers
26. MD iMAP: Maryland Recreational Uses - Guided Fishing
27. MD iMAP: Maryland Recreational Uses - Commercial Fishing
28. MD iMAP: Maryland Recreational Uses - Recreational Motorized Vessel Fishing
29. MD iMAP: Maryland Recreational Uses - Recreational Dive Fishing
30. MD iMAP: Maryland Recreational Uses - Recreational Shore Fishing
31. Iowa Real GDP by Year, Agriculture, Forestry, Fishing and Hunting Sector
32. MD iMAP: Maryland Recreational Uses - Recreational Ice Fishing
33. MD iMAP: Maryland Recreational Uses - Charter Fishing Small Vessel
34. MD iMAP: Maryland Recreational Uses - Recreational Kayak and Non Motorized Vessel Fishing

Enter the name of the dataset you want to install : Iowa Fishing Report

Dataset Information of Iowa Fishing Report: Total 1 results

1. Iowa Fishing Report
    ID : 4f5f-2rt7
    Description : The Iowa Department of Natural...
    Domain : mydata.iowa.gov
    Link : https://mydata.iowa.gov/Surveys-Inventories/Iowa-Fishing-Report/4f5f-2rt7
```

The design I chose is, we will prompt the user like this example. Then the user would enter the install command like:

```retriever install --socrata postgres 4f5f-2rt7```

After this we would prompt the user to enter the name for the script.
And then retriever would download the raw dataset for the dataset id, and then preprocess and create a script for the dataset. And then install it like any other dataset in retriever.

See you guys next week!!
