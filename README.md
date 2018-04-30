# An Analysis of Claps on Medium

## Problem

What makes an article get claps on Medium? Can we predict the number of claps an article will get based on other factors?

## Data

All Data was scraped from Medium.com.

### Step 1
This notebook is a web scraper that crawls Medium.com based on an initial seed user. The scraper loops through the graph of followers/followees (called leaders generally in this code), and creates 2 main data structures: 1) A dictionary of source:target pairs that describes the connections between leaders and followers in medium 2) A dictionary of nodes that contains each user examined and metadata of #of followers and #of leaders

This code was written for 2 main purposes: 1) To generate a list of users, whose articles will then be scraped in Step 2 for analysis and modeling in Step 3 of the project. 2) To product source:target pairs in a format readable by d3 for the purposes of making a force-directed network graph of a given medium network

Note: Medium.com does not product a comprehensive list of users or articles published, so this type of connection between users is the only way to get a large sample size on the site.

### Step 2
This web scraper takes in a list of Medium user profiles and collectsa list of articles written by each user. It then scrapes each of those articles for a set of traits, ranging from article length to a readibility score. These traits are used for analysis in Step 3 of this project.

## Analysis

* The distribution of claps (as well as followers and leaders for a given user) was highly skewed. Box-box and Standard Scaler normalizations were applied to get to a more normal distribution.
* OLS was applied with Polynomials & Lasso, Ridge and ElasticNet Regularization
* No Model reached > .30 R-squared, but the following factors were sound to significantly impact claps:
	- \# followers
	- \# leaders
	- article reading time
	- reading level
	- number of tags and specific tags
	- if the article is in a publisher

##Conclusions