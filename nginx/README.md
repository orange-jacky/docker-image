创建image命令:
docker build -t blade2iron/nginx .

运行命令:
docker run --rm -it --name nginx blade2iron/nginx  bash

新建一个nginx容器,并启动nginx服务
docker run --rm -d -P --name nginx blade2iron/nginx