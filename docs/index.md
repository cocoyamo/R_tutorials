--- 
title: "Hello and welcome to our RStudio journey!"
author: "Moya"
date: "2024-10-15"
output: 
  bookdown::gitbook: 
    output_dir: "docs"
site: bookdown::bookdown_site
documentclass: book
bibliography: [book.bib, packages.bib]
url: https://cocoyamo.github.io/R_tutorials
description: |
  This is a RStudio tutorial. 
link-citations: yes
github-repo: cocoyamo/R_tutorials
knitr:
  opts_chunk: 
    fig.show: "hold"
    fig.path: "figures/"
---



# Introduction

Hi there! I'm a student (though not for much longer) who has had a love-hate relationship with RStudio. It's been a journey of both struggle and excitement.

I frequently use statistical analyses like t-tests, ANOVAs, and linear regressions. I'm also passionate about creating graphs in RStudio. That's why I've decided to document my journey here—it'll save me from digging through old files to copy code whenever I need to perform a new analysis.

Occasionally, I use RStudio for amusing projects, such as creating national flags, just for fun. You'll likely see some of these creative endeavors here.

Feel free to leave comments or suggestions. I’m still a beginner in the fascinating world of R and am eager to learn new things!

Best, Moya

Reykjavik, 2024

# RStudio Environment and Installation

*first thing first: `install` and `library`*

I wish someone had used this analogy when I was learning R Studio for the very first time.

People are constantly saying "Oh you need to **install** this package", and therefore I install every package every time I use R Studio.

Then people will ask you to "call the package out" using a 'library' function.

These two things inside R Studio confused me a lot in the beginning, (and I was mocked by a TA who was very inconsiderate of people who have never learned coding before), hopefully here you can find some answers. And I will not mock you. I swear. I know the struggles.

I now think of this as making a sandwich. Pick whatever sandwich you like. I will do a peanut butter and chocolate sandwich here.

So, imagine you will make a peanut butter and chocolate sandwich. You need ingredients. So you went to a nearby grocery store to purchase *chocolate spread*, *peanut butter*, and *toast*. (Feel free to switch to any other food you like, also please do not follow my recipe if you are allergic to peanuts or chocolate!)

This step (getting ingredients from a store) is called `install`.

Then, you go back to your kitchen and pull these ingredients out from your reusable bag, this action is similar to the `library` function.

Let's assume these ingredients will never run out. (What a heaven!) Then, the next time you want the peanut butter and chocolate sandwich, all you need to do is pull out these ingredients again. **There is no need to go back to the store every time you want it, you already have it in your kitchen!**

Therefore, whenever you need to use some package you have not used before, you need to `install` them first. Then afterward, the only thing you need to do is to use the `library` function to pull this magical stuff out of your bag.

Okay, I hope you are still with me, and not already in the kitchen looking for your chocolate spread.

# Data Import and Reading

Let's import our data!

## Import Your Data

**Note: If this is your first time import data and your data is from an Excel file, remember to type `install.packages("readxl")` in your coding space first.**


``` r
install.packages("readxl")
```


``` r
library(readxl)
```

There are, of course, tons of ways to import your data, but the following is what I use most often.

I click "Import Dataset" in the top-right corner of the Environment box. Then choose "Import", select "From Excel" (or "From Text" if I have a `.csv` file), and use "Browse" in the top-right corner to pick the file I want to import.

You can either double-click the file or click it once and then click the "Open" at the bottom-right.

The middle part is the **Data Preview** section, where you can see your data. Don't import the wrong file! (I've done that multiple times, especially when I'm lazy about giving files proper names 😅)

Next, in the bottom-right corner, you'll see a section called **Code Preview**.

The code may look something like this (but not identical, because, hopefully, we're using different file names).


``` r
library(readxl)
weather_math <- read_excel("~/Documents/R_tutorials/example files/weather_math.xlsx")
View(weather_math)
```

Now you've seen the **Code Preview** section, at the end of it, there's a tiny icon that looks like a clipboard. What do you do? **CLICK IT!**

Great Job!!

Now you've copied the code necessary to import your file. Press **Import** in the bottom-right.

Go back to the coding section. Paste it (Ctrl/Command + v) into the coding section (the top-left section of the interface).

(Let's hope RStudio never change their default interface or I'll have to rewrite this part.😅)

Also, you can sometimes use `head()` to see the first few rows of your data, just to make sure everything was imported correctly.


``` r
head(weather_math)
```

```
## # A tibble: 6 × 3
##      id day   score
##   <dbl> <chr> <dbl>
## 1     1 sunny     9
## 2     2 sunny     8
## 3     3 sunny     7
## 4     4 sunny     8
## 5     5 sunny     8
## 6     6 sunny     8
```

Or you could just type in the data's name.


``` r
weather_math
```

```
## # A tibble: 20 × 3
##       id day   score
##    <dbl> <chr> <dbl>
##  1     1 sunny     9
##  2     2 sunny     8
##  3     3 sunny     7
##  4     4 sunny     8
##  5     5 sunny     8
##  6     6 sunny     8
##  7     7 sunny     6
##  8     8 sunny     5
##  9     9 sunny     3
## 10    10 sunny     4
## 11     1 rainy     1
## 12     2 rainy     3
## 13     3 rainy     5
## 14     4 rainy     7
## 15     5 rainy     6
## 16     6 rainy     5
## 17     7 rainy     6
## 18     8 rainy     7
## 19     9 rainy     5
## 20    10 rainy     3
```

### Weather Math Data Explanation

Let's take a peek at this data, so you'll have a better grasp of our future examples.


``` r
weather_math
```

```
## # A tibble: 20 × 3
##       id day   score
##    <dbl> <chr> <dbl>
##  1     1 sunny     9
##  2     2 sunny     8
##  3     3 sunny     7
##  4     4 sunny     8
##  5     5 sunny     8
##  6     6 sunny     8
##  7     7 sunny     6
##  8     8 sunny     5
##  9     9 sunny     3
## 10    10 sunny     4
## 11     1 rainy     1
## 12     2 rainy     3
## 13     3 rainy     5
## 14     4 rainy     7
## 15     5 rainy     6
## 16     6 rainy     5
## 17     7 rainy     6
## 18     8 rainy     7
## 19     9 rainy     5
## 20    10 rainy     3
```

This is a made-up data. Ten imaginary people participated in this imaginary research. They took a math test on both a rainy day and a sunny day, and their scores were recorded. The first column represents the participant number, the second column shows the weather (either sunny or rainy), and the third column contains their scores.

## Dataset packages

### babynames

There are various data packages available in R, and we can easily access them by installing the appropriate package. For example, we can install a package called `babynames` .

This package contains baby names in the US from the year 1880 to year 2017.

Let's take a look.


``` r
install.packages("babynames")
```


``` r
library(babynames)
babynames
```

```
## # A tibble: 1,924,665 × 5
##     year sex   name          n   prop
##    <dbl> <chr> <chr>     <int>  <dbl>
##  1  1880 F     Mary       7065 0.0724
##  2  1880 F     Anna       2604 0.0267
##  3  1880 F     Emma       2003 0.0205
##  4  1880 F     Elizabeth  1939 0.0199
##  5  1880 F     Minnie     1746 0.0179
##  6  1880 F     Margaret   1578 0.0162
##  7  1880 F     Ida        1472 0.0151
##  8  1880 F     Alice      1414 0.0145
##  9  1880 F     Bertha     1320 0.0135
## 10  1880 F     Sarah      1288 0.0132
## # ℹ 1,924,655 more rows
```

RStudio creates a separate page for the data when we use `View()`. We can see that there are 5 columns: `year`, `sex`, `name`, `n`, and `prop`.

Wait, what is `prop`?

When we encounter questions like this, we can type `?dataset` or `?function` on the Console. In this case, we typed `?babynames`.

After hitting enter, the Help screen on the right side will display some information. Upon reading the explanation of this dataset, we learn that `prop` refers to `n` divided by the total number of babies of that sex with that name born in that year.

### starwars

There are also built-in datasets within the `dplyr` package. For example, there is a dataset called `starwars`.

We can import it with just a few lines of code, simply by calling the `dplyr` package where `starwars` dataset is stored.


``` r
install.packages("dplyr")
```


``` r
library(dplyr)
```


``` r
starwars
```

```
## # A tibble: 87 × 14
##    name     height  mass hair_color skin_color
##    <chr>     <int> <dbl> <chr>      <chr>     
##  1 Luke Sk…    172    77 blond      fair      
##  2 C-3PO       167    75 <NA>       gold      
##  3 R2-D2        96    32 <NA>       white, bl…
##  4 Darth V…    202   136 none       white     
##  5 Leia Or…    150    49 brown      light     
##  6 Owen La…    178   120 brown, gr… light     
##  7 Beru Wh…    165    75 brown      light     
##  8 R5-D4        97    32 <NA>       white, red
##  9 Biggs D…    183    84 black      light     
## 10 Obi-Wan…    182    77 auburn, w… fair      
## # ℹ 77 more rows
## # ℹ 9 more variables: eye_color <chr>,
## #   birth_year <dbl>, sex <chr>,
## #   gender <chr>, homeworld <chr>,
## #   species <chr>, films <list>,
## #   vehicles <list>, starships <list>
```

## Ways to Check Data

These functions are commonly used for inspecting datasets.

-   `View()` opens a new page to display the datasets.

-   `glimpse()`, `head()`, `tail()`, `dim()`, and `slice()` provide different ways to explore data.

You can also check the dimensions of your datasets using `ncol()` and `nrow()`. Both can be displayed at once by using `dim()`.

# Overview of Tidyverse and Core Functions

I really love `tidyverse`. It's a game changer. The three packages I use most often from `tidyverse` are:

1.  `ggplot2`
2.  `dplyr`
3.  `tidyr`

But first, let's clarify what `tidyverse` is.

`Tidyverse` is a collection of packages that makes data transformation and visualization (and therefore, my life) easier. Under the `tidyverse` umbrella, we can handle data like pros.

We'll dive into `ggplot2` in a later chapter. For now, let's focus on `dplyr` and `tidyr` first.

**If you haven't use `tidyverse` before, you need to install the package first.**


``` r
install.packages("tidyverse")
install.packages("dplyr")
install.packages("tidyr")
```

Next, don't forget to **load** your packages uding the `library()` function.


``` r
library("tidyverse")
library("dplyr")
library("tidyr")
```

Now, you're all set.

Before jumping into the functions, let's meet a funny-looking friend: *The pipe* (`%>%` / `|>`).

They look like this:


``` r
%>%
|>
```

In my humble opinion, this is one of the greatest analogies of this century. Although it doesn't look like a real pipe, it functions like one.

Let's use an example to see how it works.

## pipe example

We use the `babynames` package mentioned above to demonstrate the use of the pipe.

We can take a look at the data again.


``` r
babynames
```

```
## # A tibble: 1,924,665 × 5
##     year sex   name          n   prop
##    <dbl> <chr> <chr>     <int>  <dbl>
##  1  1880 F     Mary       7065 0.0724
##  2  1880 F     Anna       2604 0.0267
##  3  1880 F     Emma       2003 0.0205
##  4  1880 F     Elizabeth  1939 0.0199
##  5  1880 F     Minnie     1746 0.0179
##  6  1880 F     Margaret   1578 0.0162
##  7  1880 F     Ida        1472 0.0151
##  8  1880 F     Alice      1414 0.0145
##  9  1880 F     Bertha     1320 0.0135
## 10  1880 F     Sarah      1288 0.0132
## # ℹ 1,924,655 more rows
```

Now, let's say we want to see the names of babies born in the year 2000.


``` r
babynames %>%
	filter(year == 2000)
```

```
## # A tibble: 29,769 × 5
##     year sex   name          n    prop
##    <dbl> <chr> <chr>     <int>   <dbl>
##  1  2000 F     Emily     25953 0.0130 
##  2  2000 F     Hannah    23080 0.0116 
##  3  2000 F     Madison   19967 0.0100 
##  4  2000 F     Ashley    17997 0.00902
##  5  2000 F     Sarah     17697 0.00887
##  6  2000 F     Alexis    17629 0.00884
##  7  2000 F     Samantha  17266 0.00866
##  8  2000 F     Jessica   15709 0.00787
##  9  2000 F     Elizabeth 15094 0.00757
## 10  2000 F     Taylor    15078 0.00756
## # ℹ 29,759 more rows
```

Here you'll see all the baby names from 2000!

In the code, I used the pipe (`%>%`) to direct my dataset (`babynames`) into the next function, `filter()`.

Inside the `filter()` function, I specified that I wanted to see only babies born in the year 2000. In other words, I **filtered** out all the rows in the `year` column except those with the value '2000'.

The great thing about the pipe (`%>%` / `|>`) is that you can chain multiple operations together. Just like water flows from east to west, you can direct your data from one operation to the next.

Let's try it out.


``` r
babynames %>%
	filter(year == 2000) %>%
	filter(sex == "F")
```

```
## # A tibble: 17,653 × 5
##     year sex   name          n    prop
##    <dbl> <chr> <chr>     <int>   <dbl>
##  1  2000 F     Emily     25953 0.0130 
##  2  2000 F     Hannah    23080 0.0116 
##  3  2000 F     Madison   19967 0.0100 
##  4  2000 F     Ashley    17997 0.00902
##  5  2000 F     Sarah     17697 0.00887
##  6  2000 F     Alexis    17629 0.00884
##  7  2000 F     Samantha  17266 0.00866
##  8  2000 F     Jessica   15709 0.00787
##  9  2000 F     Elizabeth 15094 0.00757
## 10  2000 F     Taylor    15078 0.00756
## # ℹ 17,643 more rows
```

Here, we added `"F"` inside quotes because it's a character, not a number. We need to specify this so that RStudio can understands what we mean.

Now, the data is shows female babies born in year 2000.

We can also achieve this result in another way.


``` r
babynames %>%
 filter(year == 2000 & sex == "F")
```

```
## # A tibble: 17,653 × 5
##     year sex   name          n    prop
##    <dbl> <chr> <chr>     <int>   <dbl>
##  1  2000 F     Emily     25953 0.0130 
##  2  2000 F     Hannah    23080 0.0116 
##  3  2000 F     Madison   19967 0.0100 
##  4  2000 F     Ashley    17997 0.00902
##  5  2000 F     Sarah     17697 0.00887
##  6  2000 F     Alexis    17629 0.00884
##  7  2000 F     Samantha  17266 0.00866
##  8  2000 F     Jessica   15709 0.00787
##  9  2000 F     Elizabeth 15094 0.00757
## 10  2000 F     Taylor    15078 0.00756
## # ℹ 17,643 more rows
```

Let's explore more data transformations in the next chapter.

# Data Cleaning and Transformation

Here is a dataset for superheros that I downloaded from [here](https://github.com/dariomalchiodi/superhero-datascience/blob/master/content/data/heroes.csv?plain=1).


``` r
library(readr)
setwd  ("~/Documents/R_tutorials")
heroes <- read_delim("example files/heroes.csv", 
    delim = ";", escape_double = FALSE, trim_ws = TRUE)
View(heroes)
```

Note that the spreadsheet is in `.csv` format. Therefore, when importing data, we should choose `From Text(readr)` instead of `From Text(Excel)`.

However, as you may notice from the `Preview`, the data is not ideal -- it appears as a single row, with all the information packed into one.

To resolve this, we can click on `Delimiter` and select `Semicolon`, telling RStudio that the columns in this dataset are separated by semicolons (`;`) rather than commas or tabs.

Once the data is properly imported, we can see that it contains information about many superheroes. If we want a clearer view to focus on the data that we need for analysis, we can use `select()` function to choose specific columns.


``` r
heroes |>
  select(c("Name", "Height", "Weight", "Gender", "Eye color", "Hair color", "Strength", "Intelligence"))
```

```
## # A tibble: 735 × 8
##    Name       Height Weight Gender `Eye color`
##    <chr>       <dbl>  <dbl> <chr>  <chr>      
##  1 A-Bomb       203.  442.  M      Yellow     
##  2 Abraxas       NA    NA   M      Blue       
##  3 Abominati…   203.  442.  M      Green      
##  4 Adam Monr…    NA    NA   M      Blue       
##  5 Agent 13     173.   61.0 F      Blue       
##  6 Air-Walker   189.  108.  M      Blue       
##  7 Agent Bob    178.   81.4 M      Brown      
##  8 Abe Sapien   191.   65.4 M      Blue       
##  9 Abin Sur     186.   90.9 M      Blue       
## 10 Angela        NA    NA   F      <NA>       
## # ℹ 725 more rows
## # ℹ 3 more variables: `Hair color` <chr>,
## #   Strength <dbl>, Intelligence <chr>
```

Now, if we want to filter for superheroes with high intelligence, we can use the `filter()` function.

This function allows us to extract rows that meet specified conditions.


``` r
heroes |>
  filter(Intelligence == "high")
```

```
## # A tibble: 144 × 12
##    Name       Identity `Birth place` Publisher
##    <chr>      <chr>    <chr>         <chr>    
##  1 Abraxas    Abraxas  Within Etern… Marvel C…
##  2 Abe Sapien Abraham… <NA>          Dark Hor…
##  3 Angela     <NA>     <NA>          Image Co…
##  4 Yoda       Yoda     <NA>          George L…
##  5 Zatanna    Zatanna… <NA>          DC Comics
##  6 Yellowjac… Hank Pym Elmsford, Ne… Marvel C…
##  7 X-Man      Nate Gr… American Nor… Marvel C…
##  8 Wonder Wo… Diana P… Themyscira    DC Comics
##  9 Watcher    Uatu     <NA>          Marvel C…
## 10 Warlock    Adam Wa… The Beehive,… Marvel C…
## # ℹ 134 more rows
## # ℹ 8 more variables: Height <dbl>,
## #   Weight <dbl>, Gender <chr>,
## #   `First appearance` <dbl>,
## #   `Eye color` <chr>, `Hair color` <chr>,
## #   Strength <dbl>, Intelligence <chr>
```

In fact, `select()` and `filter()` can be combined.

Let's look for female superheroes with strength over 50 and high intelligence levels.


``` r
heroes |>
  select(c("Name", "Gender", "Strength", "Intelligence")) |>
  filter(Gender == "F" & Strength >= 50 & Intelligence == "high")
```

```
## # A tibble: 18 × 4
##    Name           Gender Strength Intelligence
##    <chr>          <chr>     <dbl> <chr>       
##  1 Angela         F           100 high        
##  2 Wonder Woman   F           100 high        
##  3 Valkyrie       F            95 high        
##  4 Supergirl      F           100 high        
##  5 Silk Spectre … F            55 high        
##  6 She-Hulk       F           100 high        
##  7 Power Girl     F           100 high        
##  8 Phoenix        F           100 high        
##  9 Lady Bullseye  F            75 high        
## 10 Jean Grey      F            80 high        
## 11 Granny Goodne… F           100 high        
## 12 Giganta        F            90 high        
## 13 Faora          F            95 high        
## 14 Donna Troy     F            95 high        
## 15 Cheetah III    F           100 high        
## 16 Cat            F            90 high        
## 17 Captain Marvel F            90 high        
## 18 Big Barda      F           100 high
```

If we want to adjust this filter to include superheroes with either `good` or `high` intelligence, there are two ways to do it.

The first method is to use the `|` operator (which means "or"). The second method is to use the `%in%` operator, which selects data that fits either of the specified conditions.


``` r
# method 1
heroes |>
  select(c("Name", "Gender", "Strength", "Intelligence")) |>
  filter(Gender == "F" & Strength >= 50) |>
  filter(Intelligence == "high" | Intelligence == "good")
```

```
## # A tibble: 47 × 4
##    Name         Gender Strength Intelligence
##    <chr>        <chr>     <dbl> <chr>       
##  1 Angela       F           100 high        
##  2 Wonder Girl  F            90 good        
##  3 Wonder Woman F           100 high        
##  4 Valkyrie     F            95 high        
##  5 Vindicator   F            65 good        
##  6 Thor Girl    F            85 good        
##  7 T-X          F            65 good        
##  8 Supergirl    F           100 high        
##  9 Stargirl     F            80 good        
## 10 Spider-Gwen  F            55 good        
## # ℹ 37 more rows
```


``` r
# method 2
heroes |>
  select(c("Name", "Gender", "Strength", "Intelligence")) |>
  filter(Gender == "F" & Strength >= 50) |>
  filter(Intelligence %in% c("high", "good"))
```

```
## # A tibble: 47 × 4
##    Name         Gender Strength Intelligence
##    <chr>        <chr>     <dbl> <chr>       
##  1 Angela       F           100 high        
##  2 Wonder Girl  F            90 good        
##  3 Wonder Woman F           100 high        
##  4 Valkyrie     F            95 high        
##  5 Vindicator   F            65 good        
##  6 Thor Girl    F            85 good        
##  7 T-X          F            65 good        
##  8 Supergirl    F           100 high        
##  9 Stargirl     F            80 good        
## 10 Spider-Gwen  F            55 good        
## # ℹ 37 more rows
```

Both methods give us the same result. While the first method is more straightforward, I personally feel cooler using the second one😎.

Now, let's calculate the superheroes' Body Mass Index (BMI). The formula is:

$$
BMI = weight(kg)/height(m)^2
$$

So, we need to :

-   Add a new column that converts height from centimeters to meters.

-   Square the height in meters.

-   Divide weight by the square of the height.


``` r
heroes |>
  mutate(Height_m = Height / 100) |> # convert heights from cm to m
  mutate(Height_m2 = Height_m*Height_m) |> # square of the heights
  mutate(BMI = Weight / Height_m2) # divide weights by the squrare of the heights
```

```
## # A tibble: 735 × 15
##    Name       Identity `Birth place` Publisher
##    <chr>      <chr>    <chr>         <chr>    
##  1 A-Bomb     Richard… Scarsdale, A… Marvel C…
##  2 Abraxas    Abraxas  Within Etern… Marvel C…
##  3 Abominati… Emil Bl… Zagreb, Yugo… Marvel C…
##  4 Adam Monr… <NA>     <NA>          NBC - He…
##  5 Agent 13   Sharon … <NA>          Marvel C…
##  6 Air-Walker Gabriel… Xandar, a pl… Marvel C…
##  7 Agent Bob  Bob      <NA>          Marvel C…
##  8 Abe Sapien Abraham… <NA>          Dark Hor…
##  9 Abin Sur   <NA>     Ungara        DC Comics
## 10 Angela     <NA>     <NA>          Image Co…
## # ℹ 725 more rows
## # ℹ 11 more variables: Height <dbl>,
## #   Weight <dbl>, Gender <chr>,
## #   `First appearance` <dbl>,
## #   `Eye color` <chr>, `Hair color` <chr>,
## #   Strength <dbl>, Intelligence <chr>,
## #   Height_m <dbl>, Height_m2 <dbl>, …
```

We can either break this down into multiple steps or, for simplicity, combine everything into one line of code.


``` r
heroes |>
  mutate(BMI = Weight / (Height/100)^2) 
```

```
## # A tibble: 735 × 13
##    Name       Identity `Birth place` Publisher
##    <chr>      <chr>    <chr>         <chr>    
##  1 A-Bomb     Richard… Scarsdale, A… Marvel C…
##  2 Abraxas    Abraxas  Within Etern… Marvel C…
##  3 Abominati… Emil Bl… Zagreb, Yugo… Marvel C…
##  4 Adam Monr… <NA>     <NA>          NBC - He…
##  5 Agent 13   Sharon … <NA>          Marvel C…
##  6 Air-Walker Gabriel… Xandar, a pl… Marvel C…
##  7 Agent Bob  Bob      <NA>          Marvel C…
##  8 Abe Sapien Abraham… <NA>          Dark Hor…
##  9 Abin Sur   <NA>     Ungara        DC Comics
## 10 Angela     <NA>     <NA>          Image Co…
## # ℹ 725 more rows
## # ℹ 9 more variables: Height <dbl>,
## #   Weight <dbl>, Gender <chr>,
## #   `First appearance` <dbl>,
## #   `Eye color` <chr>, `Hair color` <chr>,
## #   Strength <dbl>, Intelligence <chr>,
## #   BMI <dbl>
```

Either approach will give the same result, so you can shoose whichever suits you best.

> **Tip:** By default, new columns appear on the right, but if you prefer them on the left (to make it easier to check when there are many columns), you can specify `.after = "column_name"` in `mutate()` to position the new column immediately after a chosen column.


``` r
heroes |>
  mutate(BMI = Weight / (Height/100)^2, .before = 1) 
```

```
## # A tibble: 735 × 13
##      BMI Name        Identity    `Birth place`
##    <dbl> <chr>       <chr>       <chr>        
##  1 107.  A-Bomb      Richard Mi… Scarsdale, A…
##  2  NA   Abraxas     Abraxas     Within Etern…
##  3 107.  Abomination Emil Blons… Zagreb, Yugo…
##  4  NA   Adam Monroe <NA>        <NA>         
##  5  20.3 Agent 13    Sharon Car… <NA>         
##  6  30.4 Air-Walker  Gabriel Lan Xandar, a pl…
##  7  25.6 Agent Bob   Bob         <NA>         
##  8  17.9 Abe Sapien  Abraham Sa… <NA>         
##  9  26.4 Abin Sur    <NA>        Ungara       
## 10  NA   Angela      <NA>        <NA>         
## # ℹ 725 more rows
## # ℹ 9 more variables: Publisher <chr>,
## #   Height <dbl>, Weight <dbl>, Gender <chr>,
## #   `First appearance` <dbl>,
## #   `Eye color` <chr>, `Hair color` <chr>,
## #   Strength <dbl>, Intelligence <chr>
```

If, for example, I want the new `BMI` column to appear immediately after the `Name` column, I can write `.after = "Name"` to achieve that.


``` r
heroes |>
  mutate(BMI = Weight / (Height/100)^2, .after = "Name")
```

```
## # A tibble: 735 × 13
##    Name          BMI Identity    `Birth place`
##    <chr>       <dbl> <chr>       <chr>        
##  1 A-Bomb      107.  Richard Mi… Scarsdale, A…
##  2 Abraxas      NA   Abraxas     Within Etern…
##  3 Abomination 107.  Emil Blons… Zagreb, Yugo…
##  4 Adam Monroe  NA   <NA>        <NA>         
##  5 Agent 13     20.3 Sharon Car… <NA>         
##  6 Air-Walker   30.4 Gabriel Lan Xandar, a pl…
##  7 Agent Bob    25.6 Bob         <NA>         
##  8 Abe Sapien   17.9 Abraham Sa… <NA>         
##  9 Abin Sur     26.4 <NA>        Ungara       
## 10 Angela       NA   <NA>        <NA>         
## # ℹ 725 more rows
## # ℹ 9 more variables: Publisher <chr>,
## #   Height <dbl>, Weight <dbl>, Gender <chr>,
## #   `First appearance` <dbl>,
## #   `Eye color` <chr>, `Hair color` <chr>,
## #   Strength <dbl>, Intelligence <chr>
```

> **Tip:** Instead of using `select()` to manually keep only the columns you've used during `mutate()` process, you can use `.keep = "used"`. This tells RStudio to retain only the columns involved in the mutation process.


``` r
heroes |>
  mutate(BMI = Weight / (Height/100)^2, .keep = "used") 
```

```
## # A tibble: 735 × 3
##    Height Weight   BMI
##     <dbl>  <dbl> <dbl>
##  1   203.  442.  107. 
##  2    NA    NA    NA  
##  3   203.  442.  107. 
##  4    NA    NA    NA  
##  5   173.   61.0  20.3
##  6   189.  108.   30.4
##  7   178.   81.4  25.6
##  8   191.   65.4  17.9
##  9   186.   90.9  26.4
## 10    NA    NA    NA  
## # ℹ 725 more rows
```

Now, I want to reflect on a personal experience from elementary school. After annual health exams, students were categorized based on their BMI, and teachers would tell those who were categorized as "overweight", "obese", or "underweight" to be cautious about their BMI.

I'm not going to dive into the mental toll this caused me as a child who often got labeled "overweight", but let's use this as an example to categorize numerical data into groups in RStudio.

According to [Wikipedia](https://en.wikipedia.org/wiki/Body_mass_index), BMI categories are (simply) defined as follows:

| BMI                     | Category           |
|-------------------------|--------------------|
| \< 18.5                 | underweight (UW)   |
| 18.5 - 24.9 (inclusive) | normal weight (NW) |
| 25.0 - 29.9 (inclusive) | overweight (OW)    |
| \>= 30                  | obese (OB)         |

Now, let's categorize the superheroes based on their BMI values.

We will use `mutate()` to create a new column for their BMI category.


``` r
heroes |>
  mutate(BMI = Weight / (Height/100)^2, .after = "Name") |> 
  mutate(BMI_status = case_when(BMI < 18.5 ~ "underweight",
                                BMI >= 18.5 & BMI <= 24.9 ~ "normal_weight",
                                BMI >= 25 & BMI <= 29.9 ~ "overweight",
                                BMI >= 30 ~ "obese"), .after = "BMI") -> heroes2
```


``` r
heroes2 |>
  count(BMI_status)
```

```
## # A tibble: 5 × 2
##   BMI_status        n
##   <chr>         <int>
## 1 normal_weight   201
## 2 obese           127
## 3 overweight      114
## 4 underweight      41
## 5 <NA>            252
```

Once this is done, we can see how many superheroes are categorized as obese.

You may notice a row with `<NA>` values, which occurs when the data is incomplete. If we don't want to include rows with missing BMI values in our analysis, we can remove them by using `na.omit()`. This makes further analysis much easier.


``` r
heroes2 |>
  na.omit() |>
  count(BMI_status) 
```

```
## # A tibble: 4 × 2
##   BMI_status        n
##   <chr>         <int>
## 1 normal_weight    48
## 2 obese            40
## 3 overweight       40
## 4 underweight      13
```

You can also **update** your dataset to exclude missing values. Here, I assigned the cleaner version of my data: `heroes2`.


``` r
heroes2 |>
  na.omit() -> heroes2
```

If you want to further categorize the data, such as determining how many male and female superheroes are categorized as obese or underweight, you can do so by adding another column to the `count()` function.


``` r
heroes2 |>
  count(Gender, BMI_status)
```

```
## # A tibble: 8 × 3
##   Gender BMI_status        n
##   <chr>  <chr>         <int>
## 1 F      normal_weight    26
## 2 F      obese             1
## 3 F      overweight        1
## 4 F      underweight      12
## 5 M      normal_weight    22
## 6 M      obese            39
## 7 M      overweight       39
## 8 M      underweight       1
```

Alternatively, you can use `group_by()`, which we will cover in a future chapters, to achieve the same result.


``` r
heroes2 |>
  group_by(Gender) |>
  count(BMI_status)
```

```
## # A tibble: 8 × 3
## # Groups:   Gender [2]
##   Gender BMI_status        n
##   <chr>  <chr>         <int>
## 1 F      normal_weight    26
## 2 F      obese             1
## 3 F      overweight        1
## 4 F      underweight      12
## 5 M      normal_weight    22
## 6 M      obese            39
## 7 M      overweight       39
## 8 M      underweight       1
```

Lastly, let's discuss renaming columns. You don't need to go back to the original `.csv` or `.xlsx` files to change column names!

For example, if we want to change the `Hair color` column to `Hair_color` and `Eye color` colun to `Eye_color`, we can do this directly in RStudio using the `colnames()` function.

**rename()??**

> another way (add later)


``` r
colnames(heroes2)[colnames(heroes2) == "Hair color"] <- "Hair_color"
colnames(heroes2)[colnames(heroes2) == "Eye color"] <- "Eye_color"
```

# Data Wrangling and Reshaping

## pivot

Pivoting can seem abstract at first, but it's incredibly useful when you have a **wide data** and need to conduct further analysis. RStudio often works best with data in a long format. Let's start with an example:

| Name  | Height (cm) | Age |
|-------|-------------|-----|
| Lily  | 150         | 20  |
| Mary  | 160         | 18  |
| John  | 156         | 14  |
| Steve | 180         | 15  |
| Amy   | 174         | 16  |

This is straightforward: new rows can be added as more people are recorded. But sometimes, you'll encounter **wide data**, such as:

| Name  | Eng_C1 | Eng_C2 | Eng_C3 | Math_C1 | Math_C2 | Math_C3 |
|-------|--------|--------|--------|---------|---------|---------|
| Kelly | 90     | 95     | 80     | 90      | 80      | 97      |
| Liam  | 70     | 80     | 94     | 80      | 89      | 79      |
| Henry | 79     | 80     | 85     | 96      | 92      | 90      |

Here, students' scores in English and Math from Chapter 1 (C1) to Chapter 3 (C3) are spread across multiple columns. This wide format can be tricky for analysis, and **pivoting** the data into a **long format** is often more effective.

### example: converting wide to long format

Let's first create a data first.


``` r
performance_original <- data.frame(
   Name = c("Kelly", "Liam", "Henry", "Alice", "Jake", "Dan"),
   Eng_C1 = c(90, 70, 79, 98, 81, 79),
   Eng_C2 = c(95, 80, 80, 93, 93, 70),
   Eng_C3 = c(80, 94, 85, 89, 73, 91),
   Math_C1 = c(90, 80, 96, 83, 92, 68),
   Math_C2 = c(80, 89, 92, 72, 84, 83),
   Math_C3 = c(97, 79, 90, 74, 70, 92))
performance_original
```

```
##    Name Eng_C1 Eng_C2 Eng_C3 Math_C1 Math_C2
## 1 Kelly     90     95     80      90      80
## 2  Liam     70     80     94      80      89
## 3 Henry     79     80     85      96      92
## 4 Alice     98     93     89      83      72
## 5  Jake     81     93     73      92      84
## 6   Dan     79     70     91      68      83
##   Math_C3
## 1      97
## 2      79
## 3      90
## 4      74
## 5      70
## 6      92
```

To convert this data into a long format, where each row represents one exam score, we can use `pivot_longer()`. The goal is to get data that looks like this:

| Name          | Subject | Score |
|---------------|---------|-------|
| Kelly         | Eng_C1  | 90    |
| Kelly         | Eng_C2  | 95    |
| Kelly         | Eng_C3  | 80    |
| Kelly         | Math_C1 | 90    |
| Kelly         | Math_C2 | 80    |
| Kelly         | Math_C3 | 97    |
| Liam          | Eng_C1  | 70    |
| Liam          | Eng_C2  | 80    |
| Liam          | Eng_C3  | 94    |
| Liam          | Math_C1 | 80    |
| Liam          | Math_C2 | 89    |
| Liam          | Math_C3 | 79    |
| Henry         | Eng_C1  | 79    |
| Henry         | Eng_C2  | 80    |
| ... and so on |         |       |

Here's the code to achieve that:


``` r
performance_original |>
  pivot_longer(!Name, names_to = "Subject", values_to = "Score") 
```

```
## # A tibble: 36 × 3
##    Name  Subject Score
##    <chr> <chr>   <dbl>
##  1 Kelly Eng_C1     90
##  2 Kelly Eng_C2     95
##  3 Kelly Eng_C3     80
##  4 Kelly Math_C1    90
##  5 Kelly Math_C2    80
##  6 Kelly Math_C3    97
##  7 Liam  Eng_C1     70
##  8 Liam  Eng_C2     80
##  9 Liam  Eng_C3     94
## 10 Liam  Math_C1    80
## # ℹ 26 more rows
```

We can see that the data format is now what we intended. Let's break down the key parts of the code used:

-   `!Name`: The `!` symbol tells RStudio to **exclude** the `Name` column from the pivot operation, meaning that we still want to keep the `Name` column intact in the dataset.

-   `names_to = "Subject"`: This argument specifies that we want to gather the multiple collumn names (e.g., `Eng_C1`, `Math_C1`, etc.) into a new column called `Subject`.

-   `values_to = "Score"`: This indicates that the values from the original columns (the actual exam scores) should be placed into a new column named `Score`.

These two arguments (`names_to` and `values_to`) allow us to compress multiple columns into one, transforming the data from a wide to a long format.

There are other ways to achieve the same result. The approach we used works well when the dataset doesn't have too many columns to exclude (in this case, just the `Name` column). However, if you have a large dataset with many columns to exclude, or if it's easier to specify the columns you want to compress directly, you can use a different method like `cols =`.

For example, you could list out the columns you want to gather explicitly, or use a range of column names depending on the situation. This flexibility allows you to choose the most efficient method based on your dataset's structure.


``` r
performance_original |>
  pivot_longer(cols = c("Eng_C1", "Eng_C2", "Eng_C3", "Math_C1", "Math_C2", "Math_C3"),
               names_to = "Subject", 
               values_to = "Score") -> performance
performance
```

```
## # A tibble: 36 × 3
##    Name  Subject Score
##    <chr> <chr>   <dbl>
##  1 Kelly Eng_C1     90
##  2 Kelly Eng_C2     95
##  3 Kelly Eng_C3     80
##  4 Kelly Math_C1    90
##  5 Kelly Math_C2    80
##  6 Kelly Math_C3    97
##  7 Liam  Eng_C1     70
##  8 Liam  Eng_C2     80
##  9 Liam  Eng_C3     94
## 10 Liam  Math_C1    80
## # ℹ 26 more rows
```

Now, let's dive a bit deeper into a more abstract concept.

If we want to **further split** our data, for instance, breaking down the `Subject` column into two new columns, like `Subject_em` (for subject name) and `Chapter` (for chapter number), we can use the `separate()` function to accomplish this.


``` r
performance |>
  separate(
    col = Subject, 
    into = c("Subject_em", "Chapter"),
    sep = "[^[:alnum:]]+",
    remove = TRUE,
    convert = FALSE) -> performance
performance
```

```
## # A tibble: 36 × 4
##    Name  Subject_em Chapter Score
##    <chr> <chr>      <chr>   <dbl>
##  1 Kelly Eng        C1         90
##  2 Kelly Eng        C2         95
##  3 Kelly Eng        C3         80
##  4 Kelly Math       C1         90
##  5 Kelly Math       C2         80
##  6 Kelly Math       C3         97
##  7 Liam  Eng        C1         70
##  8 Liam  Eng        C2         80
##  9 Liam  Eng        C3         94
## 10 Liam  Math       C1         80
## # ℹ 26 more rows
```

I know it looks scary, but please hear me out-- this function will become one of your best friends once you understand it😊.

As mentioned eariler, we want to separate our `Subject` column into `Subject_em` and `Chapter`. So, we use `col =` to specify the target column (in this case, `Subject`), and `into =` to define the names of the two new columns we want to create.

Now, let's demystify the seemingly bizarre-looking `sep = "[^[:alnum:]]+"` part. In general, this means **"one or more non-alphabet or non-numeric characters"**. Let's break it down:

-   `[:alnum:]` stands for **al**phabet (A-Z, a-z), and **num**bers (0-9).

-   `[^]` means **not include**.

-   `+` means **one or more**.

When we combine these, it means we're telling RStudio to look for **one or more things that are not alphabet nor number**. In this case, we want to find the underscore (`_`) and use it as the separation point.

We also see the parameters `remove = TRUE` and `convert = FALSE`. These are defaults in the `separate()` function, but let's briefly touch on them to understand what they do:

-   `remove = TRUE` means to delete the original column `Subject` column after separating it.

-   `convert = FALSE` ensures that RStudio doesn't automatically change the types of the new columns. For exapmle, if the separation produces numbers (e.g., separating `Eng_1` into `Eng` and `1`), setting `convert = TRUE` would make the new `1` column numeric. We can change the column type later if needed, but for now, we keep it `FALSE`.

Congratulations! You've now learned how to pivot wide-format data into long-format, and how to separate columns. (Even after 5 years of learning and using RStuido, I'm still amazed by its power. EVERY SINGLE TIME.)

If there's a `pivot_longer()`, there must be a `pivot_wider()`, right? Well, yes! But as I mentioned earlier, RStudio prefers long-format data for analysis and visualization. For that reason (and for I am not proficient with `pivot_wider()`), I'm focusing on `pivot_longer()` here since it's generally more useful for data analysis. (Maybe I'll dive into `pivot_wider()` when I'm more proficient with it, haha.)

## join

Another useful function when working with multiple datasets or files is combining them into one. Let's continue with our `performance` dataset, and imagine that we have documented students' Biology exam scores in another dataset.


``` r
performance_biology <- data.frame(
   Name = c("Kelly", "Liam", "Henry", "Alice", "Jake", "Dan"),
   Bio_C1 = c(80, 80, 83, 93, 80, 88),
   Bio_C2 = c(73, 76, 75, 77, 79, 83),
   Bio_C3 = c(90, 93, 94, 90, 81, 82))
```

We pull the original performance data and want to add the Biology columns to it.


``` r
performance_original |>
  left_join(performance_biology, by = "Name") 
```

```
##    Name Eng_C1 Eng_C2 Eng_C3 Math_C1 Math_C2
## 1 Kelly     90     95     80      90      80
## 2  Liam     70     80     94      80      89
## 3 Henry     79     80     85      96      92
## 4 Alice     98     93     89      83      72
## 5  Jake     81     93     73      92      84
## 6   Dan     79     70     91      68      83
##   Math_C3 Bio_C1 Bio_C2 Bio_C3
## 1      97     80     73     90
## 2      79     80     76     93
## 3      90     83     75     94
## 4      74     93     77     90
## 5      70     80     79     81
## 6      92     88     83     82
```

Here, we've successfully added the Biology columns to the original dataset. When dealing with multiple independent variables (columns), you can use `by = c("column1", "column2", …)` to specify the join basis.

Now, you might have guessed -- there is also a `right_join()` in RStudio. While I don't use it as often as `left_join()` in my usual data analysis, it's still important to understand the difference.

-   `left_join()`: keeps the data from the left dataset, even if there is no matching data on the right. If no match is found, it fills the right columns with `NA`.

-   `right_join()`: keeps the data from the right dataset, even if there is no matching data on the left. Again, unmatched data is filled with `NA`.

While these functions are simple, they're extremely powerful for combining datasets, and -- dare I say -- quite magical in what they can accomplish.

## bind

Besides left and right joins, there's another way to combine datasets: binding.


``` r
dataset1 <- data.frame(
  brand = c("1","2","3"),
  price = c(200, 300, 250),
  profit = c(100, 200, 200))
dataset2 <- data.frame(
  brand = c("1","2","3"),
  sales = c(20, 40, 60))
```

We have created two separate datassets. One contains a product's brand, price, and profit, and the other contains sales numbers. We can use `cbind()` (column bind) to merge these datasets side by side.


``` r
cbind(dataset1, dataset2) -> merged_data
merged_data
```

```
##   brand price profit brand sales
## 1     1   200    100     1    20
## 2     2   300    200     2    40
## 3     3   250    200     3    60
```

However, as you might notice, the column `brand` is repeated in the merged data. If this repetition doesn't affect your analysis, you can leave it. But if you prefer a cleaner result, you could opt to use `left_join()` instead, as it binds the data without duplicating columns.


``` r
dataset1 |>
  left_join(dataset2, by = "brand")
```

```
##   brand price profit sales
## 1     1   200    100    20
## 2     2   300    200    40
## 3     3   250    200    60
```

# Statistical Analysis

## t-test

### example: Independent t-test

Let's start by analyzing the difference in strength between superheroes from different publishers.


``` r
heroes2 |>
  group_by(Publisher) |>
  summarize(mean_strength = mean(Strength, na.rm = TRUE))
```

```
## # A tibble: 4 × 2
##   Publisher     mean_strength
##   <chr>                 <dbl>
## 1 DC Comics              64.6
## 2 George Lucas           33.3
## 3 Image Comics           60  
## 4 Marvel Comics          43.1
```

We can observe from the dataset that the mean strength of superheroes from different publishers seems to vary. But, is this difference **statistically significant**?

Let’s conduct a t-test to compare heroes from **DC Comics** and **Marvel Comics**.


``` r
heroes2 |>
  filter(Publisher %in% c("Marvel Comics", "DC Comics")) |>
  group_by(Publisher) |>
  summarize(Strengths = list(Strength)) |>
  with(t.test(Strengths[[1]], Strengths[[2]], paired = FALSE))
```

```
## 
## 	Welch Two Sample t-test
## 
## data:  Strengths[[1]] and Strengths[[2]]
## t = 2.8807, df = 32.441, p-value =
## 0.00698
## alternative hypothesis: true difference in means is not equal to 0
## 95 percent confidence interval:
##   6.297946 36.652054
## sample estimates:
## mean of x mean of y 
##    64.600    43.125
```

That looks complicated. I do not normally use that.

#### Step 1: Subset the data

First, we need to subset the data into two groups: one for DC Comics and one for Marvel Comics.


``` r
subset(heroes2, Publisher == "Marvel Comics") -> marvel
subset(heroes2, Publisher == "DC Comics") -> DC
```

#### Step 2: Conduct the t-test

Next, we use the `t.test()` function to calculate the difference in strength between the two groups.


``` r
heroes2 |>
  with(t.test(marvel$Strength, DC$Strength, paired = F))
```

```
## 
## 	Welch Two Sample t-test
## 
## data:  marvel$Strength and DC$Strength
## t = -2.8807, df = 32.441, p-value =
## 0.00698
## alternative hypothesis: true difference in means is not equal to 0
## 95 percent confidence interval:
##  -36.652054  -6.297946
## sample estimates:
## mean of x mean of y 
##    43.125    64.600
```

From the results, we see that there is **no significant difference** in the strength levels between superheroes from DC Comics and Marcel Comics.

> **Important Note: Independent vs Paired t-test**

In this case, we are comparing superheroes from two different groups (DC vs Marvel), which makes this an **independent** t-test. A **paired t-test** would be inappropriate here because the two groups consist of entirely different individuals.

However, when comparing repeated measurements on the **same group** of people (e.g., before and after a task), a paired t-test would be more suitable.

### example: Paired t-test

Remember the performance data from earlier? Let's say we want to analyze if there's any difference in exam scores between **Chapter 1** and **Chapter 3** for the same group of students.

We can perform a paired t-test in this case:


``` r
# group them first
subset(performance, Subject_em == "Eng" & Chapter == "C1") -> eng_c1
subset(performance, Subject_em == "Eng" & Chapter == "C3") -> eng_c3

performance |>
  with(t.test(eng_c1$Score, eng_c3$Score, paired = T))
```

```
## 
## 	Paired t-test
## 
## data:  eng_c1$Score and eng_c3$Score
## t = -0.44114, df = 5, p-value = 0.6775
## alternative hypothesis: true mean difference is not equal to 0
## 95 percent confidence interval:
##  -17.06789  12.06789
## sample estimates:
## mean difference 
##            -2.5
```

This test checks whether the students' performance significantly changed between Chapter 1 and Chapter 3. The **paired** argument ensures that the test accounts for the fact that these are the same individuals in both conditions.

## ANOVA

ANOVA is a powerful statistical tool used to compare the means of multiple groups. It helps in determining whether the observed differences between group means are statistically significant. Here's how we can use `anova_test()` in RStudio to perform various types of ANOVA.


``` r
library(rstatix)
```


``` r
heroes2 |>
  anova_test(
    dv = # dependent variable, 
    wid = # subject name/id, 
    type = NULL, # default: type II ANOVA
    between = # between-subject independent variable,
    within = # within-subject independent variable,
    effect.size = "ges", 
    error = NULL,
    white.adjust = FALSE,
    observed = NULL,
    detailed = TRUE)
```

-   `detailed = TRUE`: Requests a more detailed statistical output. `FALSE` is the default.

-   `type = NULL`: Type 2 ANOVA is the default. You can change this to `1` or `3` based on your needs.

-   `effect.size =`: Computes effect size, the default is using generalizing eta squared (`ges`) or partial eta squared (`pes`). to compute.

    -   The `Help` section in RStudio says I could choose both, but I haven't figure out how to do so yet.

-   For ANCOVA, you can add `covariate =` to include continuous variables as covariates. Insert it below `within =`, above `type =`.

### one-way ANOVA

One-way ANOVA is used when we have one independent variable (IV) and one dependent variable (DV).

#### example 1: Strength \~ Intelligence

-   IV: Intelligence

-   DV: Strength


``` r
heroes2 |>
  anova_test(
    dv = Strength, 
    wid = Name, 
    between = Intelligence,
    detailed = T)
```

```
## ANOVA Table (type II tests)
## 
##         Effect      SSn    SSd DFn DFd     F
## 1 Intelligence 8758.544 129262   4 136 2.304
##       p p<.05   ges
## 1 0.062       0.063
```

#### example 2: Strength \~ Gender

-   IV: Gender

-   DV: Strength


``` r
heroes2 |>
  anova_test(
    dv = Strength, 
    wid = Name, 
    between = Gender,
    detailed = T)
```

```
## ANOVA Table (type II tests)
## 
##   Effect      SSn      SSd DFn DFd     F    p
## 1 Gender 3772.182 134248.4   1 139 3.906 0.05
##   p<.05   ges
## 1       0.027
```

### two-way ANOVA

Two-way ANOVA is used when we have two independent variables and one dependent variable. Here, we look at how these two IVs interact with each other.

#### example 1: Strength \~ BMI_status \* Gender


``` r
heroes2 |>
   anova_test(
    dv = Strength, 
    wid = Name, 
    between = c(Gender, BMI_status), 
    detailed = TRUE) 
```

```
## ANOVA Table (type III tests)
## 
##              Effect       SSn      SSd DFn
## 1       (Intercept) 68473.044 109803.3   1
## 2            Gender    51.278 109803.3   1
## 3        BMI_status  8413.707 109803.3   3
## 4 Gender:BMI_status  6885.839 109803.3   3
##   DFd      F        p p<.05      ges
## 1 133 82.938 1.11e-15     * 0.384000
## 2 133  0.062 8.04e-01       0.000467
## 3 133  3.397 2.00e-02     * 0.071000
## 4 133  2.780 4.40e-02     * 0.059000
```

> **Note:** Be mindful of the ANOVA type. Even if you don't specify a type, RStudio may default to type III ANOVA. If you prefer type II ANOVA, specify `type = 2`.

#### example 2: strength \~ gender \* BMI


``` r
heroes2 |>
  anova_test(
    dv = Strength, 
    wid = Name, 
    between = c(Gender, BMI), 
    detailed = T)
```

However, we would encounter an error here. Why is that?

**Step 1:** Check for mismatched variable types. For example, putting both **categorical** (e.g., `Gender`) and **numerical** (e.g., `BMI`) in the `between =` section.

**Solution 1**

-   **convert numerical variables into categorical variables**

    For example, you can classify BMI into levels like obese, overweight, normal, and underweight. (We did this in the previous section.)


``` r
# Solution 1
heroes2 |>
   anova_test(
    dv = Strength, 
    wid = Name, 
    between = c(Gender, BMI_status), 
    detailed = T)   
```

```
## ANOVA Table (type III tests)
## 
##              Effect       SSn      SSd DFn
## 1       (Intercept) 68473.044 109803.3   1
## 2            Gender    51.278 109803.3   1
## 3        BMI_status  8413.707 109803.3   3
## 4 Gender:BMI_status  6885.839 109803.3   3
##   DFd      F        p p<.05      ges
## 1 133 82.938 1.11e-15     * 0.384000
## 2 133  0.062 8.04e-01       0.000467
## 3 133  3.397 2.00e-02     * 0.071000
## 4 133  2.780 4.40e-02     * 0.059000
```

**Solution 2**

-   **use ANCOVA (Analysis of Covariance)** (continuous \* category \~ continuous)

    ANCOVA is suitable when you have **continuous variable** that you want to adjust for or control while analyzing the main effects of categorical independent variables. In ANCOVA, you can include the continuous variable as a covariate.


``` r
# Solution 2 (ANCOVA)
heroes2 |>
   anova_test(
    dv = Strength, 
    wid = Name, 
    between = Gender, 
    covariate = BMI,
    detailed = T)   
```

```
## ANOVA Table (type II tests)
## 
##   Effect       SSn      SSd DFn DFd      F
## 1    BMI 23336.275 110912.1   1 138 29.036
## 2 Gender    10.606 110912.1   1 138  0.013
##          p p<.05      ges
## 1 2.99e-07     * 1.74e-01
## 2 9.09e-01       9.56e-05
```

```         
In Solution 2, the BMI variable is used as a covariate. This allows you to account for the continuous variable (BMI) while examining the effect of gender on strength.
```

#### example 3: strength \~ gender \* Intelligence

Let us take a look at another example.

In the `heroes2` dataset, the `Intelligence` is a **categorical variable**. The intelligence levels of superheroes are labelled as `high`, `good`, `average`, `moderate`, and `low`.


``` r
heroes2 |>
  distinct(Intelligence)
```

```
## # A tibble: 5 × 1
##   Intelligence
##   <chr>       
## 1 moderate    
## 2 good        
## 3 high        
## 4 average     
## 5 low
```

Therefore, we should not encounter the same problem as example 2.


``` r
heroes2 |>
  anova_test(
    dv = Strength, 
    wid = Name, 
    between = c(Gender, Intelligence), 
    detailed = T)
```

However, we still see errors here. After examining **Step 1**, we can conclude that it is not the issue here. We can try to debug using the following methods:

**Step 2**

We examine both independent variables separately to ensure they are functioning properly individually. We can delete one of the variables each time for testing. (Although this is usually not the problem, it's still good practice to check.)

-   Checking the variable `Gender`


``` r
heroes2 |>
  anova_test(
    dv = Strength, 
    wid = Name, 
    between = Gender, 
    detailed = T)
```

```
## ANOVA Table (type II tests)
## 
##   Effect      SSn      SSd DFn DFd     F    p
## 1 Gender 3772.182 134248.4   1 139 3.906 0.05
##   p<.05   ges
## 1       0.027
```

-   Checking the variable `Intelligence`


``` r
heroes2 |>
  anova_test(
    dv = Strength, 
    wid = Name, 
    between = Intelligence, 
    detailed = T)
```

```
## ANOVA Table (type II tests)
## 
##         Effect      SSn    SSd DFn DFd     F
## 1 Intelligence 8758.544 129262   4 136 2.304
##       p p<.05   ges
## 1 0.062       0.063
```

Both variables look fine, and the code works smoothly when tested individually.

**Step 3**

We examine if there are any **missing values** in any of the category. (I often forgot about this step, and spend hours confused about why my ANOVA isn't ANOVAing...)


``` r
table(heroes2$Gender, heroes2$Intelligence)
```

```
##    
##     average good high low moderate
##   F      14   20    4   0        2
##   M      24   41   27   2        7
```

Here, we see that in female superheroes category, there is a zero for low intelligence level. This prevents the ANOVA from proceeding. Now that we have identified the problem, we can remove the `intelligence == "low"` from our analysis, as it hinders the process.


``` r
heroes2 |>
  filter(Intelligence != "low") |>
   anova_test(
    dv = Strength, 
    wid = Name, 
    between = c(Gender, Intelligence), 
    type = 2,
    detailed = T)   
```

```
## ANOVA Table (type II tests)
## 
##                Effect      SSn      SSd DFn
## 1              Gender 1982.076 126823.2   1
## 2        Intelligence 3719.933 126823.2   3
## 3 Gender:Intelligence  406.757 126823.2   3
##   DFd     F     p p<.05   ges
## 1 131 2.047 0.155       0.015
## 2 131 1.281 0.284       0.028
## 3 131 0.140 0.936       0.003
```

You might think: "I'll just add `group_by()` before the `anova_test()`." However, while this approach would not give you error message, it would not yield a **two-way ANOVA** as we intended. Instead, it would just separate the data into two groups before performing a **one-way ANOVA** on each. See the codes below:


``` r
heroes2 |>
  filter(Intelligence != "low") |>
  group_by(Gender) |>
   anova_test(
    dv = Strength, 
    wid = Name, 
    between = Intelligence, 
    detailed = T)   
```

```
## # A tibble: 2 × 10
##   Gender Effect   SSn    SSd   DFn   DFd     F
## * <chr>  <chr>  <dbl>  <dbl> <dbl> <dbl> <dbl>
## 1 F      Intel… 1564. 33535.     3    36  0.56
## 2 M      Intel… 2563. 93288.     3    95  0.87
## # ℹ 3 more variables: p <dbl>, `p<.05` <chr>,
## #   ges <dbl>
```

We can see that the result table differs from the two-way ANOVA table (refer to the upper table), and the numbers are also different (see `DFn` and `DFd` in both results).

### three-way ANOVA

#### example 1: Strength \~ Gender \* Intelligence \* BMI_status

If we want to add more independent variables, we can simply include additional column names in the `between =` section.


``` r
heroes2 |>
  filter(Intelligence != "low") |>
   anova_test(
    dv = Strength, 
    wid = Name, 
    between = c(Gender, Intelligence, BMI_status), 
    type = 2,
    detailed = T)   
```

```
## ANOVA Table (type II tests)
## 
##                           Effect       SSn
## 1                         Gender  1083.194
## 2                   Intelligence  3465.586
## 3                     BMI_status 16524.941
## 4            Gender:Intelligence  2703.193
## 5              Gender:BMI_status  8295.111
## 6        Intelligence:BMI_status  7715.048
## 7 Gender:Intelligence:BMI_status        NA
##        SSd DFn DFd     F        p p<.05   ges
## 1 96626.99   1 118 1.323 0.252000       0.011
## 2 96626.99   3 118 1.411 0.243000       0.035
## 3 96626.99   3 118 6.727 0.000314     * 0.146
## 4 96626.99   2 118 1.651 0.196000       0.027
## 5 96626.99   3 118 3.377 0.021000     * 0.079
## 6 96626.99   7 118 1.346 0.235000       0.074
## 7 96626.99   0 118    NA       NA  <NA>    NA
```

Note that if the independent variable is within-subject (in the case of a mixed analysis), we place the **within-subject** independent variables in the `within =` section. This is commonly used when analyzing experimental results, such as comparing test scores before learning and after learning. See below for more details on mixed ANOVA.

### mixed ANOVA

As mentioned, mixed ANOVA is often used for analyzing experimental results, as it allows for tracking individual changes over time, which is difficult to achieve with other methods.

Let's assume a high school wants to investigate whether different teaching styles affect students' exam scores. They conducted an experiments, dividing students into two groups: one received education in a fun way, while the other was taught in a more rigid manner. The school also tested the students before and after learning the subject.

-   **Independent variable**: teaching style (fun/rigid), exam time (before/after)

-   **Dependent variable**: exam score


``` r
teaching_style <- data.frame(
  student = c("1", "2", "3", "4", "5", "6", 
              "1", "2", "3", "4", "5", "6"),
  style = as.factor(c("fun", "rigid", "fun", "rigid", "fun", "rigid",
                      "fun", "rigid", "fun", "rigid", "fun", "rigid")),
  timing = as.factor(c("before", "before", "before", "before", "before", "before", 
                       "after", "after", "after", "after", "after", "after")),
  score = c(50, 13, 10, 70, 23, 70, 70, 90, 66, 83, 80, 80))
```

The data frame is created with 6 students: 3 participated in the `fun` teaching style, and 3 experienced the `rigid` style. All of their `before` and `after` exam scores were recorded.

Here, we want to see if the teaching style influenced their exam scores.


``` r
teaching_style |>
   anova_test(
    dv = score, 
    wid = student, 
    between = style, 
    within = timing,
    detailed = T)   
```

```
## ANOVA Table (type II tests)
## 
##         Effect DFn DFd       SSn      SSd
## 1  (Intercept)   1   4 41418.750 1278.667
## 2        style   1   4   954.083 1278.667
## 3       timing   1   4  4524.083 1876.667
## 4 style:timing   1   4    90.750 1876.667
##         F       p p<.05   ges
## 1 129.569 0.00034     * 0.929
## 2   2.985 0.15900       0.232
## 3   9.643 0.03600     * 0.589
## 4   0.193 0.68300       0.028
```

From the analysis, we can observe that teaching style does not have a significant impact on their scores. However, there is a main effect of the `timing` variable.

By examining the mean scores across different times, we can see that students performed better after learning, regardless of the teaching style applied.


``` r
teaching_style |>
  group_by(timing) |>
  summarise(mean_score = mean(score))
```

```
## # A tibble: 2 × 2
##   timing mean_score
##   <fct>       <dbl>
## 1 after        78.2
## 2 before       39.3
```

**Additional notes**

-   Use `filter()` to choose specific groups for analysis.

    For instance, `filter(Intelligence %in% c("high", "good")` or `filter(Hair_color != "No Hair")`.

-   `group_by()` is useful if you want to examine ANOVA results for both conditions' simultaneously.

## Post hoc analysis

After conducting an ANOVA, if we want to explore the data further (assuming the ANOVA results are significant), we can perform a post hoc analysis.

I used to be confused about the difference between post hoc analysis and pairwise t-test. It's important to note that post hoc analysis is done **after** obtaining a significant result from ANOVA, while pairwise t-test can be applied to any two groups of data.


``` r
teaching_style |>
 group_by(style) |>
  pairwise_t_test(
    score ~ timing,
    paired = TRUE,
    p.adjust.method = "bonferroni")
```

```
## # A tibble: 2 × 11
##   style .y.   group1 group2    n1    n2
## * <fct> <chr> <chr>  <chr>  <int> <int>
## 1 fun   score after  before     3     3
## 2 rigid score after  before     3     3
## # ℹ 5 more variables: statistic <dbl>,
## #   df <dbl>, p <dbl>, p.adj <dbl>,
## #   p.adj.signif <chr>
```

In this example, we use post hoc analysis:

-   `score ~ timing`: Here, we put the **dependent variable** on the left and the **independent variable** on the right. We are comparing `scores` across different exam `timing`.

-   `paired =`: Set this to `TRUE` if it's a repeated measures design , and `FALSE` if it's a between-subject design (i.e., different participants in each group).

-   `p.adjust.method`: This argument allows us to choose a method for adjusting p values.

## Regression analysis

# Data Visualization

## bar chart

Let's use a new dataset as an example here. In the `lego_sample` dataset, there are various LEGO sets, pieces, recommended retail prices, prices on Amazon, sizes, and more.


``` r
library(openintro)
lego_sample
```

```
## # A tibble: 75 × 14
##    item_number set_name    theme pieces  price
##          <dbl> <chr>       <chr>  <dbl>  <dbl>
##  1       10859 My First L… DUPL…      6   4.99
##  2       10860 My First R… DUPL…      6   4.99
##  3       10862 My First C… DUPL…     41  15.0 
##  4       10864 Large Play… DUPL…     71  50.0 
##  5       10867 Farmers' M… DUPL…     26  20.0 
##  6       10870 Farm Anima… DUPL…     16   9.99
##  7       10872 Train Brid… DUPL…     26  25.0 
##  8       10875 Cargo Train DUPL…    105 120.  
##  9       10876 Spider-Man… DUPL…     38  30.0 
## 10       10878 Rapunzel's… DUPL…     37  30.0 
## # ℹ 65 more rows
## # ℹ 9 more variables: amazon_price <dbl>,
## #   year <dbl>, ages <chr>, pages <dbl>,
## #   minifigures <dbl>, packaging <chr>,
## #   weight <chr>, unique_pieces <dbl>,
## #   size <chr>
```


``` r
lego_sample |>
  na.omit() |>
  ggplot(aes(x = packaging, y = pieces)) +
  geom_bar(stat = "summary", position = position_dodge(.8), width = .7, fill = "#BDD5EA") +
  geom_errorbar(stat = "summary", position = position_dodge(0.5), width = .12) +
  facet_wrap(theme ~ ., scales = "free") 
```

![plot of chunk unnamed-chunk-72](figure/unnamed-chunk-72-1.png)

It seems that a lot has happened in the code chunk, and there's quite a bit of information presented by the graphs.

Let's walk through the code.

-   in `ggplot()`, we specify the `x` and `y` axes.

-   `geom_bar()` creates the bar chart.

    -   `stat = "summary"` calculates the mean value of the y-axis variable, which is `pieces` in this case.

    -   `position = position_dodge()` separates the bars to avoid overlap.

    -   `width =` sets the width of the bars. If `width = 1`, the bars will stick together.

    -   `fill =` can be a single color (as in this example) or another variable to create color variation.

-   `geom_errorbar()` calculates and displays the standard error on the graph.

    -   The `width`, `fill`, and `position` arguments work similarly to those in `geom_bar()`.

-   `facet_wrap()` separates the graphs by the variable you specify.

    -   You can use `<your variable> ~ .` or `~ <your variable>`.

    -   The `scales = "free"` option adjusts the y-axis for each graph based on its data. However, it's not always recommended, as explained below.

Now, let's analyze the graph. We can observe a few things:

1.  The graphs are separated by different LEGO themes: "DUPLO®", "Friends", and "City".

2.  In the "Friends" and "City" collections, there are only data from the Box packaging method, indicating that there is no data where the LEGO is from "City" or "Friends" collections using Plastic box.

3.  The y-axis scales differ across the graphs. Although the program automatically adjusts the scale based on the data, this might hinder important information. For example, in the "City" and "Friends" collections, the difference in pieces is harder to discern. We will explain how to address this in the **scales** section.

If we do not want to use `facet_wrap()` for separating graphs, we can use other ways to distinguish between categories. For exapmle, if we assign a variable to `fill =`, we can ask RStudio to fill different colors for each category.


``` r
lego_sample |>
  na.omit() |>
  ggplot(aes(x = packaging, y = pieces, fill = theme)) +
  geom_bar(stat = "summary", position = position_dodge(.8), width = .7) +
  geom_errorbar(stat = "summary", position = position_dodge(.8), width = .12) 
```

![plot of chunk unnamed-chunk-73](figure/unnamed-chunk-73-1.png)

## scatter plot

``` r
lego_sample |>
  na.omit() |>
  ggplot(aes(x = pieces, y = price, color = theme, shape = theme)) +
  geom_point() +
  geom_smooth(method = "lm")
```

![plot of chunk unnamed-chunk-74](figure/unnamed-chunk-74-1.png)

Let's examine the code:

In the `aes()` section, I've used both color **AND** shape to differentiate by `theme`. Usually, one type of distinction is sufficient, but sometimes colors alone may be hard to differentiate. In such cases, adding another feature (e.g., shape) can improve readability.

-   `geom_point()` is used to display individual data point, creating the scatter plot.

-   `geom_smooth()` adds trend lines to the data. By setting `method = "lm"`, we apply a linear model, which results in a straight trend line.



Next, let's try a different dataset: `movies`. This dataset is part of the `openintro` package and contains several datasets.


``` r
install.packages("openintro")
```


``` r
library("openintro")
movies
```

```
## # A tibble: 140 × 5
##    movie         genre score rating box_office
##    <chr>         <chr> <dbl> <chr>       <dbl>
##  1 2Fast2Furious acti…  48.9 PG-13      127.  
##  2 28DaysLater   horr…  78.2 R           45.1 
##  3 AGuyThing     rom-…  39.5 PG-13       15.5 
##  4 AManApart     acti…  42.9 R           26.2 
##  5 AMightyWind   come…  79.9 PG-13       17.8 
##  6 AgentCodyBan… acti…  57.9 PG          47.8 
##  7 Alex&Emma     rom-…  35.1 PG-13       14.2 
##  8 AmericanWedd… come…  50.7 R          104.  
##  9 AngerManagem… come…  62.6 PG-13      134.  
## 10 AnythingElse  rom-…  63.3 R            3.21
## # ℹ 130 more rows
```

The dataset contains 5 columns and 140 rows, representing movies released in 2003. The columns include the movie title, genre, score (by critics on a scale 0-100), MPAA rating, and `box_office` (millions of dollars earned at the box office in the US and Canada.)

You can type `movies` in the `help` section in the bottom-right panel for a detailed description of the data.


``` r
movies |> 
  ggplot(aes(x = box_office, y = score)) + geom_point() +
  geom_smooth(method = "lm")
```

![plot of chunk unnamed-chunk-77](figure/unnamed-chunk-77-1.png)

From the graph, we can see a positive relationship between the `box_office` and `score`.

## box plot

A box plot helps us visualize the interquartile range in our data. This is useful when comparing a categorical variable with numerical values.


``` r
movies |>
  ggplot(aes(x = score, y = rating)) +
  geom_boxplot() 
```

![plot of chunk unnamed-chunk-78](figure/unnamed-chunk-78-1.png)

## histogram


``` r
movies |>
  ggplot(aes(x = score)) +
  geom_histogram()
```

![plot of chunk unnamed-chunk-79](figure/unnamed-chunk-79-1.png)


``` r
movies |>
  ggplot(aes(x = score)) +
  geom_histogram(binwidth = 1)
```

![plot of chunk unnamed-chunk-80](figure/unnamed-chunk-80-1.png)


``` r
movies |>
  ggplot(aes(x = score)) +
  geom_histogram(binwidth = 10)
```

![plot of chunk unnamed-chunk-81](figure/unnamed-chunk-81-1.png)

-   `binwidth`: controls the thickness of the bars, if the bars are too thin (`binwidth = 1`), you'll see individual data points clearly. However, this may not be ideal for observing general trends in the data. Therefore, I recommend experimenting with different `binwidth` values to find what works best for your data.


``` r
movies |>
  ggplot(aes(x = score, color = rating)) +
  geom_histogram(binwidth = 5)
```

![plot of chunk unnamed-chunk-82](figure/unnamed-chunk-82-1.png)

In the histogram, the `color` argument controls the **outline** color of the bar, while `fill` controls the interior color of the bars.


``` r
movies |>
  ggplot(aes(x = score, fill = rating)) +
  geom_histogram(binwidth = 5)
```

![plot of chunk unnamed-chunk-83](figure/unnamed-chunk-83-1.png)

## density plot

Density plots are similar to connecting the peaks of a histogram to form a smooth line, providing a clearer view of the data distribution.


``` r
movies |>
  ggplot(aes(x = score)) +
  geom_density()
```

![plot of chunk unnamed-chunk-84](figure/unnamed-chunk-84-1.png)

We can also separate data into subcategories.


``` r
movies |>
  ggplot(aes(x = score, fill = rating, color = rating)) +
  geom_density()
```

![plot of chunk unnamed-chunk-85](figure/unnamed-chunk-85-1.png)

However, this graph might be hard to read due to overlapping data. For instance, the values for ratings `R` and `PG-13` are not clearly distinguishable. To resolve this, we can adjust the `transparancy` of the graph.


``` r
movies |>
  ggplot(aes(x = score, fill = rating, color = rating)) +
  geom_density(alpha = 0.5)
```

![plot of chunk unnamed-chunk-86](figure/unnamed-chunk-86-1.png)

Alternatively, we can use `geom_density_ridges()` to further separate the data, improving readability.


``` r
install.packages("ggridges")
```


``` r
library(ggridges)

movies |>
  ggplot(aes(x = score,y = rating,  fill = rating, color = rating)) +
  geom_density_ridges(alpha = 0.6)
```

![plot of chunk unnamed-chunk-88](figure/unnamed-chunk-88-1.png)

## mixed graphs

We will now create mixed graphs using another package: `GGally`.


``` r
install.packages("GGally")
```


``` r
library(GGally)
```

### categorical \* numeric

這邊的資料在下面才有介紹，不知道是要把介紹提前還是怎樣：Ｄ


``` r
lego_sample
```

```
## # A tibble: 75 × 14
##    item_number set_name    theme pieces  price
##          <dbl> <chr>       <chr>  <dbl>  <dbl>
##  1       10859 My First L… DUPL…      6   4.99
##  2       10860 My First R… DUPL…      6   4.99
##  3       10862 My First C… DUPL…     41  15.0 
##  4       10864 Large Play… DUPL…     71  50.0 
##  5       10867 Farmers' M… DUPL…     26  20.0 
##  6       10870 Farm Anima… DUPL…     16   9.99
##  7       10872 Train Brid… DUPL…     26  25.0 
##  8       10875 Cargo Train DUPL…    105 120.  
##  9       10876 Spider-Man… DUPL…     38  30.0 
## 10       10878 Rapunzel's… DUPL…     37  30.0 
## # ℹ 65 more rows
## # ℹ 9 more variables: amazon_price <dbl>,
## #   year <dbl>, ages <chr>, pages <dbl>,
## #   minifigures <dbl>, packaging <chr>,
## #   weight <chr>, unique_pieces <dbl>,
## #   size <chr>
```

Let's say we want to explore the relationship between the price of Lego sets (`price`, a **continuous numeric variable**) and their size (`size`, a **categorical variable**).


``` r
lego_sample |>
  ggpairs(columns = c("price", "size"))
```

![plot of chunk unnamed-chunk-92](figure/unnamed-chunk-92-1.png)

The top-left panel of the resulting plot shows the distribution of the `price` -- a univariate plot of `price` vs. itself. The bottom-right panel shows the distribution of `size`, where RStudio counts the number of Lego sets in each category (`large` and `small`).

The top-right panel presents a boxplot of `price` vss `size`, which is commonly used for visualizing the relationship between **numeric variable** and **categorical variable**. Similarly, the bottom-left panel shows the distribution of prices within each `size` category, but it doesn't specify which data belongs to `large` or `small` categories (possibly because I'm just couldn't figure it out yet).

### numeric \* numeric

Next, let’s examine two **numerical variables**: the recommended retail price (`price`) and the price on Amazon (`amazon_price`).


``` r
lego_sample |>
  ggpairs(columns = c("price", "amazon_price"))
```

![plot of chunk unnamed-chunk-93](figure/unnamed-chunk-93-1.png)

This graph differs from the previous one because both variables are numeric. The top-left panel shows a density plot of the recommended retail `price`, while the bottom-right panel does the `amazon_price`. Although the distributions are similar, they are not identical.

In the bottom-right panel, a scatter plot shows a strong positive correlation between the two prices, as reflected by the correlation coefficient displayed in the top-right panel.

### numeric \* numeric \* numeric

What if we add one more numeric variable? We can take a look at the relationship between `price`, `amazon_price`, and `minifigures` (after converting `minifigures` back to a numeric variable).


``` r
lego_sample |>
  ggpairs(columns = c("price", "amazon_price", "minifigures"))
```

![plot of chunk unnamed-chunk-94](figure/unnamed-chunk-94-1.png)

This gives us a clearer overview of the relationship between multiple numeric variables.

If we want to add more information, like trend lines or confidence intervals, we can use the following code:


``` r
lego_sample |>
  ggpairs(columns = c("price", "amazon_price", "minifigures"),
          lower = list(continuous = wrap("smooth")))
```

![plot of chunk unnamed-chunk-95](figure/unnamed-chunk-95-1.png)

Here, we simply add `lower =` and specify what we want.

-   `lower =`: Controls the display of the lower part of the graph.

-   `wrap()`: Helps us to specify what we want for continuous numeric variables.

-   `smoooth`: Creates trend lines on the scatter plot (similar to `geom_smooth`).

-   `continuous =`: Specifies that the data is continuous, allowing us to adjust how it's displayed.

Note that the default correlation method is `"pearson"`. To change this, you can add the `mehtod =` argument to specify another correlation method.


``` r
lego_sample |>
  ggpairs(columns = c("price", "amazon_price", "minifigures"),
          upper = list(continuous = wrap("cor", method = "spearman")),
          lower = list(continuous = wrap("smooth")))
```

![plot of chunk unnamed-chunk-96](figure/unnamed-chunk-96-1.png)

For the `upper =` part of the graph:

-   `upper = "cor"`: Displays the correlation coefficients in the upper panels.

### numeric \* numeric \* numeric \* categorical

Now that we've explore several ways to plot numeric variables, let's add a categorical variable here. A good way to differentiate groups is by assigning colors to categories in the `aes()` function.

#you have learned a few ways to deal with plots inside `ggpairs()`. Let us add some colors on it (literally).

Here's an example:


``` r
lego_sample |>
  ggpairs(columns = c("price", "amazon_price", "minifigures", "size"),
          mapping = aes(color = size, alpha = .7),
          upper = list(continuous = wrap("cor", method = "spearman")),
          lower = list(continuous = wrap("smooth")))
```

![plot of chunk unnamed-chunk-97](figure/unnamed-chunk-97-1.png)

Adding transparency (`alpha =`) helps reduce clutter in the plot by making overlapping graphs easier to distinguish.

Below is another coding style to achieve the same result, which I prefer. It separates the column selection step from the plotting step, making the code easier to manage.


``` r
lego_sample |>
  select(price, amazon_price, minifigures, size) |>
  ggpairs(mapping = aes(color = size, alpha = .7),
          upper = list(continuous = wrap("cor", method = "spearman")),
          lower = list(continuous = wrap("smooth")))
```

![plot of chunk unnamed-chunk-98](figure/unnamed-chunk-98-1.png)

Although `ggpairs()` is useful for exploring relationships between different variables (e.g., comparing test scores), it can sometimes become overwhelming with too many plots. If you're unsure whether this approach is the best for your data, I recommend creating individual plots first (e.g., density or box plots) before mixing everything together. This will help clarify the relationships you want to explore and the most effective ways to visualize them.

## additional features on the plot

### labels

A good graph includes informative labels. While you could add titles, subtitles, and other labels in separate software after downloading the graph, it's more efficient and reduces the chance of errors if you add all the labels directly in RStudio.


``` r
movies |>
  ggplot(aes(x = score,y = rating,  fill = rating, color = rating)) +
  geom_density_ridges(alpha = 0.6) +
  labs(
		title = "Movie Scores of Different MPAA Ratings.",
		subtitle = "Put your subtitle here because I don't know what to say.",
		x = "Movie Score",
		y = "MPAA Rating",
		fill = "Rating",
		color = "Rating",
		caption = "sources: movies from openintro")
```

![plot of chunk unnamed-chunk-99](figure/unnamed-chunk-99-1.png)

If you prefer not to show certain labels, you can aslo specify this in the code and let the program remove them for you.


``` r
movies |>
  ggplot(aes(x = score,y = rating,  fill = rating, color = rating)) +
  geom_density_ridges(alpha = 0.6) +
  labs(
		x = NULL,
    fill = NULL,
		color = NULL,
		fill = NULL)
```

![plot of chunk unnamed-chunk-100](figure/unnamed-chunk-100-1.png)

For example, in the code chunk above, when we set the `x-axis` to `NULL`, the label disappears from the graph. However, if we don't specify the `y-axis` in the `labs()` function, the original label from the data will still appear.

Also, if you want to remove the legend, you can do so by adjusting the `theme()` function.


``` r
movies |>
  ggplot(aes(x = score,y = rating,  fill = rating, color = rating)) +
  geom_density_ridges(alpha = 0.6) +
  labs(x = NULL, y = NULL) + 
  theme(legend.position = "hide")
```

![plot of chunk unnamed-chunk-101](figure/unnamed-chunk-101-1.png)

## 不知道怎麼改label欸 頭痛 ㄞ 可以mutate但好麻煩呀

### colors

Let's demonstrate how to change colors in a graph with the `lego_sample` dataset!


``` r
lego_sample |>
  na.omit() |>
  ggplot(aes(x = size, y = price, fill = as.factor(minifigures))) +
  geom_bar(stat = "summary", position = "dodge")
```

![plot of chunk unnamed-chunk-102](figure/unnamed-chunk-102-1.png)

For easier demonstration, we will focus on LEGO sets with 1 to 3 minifigures.


``` r
lego_sample |>
  na.omit() |>
  filter(minifigures <= 3) |>
  ggplot(aes(x = size, y = price, fill = as.factor(minifigures))) +
  geom_bar(stat = "summary", position = "dodge")
```

![plot of chunk unnamed-chunk-103](figure/unnamed-chunk-103-1.png)

Now we're all set!


``` r
lego_sample |>
  na.omit() |>
  filter(minifigures <= 3) |>
  ggplot(aes(x = size, y = price, fill = as.factor(minifigures))) +
  geom_bar(stat = "summary", position = "dodge") +
  scale_fill_manual(values = c("darkblue","yellow","pink"))
```

![plot of chunk unnamed-chunk-104](figure/unnamed-chunk-104-1.png)

It's as simple as that! Also, note that you only need to specify each color once. For instance, although the colors `"darkblue"`, `"yellow"`, and `"pink"` appear twice in the graph, we only need to type them once in stead of using `values = c("darkblue", "yellow", "pink", "darkblue", "yellow", "pink")`.

If you don't want to use default colors but don't feel like manually selecting distinct colors each time, you can use pre-existing color palettes in RStudio.


``` r
install.packages("viridis")
```


``` r
library(viridis)
```

You can also add outlines to the bars in the chart to make them pop up more.


``` r
lego_sample |>
  na.omit() |>
  filter(minifigures <= 3) |>
  ggplot(aes(x = size, y = price, fill = as.factor(minifigures))) +
  geom_bar(stat = "summary", position = "dodge", color = "black") +
	scale_fill_viridis_d() 
```

![plot of chunk unnamed-chunk-107](figure/unnamed-chunk-107-1.png)

Note that we use `scale_fill_viridis_d()` here. If you're using `color =` instead of `fill =`, remember to switch to `scale_color_viridis_d()`.


``` r
lego_sample |>
  na.omit() |>
  filter(minifigures <= 3) |>
  ggplot(aes(x = size, y = price, color = as.factor(minifigures))) +
  geom_bar(stat = "summary", position = "dodge", fill = "white") +
	scale_color_viridis_d() 
```

![plot of chunk unnamed-chunk-108](figure/unnamed-chunk-108-1.png)

### scales

Now, let's look at some data from `heroes2` dataset.


``` r
heroes2 |>
  filter(Intelligence %in% c("good", "high")) |>
  ggplot(aes(x = Gender, y = Strength)) +
  geom_bar(stat = "summary", position = position_dodge(.8), width = .7) +
  geom_errorbar(stat = "summary", position = position_dodge(0.5), width = .12) +
  facet_wrap(Intelligence ~ ., scales = "free") 
```

![plot of chunk unnamed-chunk-109](figure/unnamed-chunk-109-1.png)

Take a quick glance at the chart. It seems like the `good` intelligence group has higher strength than the `high` intelligence group as the bar is higher.

But is that really the case?

Take a closer look at the two bar charts. The y-axis scales are different from one graph to another.

To verify, let's calculate the average strength for both groups.


``` r
heroes2 |>
  filter(Intelligence %in% c("good", "high")) |>
  group_by(Intelligence, Gender) |>
  summarise(mean_strength = mean(Strength))
```

```
## # A tibble: 4 × 3
## # Groups:   Intelligence [2]
##   Intelligence Gender mean_strength
##   <chr>        <chr>          <dbl>
## 1 good         F               34  
## 2 good         M               45.4
## 3 high         F               55  
## 4 high         M               57.0
```

We can see from the results that in the `good` intelligence group, the average strength of both genders is actually lower than in the `high` intelligence group. However, without paying attention to the y-axis, we might have gotten the wrong impression that the `good` intelligence group had higher strength than the `high` intelligence group.

To fix this issue, we can manually adjust the scale using `coord_cartesian()`. You can choose to remove `scales = "free"` or leave it there. Since the code is applied in layers, if you add the manual scale after specifying `scales = "free"`, the graph will be unaffected.


``` r
heroes2 |>
  filter(Intelligence %in% c("good", "high")) |>
  ggplot(aes(x = Gender, y = Strength)) +
  geom_bar(stat = "summary", position = position_dodge(.8), width = .7, fill = "#BDD5EA") +
  geom_errorbar(stat = "summary", position = position_dodge(0.5), width = .12) +
  facet_wrap(Intelligence ~ ., scales = "free") +
  coord_cartesian(ylim = c(0,100)) 
```

![plot of chunk unnamed-chunk-111](figure/unnamed-chunk-111-1.png)

After setting the same scale for all graphs, it becomes much easier to compare them and observe relationships between variables.

You can modify the `ylim()` values based on your data.

### themes

The `theme()` function allows you to change the overall appearance of your graph. Some commonly used themes are `theme_classic()`, `theme_light()`, and the default `theme_gray()`.

# Efficiency Tips for Data Processing

# Data Export

# Colclusion and Advanced Learning
