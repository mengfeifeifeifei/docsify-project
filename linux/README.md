## 定时任务执行shell脚本

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