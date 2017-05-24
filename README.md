# Faceless 无面

一键创建人工智能助理

## 基本名词定义
一组会话，Conversation
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
- 结果展示型消息（分析结果展示，带Slider）

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

```objective-c

-(void)viewDidLoad{

    Person *person = [[Person alloc] init];
    person.name = @"King";
    person.likeCount = @1;

    NKKVOLabel *likeLabel = [[NKKVOLabel alloc] initWithFrame:CGRectMake(0, 100, 100, 100)];
    [self.view addSubview:likeLabel];
    
    likeLabel.target = self;
    likeLabel.renderMethod = @selector(stringWithNumber:);
    
    [likeLabel bindValueOfModel:person forKeyPath:@"likeCount"];
}
    
-(NSString*)stringWithNumber:(NSNumber*)number{
    
    if (!number) {
        number = @0;
    }
    NSString *finalString = [NSString stringWithFormat:@"%@", number];
    
    return finalString;
}

```

We can also set the label's frame in the renderMethod if we need.

The NKKVOLabel also provide a singleTapped action

```objective-c


    likeLabel.singleTapped = @selector(like:);
    
    
-(void)like:(id)sender{
    
    NSInteger count = [self.person.likeCount integerValue];
    count++;

    self.person.likeCount = [NSNumber numberWithInteger:count];
}
```

## Prerequisites

- iOS 6 or later.

## License

This code is distributed under the MIT license. See the `LICENSE` file for more info.
