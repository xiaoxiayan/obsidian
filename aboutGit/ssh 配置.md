# git报错ssh: connect to host github.com port 22: Connection timed out
生成 ssh
ssh-keygen -t rsa -C "a690150618@qq.com"


使用 git bash 
1. cd ~/.ssh
2. vim config 
3. 摁建 insert
4. 开始输入

Host github.com
User "a690150618@qq.com"
Hostname ssh.github.com
PreferredAuthentications publickey
IdentityFile ~/.ssh/id_rsa
Port 443
5. Esc 
6. 输入 :wq 
7. 使用 ssh git@github.com -T 测试
出现 
Hi xiaoxiayan! You've successfully authenticated, but GitHub does not provide shell access.
就可以 提交了


# gitToken
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
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

# ssh: connect to host github.com port 443: Connection refused
如何解决，不动，


[Ssh: Connect to Host ssh.github.com Port 443: Connection Refused - 丘海东 (qiuhaidong.github.io)](https://qiuhaidong.github.io/blog/2022/05/26/ssh-connect-to-host-ssh-dot-github-dot-com-port-443-connection-refused/)

可以设置代理。
也有可能是 hosts 文件 出现了清空。
重新写入 hosts 
关于 系统文件修改方面，
[无法枚举容器内对象 访问被拒绝？ - 知乎 (zhihu.com)](https://www.zhihu.com/question/31001796)


1.  刷新本地 dns 缓存：cmd执行命令行`ipconfig /flushdns`


### Permissions 0644

It is required that your private key files are NOT accessible by others.
This private key will be ignored.


私钥权限需要降低

chmod 0600 ~/.ssh/id_rsa

