#Ubuntu use daily
##1. 打开图形化文件夹
nautilus /path/to
##2. ubuntu 卡死
ubuntu图形界面卡死后,可以通过可以通过ctrl+alt+F1(F1-F6)切换到命令行模式
,通过ps -aus找到卡死进程,然后kill -9 进程号
##3. vim 剪切板与系统无法共享
比较容易的方法是通过安装gvim来进行使用.
##3. gvim 实现F11全屏操作
在~/.vimrc添加
map <silent> <F11>  :call system("wmctrl -ir " . v:windowid . " -b toggle,fullscreen")<CR> ##4. wireshart  there is no interfaces on which a capture can be done.
1. first methon: 使用超级用户进行打开wireshark,操作简单,但具有风险性.
2. second methon: 修改dumpcap权限为4755,
##5. make 2>&1 | tee error.log
1. 0-stdin, 1-stdout, 2-stderr; 2>&1标准错误重定向到标准输出
2.tee同时显示在屏幕和重定向到error.log文件当中.
##6. ubuntu 修改hostname
1. vim /etc/hostname,修改,然后使用w !sudo tee %,修改只读文件
##7. vim 保存只读文件
1. w !sudo tee %
##8. ubuntu 调试android手机
1. usb连接手机,选择调试模式
2.ubuntu terminal 输入adb devices
3.ubuntu 输入 adb shell登录到手机shell
##9. ubuntu adb push 到sdcard
1. adb push src ／dst
##10. android运行脚本
　1.会抱错没有权限，即使ls -al 显示有权限
2.需要sh ./srcipt.sh
##11. android获取root权限
su
mount -o remount,rw -t yaffs2 /dev/block/mtdblock3 /system
##12. shell script　执行sudo 自动输入密码
1.安装ｅｘｐｅｃｔ
　2．#!/usr/bin/expect
spawn sudo cp ifs.sh ifs.backup.sh
expect "Password:"
send "ispasswd\r"
interac
##13. ubuntu ssh 登录android手机
安卓手机安卓quicksshd,输入端口和密码
ubuntu 使用ssh -p 端口号 root@androidip
##14. android wifi 密码
安卓wifi密码存放/data/misc/wifi/wpa_supplicant.conf明文存储.
##15. ubuntu 使用 terminator
Ctrl+Shift+E 垂直分割窗口
Ctrl+Shift+O 水平分割窗口
F11 全屏
Ctrl+Shift+C 复制
Ctrl+Shift+V 粘贴
Ctrl+Shift+N 或者 Ctrl+Tab 在分割的各窗口之间切换
Ctrl+Shift+X 将分割的某一个窗口放大至全屏使用.
Ctrl + Tab 切换不同的窗口.
exit退出terminator
##16. Git或者APT设置goagent代理
设置git代理

直接在终端输入

export https_proxy="127.0.0.1:8087"
export http_proxy="127.0.0.1:8087"
git config --global http.sslVerify false

这样git clone就是走代理了，其实这个设置完以后apt-get的操作也是通过代理的了
设置apt-get代理

上面的方法也可以直接使apt代理，如果不想设置环境变量，可以使用下面命令

sudo apt-get -o Acquire::http::proxy="http://127.0.0.1:8087/" update
export unset http_proxy
就行了，它只是增加了一个环境变量，用unset可以把这个变量取消掉
##15 更新XXnet后需要重新导入ca.crtmZ    advanced->view certificates->authorities->goagent->ca.cr
##16 安装pandoc和texlive-full
sudo apt-get install pandoc texlive-full
##17 解决!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!  
!  
! fontspec error: "font-not-found"  
!   
! The font "SimSun" cannot be found.  
!   
! See the fontspec documentation for further information.  
!   
! For immediate help type H <return>.  
!............................................... 
a.下载winfonts.tar.gz
b.创建文件夹存放winfonts.tar.gz
cd /usr/share/fonts/ 
sudo mkdir winfonts
c.解压和安装字体
sudo chmod 664 *
sudo mkfontscale
sudo mkfontdir
sudo fc-cache -fsv

##18.ubuntu安装vimium,使用键盘上网.
##19. firefox使用backspace,回退到auto:config, backspace修改值为2
##20.user not in the sudoers file. This incident will be reported
sudo EDITOR=nano visudo
append :username ALL=(ALL) ALL
##21. 重映射caps lock按键到 esc
在/etc/profile文件中加入
xmodmap -e 'clear Lock' -e 'keycode 0x42 = Escape'

##22. 小写变成大写
" 将选择的文字变成大写,插入模式,按ctrl+u
inoremap <C-u> <esc>gUiweas

##23. mwm143@x:/etc$ sudo 
sudo: /etc/sudoers is owned by uid 1000, should be 0
sudo: no valid sudoers sources found, quitting
sudo: unable to initialize policy plugin
mwm143@x:/etc$ pkexec chown root:root /etc/sudoers /etc/sudoers.d -R

##24.ubuntu 挂载samba目录 sudo mount -t cifs //192.168.0.106/ubuntusamba /mnt -o username=mwm143,password=123456
##25. how to ext4 disk quota(journaled)
1) Enable journaled quota in  /etc/fstab for all data partitions , see an example below

------------
/dev/sda3 / ext4 defaults,noatime,usrjquota=aquota.user,grpjquota=aquota.group,jqfmt=vfsv0 0 1
/dev/sda6 /home ext4 defaults,noatime,usrjquota=aquota.user,grpjquota=aquota.group,jqfmt=vfsv0 0 1
---------

The exact flags for journaled quota is  usrjquota=aquota.user,grpjquota=aquota.group,jqfmt=vfsv0

Now  remove or empty the quota files under / and /home

After that reboot your  server  to load the new quota. If you don’t like reboot you can remount all the above partitions

2) After successful reboot do the following

# quotaoff -a
# quotacheck -avugm
# quotaon -avug
##26.离线安装系统
上述的特殊字体地方将 0 改成 1 ，这样就能够让你的 RPM 档案保存下来。不过，除非你有好多部主机要更新， 你想利用一台先 yum 升级且下载，然后将所有的 RPM 档案收集起来给内网的机器升级 (rpm -Fvh *.rpm) 之外， 上面的 vim 修改动作不建议修改！因为你的 /var 恐怕会被塞爆啊！再次提醒！ 
##27. ubuntu 搭建 nfs服务
a.sudo apt-get install nfs-kernel-server nfs-common
b.vim /etc/exports
添加/tftpboot/nfsboot *(rw,sync,no_subtree_check,no_root_squash)
c. sudo /etc/init.d/nfs-kernel-server restart
d.客户端需要安装nfs-common
sudo apt-get install nfs-common
e. mount 192.168.0.104:/tftpboot/nfsroot /mnt
sudo echo hi.nfs.client > hi.nfs.client.txt
