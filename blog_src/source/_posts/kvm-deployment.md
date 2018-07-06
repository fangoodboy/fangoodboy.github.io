---
title: kvm deployment
description: this article describe the procedure of config and deploy a kvm cluster.
tag:
    - devops, kvm
category:
    - devops
date: 2018-07-06 20:00:00 #文章生成時間
---

# 创建虚拟机

### 通用创建代码

```bash
virt-install --name leblock --ram 4096 --vcpu=4  --disk 
/data/qcow/leblock_1.qcow2,format=qcow2,size=40 --network bridge=br0 --os-type=linux --virt-type=kvm  --cdrom 
/data/ios/centos/CentOS-7-x86_64-Minimal-1708.iso  --vnc  --vncport=5901  --vnclisten=0.0.0.0
```

### 配置项

```--name``` 指定虚拟机的名称 
```--ram```  指定内存大小 
```--disk``` 指定磁盘 
```--size``` 指定虚拟机的磁盘大小 
```--vcpus``` 指定虚拟CPU 
```--os-type``` 指定GuestOS 的类型 
```--virt-type``` 指定GuestOS的类型 
```--network``` 指定虚拟机的网络类型 
```--vnc``` 指定图形的类型。
```--vncport``` 指定VNC端口 
```--vncclisten``` 指定vnc启动i

# virsh 命令

> 常用的虚拟机管理命令

- 列出所有的虚拟机
``` virsh list --all ```
- 显示虚拟机信息
``` virsh dominfo kvm-1 ```
- 示虚拟机内存和cpu的使用情况
``` 
yum install virt-top -y
virt-top
```