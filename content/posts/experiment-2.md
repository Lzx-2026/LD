---
title: "Linux用户与权限管理"
date: 2026-10-22
draft: false
categories: ["权限管理"]
tags: ["权限", "用户"]
---
## 一、 实验目的
1. 掌握 Linux 系统中用户和用户组的新增、删除与修改命令。
2. 深入理解 `rwx`（读、写、执行）权限模型及数字表示法（如 755、644）。
3. 掌握文件所有者（Owner）和所属组（Group）的变更方法。

## 二、 实验环境
* 操作系统：Ubuntu 22.04 LTS
* 所需权限：root 权限

## 三、 实验步骤与核心代码
**1. 用户与用户组管理**
创建一个新的用户组 `dev_team`：
`sudo groupadd dev_team`
创建一个新用户 `zhangsan` 并指定其主目录和所属组：
`sudo useradd -m -g dev_team zhangsan`
为用户设置密码：
`sudo passwd zhangsan`

**2. 文件权限修改（chmod）**
创建一个测试脚本，默认权限为 `rw-rw-r--` (664)：
`echo "echo 'Hello'" > 
test.sh
`
我们希望将该脚本变为可执行文件，并为所有者赋予全部权限，同组用户赋予读和执行权限，其他用户无权限（即 750）：
`chmod 750 
test.sh
`
查看修改结果：
`ls -l 
test.sh
`
结果显示为：`-rwxr-x--- 1 zhangsan dev_team ... 
test.sh
`

**3. 文件归属修改（chown）**
将 
test.sh
 的所有者更改为 root，所属组更改为 root：
`sudo chown root:root 
test.sh
`
此时再尝试以普通用户身份编辑该文件，系统会提示 `Permission denied`，证明了权限管控生效。

## 四、 实验心得
本次实验让我对 Linux 的安全机制有了直观的认识。以前对文件权限总是模棱两可，现在能熟练使用 `chmod` 和 `chown` 控制访问。实验中我也明白了，为了系统安全，日常开发应遵循“最小权限原则”，避免直接使用 root 用户进行所有操作。
