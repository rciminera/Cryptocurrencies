# Cryptocurrencies

## Overview

The Advisory Services Team at the prominent investment bank, Accountability Accounting, is interested in offering a new cryptocurrency investment portfolio for its customers.  The company, however, is lost in the vast universe of cryptocurrencies. So, they’ve asked for a report that includes what cryptocurrencies are on the trading market and how they could be grouped to create a classification system for this new investment.

To create this classifaction system, the data is not ideal so it will need to be processed to fit the machine learning models. Since there is no known output for the model, unsupervised learning was used to create the analysis. To group the cryptocurrencies, a clustering algorithm called PCA was used.  In addition, data visualizations twere created to share the findings with the board.

## Results

Jupyter Notebook was used in a machine learning environment with Pandas for the coding and data manipulation, Scikit-learn for the machine learning, and Plotly and 
hvPlot for visualization.

The Jupyter Notebook can be found here: [crypto_clustering.ipynb](crypto_clustering.ipynb.ipynb)

### I. Preprocessing the Data for PCA

The following five preprocessing steps have been performed on the crypto_df DataFrame:
1. All cryptocurrencies that are not being traded were removed
2. The IsTrading column was dropped
3. All the rows that have at least one null value were removed 
4. All the rows that do not have coins being mined was removed
5. The CoinName column was dropped

A new DataFrame was created that stores all cryptocurrency names from the CoinName column and retains the index from the crypto_df DataFrame

<img src="" width = "800" >



The get_dummies() method is used to create variables for the text features, which are then stored in a new DataFrame, X.

The features from the X DataFrame were standardized using the StandardScaler fit_transform() function.

### II. Reducing Data Dimensions Using PCA

- The PCA algorithm reduces the dimensions of the X DataFrame down to three principal components.
- The pcs_df DataFrame was created and has the following three columns, PC 1, PC 2, and PC 3, and has the index from the crypto_df DataFrame.

### III. Clustering Cryptocurrencies Using K-means

The K-means algorithm was used to cluster the cryptocurrencies using the PCA data, where the following steps have been completed:
- An elbow curve is created using hvPlot to find the best value for K.
- Predictions are made on the K clusters of the cryptocurrencies’ data.
- A new DataFrame is created with the same index as the crypto_df DataFrame and has the following columns: Algorithm, ProofType, TotalCoinsMined, TotalCoinSupply, PC 1, PC 2, PC 3, CoinName, and Class.



### IV: Visualizing Cryptocurrencies Results

- The clusters are plotted using a 3D scatter plot, and each data point shows the CoinName and Algorithm on hover.

 <img src="" width = "800" >


- A table with tradable cryptocurrencies is created using the hvplot.table() function.

 <img src="" width = "800" >

- A DataFrame is created that contains the clustered_df DataFrame index, the scaled data, and the CoinName and Class columns.

 <img src="" width = "800" >

- A hvplot scatter plot is created where the X-axis is "TotalCoinsMined", the Y-axis is "TotalCoinSupply", the data is ordered by "Class", and it shows the CoinName when you hover over the data point.

 <img src="" width = "800" >

## Summary

There are 532 tradeable currencies from which to build a portfolio.  These currencies have been grouped into 4 clusters using 