---
layout: post
title: tornado 站点上传文件到七牛
categories: [开发, Python]
---

## 酸溜溜文绉绉

作为一个感情丰富的文艺程序员，面对自己越过的坑，回过头看根本不起眼，还是要吐个苦水。

最开始看七牛的文档的时候，是茫然的，完全看不出个条理。作为一个 web 领域的新手，在这方面的技术池还是挺浅的，但是也会内心疑问到底是这个文档写得不好还是自己太嫩。

后来在 v2 上看到有人表达了同样的感受，而更有意思的是，有人回复说：“这么难用为什么还有人用”，楼下有人回复说：“用过UPYUN之后你就知道为什么选择七牛了。”；）

## 中立的感受（严肃脸）

写了一个 demo 之后，发现也没有那么夸张。估计就是文档的条理不够清晰吧，不利于入门和阅读。而当实际领会过熟悉了之后就又发现没那么糟糕，还是挺稳固的。

## 回顾应用七牛

在这里做个总结回顾，遵从自己的内心愿望，养成总结的习惯，同时也给后面的学习者做参考，当然可能我写的笔记片面或者没什么价值。朝着实现这样的目标前进：做有用的总结！

你的 Access Key 和 Secret Key 是验证身份的标志，在七牛的个人中心里可以找到。

根据七牛的空间名、待上传文件的文件名、指定过期时间生成 token 。

代码示意如下：

~~~ python
# -*- coding: utf-8 -*-
# flake8: noqa

from qiniu import Auth, put_file, etag, urlsafe_base64_encode
import qiniu.config

#需要填写你的 Access Key 和 Secret Key
access_key = 'Access_Key'
secret_key = 'Secret_Key'

#构建鉴权对象
q = Auth(access_key, secret_key)

#要上传的空间
bucket_name = 'Bucket_Name'

#上传到七牛后保存的文件名
key = 'my-python-logo.png';

#生成上传 Token，可以指定过期时间等
token = q.upload_token(bucket_name, key, 3600)

#要上传文件的本地路径
localfile = './sync/bbb.jpg'

ret, info = put_file(token, key, localfile)
print(info)
assert ret['key'] == key
assert ret['hash'] == etag(localfile)
~~~
