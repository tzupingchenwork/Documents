**Sma**

**最簡單的均線，也就是將「前N天」取平均後的價格，也就是「前N天」的每一個價格，其權重都是一樣的。**

英文：https://www.investopedia.com/terms/s/sma.asp

中文：https://www.cmoney.tw/learn/course/technicals/topic/485

**Wma**

**與SMA不一樣的地方是，權重是等比數列減少，比較近期的價格，權重比較重，而每往後一個價格，其權重多乘以 1/K**

英文：https://www.investopedia.com/articles/07/ewma.asp

中文：https://kknews.cc/zh-tw/finance/orbr66.html

**Alma**

**這個filter的權重是三角形的，也就是第 0 比價格跟第 N 比價格的權重為 0 ，而第 N/2 筆的權重為 2/N**

http://www.forexfactory.com/attachment.php?attachmentid=1123528&d=1359078631

**Detrend**

**Detrend，是先用 high pass filter 先找出雜訊的部分，再用股價減掉雜訊，就會是平滑曲線囉！**

https://c.mql5.com/forextsd/forum/77/ehlers\_-\_optimal\_detrending.pdf

**Regression**

**將 N 個價格來做線性回歸，並且看線性回歸的數值最後落在哪裡，形成的優化結果**

https://www.bookstack.cn/read/talib-zh/func\_groups-statistic\_functions.md#LINEARREG%20-%20Linear%20Regression

**Hullma**

**其公式將雜訊特別先放大兩倍，再額外用 WMA 來優化，這樣的好處是價格反應速度比較快，而且非常平滑，我設計策略的時候滿常使用的**

https://www.fidelity.com/learning-center/trading-investing/technical-analysis/technical-indicator-guide/hull-moving-average

**Lowpass**

**一般的低通率波器，將雜訊經由數學運算給去除，原理是使用離散 fourier transform 但是公式比較複雜，有興趣可以參考以下連結喔！**

https://ethz.ch/content/dam/ethz/special-interest/mtec/chair-of-entrepreneurial-risks-dam/documents/dissertation/master%20thesis/MAS\_Johan\_Boissard\_Dec12.pdf

**Zlma**

**Zero lag moving averAge，這個指標希望達成 0 延遲的作用，與hullma相似，但hullma的去雜訊過程有兩次，而zlma只有一次，雖然看似0延遲，但是我實際用起來覺得沒有很好用（至少在加密貨幣上）**

https://en.wikipedia.org/wiki/Zero\_lag\_exponential\_moving\_a