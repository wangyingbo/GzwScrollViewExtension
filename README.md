GzwTableViewLoading  
===================================  
   这是我用脚写出来的运行时框架，这是一个UIScrollView的分类，一行代码解决加载状态和没有数据下的状态，UIScrollView + UITableView + UICollectionView均可使用
  
    
样式支持全自定义  
-----------------------------------  
  ![enter image description here](http://qpic.cn/b2YFTe1FP) 
    
### 导入框架  
  把工程内的 GzwTableViewLoading 文件夹拖入自己的工程
  
  引用 #import "GzwTableViewLoading.h"
  
  现已加入CocoaPods豪华午餐:pod 'GzwTableViewLoading', '~> 1.1.0'
   
          
### 使用    
    // 在请求数据前
    self.tableView.loading = YES;
  
### 用法示例(详情看demo)
    // 只需一行代码，我来解放你的代码
    self.tableView.loading = YES;
    
    // 模拟延迟
    dispatch_after(dispatch_time(DISPATCH_TIME_NOW, (int64_t)(2 * NSEC_PER_SEC)), dispatch_get_main_queue(), ^{
        if (data) {
            for (int i = 0; i < 10; i++) {
                [self.data addObject:[NSString stringWithFormat:@"I'm data，fuck！"]];
            }
        }else {// 无数据时
            self.tableView.loading = NO;
        }
        [self.tableView reloadData];
    });
    
### 配置参数(自定义)    
    self.tableView.buttonText = @"再次请求";
    self.tableView.buttonNormalColor = [UIColor redColor];
    self.tableView.buttonHighlightColor = [UIColor yellowColor];
    self.tableView.loadedImageName = @"58x58";
    self.tableView.descriptionText = @"破网络，你还是再请求一次吧";
    self.tableView.dataVerticalOffset = 200;  
### 框架的故事：
当我把项目完成了，产品经理说要改掉所有页面的加载样式，这时候我是崩溃的，于是去找第三方库，找到了[一个可用的库](https://github.com/dzenbot/DZNEmptyDataSet)<br />  但需要对每个UITableVIew操作，(用继承？滚一边反省去), 
这都导致了强耦合，于是我用运行时，不对，我用脚封装了这个库，一行代码就搞定了，真正的低耦合

  
  
### 关于我  
> QQ 351941406 有问题，你们是加不了的。 
>  
> QQ群：180972893  可以加
>  
> 希望你们在使用框架的过程中联系我，提供更多宝贵的意见，一起把框架维护好。  
 
  
