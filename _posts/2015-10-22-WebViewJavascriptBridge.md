---
layout: post
title: WebViewJavascriptBridge–原生iOS 与 网页元素互相通信
comments: true
category: 技术
---

WebViewJavascriptBridge–原生iOS 与 网页元素互相通信



**简介**

项目地址:[WebViewJavascriptBridge](https://github.com/marcuswestin/WebViewJavascriptBridge)

最新示例：[点击下载](http://)



**使用**

* 使用UIWebview 或 WebView初始化这个WebViewJavascriptBridge
	通过js中调用bridge.send方法触发，
	
	`
	// 这是WebViewJavascriptBridge  最基础的初始化操作,只需执行一次,不建议调用多次,只需初始化一次即可.
	self.bridge = [WebViewJavascriptBridge bridgeForWebView:webView handler:^(id data, WVJBResponseCallback responseCallback) {
    NSLog(@"Received message from javascript: %@", data);
    responseCallback(@"Right back atcha");
}];`

* js调用App内方法
 通过registerHandler实现，一个响应事件只需要初始化一次即可

* OC发送消息给js
  
  `[self.bridge send:@"Well hello there"];
[self.bridge send:[NSDictionary dictionaryWithObject:@"Foo" forKey:@"Bar"]];
[self.bridge send:@"Give me a response, will you?" responseCallback:^(id responseData) {
    NSLog(@"ObjC got its response! %@", responseData);
}];`

* 最后设置javascript端
  一般不需要iOS 开发人员来设置,因为是与web页交互,这个是exmple中的例子,web开发导入或设置响应的js就可以了

//js方法
```function connectWebViewJavascriptBridge(callback) {
    if (window.WebViewJavascriptBridge) {
        callback(WebViewJavascriptBridge)
    } else {
        document.addEventListener('WebViewJavascriptBridgeReady', function() {
            callback(WebViewJavascriptBridge)
        }, false)
    }
}
connectWebViewJavascriptBridge(function(bridge) {
    bridge.init(function(message, responseCallback) {
        alert('Received message: ' + message)   
        if (responseCallback) {
            responseCallback("Right back atcha")
        }
    })
    bridge.send('Hello from the javascript')
    bridge.send('Please respond to this', function responseCallback(responseData) {
        console.log("Javascript got its response", responseData)
    })
})
```
