## make Build Setup

``` bash
1.编译nginx image
make

2.发布到 docker hub
make publish
有时候会提示超时,重新执行发布
执行发布时,修改Makefile中REGISTRY_USER,改成自己的账号

3.测试是否发布成功
make publish-test

4.删除本地和已发布到docker hub上的iamge
make rmi

5.编译,发布,发布测试
make all
```

## docker命令使用说明

``` bash
创建image命令:
docker build -t blade2iron/nginx .

运行命令:
docker run --rm -it --name nginx blade2iron/nginx  bash

新建一个nginx容器,并启动nginx服务
docker run --rm -d -P --name nginx blade2iron/nginx

打开另一个终端,登录上一步容器
docker exec -it nginx bash
```
