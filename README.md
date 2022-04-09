# Amazon Vine Analysis

## Overview

The purpose of this analysis is to take a collection of Amazon reviews and determine whether there is any obvious bias in ratings written as part of a paid review program, Amazon Vine.

For the purposes of this analysis I selected the Musical Instruments category from the [Amazon Review Datasets](https://s3.amazonaws.com/amazon-reviews-pds/tsv/index.txt). The reviews were loaded using PySpark on Google Colab, split into separate tables, then saved into PostgreSQL on Amazon RDS. To determine bias the `vine_table` contents were exported as CSV and loaded into Pandas for filtering and analysis.

## Results

Reviews with fewer than 20 votes and reviews with less than 50 percent "helpful" ratings were removed from the data set prior to analysis. Statistics for the remaining reviews are summarized as follows:

![Summary result table](<./result.png>)

For the musical instruments category:
* There were 60 Vine reviews and 14,477 non-Vine reviews
* 34 Vine reviews were 5-star, and 8,212 non-Vine reviews were 5-star
* 56.67% of the Vine reviews were 5-star. 56.72% of the non-Vine reviews were 5-star.

## Summary

There is no visible positivity bias for reviews in the Vine program. The percentage of 5-star reviews is extremely similar between Vine and non-Vine reviews for the musical instruments category, with 5-star non-Vine reviews being slightly higher as a percentage. Whether or not it is statistically significant would require further analysis.

Another way to support the outcome would be to analyze the number of 1-star reviews for similar biases; if Vine reviews have a positive bias, we would expect to see a lower percentage of 1-star reviews from participants in the program.