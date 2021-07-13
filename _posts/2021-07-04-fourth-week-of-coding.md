---
layout: post
title:  "Fourth Week of Coding"
date:   2021-07-04 18:00:00 +0530
categories: jekyll update
---
Hello everyone,

This week (28 June - 4 July), This week, I submitted my PR for the socrata api functions and started working on how to utilise the `tidycensus` R package, which contains the Census Data of USA, and had my weekly standup meetings.

&nbsp;

### Meeting 1 (28th June)

During the meeting, I presented my work on the Socrata API functions. The changes seem to match the original expectations of the Socrata API integration idea. Now, I just need to add tests for the major functions of this integration and then create a PR for it. Now that Socrata API functions are done, we proceed to adding new datasets which are present as an R package named `tidycensus`.

`tidycensus` : An integrated R interface to the decennial US Census and American Community Survey APIs and the US Census Bureau's geographic boundary files. Allows R users to return Census and ACS data as tidyverse-ready data frames, and optionally returns a listcolumn with feature geometry for all Census geographies.

My tasks till the next meeting are to add tests for the core functions of the Socrata API and to understand how the `tidycensus` package works, and which all datasets does it contain.

&nbsp;

### Meeting 2 (1st July)

During the second meeting, I explained my insight about the `tidycensus` package and the dataset it holds. So I setup `R` and `RStudio` on my system and installed the `tidycensus` package. The users need to generate a `census_api_key` which is used by the library to access the data. I did face some installation issues which were caused by the library `units`, it required the installation of system dependency `libudunits2-dev`.

After this I followed the [manual](https://cran.r-project.org/web/packages/tidycensus/tidycensus.pdf) for the `tidycensus` package. So the package contains 5 datasets, which are `county_laea`, `state_laea`, `mig_recodes`, `fips_codes` and `pums_variables`. So the `county_laea` and `state_laea` are spatial datasets, and the other three are tabular datasets.

To be able to integrate these datasets into `retriever`, we would require an interface between Python and R. One such interface that I will be using is `rpy2`. The python package `rpy2` provides support for running code written in R from python, accessing R objects in python and to convert R dataframe objects to pandas dataframe objects (and vice-versa). Till the next meeting I would be going through the `rpy2` documentation and try to see if I could extract these datasets as raw files.

I also created my PR [#1600 Added Socrata API to retriever, Added tests for the socrata functions](https://github.com/weecology/retriever/pull/1600). Since I did made a whole of lot additions, it would take some while to merge the PR, but I did my best to explain everything and testcases in the PR itself.

See you guys next week!!
