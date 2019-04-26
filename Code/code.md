setwd("D:/北大汇丰/block chain/report")
data<-read.csv("data.csv",header = T)
head(data)
tail(data)
bitcoin<-rev(data[,2]) #reverse of bitcoin
logbitcoin<-log(bitcoin) 
bitcoinreturn<-diff(logbitcoin) #bitcoin return
ts.plot(bitcoinreturn, main="Bitcoin Return plot")


ether<-rev(data[,3])
logether<-log(ether) 
etherreturn<-diff(logether) #ether return
ts.plot(etherreturn, main="Ether Return plot")


litecoin<-rev(data[,4])
loglitecoin<-log(litecoin) 
litecoinreturn<-diff(loglitecoin) #litecoin return

ts.plot(bitcoinreturn, main="Bitcoin Return plot")
ts.plot(etherreturn, main="Ether Return plot")
ts.plot(litecoinreturn, main="Litecoin Return plot")

return<-data.frame(bitcoin=bitcoin,ether=ether,litecoin=litecoin)

### statistical summary ###
library(e1071)
summary(bitcoinreturn)
skewness(bitcoinreturn)
kurtosis(bitcoinreturn)

summary(etherreturn)
skewness(etherreturn)
kurtosis(etherreturn)

summary(litecoinreturn)
skewness(litecoinreturn)
kurtosis(litecoinreturn)

library(tseries)
library(rmgarch)
library(parallel)
library(FinTS)

### time series test ###
#op<-par(mfcol=c(2,1))
acf(bitcoinreturn)
acf(bitcoinreturn^2)

acf(etherreturn)
acf(etherreturn^2)

acf(litecoinreturn)
acf(litecoinreturn^2)

#par(opar)


Box.test(bitcoinreturn,lag = 21, type = "Ljung")
Box.test(etherreturn)
Box.test(litecoinreturn,lag=10)

adf.test(bitcoinreturn)
adf.test(etherreturn)
adf.test(litecoinreturn)

ArchTest(bitcoinreturn)
ArchTest(etherreturn)
ArchTest(litecoinreturn)

ts.plot(bitcoin, main="Cryptocurrency price",col="blue",lty=1,ylab="Price")
lines(ether,main="Ether price",col="red",lty=1)
lines(litecoin, main="Litecoin price",col="green",lty=1)
legend("topright",c("bitcoin","ether","litecoin"),col=c("blue","red","green"),lty=c(1,1,1))

### Pearson correlation

cor(return)

### dcc garch fit ####
temp <- seq.Date(from = as.Date("2015/08/07",format = "%Y/%m/%d"), by = "month", length.out = 1338)
use=data.frame(date=temp,bitcoin=bitcoin,ether=ether,litecoin=litecoin)
uspec.n = multispec(replicate(2, ugarchspec(mean.model = list(armaOrder = c(1,1)))))
dcc.11mn = dccspec(uspec.n, VAR = TRUE, lag = 4, lag.max = 12, dccOrder = c(1, 1), distribution = 'mvt')
fit.2.11mn = dccfit(dcc.11mn, data =use[,2:3])
fit.2.11mn
plot(fit.2.11mn)

uspec.n = multispec(replicate(2, ugarchspec(mean.model = list(armaOrder = c(1,1)))))
dcc.11mn = dccspec(uspec.n, VAR = TRUE, lag = 4, lag.max = 12, dccOrder = c(1, 1), distribution = 'mvt')
fit.2.11mn = dccfit(dcc.11mn, data = return[,2:3])
fit.2.11mn
plot(fit.2.11mn)

uspec.n = multispec(replicate(2, ugarchspec(mean.model = list(armaOrder = c(1,1)))))
dcc.11mn = dccspec(uspec.n, VAR = TRUE, lag = 4, lag.max = 12, dccOrder = c(1, 1), distribution = 'mvt')
fit.2.11mn = dccfit(dcc.11mn, data = return[,c(1,3)])
fit.2.11mn
plot(fit.2.11mn,xlim=c(0,1338))
