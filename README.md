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
- 结果展示型消息（分析结果展示）
```

If the value is not NSSting, such as NSNumber or some other type, or we want to do some additional things when a new value is set, we can tell the label a renderMethod to tell the label the string we need.

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
