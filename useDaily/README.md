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
##4. gvim 更改配色方案
    a.到vim官网挑选心怡的配色方案,http://www.vim.org/scripts/script_search_results.php?keywords=&script_type=color+scheme&order_by=downloads&direction=descending&search=search
    b.将下载的配饰方案拷贝到 /usr/share/vim/vim74/colors/目录下,注意vim74的目录74是版本有关
    c.在~/.vimrc下添加colorscheme molokai //我下载的github.vim
