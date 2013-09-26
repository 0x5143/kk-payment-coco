kk-payment-coco
================

Node.js verification library for coco in app purchase receipts

## Installation
kk-payment-coco is available via npm

`npm install kk-payment-coco`

It has no external dependencies other than node itself.

## Overview
此模块用于快速搭建自己的支付验证服务器，针对触控用户系统的支付平台验证流程。
目前处于测试期，用于实际项目请谨慎。

## Usage
1、填写自己的coco.json配置文件 ，格式可参考包内的coco.example.json文件 ;
2、使用以下代码进行通知验证：

    var conf = require('coco.json');
    var COCO = require('kk-payment-coco');
    var coco = new COCO(conf);
    coco.verifyNotify(
        remoteip,
        reqdata,
        function(text) {
            //todo response to remote server.
        },
        function(result, oinfo) {
            if (result) {
                console.log('receive collect order notify.');
                //todo order info handle...
            } else {
                console.log('receive error order notify.');
            }
        }
    );
    
    其中, verifyNotify需要四个参数：
    第一个参数为接收到订单通知的远程主机IP地址；
    第二次参数为接收到的远程主机发过来的数据，要求是字符串，暂时不支持自行解析为JSON对象；
    第三个参数为回调函数，被调用时会传回返回给远程主机的Response数据；
    第四个参数为订单完成回调函数，可用于后续的订单处理。
    
## LICENSE - "MIT License"

Copyright (c) 2013 云景, http://yunjing.me/

Permission is hereby granted, free of charge, to any person
obtaining a copy of this software and associated documentation
files (the "Software"), to deal in the Software without
restriction, including without limitation the rights to use,
copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the
Software is furnished to do so, subject to the following
conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES
OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT
HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR
OTHER DEALINGS IN THE SOFTWARE.

![spacer](http://yunjing.me/1px.gif)
