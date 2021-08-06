---
layout: post
title:  "5th Week of Coding"
date:   2021-07-11 18:00:00 +0530
categories: jekyll update
---
Hello everyone,

This week (5 July - 11 July), This week, I updated the github-actions workflow which was failing earlier, and then created a new workflow, created some functions which would read and download the datasets present in the `tidycensus` package and had my weekly standup meetings.

&nbsp;

### Meeting 1 (5th July)

During the meeting, I presented the changes I made in the `Dockerfile`, which resolved the issue, where the tests were failing for every PR. It was resolved by adding a line `apt-get install -y --force-yes libpq-dev`, as this dependency was required for installing the `psycopg2-binary` library. As this issue was resolved, I tried making a new workflow in github-actions, which would not require the `Dockerfile` and the `docker-compose.yml`.

After the tests were passing, all pending pull requests were merged into the `main` branch. Merged pull requests which had my contribution are:

- [PR#1601 Updated docker-compose.yml and Dockerfile](https://github.com/weecology/retriever/pull/1601)
- [PR#1598 Checking for license field in scripts](https://github.com/weecology/retriever/pull/1598)

&nbsp;

### Meeting 2 (8th July)

During the meeting, I presented my work of how we can access the datasets present in the `tidycensus` package. Using `rpy2`, we can run R code in python. So, first task was to create a function which would install the library `tidycensus` and its dependent libraries. Since some dependent libraries require some additional system dependencies according to the OS, we would prompt the user for such errors.

After that I created a function which would install the tabular datasets `fips_codes`, `pums_variables` and `mig_recodes`. In this function we would call the converter in `rpy2` to convert R dataframes into Pandas dataframes. But there was one issue with this function, the `mig_recodes` dataset caused an encoding error in `rpy2`'s converter, which reads only `utf-8` encoded text. The `mig_recodes` dataset was encoded with the Windows `cp-1252` encoding.

I created a new workflow and created a pull request for it. The [PR#1603 Updated python-package.yml](https://github.com/weecology/retriever/pull/1603) is merged.

See you guys next week!!
