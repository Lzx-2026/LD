---
title: "Linux文件管理实验"
date: 2026-10-20
draft: false
categories: ["文件管理"]
tags: ["文件管理", "命令行"]
---
## 一、 实验目的
1. 熟练掌握 Linux 文件系统中常用命令（ls, cd, mkdir, cp, mv, rm 等）的使用方法。
2. 深入理解 Linux 中绝对路径与相对路径的区别，以及文件的元数据查看方式。
3. 掌握软链接与硬链接的创建及底层原理差异。

## 二、 实验环境
* 操作系统：Ubuntu 22.04 LTS (虚拟机)
* 终端环境：Bash shell

## 三、 实验步骤与核心代码
**1. 目录操作与文件查看**
首先，在根目录下创建一个名为 `test_dir` 的实验文件夹，并进入该目录：
`mkdir -p ~/test_dir`
`cd ~/test_dir`
使用 `ls` 命令结合参数查看详细属性（包括隐藏文件）：
`ls -alh`
*（注：`-a` 显示隐藏文件，`-l` 以长格式显示详细信息，`-h` 以人类可读格式显示文件大小）*

**2. 文件创建与复制移动**
创建两个空白文本文件并写入内容：
`touch file1.txt file2.txt`
`echo "Hello Linux" > file1.txt`
将 file1.txt 复制并重命名为 file1_backup.txt：
`cp file1.txt file1_backup.txt`
将 file2.txt 移动到同级目录下的 backup 文件夹中：
`mkdir backup`
`mv file2.txt backup/`

**3. 软链接与硬链接的测试**
创建一个硬链接和一个软链接指向 file1.txt：
`ln file1.txt hard_link.txt`
`ln -s file1.txt soft_link.txt`
通过 `ls -li` 观察 inode 号发现，硬链接与原文件共享同一个 inode，而软链接拥有独立的 inode。

## 四、 实验心得
通过本次实验，我不仅熟练掌握了文件管理的基础命令，还深刻理解了 Linux 系统“一切皆文件”的设计哲学。特别是通过观察 inode 号码，让我明白了硬链接就像是文件的另一个名字，而软链接更像是一个快捷方式。操作过程中也遇到了权限不足的报错，通过使用 `sudo` 成功解决，提升了排错能力。
