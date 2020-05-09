# Golang

## create

> docker build -t registry.cn-beijing.aliyuncs.com/aierui/go.1.14.2:1.0 .

## push

> docker push registry.cn-beijing.aliyuncs.com/aierui/go.1.14.2:1.0

## run 

> docker run -it -v /Users/jinrong6/develop:/data1 registry.cn-beijing.aliyuncs.com/aierui/go.1.14.2:1.0 bash

## exec

> docker exec -it go bash