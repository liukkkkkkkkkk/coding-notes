# hosts文件
## 作用
### 在本机“手动配置 域名<->ip 的映射”，让系统在访问某个域名时优先用你指定的ip,而不是去问DNS;常用于本地开发、测试、调试，以及屏蔽/重定向某些域名。
#### 一句话理解：1.DNS是公网的“电话簿”：问DNS，得到某个域名的IP  2.hosts是本机的“小电话薄”：先查本机的hosts；若hosts里有记录，就直接用它，不会再问DNS
#### 执行顺序：当本机要访问一个域名时，很多系统会按类似顺序去解析：1.优先看本机hosts文件2.若hosts没有匹配，再去查系统配置的DNS服务器（不同系统略有差别，但大多数hosts优先于DNS）
#### 文件位置：C:\Windows\System32\drivers\etc\hosts
### 简单语法示例：
```text
# IP地址       主机名
127.0.0.1      localhost
::1            localhost

# 把 example.com 指向内网测试机
192.168.1.100  example.com

### 如需屏蔽网站
  127.0.0.1  ads.example.com
  0.0.0.0    tracking.example.com
  

```
## Hosts 屏蔽
### 网站的原理并不是把网站关了，而是利用了“hosts 优先级高于 DNS”的规则，故意给浏览器指错路，让浏览器去一个不存在的地方（你自己电脑的某个死角），从而因为找不到服务而放弃加载。
<img width="959" height="308" alt="image" src="https://github.com/user-attachments/assets/3a388e29-cecb-47d0-8f9f-399fa2d50abe" />
<img width="947" height="392" alt="image" src="https://github.com/user-attachments/assets/8b3b0c86-c166-448c-9e93-614a38e2f712" />


<img width="950" height="311" alt="image" src="https://github.com/user-attachments/assets/3fd47349-d5d4-4c7c-af2f-49fe8fcfadc7" />

