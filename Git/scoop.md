# scoop安装
### 定义：
1. 开源、轻量、无需管理员权限（默认安装到用户目录）
2. 专注于开发者工具和命令行程序
3. 安装简单，更新方便：scoop update
4. 支持多“桶”（buckets),如主仓库、extras、nerd-fonts等

### 前提条件：
1.[windows7或更高版本]

2.[PowerShell5.1或更高版本]

3.[网络连接正常（因为可能需要代理访问GitHub）]
### 执行策略：
1.以**普通用户身份**打开PowerShell(不需要管理员权限)，然后运行
```POWERSHELL
Set-ExecutionPolicy -Scope CurrentUser RemoteSigned -Force
```
***这一步是为了允许POWERSHELL执行本地脚本***

2.下载并安装Scoop,在POWERSHELL中运行
```powershell
iwr -useb get.scoop.sh | iex
```
安装成功后，会看到类似提示：
```TEXT
Scoop was installed successfully!
```
## 常见问题解决：
**1.安装失败/下载慢？**
解决方法：使用国内镜像源（通过配置修改scoop配置）
```powershell
scoop config SCOOP_REPO https://gitclone.com/github.com/ScoopInstaller/Scoop
scoop config SCOOP_BRANCH master
```
## 安装 Git
```powershell
scoop install git
```
**2.命令找不到**
解决方法：确保scoop的shims目录已加入系统path,如果没有自动添加，重启终端或手动刷新环境变量。
```text
C:\Users\<你的用户名>\scoop\shims
```
### 手动刷新环境变量
1.在powershell中手动刷新加载环境变量
运行以下命令：
```powershell
# 重新加载环境变量
$env:Path = [System.Environment]::GetEnvironmentVariable("Path","Machine") + ";" + [System.Environment]::GetEnvironmentVariable("Path","User")
```
这个命令会1.读取系统的path变量（machine）2.读取用户的path变量（user）3.合并并重新赋值给当前会话的$env:path
2.通过windows图形界面修改并出发刷新
```text
1.打开系统属性：
win + r ->输入 sysdm.cpl ->回车
2.切换到“高级”选项卡
3.点击“环境变量”按钮
4.点击任意变量（如Path),点“编辑”——>不做修改——>点“确定”
5.一路“确定”退出
```
**这个操作会触发系统广播环境变量变更消息，部分程序会收到并更新**
## 最后如果想卸载scoop
直接删除~\scoop文件夹即可，不会影响系统其他部分。
