#vim config
##1.overview
  vimrc 是vim的配置文档
  将vimrc提交到github方便管理以及是软件卸载或者系统崩溃可快速恢复自己vim的配置习惯
  这个vimrc基础版本是来自https://github.com/ma6174/vim 
##2. vim 查看二进制文件
##2.1.vim 下查看二进制文件
    vim二进制方式编辑 vim -b datafile
    用xxd把这个文件转换成十六进制
    :%!xxd
##2.2.vim 比较两个文件的差异
   vim -d file1 file2
##3.vim 格式风格对齐
   使用Artistic Style 2.05链接为:http://astyle.sourceforge.net/astyle.html
   修改246行,使用linux风格,具体风格可以参考Artistic Style 2.05的doc
   将c的编译器改成gcc而不适用g++
