+++
date = '2025-08-14T01:17:13+08:00'
draft = false
title = 'vscode 常用配置、插件及使用方法'
tags = ["vscode"]
categories = ["工具"]

image = "https://images.alphacoders.com/135/thumb-1920-1357998.jpeg"
+++

## 常用配置

### 1. 所有东西全部放大/缩小一个级别
- 在设置中搜索level：
Window: Zoom Level
> 调整所有窗口的默认缩放级别。大于“0”的每个增量（例如“1”）或小于“0”的每个增量（例如“-1”）表示放大或缩小“20%”。还可以输入小数以使用更细的粒度调整缩放级别。请参阅 Window: Zoom Per Window，了解将“放大”和“缩小”命令配置为将缩放级别应用于所有窗口还是仅应用于活动窗口。

### 2. python launch.json常用配置：
```
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Python: 你想用的环境名1",
            "type": "python",
            "request": "launch",
            "program": "${file}",
            "console": "integratedTerminal",
            "justMyCode": true,
             //环境名对应的python路径
            "python": "/home/你的用户名/anaconda3/bin/python"
        },
        {
            "name": "Python: 你想用的环境名2",
            "type": "python",
            "request": "launch",
            "program": "${file}",
            "console": "integratedTerminal",
            "justMyCode": true,
            "python": "/home/你的用户名/anaconda3/envs/verse/bin/python" 
        }
    ]
}

```

## 插件们

### 1. Project Manager

### 2. background

### 3. directory-tree
根据项目目录自动生成文档树  
> - 自动过滤 .gitignore 文件中的目录和 .git 目录
> - 自动将目录树插入到 READEME.md 文件底部
使用说明：  
1. 快捷键 shift+ctrl+p，调出用于执行命令的输入框
2. 在输入框内输入 Directory Tree并确认
