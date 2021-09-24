# OMIS_482_Project
Group A repository for OMIS 482 R Studio project 
---
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
```

## Introduction
Hi, we are a group of movie reviewers! We pick a movie every month, watch it, and get together to discuss it. We love the movies so much that we wanted to ask what makes a certain movie successful? 

Using the movies dataset below, our group plans to analyze what factors affect the success of a movie. We believe a movie is successful by how much revenue a movie makes. But that is not all. By analyzing what determines success we can get a better idea of what other variables make a movie a hit. Determining this would allow movie producers to know what they can do to maximize success for their movies. We also plan to look at general trends in the movie industry to see what other patterns exist in the data. The analysis is done using data from an excel file and will be manipulated and visualized using tidyverse.

## Iporting the data:
```{r, echo=T}
library(tidyverse)
df <- read_csv("movies_project.csv")
print(movies_project_)
```

## Tidying the data:
Before we can manipulate the dataset and start to analyze the data, we need to tidy it up! We noticed that the columns "keywords", "index", "overview", "homepage", "ID", "Tagline","runtime" and Cast." We have decided to omit these columns because they add no value to our goal of trying to figure out what impacts a movie's success. These categories are mostly character/text values that do not allow us to measure descriptive statistics. In order to find the answers to our questions we plan to use mostly integer values. We want to make sure we abide by "rule of 3" ensuring each variable has its own column, row, cell. Because our data set is not in the tidyverse package, we had to assign our data frame to the name "movies." Because our dataset goes all the way back to 1930 and even predicts films to 2029, we found that using our data set from 1980 to 2017 would give us a more accurate look at how film has evolved.
```{r}

movies <-select(movies_project_,2,3,7:8,10:14,16:17,18,20,21)

bad_data <-select(movies_project_,1,4,5,6,9,13,15,19)

movies <- movies %>% separate(director,into = c("director_first_name","director_last_name"))

select(movies, "director")

select(movies, "vote_average")

rm(usable_data)
print(movies)
view(movies)

movies <- movies %>% separate(release_date, into = c("month", "day", "year"), sep = "/", convert= "TRUE")

movies %>% 
  filter(release_date >= "1980-01-01" & release_date <= "2017-12-31") 

movies %>% 
  filter(status=="Released")




```



```{r}

```
## Ideas:
In the column "status" filter by released only 
Status column look for correlation between released and months -stick with one variable ( revenue)
Min, max, mean, standard deviation, of revenue 
language and country 
popularity(?)

how does it fit in the overall idea(research question)

```
```
## Questions we have:

Is there a correlation between budget and the amount of revenue a movie makes? 
Is there a correlation between 
What is the most popular genre? 
Is there a correlation between popularity and release date
Is there a correlation between how successful a movie is and their production company? 
Is there a correlation between movie ratings and revenue?


```{r}
movies_project_ %>% 
  group_by(revenue) %>% 
  summarise(average = mean(revenue))
```


```

```
## Mapping:
```{r}
ggplot(movies)+
  geom_point(mapping = aes(x=revenue, y=genre))


```
## Calculations:

```{r}

movies %>% 
  filter(!is.na(revenue)) %>% 
  summarise(count=n(),avg.rev=mean(revenue),median.rv=median(revenue),max_rev=max(revenue),min.rev=min(revenue),sd.rev=sd(revenue)) %>% 

movies %>% 
  filter(!is.na(revenue)) %>% 
  summarise(count=n(),avg.rev=mean(revenue)


movies %>% 
  group_by(genres)
  summarise_(max.rev=max(revenue)) %>%
    
movies %>% 
    filter(!is.na(revenue)) %>% 
    summarise(avg.rev=mean(revenue))

```








