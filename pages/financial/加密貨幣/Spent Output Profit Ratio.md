# Spent Output Profit Ratio
比技術面可靠，因為資料是通常都是從 blockchain 上，直接萃取出來。
公式 : 賣出價格換算美金 / 買進換算美金
* 牛市的時候: 價格上漲的時候普遍來說SOPR都是正的，但是如果跌到1以下通常是暫時的，接近1的時候通常是好買點。
* 熊市的時候: 價格下跌的時候普遍來說SOPR都是負的，但是如果漲到1以上通常是暫時的，接近1的時候通常是好賣點。

程式: 把SOPR用sma去雜訊計算出兩種均線 黃金交叉且SOPR大於1(向上趨勢)的時候買進 死亡交叉出場
[SOPR程式碼](https://colab.research.google.com/drive/1dbveFgfVmZXXUDTrEc0rM7ZlKcYk9x7J#scrollTo=JItrU6IksvgK)

調整後的SOPR（aSOPR）（24天移動平均線）