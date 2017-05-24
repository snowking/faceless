# Faceless 无面

一键创建人工智能聊天助理

## Usage

Basic usage

```objective-c

    Person *person = [[Person alloc] init];
    person.name = @"King";
    
    NKKVOLabel *label = [[NKKVOLabel alloc] initWithFrame:CGRectMake(0, 0, 100, 100)];
    [self.view addSubview:label];
    
    [label bindValueOfModel:person forKeyPath:@"name"];

```
When we edit the name, just set the person's name, and the label will display the new name automatically.

```objective-c

    person.name = @"Another King";

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
