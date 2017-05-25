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

## 消息响应类型
不需要响应的消息，发起之后无需等待响应者回应，继续发后续的消息
```objective-c
    A:你好，我是Neo                  //不需要响应的消息
    A:你今年多大了?
```
数字类型响应
```objective-c                  
    A:你今年多大了?                  //数字类型响应的消息
    B:18
```
标准响应，接收所有文字输入
```objective-c                  
    A:能给我点建议吗?                  //标准响应
    B:我觉得你很6
```
选择题响应
```objective-c                  
    A:你喜欢下面哪位诗人?                  //选择题响应,响应者可以点击选项，或者直接输入选项中的答案
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


## 展望

- iOS 6 or later.

## License

This code is distributed under the MIT license. See the `LICENSE` file for more info.
