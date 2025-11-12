# TortoiseSVN
## TortoiseSVN 是一个 Windows 下的图形化 SVN 客户端，集成在资源管理器右键菜单中，用于与 SVN（Subversion）版本控制系统交互。
### 作用：
1.管理代码/文档的历史版本

2.多人协作开发

3.回滚错误修改

4.查看谁改了哪一行（SVN 是集中式版本控制（和 Git 不同，有一个中央服务器））

### 1.Checkout----第一次从服务器下载代码（相当于克隆项目到本地）
### 2.Update-----同步别人的新代码（获取最新的版本）
### 3.Commit -----把自己的修改上传到服务器（修改完代码，去上传）
### 4.Add ---添加文件（新建了一个xxx,svn默认不跟随它）
#### 具体操作：
1.右键 config.json → TortoiseSVN → Add...

2.勾选 → OK

3.此时文件变成 红色加号（待提交）

4.下次 Commit 时就会上传
### 5.Delete----删除，右键删除，文件变红（标记为删除），再次commit后，服务器也会删除。
### 6.查看日志 （Show Log）---右键showlog(就能看见所有的提交记录，***可双击某次提交，查看具体修改内容（Diff）)
### 7.Conflict(解决冲突)
#### 具体例子：
1.当你和同事同时修改了同一个文件的同一行，Update 时会出现冲突

2.现象：文件名变红色感叹号，出现 .mine、.rOLDREV、.rNEWREV 等临时文件

3.解决方法：
  1.右键冲突文件 → Edit Conflicts

  2.使用内置工具选择保留哪部分（或手动编辑）

  3.解决后 → Mark as resolved

  4.Commit 最终版本
### 图标含义速查：
<img width="511" height="385" alt="image" src="https://github.com/user-attachments/assets/e1542d99-b4bc-4f31-b82a-0620c58156e2" />
<img width="884" height="229" alt="image" src="https://github.com/user-attachments/assets/ce649711-e387-4298-9b4f-cd0fabd3fc43" />
<img width="817" height="482" alt="image" src="https://github.com/user-attachments/assets/b0627d44-8fa8-452a-950c-e68bf11251d0" />



  
