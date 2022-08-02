# tradingview 指標
```
指标组参考：

1分钟K线指标组：5分钟、15分钟、1小时

5分钟K线指标组：15分钟、90分钟、6小时

30分钟K线指标组：6小时、1天、3.5天

4小时K线指标组：12小时、3.5天、14天

日线指标组：1天、7天、14天

周线指标组：2周、月线、季线
```

## 4H
```
==4H

//@version=5

indicator(title='Stochastic', shorttitle='4H 12H 3.5D', format=format.price, precision=2)

  

h0 = hline(85)

h1 = hline(15)

h2 = hline(50)

  

// 4H

periodK = input.int(10, title='K', minval=1)

periodD = input.int(3, title='D', minval=1)

smoothK = input.int(3, title='Smooth', minval=1)

k = ta.sma(ta.stoch(close, high, low, periodK), smoothK)

d = ta.sma(k, periodD)

plot(k, title='%K', color=color.new(color.blue, 0), linewidth=1)

plot(d, title='%D', color=color.new(color.red, 0), linewidth=1)

  
  

// 12H 3 * 10

periodK1 = input.int(30)

periodD1 = input.int(9, title='D2', minval=1)

smoothK1 = input.int(9, title="Smooth1", minval=1)

k1 = ta.sma(ta.stoch(close, high, low, periodK1), smoothK1)

d1 = ta.sma(k1, periodD1)

plot(k1, title="%K1", color=color.silver, linewidth=1)

plot(d1, title="%D1", color=color.lime, linewidth=1)

  
  

// 3.5D 3 * 10 * 7

periodK2 = input.int(210)

periodD2 = input.int(63, title='D2', minval=1)

smoothK2 = input.int(63, title='Smooth2', minval=1)

k2 = ta.sma(ta.stoch(close, high, low, periodK2), smoothK2)

d2 = ta.sma(k2, periodD2)

plot(k2, title='%K2', color=color.new(#FFFFFF, 0), linewidth=2)

plot(d2, title='%D2', color=color.new(color.yellow, 0), linewidth=2)
```
  
## D
```
==D

//@version=5

indicator(title='Stochastic', shorttitle='4H 12H 3.5D', format=format.price, precision=2)

  

h0 = hline(85)

h1 = hline(15)

h2 = hline(50)

  

// D

periodK = input.int(10, title='K', minval=1)

periodD = input.int(3, title='D', minval=1)

smoothK = input.int(3, title='Smooth', minval=1)

k = ta.sma(ta.stoch(close, high, low, periodK), smoothK)

d = ta.sma(k, periodD)

plot(k, title='%K', color=color.new(color.blue, 0), linewidth=1)

plot(d, title='%D', color=color.new(color.red, 0), linewidth=1)

  
  

// W

periodK1 = input.int(10*7)

periodD1 = input.int(3*7, title='D2', minval=1)

smoothK1 = input.int(3*7, title="Smooth1", minval=1)

k1 = ta.sma(ta.stoch(close, high, low, periodK1), smoothK1)

d1 = ta.sma(k1, periodD1)

plot(k1, title="%K1", color=color.silver, linewidth=1)

plot(d1, title="%D1", color=color.lime, linewidth=1)

  
  

// 2W

periodK2 = input.int(10*7*2)

periodD2 = input.int(3*7*2, title='D2', minval=1)

smoothK2 = input.int(3*7*2, title='Smooth2', minval=1)

k2 = ta.sma(ta.stoch(close, high, low, periodK2), smoothK2)

d2 = ta.sma(k2, periodD2)

plot(k2, title='%K2', color=color.new(#FFFFFF, 0), linewidth=2)

plot(d2, title='%D2', color=color.new(color.yellow, 0), linewidth=2)
```
 
## 30MIN
```
==30min

//@version=5

indicator(title='Stochastic', shorttitle='30min 1D 3.5D', format=format.price, precision=2)

  

h0 = hline(85)

h1 = hline(15)

h2 = hline(50)

  

// 30min

periodK = input.int(10, title='K', minval=1)

periodD = input.int(3, title='D', minval=1)

smoothK = input.int(3, title='Smooth', minval=1)

k = ta.sma(ta.stoch(close, high, low, periodK), smoothK)

d = ta.sma(k, periodD)

plot(k, title='%K', color=color.new(color.blue, 0), linewidth=1)

plot(d, title='%D', color=color.new(color.red, 0), linewidth=1)

  
  

// D

periodK1 = input.int(10*12)

periodD1 = input.int(3*12, title='D2', minval=1)

smoothK1 = input.int(3*12, title="Smooth1", minval=1)

k1 = ta.sma(ta.stoch(close, high, low, periodK1), smoothK1)

d1 = ta.sma(k1, periodD1)

plot(k1, title="%K1", color=color.silver, linewidth=1)

plot(d1, title="%D1", color=color.lime, linewidth=1)

  
  

// 3.5D

periodK2 = input.int(10*2*24*3.5)

periodD2 = input.int(3*2*24*3.5, title='D2', minval=1)

smoothK2 = input.int(3*2*24*3.5, title='Smooth2', minval=1)

k2 = ta.sma(ta.stoch(close, high, low, periodK2), smoothK2)

d2 = ta.sma(k2, periodD2)

plot(k2, title='%K2', color=color.new(#FFFFFF, 0), linewidth=2)

plot(d2, title='%D2', color=color.new(color.yellow, 0), linewidth=2)
```