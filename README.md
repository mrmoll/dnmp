dnmp
=
master分支使用的是docker-compose v1语法，建议使用新版本v3的语法，请把项目切换到v3分支  
-
docker nginx php(5.5 5.6 7.1) mysql  
#使用场景  
&ensp;&ensp;&ensp;&ensp;假设某公司老项目使用的是php 5.3或5.5版本，正在开发的项目是5.6版本，将来的新项目用7.1，如果是开发人员则可以用phpstudy来切换版本，但是公司的测试环境想用一台服务器放这三个项目，就要是多个版本的php共存，这个时候就不能用phpstudy了，docker技术就可以解决这个痛点。
