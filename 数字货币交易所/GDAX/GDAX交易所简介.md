# GDAX交易所简介 #
--------
## 撮合机制 ##

1.按照下单时间放入交易队列进行撮合

2.同一用户的两个订单不会相互撮合

3.订单以交易队列中的订单价格进行撮合，比如，A下了100块买btc单，之后，B下了80块卖btc单，由于A的订单先到，那么，该笔撮合的成交价为100块。

4.订单生命周期：订单提交（received状态） --> 部分成交（open状态） --> 撤单/完全成交（done状态）

## 手续费 ##
### 交易手续费 ###

GDAX以 maker-taker模式进行运作。

maker：增加市场行情深度的一方，即下的单不是立即成交，而是进入到交易队列，供taker进行撮合

taker：消耗市场行情深度的一方，即下单立即成交，消耗市场行情深度

手续费为交易额的百分比，如下表：

	User 30 day USD volume	Taker fee	Maker fee
		$0 - $10m			  0.30 %	   0 %
		
		$10m - $100m		  0.20 %	   0 %

		$100m+				  0.10 %	   0 %

> 即，根据用户**最近30天等值USD的交易量**进行阶梯收费，maker不需手续费。当交易对两方都不是USD的话，需要进行换算，类似于汇率。比如：以1 ETH交易0.1 BTC，市场上最近一笔ETH-USD为1 ETH等值100USD，那本次交易量则计算为100USD。

### 充值提现手续费 ###
无手续费

## 数据中心 ##

原文：GDAX data centers are in the Amazon US East N. Virginia (us-east-1) region.


## 沙箱模式 ##
GDAX提供公共的沙箱模式，供用户测试API连接和在线交易。沙箱提供了正式交易所所有的功能，包括模拟资金数量。
沙箱与正式环境的会话和API秘钥都是隔离的。**需要用户通过网页上的接口生成沙箱使用的key**

增加资金操作，与网页上充值提现操作一致。

### 沙箱URL ###

**提示：进行实盘交易或沙箱测试前，请千万确定相应URL！！！**

When testing your API connectivity, make sure to use the following URLs.

Website

    https://public.sandbox.gdax.com
REST API

	https://api-public.sandbox.gdax.com
Websocket Feed

	wss://ws-feed-public.sandbox.gdax.com
FIX API

	tcp+ssl://fix-public.sandbox.gdax.com:4198

## 客户端示例 ##
### 官方 ###
Node.js  `https://github.com/coinbase/gdax-node`

Node.js交易工具  `https://github.com/coinbase/gdax-tt`

Ruby(不再维护)	`https://github.com/coinbase/coinbase-exchange-ruby`

### 非官方 ###
Go		`https://github.com/preichenberger/go-coinbase-exchange`

Haskell	`https://github.com/AndrewRademacher/coinbase-exchange`

Java	`https://github.com/irufus/gdax-java`

Python	`https://github.com/danpaquin/gdax-python`

Rust	`https://github.com/luqmana/gdax-client`

C#		`https://github.com/dougdellolio/gdax-csharp`

