---
layout: post
title:  "First Evaluation"
date:   2021-07-18 18:00:00 +0530
categories: jekyll update
---
Hello everyone,

This week (12 July - 18 July), This week, we had our first evaluation of GSoC'21, and I am glad to announce that I have passed my first evaluation. For work, I tried to finish the `tidycensus` dataset script in retriever and eventually created the PR for it, and had my weekly standup meetings.

&nbsp;

### Meeting 1 (12th July)

We discussed about the current status of the script that I was working on, i.e. `tidycensus` dataset script. So we went with the option of creating a python script, and I understood how do python scripts work while installing a dataset on retriever.

Later I created the python script for the dataset and followed the basic template of these type of dataset python scripts. So I just needed to make a custom download function for the dataset, that would download the raw data files in the `./retriever/raw_data` folder, and then use those raw data files to install them into the respective engine selected by the user.

&nbsp;

### Meeting 2 (15th July)

In the meeting, I presented the code of the script, and how it proceeds to download and install the dataset. So, in one dataset there was a column whose name didn't match the rules of SQL, so we needed to rename it, while installing the dataset. From that my mentor instructed me to add the column name and its correction to the `clean_column_names()` function, whose task it to correct such problem. So I created a PR for both `tidycensus` script and the change in `clean_column_names()`.

Merged PR:

- [PR#1605 Updated clean_column_name()](https://github.com/weecology/retriever/pull/1605)

Under Review:

- [PR#1606 Added tidycensus dataset](https://github.com/weecology/retriever/pull/1606)

See you guys next week!!
