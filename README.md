# OMIS_482_Project
Group A repository for OMIS 482 R Studio project 
---
title: "the_movie_reviewers"
author: "Gary Dhami, Francisco Lozano, Amelasky Mendez, Tyler Williams, Rachel Worden"
date: "`r format(Sys.time(), '%d %B, %Y')`" 
output: 
  html_document:
    
    theme: flatly
    toc: TRUE
    toc_float: TRUE
    code_download: TRUE
editor_options: 
  chunk_output_type: console
---

```{r setup, include=FALSE, cache = F}
knitr::opts_chunk$set(
  echo = TRUE,
  error = TRUE,
  warning= FALSE,
  message= FALSE)

## Introduction
Hi, we are a group of movie reviewers! We pick a movie every month, watch it, and get together to discuss it. We love the movies so much that we wanted to ask what makes a certain movie successful? 

Using the movies dataset below, our group plans to analyze what factors affect the success of a movie. We believe a movie is successful by how much revenue a movie makes. But that is not all. By analyzing what determines success we can get a better idea of what other variables make a movie a hit. Determining this would allow movie producers to know what they can do to maximize success for their movies. We also plan to look at general trends in the movie industry to see what other patterns exist in the data. The analysis is done using data from an excel file and will be manipulated and visualized using tidyverse.

## Iporting the data
```{r, echo=F}
library(tidyverse)
df <- read_csv("movies_project.csv")
print(movies_project_)
```

## Tidying the data
Before we can manipulate the dataset and start to analyze the data, we need to tidy it up! We noticed that the columns "keywords", "index", "overview", "homepage", "ID", "Tagline","runtime" and Cast." We have decided to omit these columns because they add no value to our goal of trying to figure out what impacts a movie's success. These categories are mostly character/text values that do not allow us to measure descriptive statistics. In order to find the answers to our questions we plan to use mostly integer values. 


#Ideas: 
In the column "status" filter by released only 
Status column look for correlation between released and months 
Min, max, mean, standard deviation, of revenue 
language and country 
popularity(?)


## Questions we have 
Is there a correlation between budget and the amount of revenue a movie makes? 
Is there a correlation between 
What is the most popular genre? 
Is there a correlation between popularity and release date
Is there a correlation between how successful a movie is and their production company? 
Is there a correlation between movie ratings and the revenue amount?
```{r}
movies_project_ %>% 
  group_by(revenue) %>% 
  summarise(average = mean(revenue))
```


```{r}

Used_Data <- select(movies_project_,2,7:8,10:14,15:17,19:21)

select(Used_Data, max(revenue))
