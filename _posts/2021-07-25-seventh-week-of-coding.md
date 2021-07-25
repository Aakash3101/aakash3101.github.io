---
layout: post
title:  "Seventh Week of Coding"
date:   2021-07-18 18:00:00 +0530
categories: jekyll update
---
Hello everyone,

This week (19 July - 25 July), This week, I started to research for a new source of datasets which are hosted on R packages. After I found this amazing repository [RDatasets](https://github.com/vincentarelbundock/Rdatasets), my next goal was to find a way to integrate these datasets into retriever, and had my weekly standup meetings.

&nbsp;

### Meeting 1 (19th July)

So after completing the `tidycensus` dataset, my mentor suggested me to look for more sources of datasets which are present in R packages. So I started searching for these datasets. Then I found this repository [RDatasets](https://github.com/vincentarelbundock/Rdatasets), which hosts around 1700 datasets that are available in different R packages. So in the meeting, I discussed with my mentor if this source is good enough to be added to retriever. Later we agreed upon the source as it contains datasets which are exclusive to only R packages. Now, we need to decide a design, which should be followed to install these datasets using retriever.

From our previous experience with the `tidycensus` dataset, we know that the packages which contain these datasets require a lot of dependencies to be installed for them to work. So we thought that it would be better if try not to install each individual package, but rather use the repository, as it also contains the raw data files of the datasets.

&nbsp;

### Meeting 2 (23rd July)

During the second meeting, we had a long discussion about the design for integrating `RDatasets` in retriever. So, the prototype would work in the following way:

For installing the rdataset,

```text
retriever install postgres rdataset-aer-affairs
```

and for downloading the rdataset

```text
retriever download rdataset-aer-affairs
```

where, `rdataset` is a prefix to tell that the dataset is included in `RDatasets`, followed by the package name (here `aer`), and lastly the dataset name (here `affairs`). So the syntax is `rdataset-<package>-<dataset_name>`. In the design, we would first download the raw data files, then create scripts on them and then update the scripts accordingly, and then install them as normal scripts.

I would create the prototype by the next meeting, and discuss if I should make any new changes or not.

So, I worked upon the prototype, and till now I have faced no problems in implementing the design. Looking forward to reviews from my mentor in the meeting.

See you guys next week!!
