---
layout: post
title:  "3rd Week of Coding"
date:   2021-06-27 18:00:00 +0530
categories: jekyll update
---
Hello everyone,

This week (21 June - 27 June), This week, I implemented the functions to list the datasets hosted on Socrata, display the information of the dataset requested by the user and install a particular Socrata dataset through retriever, and had my weekly standup meetings.

&nbsp;

### Meeting 1 (21th June)

During the meeting, I presented functions, which would list the autocomplete suggestions to the user input, display information about the dataset selected by the user, and to download the raw data of that dataset. Since I had created the functions, and their functionalities seem to be correct according to the discussions in the meeting. So now I just need to add them to retriever. In the meeting, we discussed which commands should be modified to accomodate these changes. So we came up with adding the autocomplete and listing the information of the dataset in the `retriever ls` command. The new modified command would be `retriever ls -socrata <name>`, where `name` would be the dataset name the user is trying to find using the autocomplete suggestions.

And for downloading the raw data and installing the dataset, we would update the `retriever download` and `retriever install` commands respectively. The new modified commands would be `retriever download --socrata <dataset-id>` and `retriever isntall --socrata <engine> <dataset-id>`, where `dataset-id` would be the id of the dataset the user wants to download or install.

I made these changes in retriever. For the installing the dataset into retriever, I have automated the process of script creation for the dataset and store the script accordingly. For the automation of creating scripts, I used the metadata of the dataset, and update the values of the default script created by the `retriever autocreate` command. After creating the script the users can use the default install command `retriever install <engine> <script-name>` without the `--socrata` flag to install the dataset.

Currently this functionality of downloading, creating the script and installing is only available for tabular and geo type datasets. The number of datasets supported by this functionality is 97,646 out of 213,965 datasets.

&nbsp;

### Meeting 2 (24th June)

During the second meeting, I explained the above changes and demonstrated the working of that piece of code. Some changes were suggested to me, which I had incorporated after the meeting. These changes are to that I should make it easier for the user to retrieve the information related to the dataset. They suggested me to use the index of the list to get the name of the dataset rather than typing the full name of the dataset. But I decided to make it more interactive, so I used the `inquirer` python library to make this process interactive. Now the users just need to select the dataset from the list of names, rather than typing the full name.

This is how it looks now:

``` text
retriever ls -socrata fishing
Autocomplete suggestions : Total 34 results

[?] Select the dataset name: Cook County - Fishing Lakes
   Recommended Fishing Rivers And Streams
   Iowa Fishing Report
   Recommended Fishing Rivers And Streams API
   Recommended Fishing Rivers, Streams, Lakes and Ponds Map
   Public Fishing Rights Parking Areas Map
   Fishing Atlas
 > Cook County - Fishing Lakes
   Public Fishing Rights Parking Areas
   [ARCHIVED] Fishing License Sellers
   Recommended Fishing Lakes and Ponds Map
   Recommended Fishing Lakes and Ponds
   Cook County - Fishing Lakes - KML
   Delaware Fishing Licenses and Trout Stamps

```

Later I found that my functions were not able to download and install some `geo` and `tabular` datasets. I thoroughly investigated the problem, and it turns out that all of the `geo` type datasets are `tabular`, but their raw data cannot be accessed with the same dataset identifier.

And some tabular datasets are actually filtered from a parent dataset. And they can also not be installed with the same dataset identifier. Their metadata also does not hold the query, using which we can install them. On their homepages, we can download the filtered data manually. I thought of webscraping the url with the query, but the website is javascript generated.

I would be discussing this problem in tomorrow's meeting (i.e. 28th June), on how to tackle these two problems. If we are not able to solve these issues, our count of datasets would decrease to 90,000 datasets. After solving these issues, I would add more tests for the socrata functions and then create a PR for it.

See you guys next week!!
