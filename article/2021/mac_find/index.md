# MAC命令快速模糊查找文件



### find命令

描述：通过 find命令查找
语法：find ~ -iname “文件名*”
```bash
/**
* 比如我要查找一个以‘vue-’开头的.zip文件,
* 但是你忘了它的全名也忘了在那个文件夹，
* 查找范围是‘～’节点以内
* 就可以用这种方式进行模糊搜索
*/

 find ~ -iname "vue-*.zip"

/**
* 然后它就把所有包含符合条件的文件和路径都打印出来了
*/
```

find不但能查找文件，还能查找文件夹
```bash
/**
* 比如我要查找所有包含‘vue’的文件或文件夹
*/
find ~ -iname "*vue*"

/**
* 结果它找到了所有包含‘vue’的文件或文件夹
*/
```

find方式很简单但是需要一点专业知识，需要知道一些正则的基本常识，需要指定路径范围，搜索的名字需要加引号等等

### mdfind命令

描述：通过 mdfind命令查找
语法：mdfind -name 文件名
```bash
/**
* 比如我要查找所有包含‘vue’的文件或文件夹
*/
mdfind -name vue

/**
* 看，我直接输入我要找的关键字‘vue’
* 就把所有文件和文件夹都输出出来了，是不是很方便
*/
```

mdfind 简单粗暴，没缺点，但有个前提是你mac电脑要支持Spotlight功能，不过也不用担心，一般mac默认是支持的

### 在 shell 中执行命令

>你是找到这个文件或文件夹了，但是你想直接打开它，那么怎么打开呢，看下面

若要运行当前用户个人文件夹中的命令，请在前面加上文件夹说明符。例如，若要运行 MyCommandLineProg，请使用以下命令：

```bash
% ~/MyCommandLineProg
```

若要打开一个 App，请使用打开命令：
```bash
% open -a MyProg.app
```

### 终止命令
*   在 Mac 上的“终端” App 中，点按正在运行您想要终止的命令的“终端”窗口。

*    按下 Control-C 键。

*    这会发出一个让大多数命令终止的信号。


### 参考
在 Mac 上的“终端”中执行命令和运行工具 [[1]](https://support.apple.com/zh-cn/guide/terminal/apdb66b5242-0d18-49fc-9c47-a2498b7c91d5/mac)

MAC命令快速全局查找文件或文件夹，支持模糊搜索 [[2]](https://blog.csdn.net/weixin_34403976/article/details/88844651)
