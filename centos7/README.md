# Centos7 

## create

> docker build -t registry.cn-beijing.aliyuncs.com/aierui/centos7:1.0 .

## push

> docker push registry.cn-beijing.aliyuncs.com/aierui/centos7:1.0

## run 

> docker run -itd --name=centos7 -v /Users/jinrong6/develop:/data1 registry.cn-beijing.aliyuncs.com/aierui/centos7:1.0 bash

## exec

> docker exec -it centos7 bash