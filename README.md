# Capstone
My Objective for my Capstone was to redifine Modern NBA player positions using Clustering Methods.

First thing to do was to- Webscrape our data: So I was able to scrape all NBA players and their statistics between the 2016-2019 Seasons from basketball-reference.com. I decided to leave out the 2020 season since covid cut the season short so the Stats would not have been accurate. So at first I scraped all players “basic stats” which include things like average points per game, average shots attempted per game etc. But then I quickly realized in order for my clustering model to perform as best as possible I needed to bring in more statistics, so I scraped the advanced statistics as well. After I had my dataframe with all my players with their basic stats and advanced stats I decided to drop all players with less than 15 minutes played per game, I wanted to grab the “more important players”

So now that I had my Dataframe it was time for me to begin the process of fitting a K-means model. First I needed too Standardize my data in order to put all of my features on the same scale. Next was to use PCA or principal component analysis on my scaled features. As we know, PCA is a dimensionality reduction method that grabs all of our data and gives us the most important information in a much smaller number of variables or components. So after I used PCA on my scaled data I had to decide how many components to use for my K-Means clustering model. I decided to go with 5 PCA components since it accounted for more than 95% of variance in the data.

So now it was time to actually fit a K-Means Model with our 5 PCA’d components. The next thing to do was to decide our k or number of centroids to use in the dataset. Subjectively I decided to try between 7-12 clusters; the reason I decided to go with 7-12 clusters was because we already have our 5 original positions and the whole argument I am trying to make here is that there are positions within each player position so 7-12 felt appropriate to me. And the number of clusters that worked best was 8. So K-Means was not doing an excellent job so it was time to try other clustering methods!

I tried to use the DBSCAN clustering method and early on I could just tell it was not doing a good job at all. I tried multiple varieties of epsilon and min samples and I was mostly getting back a large (-1) cluster which means DBSCAN was clustering most of my data as noise; and the best silhoute score I achieved was 0.05 so DBSCAN was not the right clustering method.

Last but surely not least is Hierarchical Clustering. There are two forms of Hierarchical clustering, Divisive and Agglomerative. I know I had to do some research since we didn’t learn this Modeling algorithm in class and based on my research, the Agglomerative method was the best at clustering statistics, so I gave that a shot! With Hierarchical clustering we do have to manually choose our number of clusters so I ran between 7-12 clusters and once again 8 was the sweet spot! Most of my players were clustered in groups that made complete sense to me and that was it, I had my model! There are two parameters I used worth mentioning, there was the “affinity” parameter which computes the linkage, and for that I used Euclidian; and there was the “linkage” parameter determines which distance to use between sets of observation. “linkage options”: • Ward - minimizes the variance of the clusters being merged. • average - uses the average of the distances of each observation of the two sets. • complete or maximum linkage - uses the maximum distances between all observations of the two sets. • Single - uses the minimum of the distances between all observations of the two sets.

Finally I created an interactive Tableau visual showing all the clusters and using drop downs for players, teams and cluster labels!

https://public.tableau.com/profile/christopher.homsi#!/vizhome/NBAStats2016-2019playerslatestseasons/Dashboard1
