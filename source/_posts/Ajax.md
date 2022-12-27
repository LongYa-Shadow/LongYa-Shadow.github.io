---
title: 'AJAX'
data:  '2021-8-1 00:14:06'
tags:  
- 教程
- AJAX
- 前端
description: 'AJAX简介、特点与优点、XML简介、http协议、响应报文、请求报文、GEI请求、POST请求、 原生AJAX使用方法、jQuery使用方法、原生Fetch使用方法、'
cover: https://klcxy.top/oss-manage-service/ossinfo/queryOssUrl?tbOssInfo.oiid=295
---****



## 1.1 Ajax 简介
Ajax 全称为Asynchronous Javascript And XML,就是异步的JS和XML.
通过Ajax可以在浏览器中向服务器发送异步请求，最大优势：**无刷新获取数据**

## 1.2 XML 简介
XML	可以扩展标记语言。
XML	被设计用来传输和储存数据。
XML	和 HTML类似，不同的是HTML中都是预定义标签，而XML中没有预定义标签，
全都是自定义标签，用来标识数据。

```
比如说我有一个学生数据：
name="谢尔比"age=18;gender="男"
用XML标识：
<student>
<name>谢尔比</name>
<age>18</age>
<gender>男</gender>
</student> 
```
现在已经被JSON取代了
```
用JSON标识
{"name":"谢尔比","age":"18","gennder":"男"}
```
## 1.3 Ajax 的特点
### 1.3.1 Ajax 的优点

1.  可以无需刷新页面与服务器端进行通信
2.  允许你根据用户事件来更新部分页面内容(事件：鼠标，键盘，文档事件)

### 1.3.2 Ajax 的缺点
1. 没有浏览记录历史，不能回退
2. 存在跨域问题(同源)
3. SEO不友好(SEO:搜索引擎优化的意思)

## 2 HTTP协议，请求和响应报文
### 2.1	HTTP协议
HTTP(hyperte transport protocol) 协议[超文本传输协议]，协议详细规定了浏览器和万维网服务器之间互相通信的规则

### 2.2 请求报文
重点是格式与参数
```
行		POST	/S?ie-utf-8	HTTP/1.1	[请求方法 /url 协议版本]
头部		HOST:atguigu.com
		cookie：name=guigu
		Content-type: application/x-www-form-urlencoded
		User-Agent: chrome 83
空行
体		username=andmi&&password=admin
```
如果是GET请求，请求体为空，如果是POST请求，请求体可以不为空。
### 2.3 响应报文
```
行	HTTP/1.1	200 Ok		[协议版本，状态码，状态描述，之间用空格隔开
头	ContentType: text/html;charset=utft-8
	 Content-length: 2048
	 Content-encoding: gzip
空行
体<html>
	<head>
	</head>
	<body>
	</h1>Ajax</h1>
	</body>
</html>
```


| 状态码( 常见) | 说明                                       |
| ------------- | ------------------------------------------ |
| 200           | 响应成功                                   |
| 404           | 请求资源不存在                             |
| 403           | 服务器接收到请求，但是拒绝提供服务(被禁止) |
| 401           | 未授权                                     |
| 500           | 服务器内部错误                             |

详细请看：

[https://blog.csdn.net/a19881029/article/details/14002273]: 

## 3 Node.js安装
[http://nodejs.cn/download/]:

在命令行输入	node -v	出现版本则安装成功

![image-20210911154123750](C:\Users\Code muscle\AppData\Roaming\Typora\typora-user-images\image-20210911154123750.png)

## 4 Express框架
	npm init --yes	初始化
	npm i express 安装express	
```javascript
	//1、引入入express
	const express = require('express');
	//2、创建应用对象
	const app = express();
	//3、创建路由规则
	app.("/",(reqest,response)=>{
	response.send("hello,express");
	})
	
	//4、监听端口启动服务
	app.listen(8000,()=>{
	console.log("服务已经启动，8000端口监听中....")
	}
```
	node 文件名.js	启动测试	访问127.0.0.1:8000

## 5 Ajax请求
### 5.1	案例准备
GET.HTML
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AJAX GET 请求</title>
    <style>
        #result {
            width: 200px;
            height: 150px;
            border: 1px solid #90b;
        }
    </style>
</head>

<body>
    <button>按钮</button>
    <div id="result"></div>
</body>
</html>
```

Server.js
```javascript
//1.引入express
const express = require('express');

//2.创建应用对象
const app = express();

//创建路由规则
//request   是对请求报文的封装
//response 是对响应报文的封装
app.get('/server', (request, response) => { 
    //设置响应头    允许跨域
    response.setHeader('Access-Control-Allow-Origin','*')
  //设置响应
  response.send('HELLO AJAX');
});

//4.监听端口启动服务
app.listen(8000, () => {
  console.log('服务已经启动,8000 端口监听中...');
});

```
```cmd
在当前文件夹启动终端	
文件名.js	启动测试
在浏览器输入输入127.0.0.1:8000/server	测试
```

### 5.2	GET请求基本操作(原生)
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AJAX GET 请求</title>
    <style>
        #result {
            width: 200px;
            height: 150px;
            border: 1px solid #90b;
        }
    </style>
</head>

<body>
    <button>按钮</button>
    <div id="result"></div>


    <script>
        //获取button元素
        const btn = document.getElementsByTagName('button')[0]
        const result = document.getElementById('result')
        //绑定事件
        btn.onclick = function () {
            //1、创建对象
            const xhr = new XMLHttpRequest()
            //2、初始化，设置请求方法和url
            xhr.open('GET', 'http://127.0.0.1:8000/server')
            //3、发送
            xhr.send()
            //4、事件绑定 处理服务器端返回的结果
            //on when 当...时候
            /*readystate   是xhr对象中的属性，标识状态 0 1 2 3 4
            0： 请求未初始化
            1： 与服务器建立链接
            2： 请求以接收
            3： 请求处理中
            4： 请求以完成，且响应以就绪
            */
            //change    改变
            xhr.onreadystatechange = function () {
                //判断服务器返回了所有结果
                if(xhr.readyState===4){
                    // 判断响应状态码   200 404 500 403
                    //2xx   成功
                    if(xhr.status>=200&&xhr.status<300){
                        //处理结果  行 头 空行 体
                        //响应
                        console.log(xhr.status);    //状态码
                        console.log(xhr.statusText);//状态字符串
                        console.log(xhr.getAllResponseHeaders());//所有响应头
                        console.log(xhr.response);//响应体
                        //设置result的文本
                        result.innerHTML=xhr.response
                    }else{

                    }
                }
            }

        }
    </script>
</body>

</html>
```
Server.js	和5.1案例准备Server.js相同


### 5.3  POST请求(原生)
AJAX POST.html
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AJAX POST 请求</title>
    <style>
        #result {
            width: 200px;
            height: 100px;
            border: 1px solid #903;
        }
    </style>
</head>

<body>
    <div id="result"></div>
    <script>
        //获取元素
        const result = document.getElementById('result')

        //绑定事件
        result.addEventListener('mouseover', function () {
            //1、创建对象
            const xhr = new XMLHttpRequest()
            //2、初始化设置请求类型与URL
            xhr.open('POST', 'http://127.0.0.1:8000/server')
            //设置请求头
            xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded')
            //设置自定义请求头
            xhr.setRequestHeader('name','gaopeng623')
            //3、发送   (参数可以任意格式，前提是服务端有对应处理方法)
            xhr.send('a=100&b=200&c=300')   //传递参数（ url格式居多和json格式）
            xhr.send('a:100&b:200&c:300')
            xhr.send('1212')
            //4、事件绑定
            xhr.onreadystatechange = function () {
                //判断
                if (xhr.readyState === 4) {
                    if (xhr.status >= 200 && xhr.status < 300) {
                        //处理服务器返回的结果
                        result.innerHTML = xhr.response
                    }
                }
            }
        })

    </script>
</body>
	
</html>

```
Server.js
``` javascript
//1.引入express
const express = require('express')

//2.创建应用对象
const app = express()

//创建路由规则
//request   是对请求报文的封装
//response 是对响应报文的封装
app.get('/server', (request, response) => {
  //设置响应头    允许跨域
  response.setHeader('Access-Control-Allow-Origin', '*')
  //设置响应
  response.send('HELLO AJAX')
})
//可以接收任意类型的请求 
app.all('/server', (request, response) => {
  //设置响应头    允许跨域
  response.setHeader('Access-Control-Allow-Origin', '*')
  //设置自定义响应头需要开发所有
  response.setHeader('Access-Control-Allow-Headers','*')
  //设置响应
  response.send('HELLO AJAX POST')
})

//4.监听端口启动服务
app.listen(8000, () => {
  console.log('服务已经启动,8000 端口监听中...')
})

```

### 5.4设置JSON响应
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JSON响应</title>
    <style>
        #result {
            width: 200px;
            height: 100px;
            border: solid 1px #89b;
        }
    </style>
</head>

<body>
    <div id="result"></div>
    <script>
        const result = document.getElementById('result')

        //绑定键盘按键事件
        window.onkeydown = function () {
            //发送请求
            const xhr = new XMLHttpRequest();   //创建对象
            //设置响应体数据类型
            xhr.responseType = 'json'
            //初始化
            xhr.open('GET', 'http://127.0.0.1:8000/json-server');
            //发送请求
            xhr.send();
            //事件绑定
            xhr.onreadystatechange = function () {
                if (xhr.readyState === 4) {
                    if (xhr.status >= 200 && xhr.status < 300) {
                        //手动数据转换
                        console.log(xhr.response);
                        // let data = JSON.parse(xhr.response)
                        // result.innerHTML = data.name;
                        //自动转换!!!(需设置响应体数据类型)
                        console.log(xhr.response);
                        result.innerHTML = xhr.response.name; 

                    }
                }
            }
        }
    </script>
</body>

</html>
```

```javascript
//1.引入express
const express = require('express')

//2.创建应用对象
const app = express()

//创建路由规则
//request   是对请求报文的封装
//response 是对响应报文的封装
//可以接收任意类型的请求 
app.all('/json-server', (request, response) => {
  //设置响应头    允许跨域
  response.setHeader('Access-Control-Allow-Origin', '*')
  //设置自定义响应头需要开发所有
  response.setHeader('Access-Control-Allow-Headers','*')
  //响应一个数据
  const data = {
    name :'gaopeng'
  }
  //对对象进行字符串转换
  let str  = JSON.stringify(data)

  //设置响应(只接收字符串)
  response.send(str)
})  

//4.监听端口启动服务
app.listen(8000, () => {
  console.log('服务已经启动,8000 端口监听中...')
})

```

### 5.5	jQuery发送请求
	$.get('url',{data:data},callback,type)
	$.post('url',{data:data},callback,type)
	url:发送请求地址
	data:数据(对象形式)
	callback:回调函数
		type:返回值类型

### 5.6 fetch发送请求
```html
<script>
	fetch('url',{
	//请求方法
	method:'POST'，
	//请求头
	headers:{
	name:'name',
	age:18
	},
	body:'username=admin&password=admin'
}	
	}).then(response=>{
	console.log(response)
})
</script>

```