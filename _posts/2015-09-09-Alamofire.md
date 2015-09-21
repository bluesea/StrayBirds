---
layout: post
title: Alamofire 学习笔记
comments: true
category: Swift
---
						Alamofire 学习笔记

Alamofire下载地址:https://github.com/Alamofire/Alamofire

HTTP请求方法：参照RFC 7231 §4.3

			

		public enum Method: String {

		   	    case OPTIONS = "OPTIONS"

			    case GET = "GET"

			    case HEAD = "HEAD"

			    case POST = "POST"

			    case PUT = "PUT"

			    case PATCH = "PATCH"

			    case DELETE = "DELETE"

			    case TRACE = "TRACE"

			    case CONNECT = "CONNECT"

		}

		

参数Parameters

					

		1.GET:

		Alamofire.request(.GET, "http://httpbin.org/get", parameters: ["foo": "bar"])

		// http://httpbin.org/get?foo=bar

		2.POST:

		let parameters = [

		    "foo": "bar",

		    "baz": ["a", 1],

		    "qux": [

		        "x": 1,

		        "y": 2,

		        "z": 3

		    ]

		]

``		

		Alamofire.request(.POST, "http://httpbin.org/post", parameters: parameters)

		// HTTP body: foo=bar&baz[]=a&baz[]=1&qux[x]=1&qux[y]=2&qux[z]=3

		3.参数编码：（URL,JSON,PropertyList，Custom）

		let URL = NSURL(string: "http://httpbin.org/get")!

		var request = NSURLRequest(URL: URL)

``		

		let parameters = ["foo": "bar"]

		let encoding = Alamofire.ParameterEncoding.URL

		(request, _) = encoding.encode(request, parameters: parameters)

``		

		let parameters = [

		    "foo": [1,2,3],

		    "bar": [

		        "baz": "qux"

		    ]

		]

		

		Alamofire.request(.POST, "http://httpbin.org/post", parameters: parameters, encoding: .JSON)

		// HTTP body: {"foo": [1, 2, 3], "bar": {"baz": "qux"}}

Get请求：

		

		Making a Request：

			import Alamofire

			Alamofire.request(.Get,"http://httpbin.org/get")

		处理响应

			Alamofire.request(.GET, "http://httpbin.org/get", parameters: ["foo": "bar"])

   .response { (request, response, data, error) in
               println(request)
               println(response)
               println(error)
             }
   同样也可以返回其他类型的参数（responseString,responseJson,responsePropertyList）
   具体如下:
  1. Alamofire.request(.GET, "http://httpbin.org/get")
   .responseString { (_, _, string, _) in
            println(string)
   }

  2.
  Alamofire.request(.GET, "http://httpbin.org/get")
   .responseJSON { (_, _, JSON, _) in
            println(JSON)
   }

  3.链式
  Alamofire.request(.GET, "http://httpbin.org/get")
   .responseString { (_, _, string, _) in
            println(string)
   }
   .responseJSON { (_, _, JSON, _) in
            println(JSON)
   }
* 

