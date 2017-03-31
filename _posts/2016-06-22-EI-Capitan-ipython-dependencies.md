---
layout: post
title: Mac OS X EI Capitan 下 pip 的一个包依赖问题
categories: [io]
---

## 安装 ipython 时发现错误

最近换了新的 10.11 系统，配置一些工具时遇到了小问题。安装 ipython 时，有个依赖的包已经被预装导致无法顺利安装。

错误原因是一个名为 six 的组件已经有低版本了，而 ipython 需要更高的版本：

~~~bash
:~ jwoops$ sudo -H pip install ipython
Password:
Exception:
Traceback (most recent call last):
  File "/Library/Python/2.7/site-packages/pip-8.1.2-py2.7.egg/pip/basecommand.py", line 215, in main
    status = self.run(options, args)
  File "/Library/Python/2.7/site-packages/pip-8.1.2-py2.7.egg/pip/commands/install.py", line 299, in run
    requirement_set.prepare_files(finder)
  File "/Library/Python/2.7/site-packages/pip-8.1.2-py2.7.egg/pip/req/req_set.py", line 370, in prepare_files
    ignore_dependencies=self.ignore_dependencies))
  File "/Library/Python/2.7/site-packages/pip-8.1.2-py2.7.egg/pip/req/req_set.py", line 458, in _prepare_file
    req_to_install, finder)
  File "/Library/Python/2.7/site-packages/pip-8.1.2-py2.7.egg/pip/req/req_set.py", line 397, in _check_skip_installed
    req_to_install.check_if_exists()
  File "/Library/Python/2.7/site-packages/pip-8.1.2-py2.7.egg/pip/req/req_install.py", line 1004, in check_if_exists
    self.req.name
  File "/Library/Python/2.7/site-packages/pip-8.1.2-py2.7.egg/pip/_vendor/pkg_resources/__init__.py", line 535, in get_distribution
    dist = get_provider(dist)
  File "/Library/Python/2.7/site-packages/pip-8.1.2-py2.7.egg/pip/_vendor/pkg_resources/__init__.py", line 415, in get_provider
    return working_set.find(moduleOrReq) or require(str(moduleOrReq))[0]
  File "/Library/Python/2.7/site-packages/pip-8.1.2-py2.7.egg/pip/_vendor/pkg_resources/__init__.py", line 943, in require
    needed = self.resolve(parse_requirements(requirements))
  File "/Library/Python/2.7/site-packages/pip-8.1.2-py2.7.egg/pip/_vendor/pkg_resources/__init__.py", line 834, in resolve
    raise VersionConflict(dist, req).with_context(dependent_req)
ContextualVersionConflict: (six 1.4.1 (/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python), Requirement.parse('six>=1.9.0'), set(['prompt-toolkit']))

~~~

## Github 上的一个 issue

在 Stackoverflow 上查找一番后没有发现准确的原因，之后在 Github 的一个讨论里看到了相同的情形：

[Six issue when installing package #3165](https://github.com/pypa/pip/issues/3165)

在这之前我完全不知道是系统变更的问题，而是以为 easy_install 和 pip 相关的原因。

## 加入 --ignore 参数

使用如下命令顺利安装：

~~~bash
$ sudo -H pip install ipython --ignore-installed six
~~~

并且，所需的依赖 six 也会被自动更新。

希望自己和大家都少被这种客观问题所困扰。
