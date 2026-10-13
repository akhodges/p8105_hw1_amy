Data Science: Homework 1
================
Amy Hodges
2026-10-13

``` r
#Uploading data
data("penguins", package = "palmerpenguins")

#Exploring Variables
head(penguins)
```

    ## # A tibble: 6 × 8
    ##   species island    bill_length_mm bill_depth_mm flipper_length_mm body_mass_g
    ##   <fct>   <fct>              <dbl>         <dbl>             <int>       <int>
    ## 1 Adelie  Torgersen           39.1          18.7               181        3750
    ## 2 Adelie  Torgersen           39.5          17.4               186        3800
    ## 3 Adelie  Torgersen           40.3          18                 195        3250
    ## 4 Adelie  Torgersen           NA            NA                  NA          NA
    ## 5 Adelie  Torgersen           36.7          19.3               193        3450
    ## 6 Adelie  Torgersen           39.3          20.6               190        3650
    ## # ℹ 2 more variables: sex <fct>, year <int>

``` r
colnames(penguins)
```

    ## [1] "species"           "island"            "bill_length_mm"   
    ## [4] "bill_depth_mm"     "flipper_length_mm" "body_mass_g"      
    ## [7] "sex"               "year"

This dataset includes data about penguins, including species, island,
sex, year, bill length, bill depth, flipper length, and body mass.

``` r
#Size of dataset
nrow(penguins)
```

    ## [1] 344

``` r
ncol(penguins)
```

    ## [1] 8

This dataset contains 344 observations and 8 variables.

``` r
#Mean flipper length
mean_flipper_length <- mean(penguins$flipper_length_mm, na.rm=TRUE)
```

The mean flipper length is 200.9 mm.

``` r
#Plot of flipper length vs. bill length, colored by species
library(ggplot2)
penguin_scatterplot <- 
ggplot(penguins, aes(x=bill_length_mm, y=flipper_length_mm, 
color= species)) + 
geom_point() +
labs(title="Penguin Flipper Length vs. Bill Length by Species",
    x = "Bill Length (mm)",
    y = "Flipper Length (mm)",
    color = "Species") +
    theme_minimal()

#Saving Plot
ggsave(
  filename = "penguin_scatterplot.png",
  plot = penguin_scatterplot,
  width = 6,
  height = 4,
  dpi = 300
)
```

    ## Warning: Removed 2 rows containing missing values or values outside the scale range
    ## (`geom_point()`).

``` r
#Create dataframe
hw1_df <- data.frame(normal_sample = rnorm(10, mean = 0, sd = 1),
is_positive = logical(10),
character_vector = c("Apple", "Banana", "Cherry", "Raspberry", "Elderberry", 
                     "Fig", "Lime", "Honeydew", "Kiwi", "Lemon"),
factor_vector=factor(sample(c("Low", "Medium", "High"), 10, replace = TRUE))
)

hw1_df$is_positive <- hw1_df$normal_sample > 0

print(hw1_df)
```

    ##    normal_sample is_positive character_vector factor_vector
    ## 1      0.5115251        TRUE            Apple          High
    ## 2      0.7400449        TRUE           Banana           Low
    ## 3      0.3048006        TRUE           Cherry          High
    ## 4     -0.1552122       FALSE        Raspberry           Low
    ## 5     -0.2136772       FALSE       Elderberry        Medium
    ## 6     -0.8223922       FALSE              Fig          High
    ## 7      0.3959958        TRUE             Lime          High
    ## 8      1.0029694        TRUE         Honeydew          High
    ## 9      0.6389901        TRUE             Kiwi          High
    ## 10     0.8282593        TRUE            Lemon          High

``` r
#Calculating means
mean(hw1_df$normal_sample)
```

    ## [1] 0.3231303

``` r
mean(hw1_df$is_positive)
```

    ## [1] 0.7

``` r
mean(hw1_df$character_vector)
```

    ## Warning in mean.default(hw1_df$character_vector): argument is not numeric or
    ## logical: returning NA

    ## [1] NA

``` r
mean(hw1_df$factor_vector)
```

    ## Warning in mean.default(hw1_df$factor_vector): argument is not numeric or
    ## logical: returning NA

    ## [1] NA

The mean of the random sample from a normal distribution is 0.3231303
and the mean of the logical vector indicating whether values are greater
than zero is 0.7. The other two means yielded a results of NA because
they are not numerical variables. The logical variable mean reflects the
proportion of TRUE outcomes in the dataset.
