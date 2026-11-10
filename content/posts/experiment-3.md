---
title: "Shell脚本编程基础"
date: 2026-10-25
draft: false
categories: ["Shell脚本"]
tags: ["Shell", "脚本"]
---
## 一、 实验目的
1. 掌握 Shell 脚本的基本结构，包括 Shebang（#!）的声明。
2. 熟练使用变量、条件判断（if）和循环结构（for/while）。
3. 能够结合实际需求，编写自动化运维脚本。

## 二、 实验环境
* 操作系统：Ubuntu 22.04 LTS
* 脚本编辑器：Vim

## 三、 实验步骤与核心代码
**1. 编写系统信息收集脚本**
创建一个名为 `
sys_info.sh
` 的脚本，用于自动输出当前系统的时间、内存使用率和磁盘占用情况。
```bash
#!/bin/bash
# 这是一个系统信息查看脚本
echo "===================="
echo "当前系统时间: $(date)"
echo "内存使用情况:"
free -h | grep -i mem
echo "磁盘根目录占用:"
df -h /
echo "===================="
