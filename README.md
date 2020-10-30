# Having Fun with a League of Legends Data Set

I decided to mix data science with a small hobby of mine and create a side project dedicated to applying clustering and predictive modeling on a League of Legends data set. The data set consists of in game statistics from the first 10 minutes of high-elo ranked games (high-elo meaning Diamond 1 to Master tier) and can be located at [This Kaggle Link](https://www.kaggle.com/bobbyscience/league-of-legends-diamond-ranked-games-10-min).

## About League of Legends

League of Legends is a multiplayer online battle arena (MOBA) game that has been around for around 11 years. I started playing the game around 2013 and have played on and off since. Playing this video game has helped me to meet many new people, and also keep in touch with friends who are no longer in the same location as me. The game involves two (2) teams of five (5) facing off against each other. There are three (3) lanes and one (1) jungle. There are five (5) roles each player on each team belong to. Four (4) of the five (5) belong in lanes, and the last one (1) belongs in the game's jungle. In order for one team to win they must push through a lane into the other team's base and destroy the Nexus.

![Map](map.jpg)

## About the Data Set

There are around 10,000 different games recorded within the data set. The original data set contained information for both teams, however for this specific project I decided to just focus on the blue side. The entire data set was numeric and there were no missing values that needed to be dealt with. 

## Clustering Methodology

Initial EDA was applied to the data set. Once a cleaner data set was obtained, four (4) clustering algorithms were created to separate and group the data. Three (3) dimensionality reduction methods were applied to each clustering algorithm and the silhouette score was calculated to determine the best algorithm and best dimensionality reduction method.

### Dimensionality Reduction Methods

* Principal Component Analysis (PCA)
* T-Distributed Stochastic Neighbor Embedding (t-SNE)
* Uniform Manifold Approximation and Projection (UMAP)

### Clustering Methods

* KMeans
* DBSCAN
* Agglomerative Clustering
* Gaussian Mixture Model

### Comapring Dimensionality Reduction Methods 

In order to determine the number of componentes used for PCA, the cumulative sum was calculated. I chose to have a sum of around 0.9 which equates to the features having 90% variance. As a result, nine (9) of the fifteen (15) features were chosen and thus explains why n_components = 9. 

When using t-SNE on the data, I chose to take a more global approach. This is the reasoning behind why perplexity = 50. This was also the case for when UMAP was applied to the data and explains why n_neighbors = 20. 

Scatterplots were created for each of the dimensionality reduction methods when applied to the data to visualize how the observations were split up. 

![Plot](pca.png)

![Plot](tsne.png)

![Plot](umap.png)

Comparing the plots, we see PCA did a much worse job of separating the data. UMAP and t-SNE did a good job of splitting and grouping the observations, but just by eyeballing the scatter plots it was difficult to determine which method was better. Therefore, the Silhouette Score for each clustering algorithm was calculated to have a better understanding.

### Results
