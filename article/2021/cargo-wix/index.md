# Cargo Wix 创建Windows安装程序的cargo子命令



cargo-wix：创建Windows安装程序的cargo子命令
它使用二进制项目的发行版中的构建Windows安装程序（msi）。 如果可以使用提供的应用程序提供代码签名证书，则它还支持对Windows安装程序进行签名。

### 快速开始
启动命令提示符（cmd.exe），然后执行以下命令：

```
C:\>cargo install cargo-wix
C:\>cd Path\To\Project
C:\Path\To\Project\>cargo wix init
C:\Path\To\Project\>cargo wix
```

该项目的Windows安装程序（msi）将位于C:\Path\To\Project\target\wix文件夹中。

### 官方文档
https://crates.io/crates/cargo-wix
