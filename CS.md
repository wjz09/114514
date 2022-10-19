## CS服务器端部署位置：

cd /usr/CS/cobaltstrike4.3/cobaltstrike4.3

启动：

```bash
./teamserver 114.132.124.214 passwd
```

### screen使用（解决云服务器分shell问题）：

```powershell
screen  //创建新命令界面，并在此开启teamserver
ctrl +a+b //退出当前shell，进入主shell
screen -ls //查看分任务列表
screen -r 任务编号进入任务
exit 	//在分任务中执行，退出且关闭分任务一切进程
```

## 主机上线信息收集阶段(前置shell命令):

```powershell
ipconfig /all	#主机ip

systeminfo #操作系统版本 | 补丁列表

wmic product get name,version	#安装软件版本、路径

wmic service list brief	#服务信息查询

tasklist -v	wmic process list brief	#进程查询

wmic startup get command,caption	#启动项

net statistics workstation #开机时间
······································································
wmic脚本工具 wmic_info.rar 已上传
······································································



······································································

net user #用户信息

net localgroup administrators 	#获取本地管理员或用户信息

query user || qwinsta #查看当前在线用户 winserver还有，7，10无

net session # 本地与客户端会话

·······································································

netstat -ano #端口信息

net share #本机共享列表

route print #路由表

arp -a #arp缓存表

·······································································

netsh firewall show config #查看防火墙配置

#实现防火墙开启关闭 

//server2003 之后
netsh advfirewall set allprofiles state on 
//server2003 之前
netsh firewall set opmode disable #关闭
netsh firewall set opmode mode=enable #开启


·······································································

whoami #获取域SID

net user XXX /domain #指定用户详细信息

·······································································

#判断是否存在域：
ipconfig/all

nslookup 反差dns ip与域控是否一致

net config workstation # 检查当前登录域信息

#检查 当前用户是否为域用户

net time /domain
拒绝访问	不为域用户
返回time 	  存在且为域用户
找不到域控	不存在域  ································判断域是否存在

·······································································

#域内存活主机检测	工具在靶机win7桌面 上传git-tools （工具\Neiwang）
1.NetBIOS
nbtscan.exe 内网网段 #扫描内网网段 

2.arp-scan
arp-scan.exe -t 网段  不是很好用，建议结合netscan使用s

3.主机ping
for /L %I in (1,1,254) DO @ping -w 1 -n 1 192.168.52.%I | findstr "TTL="
来自 192.168.52.138 的回复: 字节=32 时间<1ms TTL=128
来自 192.168.52.143 的回复: 字节=32 时间<1ms TTL=128


#端口扫描
4.ScanLine (tcp、udp扫描)

sl.exe -h -t 22,80-89,110,445,139,389 -u 53,161 -o ./1.txt -p 192.168.244.1.1-254
-t tcp端口 -u udp 

5.CS上线端口扫描
```

## 域信息收集

域信息收集：

```shell
#查询域：
net view /domain

#域内所有计算机
net view /domain:GOD

#查询所有用户信息
wmic useraccount get /all

#存在用户信息：都是域管理工具，必须在windows server服务器上才有，
dsquery user

```





