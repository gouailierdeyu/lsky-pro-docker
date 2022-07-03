# lsky-pro-docker
Lsky Pro 兰空图床 docker 镜像，适用于 Linux amd64 架构。镜像地址: https://hub.docker.com/r/gouailideyu/lsky-pro/tags

之前看其他作者的镜像都是只能使用mysql作为数据库，因此

我添加了部分命令使得可以使用postgresql作为数据库。
主要命令为：
```dockerfile
RUN apt update && apt install imagemagick libmagickwand-dev postgresql-server-dev-13 -y \
    && pecl install imagick \
    && docker-php-ext-install bcmath \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-install pdo_pgsql \
    && docker-php-ext-enable imagick 
```
因此如果要添加其他数据库支持，方法应该内同。

镜像使用

```
# 拉取镜像
# docker pull gouailideyu/lsky-pro:2.0.4

# 启动容器
# docker run -d --name=lsky-pro --restart=always -v /path/to/mount/lsky-pro-data:/var/www/html -p 7791:80 dko0/lsky-pro:2.0.4
```
