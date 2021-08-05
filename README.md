# HEBE-Wallet
HEBE-Wallet对外接口

> dapp接口，网页应用可以通用webkit.messageHandlers.cordova_iab进行调用

1.获取当前钱包地址：getAddr

| method | getAddr | |
| :-----| ----: | ----: | 
| args | callbackName |coin | 
|  |  回调函数名| 币种名称 | 

例：
```javascript
//发送请求
 var callbackName ="iab_callback"
 webkit.messageHandlers.cordova_iab.postMessage(JSON.stringify({
            method: "getAddr",
            args: ['iab_callback', 'hebe']
 }))

//接受返回
 window[callbackName] = function (successful, position) {
        //position.method 返回的方法名如：getAddr
        if (position.method == "getAddr") { 
        }
    };
```

2.拉起App支付模块：pay

| method | pay | |
| :-----| ----: | ----: | 
| args | callbackName |model | 
|  |  回调函数名| {addr: "",sum:0,coin: '',msg: ""} | 

例：
```javascript
//发送请求
 var callbackName ="iab_callback"
 webkit.messageHandlers.cordova_iab.postMessage(JSON.stringify({
            method: "pay",
            args: ['iab_callback', {addr: "HEBE-NVCZ-X888-HMND-HHLBL",sum: 0.1,coin: 'Hebe',msg: "测试hebe转账" }]
 }))

//接受返回
 window[callbackName] = function (successful, position) {
        //position.method 返回的方法名如：getAddr
        if (position.method == "pay") { 
        }
    };
```
> Hebe Wallet app拉起支付参数
```javascript
let href="hebewallet://?model="+encodeURIComponent(JSON.stringify({
                                    "addr": "HEBE-N4BJ-D93A-FNSZ-EYR6D",
                                    "sum": "18.75",
                                    "type": "HEBE",
                                    "msg": "p:55340232252800822516",
                                    "url":"hebewalletxjk://?model="})
```         
