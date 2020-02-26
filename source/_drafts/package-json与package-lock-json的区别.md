---
title: package.json与package-lock.json的区别
tags:
---

## 简单介绍

* package-lock.json 是项目依赖的快照，如果package.json更新，则会更新package-lock.json

* 当项目有package-lock.json，无需重新构建生成依赖树（疑问）

* package-lock.json确保团队协作间安装完全相同的依赖关系（前提是只要package.json不改动，就可以保证团队成员安装一致的依赖项。）因为存在package.json依赖版本为^1.0.0时，实际安装1.8.0，如果该依赖更新到了1.9.0，新成员在无package-lock.json下，会安装到最新的版本。

* 允许npm跳过以前安装的软件包的重复元数据解析，从而优化安装过程


