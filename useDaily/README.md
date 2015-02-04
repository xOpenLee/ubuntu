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
    map <silent> <F11>  :call system("wmctrl -ir " . v:windowid . " -b toggle,fullscreen")<CR>
