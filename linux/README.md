## 定时任务执行shell脚本

`service crond status 查看当前定时任务启动状态等信息`

`service crond start/stop  启动/停止 定时任务`

`报错：`

`1.错误 -bash: ....:permission denied` **是对文件夹没权限 执行 `chmod u+x/755` 文件名**

`2.fatal: parameter inet_interfaces: no local interface found for ::1 `

**执行`vi /etc/postfix/main.cf`配置`inet_interfaces = all` 重新启动 `service postfix start`**
```text
服务器下
crontab -e  回车
进入vim编辑模式   编辑要执行的规则 例如:
(*/1 * * * * /www/wwwroot/test.sh) 每分钟执行一次test脚本文件
此时在
cd /var/spool/cron目录下出现root 文件  root文件中内容为vim编辑的内容
执行crontab root | 文件名字    
在/var/log/cron 中可以看到crontab执行的日志 

shell脚本中内容为 
echo "123456" >> /www/wwwroot/test.txt 
每分钟会把内容保存到test.txt文件中

终端输入service crond stop可以停止crontab定时任务执行
```

## Vim
**快速查找：**

`/xx 从上到下查找  查找下一个按n即可`

`?xx 从下到上查找  查找上一个按n即可`

**vim进入编辑文件时出现如下情况**

`Swap file ".test.txt   .swp" already exists!`

`[O]pen Read-Only, (E)dit anyway, (R)ecover, (Q)uit, (A)bor`

**这是因为在vim编辑文件的时候，其实是先copy一份临时文件夹映射到内存中供你编辑，编辑的是临时的文件，当执行w才保存临时文件到原文件中，执行q后删除临时文件**
**每次启动vim都会检索是否有临时文件，如果有就会弹出以上情况。就是之前用vim时 临时的文件夹没有删除，所以出现这情况。**

**解决：**

`ll -a  显示隐藏的文件`

`rm -rf 临时文件(.xx.xxx.swp)`