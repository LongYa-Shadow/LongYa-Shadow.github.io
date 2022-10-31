
---
title: '网络通信'
data:  '2022-10-31 17:19:06'
tags:  
- 教程
- http
- 前端
- 网络通信
- TCP/IP协议族
description: '网络通信和TCP/IP及http协议简单概述，以及报文相关等...'
cover: https://klcxy.top/oss-manage-service/ossinfo/queryOssUrl?tbOssInfo.oiid=522
---

# 网络通信和TCP/IP及http协议简单概述

  #### 网络的服务器给予请求和响应的
 一[当在浏览器中输入地址后发生什么？](https://gaopeng623.top/vue-message/message/home)
        ```https:协议名 http/https/ftp..
        gaopeng623.top 域名 domain
            整个网络中存在着无数个服务器，每一个服务器都有它自己的唯一标识
              这个标识被称为 ip地址 192.168.1.17，但是ip地址不方便记忆
              域名相当于ip地址的别名
        /vue-message/message/home   网站路径资源```
      ------------------
  - DNS解析，获取网站的ip地址
  - 浏览器需要和服务器建立连接(tcp/ip)(通过三次握手)
  - 向服务器发送请求(http协议)
  - 服务器处理请求，并返回响应(http协议)
  - 浏览器将响应的页面渲染
  - 断开和服务器的连接(四次挥手)
    **客户端如何和服务器建立（断开）连接**
        通过三次握手和四次挥手
             (1)三次握手(建立连接)三次握手事客户端和服务器建立连接的过程
                  1. 客户端向服务器发送连接请求
                            SYN
                  2. 服务器收到连接请求，向客户端返回消息
                            SYN 
                            ACK
                  3. 客户端向服务器发送同意连接的信息
                            ACK
              (2)四次挥手(断开连接)
                  1. 客户端向服务器发送请求，通过知服务器数据发送完毕，请求断开连接
                            FIN
                  2. 服务器向客户端返回数据，知道
                            ACK
                  3. 服务器向客户端返回数据，收完了，可以断开连接
                            FIN
                            ACK
                  4. 客户端向服务器发送数据，知道了
                            ACK
        1.  请求和响应实际上就是一段数据，只是这段数据需要遵循一个特殊的格式
           这个特殊的格式由HTTP协议来规定
  ### TCP/IP协议族
TCP/IP协议族中包含了一组协议,这组协议规定了互联网中所有的通信的细节
 (1) 网络通信的过程由四层组成
        1. 应用层
           - 软件的层面，浏览器 服务器都属于应用层
                2. 传输层
           - 负责对数据进行拆分，把大数据拆分为一个一个小包
                3. 网络层
           - 负责给数据包，添加信息
                4. 数据链路层
           - 传输信息
           (2) HTTP(超文本传输协议)协议就是应用层的协议，
                    用来规定客户端和服务器间通信的报文格式
    - 报文（message）？
          
          浏览器和服务器之间通信是基于请求和响应的
          浏览器向服务器发送请求(request)
          服务器向浏览器返回响应(response)
          而HTTP协议就是对这个报文的格式进行规定
          
          - 请求报文（request）
              客户端发送给服务端的报文称为请求报文，请求报文格式如下:
          
                - 请求首行
               ```GET/index.html?username=gaopeng HTTP/1.1
               1. get表示请求方式（GET），常用的请求方式由get/post，get请求主要用于向服务器请求资源，post请求主要用于向服务器发送数据.  
               2. 请求的路径（index.html?username=gaopeng），？后面的内容为查询字符串，是一个名值对结构，多个名值对使用&分割.  
                 - get请求通过查询字符串将数据发送到服务器，由于查询查询字符串串在浏览器中地址栏中直接显示，安全性较差，且url地址长度有限，无法发送较大的数据  
                 - post请求通过请求体来发送数据，可以通过浏览器中的Payload中查看,不会直接显示到浏览器地址栏上，对比get安全性较好，对请求体大小没有限制，可以发送任意大小数据  
               3. 协议版本（HTTP/1.1）
               ```
                - 请求头  
                    请求头也是名值对结构，用于告诉服务器我们浏览器的信息
                  每一个头都有它的作用
                    - Accept 浏览器可以接受的文件类型
                    - Accept-Encodeing 浏览器允许的压缩编码
                    - User-Agent用户代理，他是一段用来描述浏览器信息的字符串
                - 空行
                  分割请求头和请求体
                - 请求体
                  post请求通过请求体来发送数据

``` 请求报文
请求报文
GET/index.html?username=gaopeng HTTP/1.1
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Accept-Encoding: gzip, deflate, br
Accept-Language: zh-CN,zh;q=0.9
Connection: keep-alive
Host: 127.0.0.1:5500
If-Modified-Since: Mon, 31 Oct 2022 06:59:53 GMT
If-None-Match: W/"16f-1842cd6eced"
Referer: http://127.0.0.1:5500/HTTP%E5%8D%8F%E8%AE%AE/http%E5%8D%8F%E8%AE%AE.html
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: same-origin
Sec-Fetch-User: ?1
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/106.0.0.0 Safari/537.36
sec-ch-ua: "Chromium";v="106", "Google Chrome";v="106", "Not;A=Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
```

  - 响应报文格式如下：
    响应首行HTTP/1.1 200 OK
    
    - 200响应状态码
    - OK表示对响应状态码的描述
    - 响应状态码的规则
      - 1xx 请求处理中
      - 2xx 请求成功
      - 3xx 请求重定向
      - 4xx 客户端错误
      - 5xx 服务器错误
      响应头
      响应头也是一个一个的名值对结构，用来告诉浏览器响应的信息
      - Content-Type 用来描述响应体的类型
      - Content-Length 用来描述响应体的大小
      空行
      用来分割响应头和响应体
      响应体
      - 响应体就是服务器返回给客户端的内容
     ```响应体
     <!DOCTYPE html>
                    <html lang="zh">
                        <head>
                            <meta charset="UTF-8" />
                            <meta http-equiv="X-UA-Compatible" content="IE=edge" />
                            <meta name="viewport" content="width=device-width, initial-scale=1.0" />
                            <title>Document</title>
                        </head>
                        <body>
                            <form method="post" action="./02_target.html">
                                <input type="text" name="username" />
                                <input type="password" name="password" />
                                <button>提交</button>
                            </form>
                    </body>
                    </html>```
     - 响应报文：
    
      ```HTTP/1.1 200 OK
                Vary: Origin
                Access-Control-Allow-Credentials: true
                Accept-Ranges: bytes
                Cache-Control: public, max-age=0
                Last-Modified: Thu, 27 Oct 2022 11:31:54 GMT
                ETag: W/"20c-18419368696"
                Content-Type: text/html; charset=UTF-8
                Content-Length: 2017
                Date: Thu, 27 Oct 2022 11:52:29 GMT
                Connection: keep-alive
                Keep-Alive: timeout=5
```
