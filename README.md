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

## Results

### Silhouette Scores

In order to determine the most optimal pair of clustering and dimensionality reduction method, the Silhouette Scores were calculated and compared with one another.

#### KMeans with PCA Silhouette Score Results:

* 3 clusters: 0.17751553632732925
* 4 clusters: 0.174171320226354
* 5 clusters: 0.17591190406998541
* 6 clusters: 0.1585760284556778
* 7 clusters: 0.1640629407248322
* 8 clusters: 0.16455040798973974
* 9 clusters: 0.17027904442946798
* 10 clusters: 0.16287427847191216

#### DBSCAN with PCA Silhouette Score Results:

* 26 cluster score(epsilon = 1): -0.13906358366571828
* 14 cluster score(epsilon = 1.5): 0.14739303978293924
* 10 cluster score(epsilon = 2): 0.17724452791750125
* 7 cluster score(epsilon = 2.5): 0.1852872463222325
* 3 cluster score(epsilon = 3): 0.3555809507181026
* 3 cluster score(epsilon = 3.5): 0.35767014679235165
* 3 cluster score(epsilon = 4): 0.35815449702653096
* 3 cluster score(epsilon = 4.5): 0.35896084731457545
* 2 cluster score(epsilon = 5): 0.5470454920663432

#### Agglomerative Clustering with PCA Silhouette Score Results:

##### Complete Linkage:

* 3 clusters is: 0.09001934310702729
* 4 clusters is: 0.11991539369910201
* 5 clusters is: 0.06609544253693514
* 6 clusters is: 0.04219258073056444
* 7 clusters is: 0.04612100051727293
* 8 clusters is: 0.04484446937320177
* 9 clusters is: 0.07202883401986299
* 10 clusters is: 0.07641897618938209

##### Average Linkage:

* 4 clusters is: 0.16184144774615958
* 5 clusters is: 0.1233482760822222
* 6 clusters is: 0.15308406440632782
* 7 clusters is: 0.14755885940473779
* 8 clusters is: 0.14559854853705745
* 9 clusters is: 0.13021519019954858
* 10 clusters is: 0.11995913423793382

##### Ward Linkage:

* 4 clusters is: 0.1532527334233306
* 5 clusters is: 0.17018040774754256
* 6 clusters is: 0.16115705352567145
* 7 clusters is: 0.1467820637214655
* 8 clusters is: 0.14834859009156706
* 9 clusters is: 0.11438776227717598
* 10 clusters is: 0.1182766085820967

#### Gaussian Mixture Model with PCA Silhouette Score Results:

* 3 clusters is: 0.1798293947077883
* 4 clusters is: 0.16079053875207625
* 5 clusters is: 0.15205186132718806
* 6 clusters is: 0.14363874566492935
* 7 clusters is: 0.12459468379358489
* 8 clusters is: 0.13164980603507287
* 9 clusters is: 0.1197192990338002
* 10 clusters is: 0.10165722263946232

#### KMeans with t-SNE Silhouette Score Results:

* 3 clusters: 0.42579216
* 4 clusters: 0.40669176
* 5 clusters: 0.46755275
* 6 clusters: 0.4944979
* 7 clusters: 0.51087385
* 8 clusters: 0.529089
* 9 clusters: 0.5534471
* 10 clusters: 0.5827098

#### DBSCAN with t-SNE Silhouette Score Results:

* 162 cluster score(epsilon = 1): -0.058818676
* 35 cluster score(epsilon = 1.5): 0.29350296
* 20 cluster score(epsilon = 2): 0.4054613
* 15 cluster score(epsilon = 2.5): 0.5636081
* 12 cluster score(epsilon = 3): 0.5132488
* 11 cluster score(epsilon = 3.5): 0.42236155
* 10 cluster score(epsilon = 4): 0.4847864
* 9 cluster score(epsilon = 4.5): 0.42645922
* 9 cluster score(epsilon = 5): 0.42645922

#### Agglomerative Clustering with t-SNE Silhouette Score Results:

##### Complete Linkage:

* 3 clusters is: 0.38442212
* 4 clusters is: 0.38659537
* 5 clusters is: 0.36068788
* 6 clusters is: 0.28760898
* 7 clusters is: 0.26581135
* 8 clusters is: 0.29181427
* 9 clusters is: 0.3152243
* 10 clusters is: 0.2961534

##### Average Linkage:

* 4 clusters is:0.40635872
* 5 clusters is:0.4315434
* 6 clusters is:0.41967356
* 7 clusters is:0.4262616
* 8 clusters is:0.42150497
* 9 clusters is:0.39392674
* 10 clusters is:0.3505486

##### Ward Linkage:

* 4 clusters is:0.44230306
* 5 clusters is:0.45998305
* 6 clusters is:0.48000228
* 7 clusters is:0.5054975
* 8 clusters is:0.5274096
* 9 clusters is:0.5505204
* 10 clusters is:0.57985306

#### Gaussian Mixture Model with t-SNE Silhouette Score Results:

* 3 clusters is:0.4183046
* 4 clusters is:0.4354513
* 5 clusters is:0.44269177
* 6 clusters is:0.4897826
* 7 clusters is:0.5046062
* 8 clusters is:0.5244155
* 9 clusters is:0.55490243
* 10 clusters is:0.5814268

#### KMeans with UMAP Silhouette Score Results:

* 3 clusters: 0.48952344
* 4 clusters: 0.5490662
* 5 clusters: 0.5929982
* 6 clusters: 0.6353665
* 7 clusters: 0.6577166
* 8 clusters: 0.7285267
* 9 clusters: 0.7504744
* 10 clusters: 0.79534936

#### DBSCAN with UMAP Silhouette Score Results:

* 12 cluster score(epsilon = 1): 0.8164647
* 12 cluster score(epsilon = 1.5): 0.8164647 
* **11 cluster score(epsilon = 2): 0.8329651**
* **11 cluster score(epsilon = 2.5): 0.8329651**
* **11 cluster score(epsilon = 3): 0.8329651**
* **11 cluster score(epsilon = 3.5): 0.8329651**
* 8 cluster score(epsilon = 4): 0.63531333
* 7 cluster score(epsilon = 4.5): 0.6253582
* 7 cluster score(epsilon = 5): 0.6253582

#### Agglomerative Clustering with UMAP Silhouette Score Results:

##### Complete Linkage:

* 3 clusters is: 0.3448556
* 4 clusters is: 0.47346213
* 5 clusters is: 0.5215132
* 6 clusters is: 0.5554382
* 7 clusters is: 0.59623265
* 8 clusters is: 0.6281245
* 9 clusters is: 0.57884306
* 10 clusters is: 0.5671031

##### Average Linkage:

* 4 clusters is:0.50785667
* 5 clusters is:0.52198416
* 6 clusters is:0.53432727
* 7 clusters is:0.59150916
* 8 clusters is:0.6281245
* 9 clusters is:0.67577875
* 10 clusters is:0.6276073

##### Ward Linkage:

* 4 clusters is:0.5490662
* 5 clusters is:0.5929982
* 6 clusters is:0.6353665
* 7 clusters is:0.68736744
* 8 clusters is:0.7285267
* 9 clusters is:0.7504744
* 10 clusters is:0.79534936

#### Gaussian Mixture Model with UMAP Silhouette Score Results:

* 3 clusters is:0.48285776
* 4 clusters is:0.5408097
* 5 clusters is:0.49254245
* 6 clusters is:0.55806684
* 7 clusters is:0.6540987
* 8 clusters is:0.68675715
* 9 clusters is:0.7388549
* 10 clusters is:0.78457123*

**The best Silhouette Score was obtained when using DBSCAN with UMAP (0.838) where epsilon = 2,2.5,3, and 3.5**

### Findings
