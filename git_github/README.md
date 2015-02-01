# git and gitHub
##1.create a new rep on the command line 
    echo "# wmaDecode" >> README.md
    git init
    git add README.md
    git commit -m "first commit"
    git remote add origin https://github.com/xOpenLee/wmaDecode.git
    git push -u origin master
##2. github README.md add the picture method
    1.先将图片上传到reposity当中,任何在github当中打开,复制路径
    2.![](复制的路径),注意这行一定要没有空格.
    3.再次提交即可
##3. 解决每次git push 都需要输入用户名和密码
    1.因为之前我用另一个邮箱生产过SSH key,因此,需要删除之前位于在~/.ssh/目录下的所有文件
    2.之后的操作请参照https://help.github.com/articles/generating-ssh-keys/
    3.如果之前是用https进行git clone 的reposity的话,需要进行https切换到ssh.
    4.https切换到ssh参照https://help.github.com/articles/changing-a-remote-s-url/
##4. git operation
    git目录下,所有操作需带git操作,否则.git无法知道状态的变化.
    如删除使用git rm 替代rm
##5. git reset
    git reset HEAD filename  从暂存区中移除文件
    git reset –hard HEAD~3  会将最新的3次提交全部重置，就像没有提交过一样。
    git reset –hard commit (38679ed709fd0a3767b79b93d0fba5bb8dd235f8) 回退到 38679ed709fd0a3767b79b93d0fba5bb8dd235f8 版本
##6. git reset 错误
    若发现git reset 回滚错误,可以通过git reflog查找版本信息,然后通过git reset --hard (verID)进行恢复
