---
title: "Window系统下JDK安装配置"
date: 2023-01-29
publishdate: 2023-01-04
draft: false
description : "在Windows操作系统中，通过非安装模式安装配置JDK。"
tags: ["Windows","JDK"]
categories: ["IT"]
menu: ""
---

#### 一. 安装

官网下载安装 ZIP 版本，解压到安装文件夹。

如 JDK17 下载地址： https://download.oracle.com/java/17/latest/jdk-17_windows-x64_bin.zip

#### 二. 配置

##### 1. 配置环境变量

通过 PowerShell（管理员）工具配置 JAVA_HOME、PATH 及 JAVA_TOOL_OPTIONS

```PowerShell
# 配置JAVA_HOME，假设JDK解压路径为 "D:\java\jdk-17.0.5"
$java_path = "D:\java\jdk-17.0.5"
[Environment]::SetEnvironmentVariable("JAVA_HOME", "$java_path", 'Machine')

# 配置PATH
$PATH = [Environment]::GetEnvironmentVariable("PATH")
if( $PATH -notlike "*"+$java_path+"*" ){
  [Environment]::SetEnvironmentVariable("PATH", "$PATH;$java_path\bin", 'Machine')
}

# 配置 JAVA_TOOL_OPTIONS （根据实际需求配置）
[Environment]::SetEnvironmentVariable("JAVA_TOOL_OPTIONS", "-Dfile.encoding=UTF-8", 'Machine')
```
