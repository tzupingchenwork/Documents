# AI筆記
## 1-1 打造專屬實驗室
* miniconda python 懶人包
	* 可以管理不同版本的 python
	* 管理不同 environments 和 packages

* 安裝 jupyter lab
```
conda install -c conda-forge jupyterlab

jupyter lab
```

本章主要在介紹 如何建置環境和 jupyter lab 使用教學

## 1-2 打造專屬實驗室
* 創建環境
```
conda create -n finlabAI python=3.6
```
* 啟用環境
```
conda active finlabAI
```

* 安裝方法(MacOS)

1. [安裝miniconda](https://docs.conda.io/en/latest/miniconda.html)

2. 打開 terminal 並一次性輸入以下指令後，按下enter執行：
```
fileid="1Wwlk1PccBoH7L2ELTNhCjG\_D4t8rCZcA" && filename="setup_env.sh" && curl -c ./cookie -s -L "https://drive.google.com/uc?export=download&id=${fileid}" > /dev/null && curl -Lb ./cookie "https://drive.google.com/uc?export=download&confirm=`awk '/download/ {print $NF}' ./cookie\`&id=${fileid}" -o ${filename}
```

3. 接著輸入第二行
```
echo Y | source setup_env.sh
```

耐心等待，假如跑到一個地方跑太久，可以按 Enter ，假如卡住就會自動繼續跑。跑完最後沒有出現 ERROR 就是安裝成功囉！這個程式會幫你重新安裝 finlab 環境、並且安裝需要的 packages，最後還會幫你下載並且測試課程範例喔！

本章主要在介紹 如何建置環境和 安裝所需要的packages , ipywidgets , talib 

## 1-3 大盤1分k爬蟲練習

```
import request
res = request.get('目標網址')
```

```
import pandas as pd
import io #轉成虛擬的的檔案
df = pd.read_csv(io.StringIO(res.text),header=1,index_col='時間')
```
* index_col='時間' 把時間的col轉換成 index
* 資料整理清除不必要資料
```
df = df.dropna(how='all', axis=0)
```
* 時間加上日期
1. 日期轉換成字串
```
date = datetime.date(2019,1,2)
datestr = date.strftime("%Y%m%d")
res = requests.get("http://www.twse.com.tw/exchangeReport/MI_5MINS_INDEX?response=csv&date=" + 
                   date_str + "&_=1544020420045")
```
2.把index時間加上日期
```
df.index = pd.to_datetime(date.strftime('%Y %m %d ') + pd.Series(df.index))
```
* 千位數處理 轉成空自串 再把所有的資料轉 float
```
def abc(e):
    ret = str(e)
    ret = ret.replace(",", "")
    ret = float(ret)
    return ret#float(str(e).replace(",", ""))

df = df.applymap(abc)
```

本章主要在介紹 如何爬蟲並做資料處理

>  u01_benchmark_crawler.ipynb
> [課程連結](https://hahow.in/courses/5b9d3a6dca498a001e917383/discussions?item=5b9d4830ca498a001e917696)

## 1-4 獨家上市櫃資料儲存
* 讀取pkl檔案
```
import pandas as pd
df = pd.read_pickle("history/tables/price.pkl")
```
* 時間區間 幫忙枚舉區間日期
	* date_range()
	* month_range()
	* season_range()
* GUI 介面產生
```
widget("price", crawl_price, date_range)
```

* 轉換成方便進行財經研究的格式
```
from finlab.crawler import commit
commit()
```

本章主要在介紹 如何使用 finlabb api
>  u02_crawlers.ipynb
> [課程連結](https://hahow.in/courses/5b9d3a6dca498a001e917383/discussions?item=5c4c683059ffe1002002f352)

## 1-5 獨家上市櫃資料儲存
* table_date_range() 會去找table 的資料開始結束時間
* update_table() 更新資料庫
	update_table(table_name, crawl_function, dates)
* 某些爬蟲不需要傳入參數 例如減資和除權息
	* 檢查函式需不需要參數 
```
from inspect import signature
sig = signature(crawl_function)
if len(sig.parameters) != 0:
```
* to_pickle() 把新舊資料庫做合併
* 加入新的爬蟲到finlab API中
* 讀取資料庫資料
```
from finlab.data import Data

data = Data()

df = data.get("發行量加權股價指數")
```

本章主要在介紹 如何使用 finlabb api 自動更新 並加入新的爬蟲
>  u02_crawlers.ipynb
> [課程連結](https://hahow.in/courses/5b9d3a6dca498a001e917383/discussions?item=5cced48ac217950020eba563)

## 2-1 大盤歷史圖表分析
* 可以畫漂亮的圖
```python 
import seaborn as sns 
sns.set()
```
* groupby() 可以把 series dataframe 分組做分類
* reset_index() 可以將 series 變成 dataframe
* pd.to_datetime() 可以將字串時間轉成 datetimeindex
* 計算股價與均線的乖離率
* 把股價與乖離率作圖並做分析 發現規律會呈現反比的狀況
	正乖離的時候股價越有可能會往下
	
> 可以單拉200筆(課程中)或是一年的資料 判斷當年的乖離率區間，並判斷目前的乖離率是否過大，就有下跌的可能

本章主要在介紹 如何使用 seaborn 做圖表分析，並以乖離率作為例子
>  u03_benchmark_analysis.ipynb
> [課程連結](https://hahow.in/courses/5b9d3a6dca498a001e917383/discussions?item=5c4c687559ffe1002002f374)