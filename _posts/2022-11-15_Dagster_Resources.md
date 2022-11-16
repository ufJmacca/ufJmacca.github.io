---
title: Dagster Resources
date: 2022-11-15 10:00:00 +1100
categories: [Data, dagster]
tags: [til] 
---

# Dagster Resources

While refactoring a previous project to leveage dagster, I came accross a class that holds to logic to interact with a mobile API. I am calling this class to authenticate into the mobile API, and then make multiple data requests. When thinking about where this type of class falls within dagster, I did not feel that it sits as a data asset, neither did I feel it was part of job. I felt that it sits as an external resources that a could be leveaged by a data asset, or job.

After some sleuthing around in the dagster documentation, I came across [Resources](https://docs.dagster.io/concepts/resources). Here's what a resource is

> Resources are objects that are shared across the implementations of multiple software-defined assets and ops and that can be plugged in after defining those ops and assets.
> 
> Resources typically model external components that assets and ops interact with. For example, a resource might be a connection to a data warehouse like Snowflake or a service like Slack.

## One apparent downside

Looking at some of the examples provided by dagster, the only downside is that resources do not feature prominently on asset graphs, which is a bit dissapointing, hopefully they will find a way to feature them more prominently. The asset/lineage graphs are the one of the most powerful and useful aspects of dagster.