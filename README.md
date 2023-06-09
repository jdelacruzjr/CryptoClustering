# Crypto Clustering
## Unsupervised Learning Prediction of CryptoCurrency

### Load and Preview Summary of Data
Load the `crypto_market_data.csv` into a DataFrame.
Preview Summary Statistics and Plot the Data to gain insight of dataset before proceeding.

![market_data_plot](Images/market_data_plot.png)

### Prepare the Data
Using the `StandardScaler()` module from `scikit-learn` I normalized the data from the CSV file.

Created a DataFrame with the scaled data and set the "coin_id" index from the original DataFrame as the index for the new DataFrame.

### Find the Best Value for k using the Original Scaled DataFrame
Used the elbow method to find the best value for `k` using the following steps:
* Created a list with the number of k values from 1 to 11.
* Created an empty list to store the inertia values.
* Created a `for` loop to compute the inertia with each possible value of `k`.
* Created a dictionary with the data to plot the elbow curve.
* Plotted a line chart with all inertia values computed with the different values of `k` to visually identify the optimal value for `k`.
* Documented the best value for `k` as 4.

![elbowmarket_dataplot](Images/elbowmarket_dataplot.png)
### Cluster Cryptocurrencies with K-means Model using the Original Scaled Data
* Used the following steps to cluster the cryptocurrencies for the best value for `k` on the original scaled data:
    * Initialized the K-means model with the best value for `k`.
    * Fit the K-means model using the original scaled DataFrame.
    * Predicted the clusters to group the cryptocurrencies using the original scaled DataFrame.
    * Created a copy of the original data and added a new column for the predicted clusters.
#### Created a scatter plot using hvPlot as follows:
* Set the x & y axes as `x="price_change_percentage_24h"` and `y="price_change_percentage_7d"`, respectively.
* Colored the graph points with the labels found using K-Means.
* Added the crypto name in the `hover_cols` parameter to identify the cryptocurrency represented by each data point.

![cluster247_plot](Images/cluster247_plot.png)

### Optimized the Clusters with Principal Component Analysis

* Used the original scaled DataFrame, to perform a PCA and reduced the features to three principal components.
* Retrieved the explained variance to determine how much information can be attributed to each principal component and then provided insight and explanation on the total explained variance of the three principal components.
    * Calculated the total explained variance of the three principal components as approximately 89.5%

* Created a new DataFrame with the PCA data and set the `"coin_id"` index from the original DataFrame as the index for the new DataFrame.

### Find the Best Value for `k` using the PCA DataFrame
Used the elbow method to find the best value for `k` using the following steps:
* Created a list with the number of k values from 1 to 11.
* Created an empty list to store the inertia values.
* Created a `for` loop to compute the inertia with each possible value of `k`.
* Created a dictionary with the data to plot the elbow curve.
* Plotted a line chart with all inertia values computed with the different values of `k` to visually identify the optimal value for `k`.
* Documented the best value for `k` as 4, which is identical to the k value from the original data.

![pca_elbow_plot](Images/pca_elbow_plot.png)
### Cluster Cryptocurrencies with K-means using the PCA Data
* Used the following steps to cluster the cryptocurrencies for the best value for `k` on the PCA data:
    * Initialized the K-means model with the best value for `k`.
    * Fit the K-means model using the PCA DataFrame.
    * Predicted the clusters to group the cryptocurrencies using the PCA DataFrame.
    * Created a copy of the data frame with the PCA data and added a new column for the predicted clusters.
#### Created a scatter plot using hvPlot as follows:
* Set the x & y axes as `x="price_change_percentage_24h"` and `y="price_change_percentage_7d"`, respectively.
* Colored the graph points with the labels found using K-Means.
* Added the crypto name in the `hover_cols` parameter to identify the cryptocurrency represented by each data point.

![coinid_scatterplot](Images/coinid_scatterplot.png)

### Created side by side composites to compare & contrast the original data from the PCA data

* Used hvPlot and the plus sign `(+)` operator to compare the elbow curve from the original data with that of the PCA data

![elbowplot_pca_elbowplot](Images/elbowplot_pca_elbowplot.png)

* Used hvPlot and the plus sign `(+)` operator to compare the cryptocurrency clusters from the original data with that of the PCA data

![247clusters_pcclusters](Images/247clusters_pcclusters.png)