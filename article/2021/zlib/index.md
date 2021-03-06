# Ubuntu安装 Zlib



>如果你尝试在 Ubuntu 上安装 zlib，它会抛出 “unable to locate package zlib” 错误。

Zlib 是一个用于数据压缩的开源库。

作为使用者，你可能会遇到需要安装 zlib（或 zlib-devel 包）作为另一个应用程序的依赖项的情况。

但问题来了，如果你尝试在 Ubuntu 上安装 zlib，它会抛出 “unable to locate package zlib” 错误。
```bash
    sudo apt install zlib
    Reading package lists... Done
    Building dependency tree
    Reading state information... Done
    E: Unable to locate package zlib
```
为什么会看到这个 Ubable to locate package 错误呢？因为没有名为 zlib 的包。

如果你 使用 apt search 命令，你会发现有几个包可以让你安装：zlib 1g 和 zlib 1g-dev。当你知道这些后，只需一个 apt 命令就可以安装它们。

##  在基于 Ubuntu 的 Linux 发行版上安装 Zlib

打开终端，使用以下命令：
```bash
    sudo apt install zlib1g
```
请记住 g 前面的字母是数字 1，而不是小写的字母 L。很多人在输入命令时都会犯这个错误。

另一个包，zlib 1g-dev 是开发包。只有在你需要时才安装它，否则你应该使用 zlib 1g 包。
```bash
    sudo apt install zlib1g-dev
```
你也可以 Zlib 网站 下载源代码并安装它。但是，除非你有充分的理由，否则我不推荐使用源代码方式来安装 zlib。例如，如果你需要最新或特定版本的 zlib，但该版本在发行版的仓库中不可用。

有趣的是，像安装 zlib 这样看似很小的东西可能会变得很麻烦，有两个原因：一个是不同的包名；另一个是包含“隐藏”数字 1，它与小写 L 混淆了。


##  参考
Zlib [[1]](https://zlib.net/)
