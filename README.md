# TPLINK
# TPLINK reboot script

# -*- coding: gbk -*-
import sys
import time
import telnetlib

HOST = "192.168.1.1"#路由IP
Port = "23"#路由端口
username = "admin_BY"#路由用户名
password1 = "gz_baoyugame"#路由密码
enable = "enable"#高级模式进入命令
password2 = "admin"#高级模式进入密码
cmd=b"sys reboot"#路由重起命令
test=b"sys show"
#cmd1=b"exit"
 
tn = telnetlib.Telnet(HOST,Port)#telnet连接主机
tn.set_debuglevel(2);#设置调试等级为2
 
time.sleep(2)#停2秒
tn.read_until(b"Username:")#当读取到Username:时
time.sleep(2)#停2秒
tn.write(username+"\rn")#写入用户名,并回车
time.sleep(2)#停2秒

tn.read_until(b"Password:")#当读取到Password:时
tn.write(password1+"\n")#写入密码并回车
time.sleep(1)#停1秒
tn.write(enable+"\n")#进入高级使用enable
time.sleep(2)#停1秒
tn.write(password2+"\n")#输入密码
#tn.write(cmd+"\n")#执行路由重起命令
#tn.write(cmd1)

#print(tn.read_all())
