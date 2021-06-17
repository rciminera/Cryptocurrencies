# Cryptocurrencies

## Overview

The Advisory Services Team at the prominent investment bank, Accountability Accounting, is interested in offering a new cryptocurrency investment portfolio for its customers.  The company, however, is lost in the vast universe of cryptocurrencies. So, they’ve asked for a report that includes what cryptocurrencies are on the trading market and how they could be grouped to create a classification system for this new investment.

To create this classification system, the data is not ideal so it was processed to fit the machine learning models. Since there is no known output for the model, unsupervised learning was used to create the analysis. To group the cryptocurrencies, the Principal Component Analysis (PCA) clustering algorithm was used.  In addition, data visualizations were created to share the findings with the board.

## Results

Jupyter Notebook was used in a machine learning environment with Pandas for the coding and data manipulation, Scikit-learn was used for machine learning, and Plotly and hvPlot were used to create interactive visualizations.

The Jupyter Notebook can be found here: [crypto_clustering.ipynb](https://github.com/rciminera/Cryptocurrencies/blob/main/Notebooks/crypto_clustering.ipynb)

### I. Preprocessing the Data for PCA

The following five preprocessing steps have been performed on the crypto_df DataFrame to prepare for PCA:
1. Removed all cryptocurrencies not being traded
2. Dropped IsTrading column 
3. Removed all rows with at least one null value
4. Removed all rows that do not have mined coins
5. Dropped CoinName column

A new DataFrame was created to store all cryptocurrency names from the CoinName column and retain the index from the crypto_df DataFrame.

<img src="https://github.com/rciminera/Cryptocurrencies/blob/main/ScreenShots/crypto_df.png" width = "800" >

The get_dummies() method was used to create variables for the text features, and then stored in a new DataFrame, X.

The features from the X DataFrame were standardized using the StandardScaler fit_transform() function.

### II. Reducing Data Dimensions Using PCA

- The PCA algorithm was used to reduce the dimensions of the X DataFrame down to three principal components.
- The pcs_df DataFrame was created with columns for each of 3 Principal Components: PC 1, PC 2, and PC 3, with the index from the crypto_df DataFrame.

<img src="https://github.com/rciminera/Cryptocurrencies/blob/main/ScreenShots/principal_components.png" width = "800" >


### III. Clustering Cryptocurrencies Using K-means

The K-means algorithm was used to cluster the cryptocurrencies using the PCA data, and the following steps were completed:
- An elbow curve was created using hvPlot to find the best value for K.

<img src="https://github.com/rciminera/Cryptocurrencies/blob/main/ScreenShots/elbow_curve.png" width = "800" >

- Predictions are made on the K clusters of the cryptocurrencies’ data.
- Created a new DataFrame with the same index as the crypto_df DataFrame with the following columns: Algorithm, ProofType, TotalCoinsMined, TotalCoinSupply, PC 1, PC 2, PC 3, CoinName, and Class.

<img src="https://github.com/rciminera/Cryptocurrencies/blob/main/ScreenShots/clustered_df.png" width = "800" >

### IV: Visualizing Cryptocurrencies Results

- Plotted clusters using a 3D scatter plot, with each data point showing the CoinName and Algorithm on hover.

 <img src="https://github.com/rciminera/Cryptocurrencies/blob/main/ScreenShots/3D_scatterplot.png" width = "800" >


- Created a table with tradable cryptocurrencies using the hvplot.table() function.

 <img src="https://github.com/rciminera/Cryptocurrencies/blob/main/ScreenShots/hvplot_table.png" width = "800" >

- Created a DataFrame that contains the clustered_df DataFrame index, the scaled data, and the CoinName and Class columns.

 <img src="https://github.com/rciminera/Cryptocurrencies/blob/main/ScreenShots/plot_df.png" width = "800" >

- Created a hvplot scatter plot where the X-axis is "TotalCoinsMined", the Y-axis is "TotalCoinSupply", the data is ordered by "Class", and it shows the CoinName when you hover over the data point.

 <img src="https://github.com/rciminera/Cryptocurrencies/blob/main/ScreenShots/scatter_plot.png" width = "800" >

## Summary

There are 532 tradeable currencies from which the Advisory Services Team at the prominent investment bank, Accountability Accounting can choose from to build a portfolio.  These currencies have been grouped into 4 clusters of which the cluster of Classes 0 and 1 represent the highest density of coins.

Next steps should be further analysis on these classes of cryptocurrencies to look at other elements such as trading price, market cap, and a qualitative analysis on their strategy and use.