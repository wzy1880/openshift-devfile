docker build -t php .

docker tag php registry.cn-hongkong.aliyuncs.com/topkeecloud/php:8.0-fpm-bullseye

docker push registry.cn-hongkong.aliyuncs.com/topkeecloud/php:8.0-fpm-bullseye
