Puell Multiple指標的意義就是 究竟我們在一整天當中 所有的礦工總共可以挖到多少美金單位價值
https://zhuanlan.zhihu.com/p/265937933
**Puell Multiple =每日挖礦產值（美元）/每日挖礦產值（美元）的移動平均值**

程式: 使用Puell Mutltiple指標判斷 在Puell Multiple低的時候買入BTC Puell Multiple高的時候換成現金 存股與換回現金並回測
策略:
```
# 每個月固定投入10000元現金。

# Puell multiple 指數低時(< 1.2)，直接買入BTC；指數高時(>=1.2)先存起來。

# Puell multiple 指數非常高時(>2.5)，贖回 20%。

# Puell multiple 指數非常低時(<0.7)，將之前存下來或贖回的錢，加碼買入BTC。
```
[Puell Mutltiple 優化過業程式碼](https://colab.research.google.com/drive/1IsJaspZOCpRE5LLRh5IlbAZ16aTk3l_1#scrollTo=glWhKvs1kdKV)