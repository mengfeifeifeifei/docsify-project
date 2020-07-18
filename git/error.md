>`git clone出现这种报错是因为没有配置ssh密钥`

![error](../image/git/error.jpg)

```git
cat ~/.ssh  (查看密钥文件)
ls
ssh-keygen -t rsa -C "git的邮箱或账户名"  （生成密钥）
cat ~/.ssh/id_rsa.pub  (查看密钥) 
复制密钥到github的配置中
```