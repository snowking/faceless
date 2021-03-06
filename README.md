# Faceless 无面

一键创建人工智能助理

## 基本名词定义
会话，Conversation
```objective-c
    A:你好，我是Neo
    A:你今年多大了?
    B:18
    A:你真年轻
    B:谢谢
```
A是会话的发起者，B是会话的响应者，其中的每一条定义为消息，Message
```objective-c
    A:你好，我是Neo
```
```objective-c
    B:28                      
```
## 消息类型
- 纯文本
- 纯图片
- 图文
- 选择题（单选、多选）
- 带注释的消息
- 结果展示型消息（分析结果展示，带Slider，计算结果）
- 带跳转链接的消息

## 消息响应类型
不需要响应的消息，发起之后无需等待响应者回应，继续发后续的消息
```objective-c
    A:你好，我是Neo
    A:你今年多大了?
```
数字类型响应
```objective-c                  
    A:你今年多大了?                  
    B:18
```
标准响应，接收所有文字输入
```objective-c                  
    A:能给我点建议吗?
    B:我觉得你很6
```
选择题响应，响应者可以点击选项，或者直接输入选项中的答案
```objective-c                  
    A:你喜欢下面哪位诗人?
     -李白
     -杜甫
     -King
     
    B:King
    
    A:你喜欢下面哪些诗人?
     -李白
     -杜甫
     -King
     -子月
     确定
     
    B:King,子月
```
跳转链接响应，用户点击消息，跳转到对应的链接网页
```objective-c                  
    A:我这里有一套武林秘籍，点击查看
```
## 处理响应
基于数字范围处理响应
```objective-c                  
    A:你年收入多少?                 
    B:10w
    A:很有潜力
    
    A:你年收入多少?                 
    B:30w
    A:解决温饱
    
    A:你年收入多少?                 
    B:100w
    A:😄
    
    A:你年收入多少?                 
    B:1000w
    A:大腿拿过来
```
基于选项处理响应
```objective-c                  
    A:你的性别?
     -男
     -女
    B:男
    A:你好帅哥
    
    A:你的性别?
     -男
     -女
    B:女
    A:你好美女
```
基于上下文处理响应
```objective-c                  
    A:你说出两个数字，我能算出他们的和
    A:请说第一个
    B:100
    A:请说第二个
    B:50
    A:好的, 100+50=150
```
需要发送服务请求的响应处理
```objective-c
    //接收到手机号时，发送给对应的服务API
    A:我要验证一下你的手机，请告诉我手机号码
    B:18602195219                      
    A:给你手机发了验证码
    B:123456
    A:OK
```
响应的错误处理
```objective-c  
    //本地处理
    A:你年收入多少?
    B:我很开心
    A:我问的是收入
    
    //显示API返回的错误
    A:我要验证一下你的手机，请告诉我手机号码        
    B:18602195219
    A:这个手机已经注册了 
```
处理响应者发起的消息
```objective-c
    //查询对应的响应
    B:今天天气怎样
    A:天气晴朗
    
    B:我想上天
    A:我不支持
```

## 展望

- 支持更多消息类型（语音，视频）
- 支持更多消息响应类型
- 更聪明的处理响应
- 处理响应者发起的消息，增加词库和功能库

## License

This code is distributed under the MIT license. See the `LICENSE` file for more info.
