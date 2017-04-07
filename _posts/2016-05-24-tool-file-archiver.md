---
layout: post
title: tar zip 等压缩工具的使用手册
categories: [开发]
---

## 对 tar 的认识

最开始接触 tar 是在 Linux 下，发现 Linux 情景下的文件、软件大多都是gz.tar结尾的。

只知道它有别于 windows 下的那些图形化压缩软件，以及基本用法。

写一篇博客当作使用手册，方便以后查阅，也可以记录自己的使用情景，供大家参考。

## 格式

tar代表未被压缩的tar文件。已被压缩的tar文件则追加压缩文件的扩展名，如经过gzip压缩后的tar文件，扩展名为“.tar.gz”。

## 命令写法

~~~bash
tar 功能 选项 文件
~~~


## tar 的基本参数

功能
-c，--create 创建新的tar文件
-x，--extract，--get 解开tar文件
-t，--list 列出tar文件中包含的文件的信息
-r，--append 附加新的文件到tar文件中
-u，--update 用已打包的文件的较新版本更新tar文件
-A，--catenate，--concatenate 将tar文件作为一个整体追加到另一个tar文件中
-d，--diff，--compare 将文件系统里的文件和tar文件里的文件进行比较
--delete 删除tar文件里的文件。注意，这个功能不能用于已保存在磁带上的tar文件！

常用选项
-v，--verbose 列出每一步处理涉及的文件的信息，只用一个“v”时，仅列出文件名，使用两个“v”时，列出权限、所有者、大小、时间、文件名等信息。
-k，--keep-old-files 不覆盖文件系统上已有的文件
-f，--file [主机名:]文件名 指定要处理的文件名。可以用“-”代表标准输出或标准输入。
-P，--absolute-names 使用绝对路径
-j，--bzip2 调用bzip2执行压缩或解压缩。注意，由于部分老版本的tar使用-I实现本功能，因此，编写脚本时，最好使用--bzip2。
-J，--xz，--lzma 调用XZ Utils执行压缩或解压缩。依赖XZ Utils。
-z，--gzip，--gunzip，--ungzip 调用gzip执行压缩或解压缩
-Z，--compress，--uncompress 调用compress执行压缩或解压缩

## 实例

下载了一个 .tar.gz 的文件：

~~~bash
tar -zxvf lalala.tar.gz
~~~

解压过程中会输出当前正在处理的文件信息。

用这个参数也能解压：

~~~bash
tar -xf lalala.tar.gz
~~~

用这个命令解压不会出现当前正在处理的文件信息，但是奇怪的是没有加上z参数居然也可以解压gz。

# 另一个实例 unzip

在 Ubuntu 下下载了一个 .zip 文件，用 tar 命令去解压发现没有反应。

查了资料后，尝试用 unzip 解压，可以解压。
