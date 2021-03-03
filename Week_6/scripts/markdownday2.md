Rmarkdown Day 2
================
Nyssa
3/2/2021

# Introduction

Today, we will use palmer penguins to manipulate figures in RMarkdown

# Load libraries

``` r
library(palmerpenguins)
library(tidyverse)
library(kableExtra)
```

# Make a plot

``` r
PenguinFigure<-penguins %>%
  ggplot(aes(x = species, y = flipper_length_mm, color = island))+
  geom_boxplot()

PenguinFigure
```

<div class="figure" style="text-align: center">

<img src="C:/Users/nyssa/Desktop/Repositories/Spring-2021/Week_6/outputPenguinFig-1.png" alt="This is a boxplot of penguins"  />

<p class="caption">

This is a boxplot of penguins

</p>

</div>

# Make a table

We are looking at bill length of **Gentoo** penguins from Biscoe.

``` r
penguins %>%
  group_by(species) %>%
  summarise(billmean = mean(bill_length_mm, na.rm = TRUE)) %>%
  kbl() %>% # make it a kable table
  #kable_classic()
  kable_paper() %>%
  row_spec(2, bold = T, color = "white", background = "red")
```

<table class=" lightable-paper" style="font-family: &quot;Arial Narrow&quot;, arial, helvetica, sans-serif; margin-left: auto; margin-right: auto;">

<thead>

<tr>

<th style="text-align:left;">

species

</th>

<th style="text-align:right;">

billmean

</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

Adelie

</td>

<td style="text-align:right;">

38.79139

</td>

</tr>

<tr>

<td style="text-align:left;font-weight: bold;color: white !important;background-color: red !important;">

Chinstrap

</td>

<td style="text-align:right;font-weight: bold;color: white !important;background-color: red !important;">

48.83382

</td>

</tr>

<tr>

<td style="text-align:left;">

Gentoo

</td>

<td style="text-align:right;">

47.50488

</td>

</tr>

</tbody>

</table>
