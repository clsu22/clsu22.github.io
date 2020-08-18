---
layout: post
title: IBM Data Science Capstone Project - The Battle of Neighborhoods in Vancouver
---
Author: Haoyu Su  
Updated: August 17, 2020

<img src="/images/vancouver.jpg"/>


# Introduction

Vancouver, a bustling west coat seaport, is full of business opportunities. Millions of tourists come here every year to enjoy the
beautiful scenery. So there are always unlimited possibilities for those who want to open their own restraurant. The biggest challenge they are facing is which location is the best that has relatively small competition, large passenger flow and good surrounding resources. To solve this question, the project is going to segment neighborhoods in Vancouver using a popular clustering technique, trying to figure out a solution for potential restaurant investors.

# Data

The neighborhood data is scraped from [Wekipedia](https://en.wikipedia.org/wiki/List_of_neighbourhoods_in_Vancouver)
and corresponding coordinates are obtained using [geocoder](https://geocoder.readthedocs.io/), and all data of venues in
each neighborhoods is returned by [Foursquare API](https://developer.foursquare.com/). There are 20 official neighborhoods and 510 venues in Vancouver, which will be the main research objects.

# Methods

Several techniques are applied for data acquisition, data proprocessing and model development in Python.

## Data Acquisition

The list of official neighborhoods is found on
[Wekipedia](https://en.wikipedia.org/wiki/List_of_neighbourhoods_in_Vancouver)
which is scraped using BeautifulSoup and Requests packages with Python.
The corresponding coordinates of each neighborhoods are obtained using
[geocoder](https://geocoder.readthedocs.io/). All venure information is
returned by [Foursquare API](https://developer.foursquare.com/).

## Data Preprocessing

Venue Category, a categorical feature is transformed to numeric features by using one-hot encoding. The frequency of each venue category in each neighborhood is calculated to be used as key features in neighborhood segementation. And the top 10 most common venues category are identified for each neighborhood.

## Model Development

The unsupervised machine learning technique **Kmean** is used to cluster similar neighborhoods. Elbow plot is used to find the optimal number of clusters. Folium is used to visualize those resulting clusters on the map.

# Result

Please refer to
[here](https://nbviewer.jupyter.org/github/clsu22/IBM-Capstone-Project/blob/master/src/Final-Project-Analysis.ipynb)
to see the whole analysis and interactive visualization.

## EDA

Figure 1 shows the number of venues in each neighborhood and Figure 2 shows the relative frequency of top 10 most common venues in each neighborhood. There are the most number of vanues in Downtown while the least number of venues Killarney.

<div class="figure" style="text-align: center">

<img src="/images/count_bar.png" alt="Figure 1. The number of venues in each neighborhood" width="100%" height="100%" />

<p class="caption">

Figure 1. The number of venues in each neighborhood

</p>

</div>

<div class="figure" style="text-align: center">

<img src="/images/heatmap.png" alt="Figure 2. The frequency of top 10 venues in each neighborhood" width="800" height="600" />

<p class="caption">

Figure 2. The frequency of top 10 venues in each neighborhood

</p>

</div>

## Clustering

Given the elbow plot shown in Figure 3, the kmeans will segement all
neighborhoods in 5 clusters. The result of clustering is shown in Table
1.

<div class="figure" style="text-align: center">

<img src="/images/elbow_plot.png" alt="Figure 3. Elbow plot" width="100%" height="100%" />

<p class="caption">

Figure 3. Elbow plot

</p>


</div>

# Discussion

Neighborhoods in cluster 1 (purple) and cluster 2 (blue) are full of different kinds of restraurants. Japanese and Chinese restaurants are mostly located in cluster 1 while French Restaurants are mostly located in cluster 2. Cluster 1 includes downtown vancouver with a high volume of people flow and relative large competition while cluster 2 is a little far from downtown but will have less rents. Other clusters have less restaurant but cluster 3 has a lot of Café and Coffee shop which is a good place to open dessert restaurants. Therefore if you have enough money, I would recommand you to open restaurants in neighborhoods closer to downtown in cluster 1 such a Downtown, South Cambie and Oakridge. But if you don’t have enough money and want to have less stress of peer competition, I would recommand you to open restaurants in neighborhoods relatively from Downtown in cluster 1 or other neighborhoods in cluster 2 or cluster 3.


<iframe id="inlineFrameExample"
    title="Inline Frame Example"
    width="600"
    height="500"
    src="/images/vancouver_neighborhood_clustering.html">
</iframe>

Figure 4. Neighborhood segmentation result



# Conclusion

This project applied the kmeans technique to successfully segement 20 neighborhoods into 5 clusters. Some useful suggestions on opening restaurants are given based on the cluster result. More analysis can be done using more information such as neighborhoods’ GDP and population.
