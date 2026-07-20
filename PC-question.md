# 1.任务管理器相关解释

***I.***[任务管理器] <img width="2000" height="900" alt="image" src="https://github.com/user-attachments/assets/85fac575-a9a7-44f7-9f1b-7aab9377b339" />


# 任务管理器资源使用详解

## 🔹 11% CPU：计算机的“大脑”，负责执行各种计算任务。
- 含义：所有进程共用 CPU 的 11%
- 正常范围：< 50%
- 高风险：> 80% 可能卡顿
- 排查方法：点击 CPU 列排序，找耗 CPU 进程

## 🔹 79% 内存：内存（RAM）是临时存储空间，用于存放正在运行的程序和数据。
- 含义：已使用 79% 的物理内存
- 示例：16GB RAM 中已用约 12.6GB
- 建议：关闭不必要程序，防止内存不足
- 风险：接近 80% 时可能触发虚拟内存，变慢

## 🔹 3% 磁盘： 硬盘或 SSD 正在进行读写操作的繁忙程度。
- 含义：磁盘读写繁忙度为 3%
- 正常范围：< 50%
- 高负载表现：系统卡顿、硬盘响声
- 常见原因：系统更新、杀毒扫描、文件复制

## 🔹 0% 网络：当前所有应用程序通过网络发送或接收数据的速度占最大带宽的比例。
- 含义：当前无网络传输活动
- 单位：Mbps（兆比特每秒）
- 常见用途：下载、上传、在线视频
- 提示：若实际在上网却显示 0%，可能是刷新延迟

## ✅ 当前系统状态评估
- CPU：良好 ✅
- 内存：偏高 ⚠️（建议优化）
- 磁盘：正常 ✅
- 网络：空闲 ✅

# 2.电脑中有两个Windows系统，要删除一个，解决方法
<img width="712" height="2531" alt="image" src="https://github.com/user-attachments/assets/535ce553-7486-42bd-8cd0-09c910e24fd6" />

# 3.修复损坏U盘
## 3.1 win+r 输入 cmd,然后输入 chkdsk u盘的名字: /f /r

# 4.将u盘格式改为fat32
## 4.1 下载DiskGenius，网址为 url=https://www.diskgenius.cn/
## 4.2 在此页面上 
<img width="605" height="712" alt="image" src="https://github.com/user-attachments/assets/7c91c598-3079-41af-9caf-644222c4ba54" />

# 4.用命令行重命名文件（绕过资源管理器缓存）
以管理员身份打开命令提示符（cmd）或者powershell
执行
```cmd
ren "C:\完整路径\原文件名.txt" "新文件名.txt"
```
# 5.访问共享文件夹时提示出现了扩展错误
<img width="451" height="181" alt="image" src="https://github.com/user-attachments/assets/67aa0c21-4ad7-4e1f-b016-a1efd4bafb14" />
## 解决办法： 

# 一般在win11家庭中文版会出现这个问题（红米笔记本）

## 5.1首先是没有组策略，所以必须先安装组策略

## 5.2 然后在打开组策略进行配置

## 5.3组策略安装方法
### 1.先在桌面上新建一个txt文本文档，然后在里面加入
```p
@echo offpushd "%~dp0"dir /b C:\Windows\servicing\Packages\Microsoft-Windows-GroupPolicy-ClientExtensions-Package~3*.mum >List.txtdir /b C:\Windows\servicing\Packages\Microsoft-Windows-GroupPolicy-ClientTools-Package~3*.mum >>List.txtfor /f %%i in ('findstr /i . List.txt 2^>nul') do dism /online /norestart /add-package:"C:\Windows\servicing\Packages\%%i"pause
```
### 2.保存后将 .txt 改为 .cmd 并右键管理员身份运行，系统会自动安装组策略，安装完毕后重启生效。
### 3.接下来打开组策略，按照图示操作即可
<img width="879" height="874" alt="image" src="https://github.com/user-attachments/assets/e9f1e541-f80a-4a28-9b78-7780921d02d2" />

