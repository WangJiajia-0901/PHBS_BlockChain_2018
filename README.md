# Volatility spillover effects in leading cryptocurrencies: A DCC-GARCH Analysis
## Introduction
The cryptocurrency is a digital asset designed to work as a medium of exchange that uses strong cryptography to secure financial transactions, control the creation of additional units and verify the transfer of assets. The cyptocurrency arouses the attention of academic community as well as the industry. In the present paper, the authors investigate connectedness within cryptocurrency markets as well as across the Bitcoin index (hereafter, BPI) and widely traded asset classes such as traditional currencies, stock market indices and commodities, such as gold and Brent oil. A spill over index approach with the spectral representation of variance decomposition networks, is employed to measure connectedness. (Nader, 2018). Through the application of three pair-wise bivariate BEKK models, this paper examines the conditional volatility dynamics along with interlinkages and conditional correlations between three pairs of cryptocurrencies, namely Bitcoin-Ether, Bitcoin-Litecoin, and Ether-Litecoin. (Paraskebi, Shaen and Brain, 2019). <br>
In this project, I want to use DCC-GARCH model to analyze the volatility spillover effects in the three leading cryptocurrencies: Bitcoin, Ether and Litecoin.
## Data
The data used in this project contains the returns of the Bitcoin, Ether and Litecoin, using each market’s closing prices from 2015/08/07 to 2019/04/05. The total sample of the observations of each time series is 1338. All the prices are listed in US dollars. The data is downloaded from the [CoinMarketCap website](https://coinmarketcap.com/). <br>
![Bitcoinprice](https://github.com/WangJiajia-0901/PHBS_BlockChain_2018/blob/master/Image/Bitcoin%20price.bmp)
![Etherprice](https://github.com/WangJiajia-0901/PHBS_BlockChain_2018/blob/master/Image/Ether%20price.bmp)
![Litecoinprice](https://github.com/WangJiajia-0901/PHBS_BlockChain_2018/blob/master/Image/Litecoin%20price.bmp) <br>
Define the daily price returns of cryptocurrency i, y<sub>i,t</sub> as: y<sub>i,t</sub>=ln(p<sub>i,t</sub>)-ln(p<sub>i,t-1</sub>), where p<sub>i,t</sub> is the closing price of cryptocurrency i on day t.<br>
![BItcoinreturnplot](https://github.com/WangJiajia-0901/PHBS_BlockChain_2018/blob/master/Image/Bitcoin%20Return%20plot.bmp)
![Etherreturnplot](https://github.com/WangJiajia-0901/PHBS_BlockChain_2018/blob/master/Image/Ether%20Return%20plot.bmp)
![Litecoinreturnplot](https://github.com/WangJiajia-0901/PHBS_BlockChain_2018/blob/master/Image/Litecoin%20Return%20plot.bmp)

## Method
### Basic idea
Dynamic Conditional Correlation (DCC-) GARCH,one of the multivariate GARCH models, was introduced by Engle and Sheppard in 2001.
GARCH is the good model to successfully capture the volatility clustreing and predicting future volatilities. Multivariate GARCH is the extend from univariate GARCH.<br>
The basic idea to extend from univariate to multivariate is as following:
* In financial econometrics and management understanding, predicting the dependence in the comovements of asset returns is important. For example, asset pricing depends on the covariance of the assets in a portfolio. Hence it is important to consider the comovements in the portfolio. <br>
* Financial volatilities move together more or less closely over time across assets and markets. <br>
* Recognizing this feature through a multivariate model should lead to more relevant empirical models than working with separate univariate models. <br>
* In financial applications, extending from univariate to multivariate modelling opens the door to better decision tools in various areas such as asset pricing models, portfolio selection, hedging, and Value-at-Risk forecasts. <br>
The Dynamic Conditional Correlation (DCC-) GARCH belongs to the multivariate GARCH models. <br>
The different specifications of MGARCH models can be divided into four categories as suggested in: <br>
1. `Models of the conditional covariance matrix`: In this class the conditional covariance matrices, Ht, are modelled directly. This class includes the VEC and BEKK models. These models were among the first parametric MGARCH models. <br>
2. `Factor models`: The idea of factor models comes from economic theory. In this class the conditional covariance matrices are motivated by parsimony. The process at is assumed to be generated by a (small) number of unobserved heteroskedastic factors, hence these models are called factor models. These factors can be studied and one may make assumptions that some characteristics of the data is captured, similar as for principal component analysis. This approach has the advantage that it reduces the dimensionality of the problem when the number of factors relative to the dimension of the return vector at is small. <br>
3. `Models of conditional variances and correlations`: The models in this class are built on the idea of modelling the conditional variances and correlations instead of straightforward modelling the conditional covariance matrix. <br>
4. `Nonparametric and semiparametric approaches`: Models in this class form an alternative to parametric estimation of the conditional covariance structure. The advantage of these models is that they do not impose a particular structure (that can be misspecified) on the data.<br>
The DCC-GARCH model belongs to the category 3 above.
### Model
Mathematics in progress.
## Emprical Analysis
### Statistical View of Data
### Unit Root Test
### Arch Test
### Multivariate GARCH Fit
### Results
## Conclusion 
## References
