# Group 10's Readme file: Calculation and early warning of stock stop loss points

## Overview of our project
##### The purpose of our project is to calculate stock stop loss point and give early warning,so that investors can avoid large scale loss.We use python to write our code.We will introduce 4 ways to calculate stop loss points,including **fixed percentage stop loss method,moving stop method,reason disappear stop loss method,moving average stop loss method**.And we will write code to display **fixed percentage stop loss method and moving stop method**.

## Usage
##### To process the code,you have to:
##### import yfinance
##### import matplotlib.pyplot
##### import numpy 

## Link of code
##### [sample code(writing with google colab)](https://colab.research.google.com/drive/15Mct6zQCICH-HlnkSSqYgKHWxnMIBvz7?usp=sharing).

## How our code works
##### At first input the stock you want to calculate and time period you want to observe.We use **AAPL** stock from 2023-01-01 to 2023-04-01 as example.In our example,when stock's closing price decreases 5%,it will trigger fixed percentage stop loss method to print stop loss point.And when Minimum value within rolling window decreases 5% it triggers moving stop method to print.

## Introduction to our codes
#### import yfinance as yf 　用於下載股票數據 
#### import matplotlib.pyplot as plt 　用於於繪製數據的圖表
#### import numpy as np  　提供數值計算的函式，如陣列操作和條件運算
####     
#### def 停損點計算(ticker, start_date, end_date, fixed_stop_loss_percentage=0.05, trailing_stop_loss_period=10):
####    """
####    :param ticker: 股票代碼（例如 'AAPL'）
####    :param start_date: 開始日期，格式 'YYYY-MM-DD'
####    :param end_date: 結束日期，格式 'YYYY-MM-DD'
####    :param fixed_stop_loss_percentage: 固定止損比例，預設為 5%
####    :param trailing_stop_loss_period: 滾動止損的時間區間（天數），預設為 10 天
####    """

####    data = yf.download(ticker, start=start_date, end=end_date)  　用於下載股票歷史數據，包含開盤、最高、最低、收盤價格、成交量等

####    fixed_stop_loss_price = data["Close"] * (1 - fixed_stop_loss_percentage)  　計算固定止損價格，固定止損是基於當日的收盤價減少固定比例

####    trailing_stop_loss_price = data["Close"].rolling(window=trailing_stop_loss_period).min()  　計算滾動止損價格，滾動止損是基於過去指定天數的最低收盤價

####    data['Fixed_Stop_Alert'] = np.where(data['Close'] <= fixed_stop_loss_price, 'Fixed Stop-Loss Hit', 'Safe')  假設若股價低於固定止損價格，則觸發固定止損警報

####    data['Trailing_Stop_Alert'] = np.where(data['Close'] <= trailing_stop_loss_price, 'Trailing Stop-Loss Hit', 'Safe')  　假設若股價低於滾動止損價格，則觸發滾動止損警報

####    alerts = data[(data['Fixed_Stop_Alert'] == 'Fixed Stop-Loss Hit') | (data['Trailing_Stop_Alert'] == 'Trailing Stop-Loss Hit')] 　　提取觸發止損警報的數據，篩選出那些觸發固定止損或滾動止損的日期

####    print(f"Stop-Loss Alerts for {ticker}:")　 打印觸發止損警報的數據
####    print(alerts[['Close', 'Fixed_Stop_Alert', 'Trailing_Stop_Alert']])　　 顯示那些觸發止損的日期、收盤價，以及是哪種止損（固定或滾動）

    
####    plt.figure(figsize=(10, 6))   設定圖表的大小為 10x6
####    plt.plot(data["Close"], label="Close Price", linewidth=2)   繪製股價的收盤價格曲線（藍色實線）
####    plt.plot(fixed_stop_loss_price, label="Fixed Stop-Loss", linestyle="--")  　繪製固定止損價格（黃線，虛線）
####    plt.plot(trailing_stop_loss_price, label="Trailing Stop-Loss", linestyle="--")   　繪製滾動止損價格（綠線，虛線）
####    上述四行程式碼用來畫出股價和止損線的圖表
    
####    plt.scatter(alerts.index, alerts["Close"], color="red", label="Stop-Loss Triggered", zorder=5)　　當股價觸發止損警報時，會用紅色圓點標註這些點

####    plt.title(f"{ticker} Stop-Loss Alert System")  　設置圖表的標題為股票代碼
####    plt.xlabel("Date")   　設置 X 軸標籤為「日期」
####    plt.ylabel("Price")   　設置 Y 軸標籤為「價格」
####    plt.legend()   　顯示圖例，標註不同的線條和標註的意圖
####   plt.show()   　顯示圖表




## Our sample graph
![image](https://github.com/Jameshsu226/skills-copilot-codespaces-vscode/blob/main/.github/%E4%B8%8B%E8%BC%89%20(3).png)

## Our reference resources
##### [停損/停利是什麼？如何設置停損點與停利點？股市賺錢必學觀念](https://finguider.cc/Article/ArticleIndex/726).
##### [停損是什麼？如何設置停損點？停損優缺點分析](https://rich01.com/stop-loss-point/).
