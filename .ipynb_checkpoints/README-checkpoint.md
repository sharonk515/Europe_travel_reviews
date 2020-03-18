# Europe Travel Reviews

by Sharon Kwak

- Which type of tourist sites are the most popular?
- Can a review of one type predict the user's review for another type?
- What groups can be created based on users' reviews of tourist sites?

## Dataset
[UCI Europe Travel Review Ratings](https://archive.ics.uci.edu/ml/datasets/Tarvel+Review+Ratings)

The dataset has review ratings from 5456 users for 24 different tourist site types in Europe. The ratings are from 0 to 5. It includes the user id and the average ratings for the following tourist site types:

|Features||||||||
|--------|--|--|--|--|--|--|--|
|churches|resorts|beaches|parks|theatres|museums|malls|zoo|
|restaurants|pubs/bars|local services|burger/pizza shops|hotels/other lodgings|juice bars|art galleries|dance clubs|
|swimming pools|gyms|bakeries|beauty & spas|cafes|viewpoints|monuments|gardens|

**General overview of the ratings for each type of tourist site type**

<img src = 'Images/boxplot.png'>

Simply based on the above boxplot and observing the quartiles (25%, 50%, and 75%), gyms, bakeries, and beauty & spas had more lower ratings while restaurants and malls had more higher ratings.

## Clustering
With no specified ('labeled') target variable (dependent variable), unsupervised learning will be used with clustering. I chose the K-means clustering algorithm to find center-based clusters, finding a 'consensus' for the whole dataset, which other methods do not do. I was able to use an algorithm that considers the full dataset without worrying about computation efficiency due to the dataset being small with 5456 rows and 25 features.

First, I used the 'Elbow' method to find the best k-value for this data.

<img src = 'Images/kmeans_elbow.png'>

According to the elbow visualizer above, 4 was the most optimal. Using 4 as the k-value, I ran K-means and fit it to the dataset to get the following clusters (0-3):

<img src = 'Images/cluster_plot.png'>

Based on the clusters, I found the average ratings for each tourist site type and explored the most and least popular sites for each cluster.

**Most popular sites**

<img src = 'Images/popular_sites.png'>

**Least popular sites**

<img src = 'Images/least_popular_sites.png'>

### Summary
**Group 0**:
- fewest values
- highest average ratings for juice bars (4.6), art galleries (4.2), and hotels/other lodgings (3.8)
- lowest average rating for monuments (0.731), cafes (0.733), and viewpoints (0.76)

**Group 1**:
- theatres had highest average ratings for theatres (4.3), with parks (4.1) and museums following (3.6)
- gyms had lowest average rating (0.57), with bakeries (0.59) and pools (0.7) following

**Group 2**:
- viewpoints had highest average rating (2.8), with resorts (2.7) and gardens (2.6) following
- burger/pizza shops had lowest average rating (1.4), with hotels/other lodgings (1.5 and zoos following

**Group 3**:
- most values
- highest average rating for malls (4.2), restaurants, and pubs/bars
- lowest average rating for gyms (0.5), bakeries, and beauty/spas

## Classification
Using the clusters from above as the classes, I trained a classification model to predict which users will be assigned to which cluster.

<img src = 'Images/class_balance.png'>

