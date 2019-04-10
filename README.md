# dnmp
docker nginx php(5.5 5.6 7.1) mysql
需要安装 git docker docker-compose
v3分支使用的docker-compose v3 语法
1、git下载此项目
2、在改项目的根目录执行docker-compose up(执行该命令之前需要保证80端口没有被其他程序占用)
3、本地hosts配置 127.0.0.1 指向 a.com 和 b.com 域名
4、curl http://a.com和 curl http://b.com 则得到php5.6和7.1phpinfo页面内容(或者用浏览器访问这两个域名)

