# PHP 7.4.5

## create

> docker build -t registry.cn-beijing.aliyuncs.com/aierui/php7.4.5:1.0 .

## push

> docker push registry.cn-beijing.aliyuncs.com/aierui/php7.4.5:1.0

## run 

> docker run -itd --name=php7.4.5 -v /Users/jinrong6/develop:/data1 registry.cn-beijing.aliyuncs.com/aierui/php7.4.5:1.0 bash

## exec

> docker exec -it php7.4.5 bash