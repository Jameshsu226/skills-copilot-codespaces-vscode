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

## Our sample graph
![image](https://github.com/Jameshsu226/skills-copilot-codespaces-vscode/blob/main/%E4%B8%8B%E8%BC%89%20(2).png)

## Our reference resources
##### [停損/停利是什麼？如何設置停損點與停利點？股市賺錢必學觀念](https://finguider.cc/Article/ArticleIndex/726).
##### [停損是什麼？如何設置停損點？停損優缺點分析](https://rich01.com/stop-loss-point/).
