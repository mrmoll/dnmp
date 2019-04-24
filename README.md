# dnmp
docker nginx php(5.5 5.6 7.1) mysql  
需要安装 git docker docker-compose  
v3分支使用的docker-compose v3 语法  
1、git下载此项目  
2、在该项目的根目录执行以下命令(执行该命令之前需要保证80端口没有被其他程序占用)  
前台启动各个容器
~~~
docker-compose up  
~~~
以守护进行的形式启动
~~~
docker-compose up -d
~~~
若自己给php添加扩展，在对应版本的php dockerfile文件中增加命令 (有些扩展可能比较难装，需自行google解决)
~~~
docker-php-ext-install 扩展名
~~~
安装新的扩展之后需要重新编译镜像 然后再启动服务
~~~
docker-compose build
~~~
停止服务命令
~~~
docker-compose down
~~~
或者
~~~
docker-compose stop
~~~
3、本地hosts配置 127.0.0.1 指向 a.com 和 b.com 域名  
4、curl http://a.com和 curl http://b.com 则得到php5.6和7.1的phpinfo页面内容(或者用浏览器访问这两个域名)  
5、nginx网站根目录挂在到该项目文件夹的html文件夹下，当php代码里出现mkdir等命令时可能会无权限创建文件和文件夹，
查看php-fmp的配置文件 www.conf文件可以发现 user = www-data group = www-data ,这代表fpm的用户和用户组都是www-data，  
而在php容器里使用命令cat /etc/passwd | grep www-data 可以看到 www-data的用户uid和组uid都是82，  
所以只要把html下的每个项目文件夹 执行chown -R 82:82 命令就可以了  
执行composer命令
~~~
docker-compose run php71 composer config -gl
~~~
安装laravel 和执行artisan命令
~~~
docker-compose run --rm -w /usr/share/nginx/html/ php71 composer create-project --prefer-dist laravel/laravel l58 5.8.*
docker-compose run --rm -w /usr/share/nginx/html/l58 php71 /usr/share/nginx/html/l58/artisan make:controller userController
~~~
docker hub用的是国内中科大的镜像源，四月20号左右发现该源有点不稳定，刚开始拉取镜像的时候可能会有拉取失败的问题，需要多拉取几次。
---
注意：该项目mysql中root帐号的密码是root,如果在公网上拉取此项目，请把docker-compose.yml文件中MYSQL_ROOT_PASSWORD变量值改成其他复杂的密码，否则有被黑客攻击的危险
---
