---
layout:     post
title:      Clang Static Analyzer：源代码分析（C/C++/Objective-C）
date:       2021-1-18
author:     huangbaoLiu
header-img: img/post-bg-desk.jpg
catalog: true
tags:
    - Tool skills
---
## 1、Clang Static Analyzer介绍

> Clang Static Analyzer是一个源代码分析工具，可以找出C、C++和Objective-C程序中的错误。目前可以作为独立的工具运行，也可以在开发工具中运行。如果是独立的工具，在命令行调用，使它和一些基本代码库串联运行。
> Clang Static Analyzer的目标是为分析C、C++和Objective-C程序提供一个工业品质静态分析框架，它可以免费获取、可扩展，并且高质量完成。
> 正如其名称所示，Clang Static Analyzer在Clang和LLVM顶层生成。严格来说，这个分析器是Clang的一部分，因为Clang包含一套可重复使用的C++库，用来生成强大的源码级工具。Clang
> Static Analyzer使用的这个静态分析引擎是一个Clang库，可以在不同的环境和客户端中被重复使用。
> 静态分析器是不完美的。它可能在代码正确的程序中错误的检测出漏洞。因为一些代码检测比另一些需要更精确的分析，所以误检率在不同的检测中变化很大。

------
# 2、linux如何采用Clang Static Analyzer开展静态分析
## 1)	首先下载android ndk包，并解压

> ​    本人linux下采用了android开发人员提供的android-ndk-r12b-linux-x86_64.zip，解压到/opt目录下，得到了android-ndk-r12b
>

## 2)	静态分析只关心两个文件

> Scan-build：scan-build是运行分析器的高级命令行工具。 Scan-view:
> scan-view是与scan-build相伴的命令行工具，用来查看scan-build产生的分析结果。有一个选项是可以传给scan-build一个命令使scan-view在分析完成时立刻运行。
> 根据前面的解压路径，可以在：/opt/android-ndk-r12b/toolchains/llvm/prebuilt/linux-x86_64/tools/scan-build/bin/scan-build找到scan-build脚本工具
> Scan-build工具，依赖clang编译器命令，默认会从scan-build脚本的当前的目录进行查找，但clang位于与tools平级的bin目录下，因此需要在scan-build所在的目录建立以下软连接：

    [root@localhost bin]# ln –s ../../../bin/clang clang

## 3)	scan-build进行代码分析

> Scan-build命令可以用于分析整个项目，本质上是介入项目的编译过程。这意味着使用scan-build运行分析器，你将使用scan-build分析在项目编译期间由gcc/clang编译的源文件。这也意味着任何没有编译的文件将不会被分析。
> Scan-build的基本用法被设计的很简单：只是将字符“scan-build”放在编译命令前面：

    [root@localhost tid_aid]# scan-build make
    [root@localhost tid_aid]# scan-build xcodebuild

> 第一个命令scan-build分析make编译的项目代码；第二个命令是scan-build分析使用xcodebuild编译的项目。
> 这里是一个调用scan-build的通用格式 [root@localhost tid_aid]# scan-build
> [scan-build options] <command> [command options]
> 在操作上，scan-build确实运行<command>
> 和所有在其之后传给它的选项。例如，一个命令可以是传给make命令-j4，实现超过4核的并行编译。 [root@localhost
> tid_aid]# scan-build make -j4
> Windows用户必须安装脚本才能使用scan-build。Scan-build.bat脚本允许用户启动scan-build，方式和上面介绍的基本用法相同。为了在任意位置调用scan-build，只需添加包含scan-build.bat的文件夹路径至环境变量即可。

------
# 3、静态分析结果分析

## 1)	采用以下命令进行静态分析

    [root@localhost tid_aid]# /opt/android-ndk-r12b/toolchains/llvm/prebuilt/linux-x86_64/tools/scan-build/bin/scan-build -o alyout make all

## 2)	静态分析结果保存在alyout文件夹下

![layout](https://huangbaoliu.github.io/img/blog_img/layout.png)

## 3)	查看静态分析结果，修改bug

> 双击index.html，即可查看本次静态分析的结果：
>

![analysis](https://huangbaoliu.github.io/img/blog_img/analysis.png)

> 点击相应的View Report，即可查看相应的潜在bug。点击第5个View Report，可以看到以下结果：
> ![Bug_analysis](https://huangbaoliu.github.io/img/blog_img/bug_analysis.png)
> 通过静态分析，可以确定潜在bug，查看源码确定，是否需要修改；如果修改，怎么修改；最终达到改进代码质量的目的。

# 4、总结

- Clang Static Analyzer进行静态分析的环境搭建、使用简单；
- 静态分析的结果，可以快速确定潜在的bug,以及bug发生的步骤，方便改进代码质量。
- 建议C、C++和Objective-C开发人员，所有的代码，都采用该工具进行静态分析，避免人为失误，改进代码质量。





