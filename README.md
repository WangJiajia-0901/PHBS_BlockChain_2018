# Dynamic Relationship in leading cryptocurrencies: A DCC-GARCH Analysis
## Introduction
The cryptocurrency is a digital asset designed to work as a medium of exchange that uses strong cryptography to secure financial transactions, control the creation of additional units and verify the transfer of assets. The first cyrptocurrency, Bitcoin, was created in 2009. Since then, cryptocurrencies have emerged and the number of them is over 2,000. As we all know, the price of cryptocurrency fluctuates very sharply, and the biggest drop in bitcoin has reached 94%. The motivation of this research is to see wether there are comovements in the leading cyrptocurrencies: Bitcoin, Ether and Litecoin. Before I started my project, I simply guessed that  cryptocurrencies' returns co-changed  considering the regulation and policy for all cryptocurrencies. I also interviewed a few friends who were familar with cryptocurrencies for that question. Majority of them answered yes and thought the Bitcoin was the most leading cryptocurrencies. <br>
In the present paper, the authors investigate connectedness within cryptocurrency markets as well as across the Bitcoin index (hereafter, BPI) and widely traded asset classes such as traditional currencies, stock market indices and commodities, such as gold and Brent oil. A spill over index approach with the spectral representation of variance decomposition networks, is employed to measure connectedness. (Nader, 2018). Through the application of three pair-wise bivariate BEKK models, this paper examines the conditional volatility dynamics along with interlinkages and conditional correlations between three pairs of cryptocurrencies, namely Bitcoin-Ether, Bitcoin-Litecoin, and Ether-Litecoin (Paraskebi, Shaen and Brain, 2019). <br>
In this project, I want to use pair-wise DCC-GARCH model to analyze the dynamic relationship in the three leading cryptocurrencies: Bitcoin, Ether and Litecoin.
## Data
The data used in this project contains the returns of the Bitcoin, Ether and Litecoin, using each market’s closing prices from 2015/08/07 to 2019/04/05. The total sample of the observations of each time series is 1338. All the prices are listed in US dollars. The data is downloaded from the [CoinMarketCap website](https://coinmarketcap.com/). <br>
![Bitcoinprice](https://github.com/WangJiajia-0901/PHBS_BlockChain_2018/blob/master/Image/Bitcoin%20price.bmp)
![Etherprice](https://github.com/WangJiajia-0901/PHBS_BlockChain_2018/blob/master/Image/Ether%20price.bmp)
![Litecoinprice](https://github.com/WangJiajia-0901/PHBS_BlockChain_2018/blob/master/Image/Litecoin%20price.bmp) <br>
![Cryptocurrencyprice](https://github.com/WangJiajia-0901/PHBS_BlockChain_2018/blob/master/Image/Crptocurrency%20price.bmp) <br>
It can be seen from the figure that the price movements of the three are very similar although Bitcoin's price is much higher than the other two. At the beginning of 2017, their prices began to rise and then grew rapidly from the second quarter of 2017, and prices fluctuated at high levels in the following six months. However, prices have fallen sharply since 2018. <br>
Define the daily price returns of cryptocurrency i, y<sub>i,t</sub> as: y<sub>i,t</sub>=ln(p<sub>i,t</sub>)-ln(p<sub>i,t-1</sub>), where p<sub>i,t</sub> is the closing price of cryptocurrency i on day t.<br>
![BItcoinreturnplot](https://github.com/WangJiajia-0901/PHBS_BlockChain_2018/blob/master/Image/Bitcoin%20Return%20plot.bmp)
![Etherreturnplot](https://github.com/WangJiajia-0901/PHBS_BlockChain_2018/blob/master/Image/Ether%20Return%20plot.bmp)
![Litecoinreturnplot](https://github.com/WangJiajia-0901/PHBS_BlockChain_2018/blob/master/Image/Litecoin%20Return%20plot.bmp) <br>
It is obvious to observe that their returns have the volatility clustering effects which first noted as Mandelbrot (1963), that "large changes tend to be followed by large changes, of either sign, and small changes tend to be followed by small changes." So it is reasonable to capture their features with GARCH model.

## Method
### Basic idea
Dynamic Conditional Correlation (DCC-) GARCH,one of the multivariate GARCH models, was introduced by Engle and Sheppard in 2001.
GARCH is the good model to successfully capture the volatility clustreing and predicting future volatilities. Multivariate GARCH is the extend from univariate GARCH.<br>
<br>
The basic idea to extend from univariate to multivariate is as following:
* In financial econometrics and management understanding, predicting the dependence in the comovements of asset returns is important. For example, asset pricing depends on the covariance of the assets in a portfolio. Hence it is important to consider the comovements in the portfolio. <br>
* Financial volatilities move together more or less closely over time across assets and markets. <br>
* Recognizing this feature through a multivariate model should lead to more relevant empirical models than working with separate univariate models. <br>
* In financial applications, extending from univariate to multivariate modelling opens the door to better decision tools in various areas such as asset pricing models, portfolio selection, hedging, and Value-at-Risk forecasts. <br>
  
The different specifications of MGARCH models can be divided into four categories as suggested in: <br>
1. `Models of the conditional covariance matrix`: In this class the conditional covariance matrices, Ht, are modelled directly. This class includes the VEC and BEKK models. These models were among the first parametric MGARCH models. <br>
2. `Factor models`: The idea of factor models comes from economic theory. In this class the conditional covariance matrices are motivated by parsimony. The process at is assumed to be generated by a (small) number of unobserved heteroskedastic factors, hence these models are called factor models. These factors can be studied and one may make assumptions that some characteristics of the data is captured, similar as for principal component analysis. This approach has the advantage that it reduces the dimensionality of the problem when the number of factors relative to the dimension of the return vector at is small. <br>
3. `Models of conditional variances and correlations`: The models in this class are built on the idea of modelling the conditional variances and correlations instead of straightforward modelling the conditional covariance matrix. <br>
4. `Nonparametric and semiparametric approaches`: Models in this class form an alternative to parametric estimation of the conditional covariance structure. The advantage of these models is that they do not impose a particular structure (that can be misspecified) on the data.<br>
  
The DCC-GARCH model belongs to the category 3 above.
### Models
Suppose we have returns,_a<sub>t</sub>_, from _n_ assets with expected value 0 and covariance matrix _H<sub>t</sub>_. The the Dynamic Conditional Correlation GARCH Model is defined as:<br>
 _r<sub>t</sub>_ = _μ<sub>t</sub>_ + _a<sub>t</sub>_  <br> 
              
 _a<sub>t</sub>_ = _H<sub>t</sub><sup>1/2</sup>_ * _z<sub>t</sub>_  <br>
               
 _H<sub>t</sub>_ = _D<sub>t</sub>_ * _R<sub>t</sub>_ * _D<sub>t</sub>_  <br>
      
The notation is as following: <br>
_r<sub>t</sub>_:  n * 1 vector which represents the returns of  _n_ assets at time _t_ <br>
_a<sub>t</sub>_:  n * 1 vector which is the mean-corrected returns of  _n_ assets at time _t_ <br>
_μ<sub>t</sub>_:  n * 1 vector which is the ecpected value of the conditional _r<sub>t</sub>_ <br>
_H<sub>t</sub>_:  n * n conditional variances of _a<sub>t</sub>_ <br>
_D<sub>t</sub>_:  n * n diagonal matrix of conditional standard deviations of _a<sub>t</sub>_ at time _t_ <br>
_R<sub>t</sub>_:  n * n diagnoalcorrelation matrix of _a<sub>t</sub>_ at time _t_ <br>
_z<sub>t</sub>_:  n * 1 vector of i.i.d errors <br>

    
h<sub>it</sub>= ω<sub>i</sub>+∑α<sub>iq</sub>a<sub>i,t-q</sub><sup>2</sup>+∑β<sub>ip</sub>h<sub>i,t-p</sub>
                  
 
## Emprical Analysis
### Statistical View of Data
|Cryptocuurency return| Min|1st Qu|Median|Mean|3rd Qu|Max|skewness|kurtosis|
|:------:|:------:|:------:|:------:|:------:|:------:|:------:|:------:|:------:|
|Bitcoin|-0.207530|-0.010107|0.002263|0.002162|0.017238|0.225119|-0.2214035|4.964624|
|Ether|-1.3065294|-0.0260256|-0.0007707|0.0030592|0.0298530|0.4101490|-3.427667|66.89897|
|Litecoin|-0.395151|-0.017611|0.000000|0.002279|0.018920|0.510348|1.271129|12.16704|
        
As it shows in the table, we can conclude that Bitcoin's return and Ether's return are left-skewed with negative skewness. On the contratry, Litecoin's return has the right-skewed distribution. All of them own the heavy-tailed distributions. <br>
### Unit Root Test
* Bitcoin return unit root test <br>
![bitcoinreturnunitroottest](https://github.com/WangJiajia-0901/PHBS_BlockChain_2018/blob/master/Image/adfbitcoinreturn.bmp) <br>
`Augmented Dickey-Fuller Test` <br>
Dickey-Fuller = -9.7392, Lag order = 11, p-value = 0.01 <br>
*Alternative hypothesis: stationary* <br>
    
* Ether return unit root test <br>
![etherreturnunitroottest](https://github.com/WangJiajia-0901/PHBS_BlockChain_2018/blob/master/Image/adfetherreturn.bmp) <br>
`Augmented Dickey-Fuller Test` <br>
Dickey-Fuller = -9.8653, Lag order = 11, p-value = 0.01 <br>
*Alternative hypothesis: stationary* <br>
   
* Litecoin return unit root test <br>
![litecoinreturnunitroottest](https://github.com/WangJiajia-0901/PHBS_BlockChain_2018/blob/master/Image/adflitecoinreturn.bmp) <br>
`Augmented Dickey-Fuller Test` <br>
Dickey-Fuller = -10.15, Lag order = 11, p-value = 0.01 <br>
*Alternative hypothesis: stationary* <br>
            
All the ADF tests present the small p-value rejecting the null hypothesis of unit root which means that all the three cryptocurrencies' returns are stationary. <br> 

### Arch Test
* Bitcoin return Arch Test <br>
`ARCH LM Test` <br>
Chi-squared = 110.91, df = 12, p-value < 2.2e-16 <br>
*Null hypothesis: no ARCH effects* <br>
   
* Ether return Arch Test <br>
` ARCH LM Test` <br>
Chi-squared = 135.77, df = 12, p-value < 2.2e-16 <br>
*Null hypothesis: no ARCH effects* <br>
    
* Litecoin return Arch Test <br>
`ARCH LM Test` <br>
Chi-squared = 76.184, df = 12, p-value = 2.193e-11 <br>
*Null hypothesis: no ARCH effects* <br>

All the ARCH-LM tests reach the small p-value which means that there are truly ARCH effects in returns of cryptocurrencies.

### Pearson correlation 
| |Bitcoin return| Ether| Litecoin|
|:------:|:------:|:------:|:------:|
|Bitcoin| 1.0000000|0.9001795|0.9400632|
|Ether| 0.9001795|1.0000000|0.9356845|
|Litecoin|0.9400632|0.9356845|1.0000000|
              
The Pearson correlation matrix further shows that the significantly positive correlation in the three crptocurrencies with  nearly 1 correlation coefficients. 

### Multivariate GARCH Fit
Now, estimating the three bivariate ARMA(1,1)-DCC-GARCH(1,1) models. <br>
#### Bitcoin and Ether
| |Estimated|Std.Error|t value| p value|
|:------:|:------:|:------:|:------:|:------:|
|bitcoinomega |7.476703  | 10.242742 | 0.72995 |0.465420|
|bitcoinalpha1 |0.080691 |0.031054 |  2.59845 | 0.009365 |
|bitcoinbeta1|0.918309|0.044749|20.52117|0.000000 |
|etheromega|0.005664|0.003738|1.51496|0.129783 |
|etheralpha1|0.169568|0.024274|6.98553|0.000000 |
|etherbeta1|0.829432|0.031814|26.07168|0.000000 |
|Jointdcca1|0.089803|0.011608|7.73622|0.000000 |
|Jointdccb1|0.905648|0.012416|72.94382|0.000000 |
|Jointmshape|4.513015|0.255703|17.64946|0.000000 |
                          
|Information criteria|value|
|:------:|:------:|
|Akaike    |   16.417|
|Bayes    |    16.479|
|Shibata  |    16.416|
|Hannan-Quinn| 16.440|
               
                  
The the coefficients are signicant except the omega of bitcoin and omega of ether which means that there truly exists the dynamic correlations in Bitcoin and Ether.
              
![2](https://github.com/WangJiajia-0901/PHBS_BlockChain_2018/blob/master/Image/be.png) <br>
        
From the dynamic conditional correlation plot between Bitcoin and Ether, we can further conclude that they are co-related most of time, especially after mid-2017. <br>

#### Bitcoin and Litecoin
| |Estimated|Std.Error|t value| p value|
|:------:|:------:|:------:|:------:|:------:|
|bitcoinomega   | 6.012333   | 4.151115 |  1.4484 | 0.14752|
|bitcoinalpha1 |  0.148902  |  0.026379  | 5.6448 | 0.00000|
|bitcoin].beta1  |  0.850098   | 0.042624 | 19.9442 | 0.00000|
|litecoinomega  | 0.002274 |   0.001860 |  1.2227 | 0.22146|
|litecoinalpha1 | 0.089735 |   0.017098  | 5.2482|  0.00000|
|litecoin].beta1  | 0.909265 |   0.024931 | 36.4718 | 0.00000|
|Jointdcca1    |   0.101047  |  0.016398   |6.1621 | 0.00000|
|Jointdccb1    |   0.892507  |  0.017998 | 49.5883 | 0.00000|
|Jointmshape  |    4.609205  |  0.307277 | 15.0001 | 0.00000|
                    
|Information criteria|value|
|:------:|:------:|
|Akaike    |   14.074|
|Bayes    |    14.136|
|Shibata  |    14.074|
|Hannan-Quinn| 14.098|
                 
The the coefficients are signicant except the omega of bitcoin and omega of litecoin which means that there truly exists the dynamic correlations in Bitcoin and Litecoin. <br>

![bl](https://github.com/WangJiajia-0901/PHBS_BlockChain_2018/blob/master/Image/bl.png) <br>
Also, the dynamic conditional correlation plot shows the correlations between Bitcoin and Litecoin, especially from the second quarter of 2017. <br>

#### Ether and Litecoin
| |Estimated|Std.Error|t value| p value|
|:------:|:------:|:------:|:------:|:------:|
|etheromega    |  0.018801  |  0.013171  |1.42744 | 0.15345|
|etheralpha1  |   0.126511  |  0.017359|  7.28812 | 0.00000|
|etherbeta1    |  0.872489 |   0.022616 |38.57800 | 0.00000|
|litecoinomega  | 0.003782  |  0.003792 | 0.99721 | 0.31866|
|litecoinalpha1 | 0.088651  |  0.015605 | 5.68104 | 0.00000|
|litecoinbeta1  | 0.910349  |  0.024512 |37.13929 | 0.00000|
|Jointdcca1      | 0.112778 |   0.017238  |6.54238|  0.00000|
|Jointdccb1    |   0.884633  |  0.017867 |49.51105  |0.00000|
|Jointmshape   |   4.807511  |  0.282406| 17.02342 | 0.00000|
                
|Information criteria|value|
|:------:|:------:|
|Akaike    |   8.5011|
|Bayes    |  8.5633|
|Shibata  |    8.5008|
|Hannan-Quinn| 8.5224|
                
Similarily, except the omega of ether and omega of litecoin all the coefficients are significant which proves the dynamic relations between ether and litecoin. <br>
               
![el](https://github.com/WangJiajia-0901/PHBS_BlockChain_2018/blob/master/Image/el.png)

Similar as the above two plots, this figure also confirms the correlations between ether and litecoin. Moreover, the most of time the correlations are positive. <br>

## Conclusion 
The  emprical analysis of the volatility spillover effects in Bitcoin, Ether and Litecoin with pair-wise DCC-GARCH models proves my original guess about that. There are comovements  in the three cryptocurrencies and most time are positively correlated. With this conculsion, we can make better investment decisions in cryptocurrencies. The future study is to deeper this project to find more detailed relationship and analyze the ceration changes in different certain period instead of getting the overall conclusion.
## References
[1]  Mandelbrot, B. B.(1963) The Variation of Certain Speculative Prices. The Journal of Business 36, No. 4,394-419.
[2]  Nader Trabelsi.(2019) Are There Any Volatility Spill-Over Effects among Cryptocurrencies and Widely Traded Asset Classes? Journal of Rish and Financial Management, 11, 66-83.
[3]  Norwegian University of Science and Technology, Multivariate DCC-GARCH Model-with various error distributions. Lecture notes.
[4]  Paraskevi Katsiampaa.(2019) Shaen Corbet, Brian Lucey. Volatility spillover effects in leading cryptocurrencies: A BEKKMGARCH
analysis, Finance Research Letters,29, 68–74.
