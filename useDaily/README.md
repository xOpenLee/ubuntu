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
   安卓wifi密码存放/data/misc/wifi/wpa_supplicant.conf
   明文存储.
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
