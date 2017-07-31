
 
运行环境
---------
阿里云docker集群  


适合项目
---------
```
Dockerfile_crontab
任何前端

Dockerfile_api
php + apache + redis + mysql

Dockerfile_crontab
php + apache + redis + mysql
```



构建docker使用说明
---------
```
pwd #查看路径
ls  #查看目录内容
#登录到镜像服务器
sudo docker login --username=myname -p mypass registry.cn-hangzhou.aliyuncs.com
#构建镜像
sudo docker build -t registry.cn-hangzhou.aliyuncs.com/domain/php7-swcb -f ${WORKSPACE}/xcd/cd/Dockerfile . 
#推送到镜像服务器
sudo docker push registry.cn-hangzhou.aliyuncs.com/domain/php7-swcb
#触发，重建应用
#curl 'https://cs.console.aliyun.com/hook/trigger?triggerUrl=YzUxNGU0YjJjYWRiNTRhYWJwNzE5NTZkfHNkZWItZGVmYXVsdHxyZWRlcGxveXwxOWJsamJlOGI0MDR1fA==&secret=483174424c753656617a787a1761493f5ef83a4377435020391a21a3'
```

注意事项
1. Dockerfile中的COPY读的相对路径，且只能是子目录
2. docker build时 "-f" 指定Dockerfile的路径
3. docker build时 "." 指的是工作目录


其他项目引入
---------
```
git subtree add --prefix=xcd  git@github.com:cssharp/dockerFile.git master --squash
git subtree pull --prefix=xcd  git@github.com:cssharp/dockerFile.git master --squash
```
