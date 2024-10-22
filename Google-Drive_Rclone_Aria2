# Google-Drive_Rclone_Aria2
GCP挂载Google Drive并通过aria2下载资源自动上传至网盘并删除本地文件

#进入ROOT用户
```
sudo -i
```

#设置ROOT密码
```
passwd
```
```
vim /etc/ssh/sshd_config
```
```
PermitRootLogin no   #修改为yes
```
```
PasswordAuthentication no   #修改为yes
```

#重启ssh服务使修改生效

```
/etc/init.d/ssh restart
```


#安装wget
```
apt-get install wget
```


#安装zip或unzip
```
apt-get install zip
```
```
apt-get install unzip
```


#安装fuse
```
apt-get update && apt-get install -y fuse
```


#windows下载rclone并放于根目录
```
https://rclone.org/downloads/
```


#Windos cmd 配置代理（clash默认端口）
```
set http_proxy=socks5://127.0.0.1:7890
``` 
``` 
set https_proxy=socks5://127.0.0.1:7890
```
```
export http_proxy=http://127.0.0.1:8888
```
```
export https_proxy=http://127.0.0.1:8888
```

#检查代理是否成功
```
curl -v google.com
```


#安装rclone
```
curl https://rclone.org/install.sh | sudo bash
```

#配置rclone

#新建google文件夹
```
mkdir /root/google
```

#挂载Google Drive
```
rclone mount google:/ /root/google --copy-links --allow-other --allow-non-empty --umask 000 --daemon
```

#下载并编辑自启脚本
```
wget -N git.io/rcloned && nano rcloned
```

#修改内容
```
NAME="Onedrive"   #Rclone配置时填写的name
REMOTE=''    #远程文件夹，网盘里的挂载的一个文件夹，留空为整个网盘
LOCAL='/Onedrive'   #挂载地址，VPS本地挂载目录
```

#设置开机自启
```
mv rcloned /etc/init.d/rcloned
```
```
chmod +x /etc/init.d/rcloned
```
```
update-rc.d -f rcloned defaults
```
```
bash /etc/init.d/rcloned start
```
#看到 rclone 启动成功 ! 即可

#管理命令

#开始挂载 
```
bash /etc/init.d/rcloned start
```
#停止挂载 
```
bash /etc/init.d/rcloned stop
```
#重新挂载 
```
bash /etc/init.d/rcloned restart
```
#查看日志 
```
tail -f /$HOME/.rclone/rcloned.log
```


#安装Aria2
```
wget -N git.io/aria2.sh && chmod +x aria2.sh && ./aria2.sh
```

#修改配置 __ VPS需开放aria2配置端口
```
./aria2.sh
```

#配置自动上传脚本
```
nano /root/.aria2c/aria2.conf
```
```
on-download-complete=/root/.aria2c/clean.sh   #clean.sh替换为upload.sh
```

#附加功能脚本配置文件修改
```
nano /root/.aria2c/script.conf
```
#drive-name修改为rclone挂载的名称

3重启aria2 __ 需关闭Aira2NG网页
```
service aria2 restart
```

检查配置是否成功
```
/root/.aria2c/upload.sh
```
出现success即为成功 __ 下载任意文件测试是否会自动下载并上传至网盘后删除本地文件

至此Aira2下载并自动上传至网盘后删除本地文件流程结束

参考链接：

https://p3terx.com/archives/linux-vps-uses-rclone-to-mount-network-drives-such-as-onedrive-and-google-drive.html

https://p3terx.com/archives/offline-download-of-onedrive-gdrive.html

https://p3terx.com/archives/aria2-telegram-bot-automatically-uploads-to-google-drive-onedrive.html

安装Emby
```
sudo service stop emby-server
```
```
wget https://github.com/MediaBrowser/Emby.Releases/releases/download/4.7.8.0/emby-server-deb_4.7.8.0_amd64.deb
```
```
dpkg -i emby-server-deb_4.7.8.0_amd64.deb
```





