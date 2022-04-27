# git报错ssh: connect to host github.com port 22: Connection timed out
生成 ssh
ssh-keygen -t rsa -C "your_email@example.com"


使用 git bash 
1. cd ~/.ssh
2. vim config 
3. 摁建 insert
4. 开始输入

Host github.com
User “你的邮箱”
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


