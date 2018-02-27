## Gitbook 命令行安装与使用

#### 安装
* Gitbook命令行是NMP安装的，运行 cmd.exe
* 安装
```shell
> npm install gitbook-cli -g
> gitbook -V
```

#### 使用 serve 命令，输出为静态html
```shell
> cd F:a/b/c
> gitbook serve ./ 
# 打开 127.0.0.1:4000 在线查看
# 在书本目录下，已经生成 _book 目录，可本地打开
```

#### 使用 build 命令，输出到指定目录静态html
```shell
> gitbook build a/b/c a/b/c/_book
```
