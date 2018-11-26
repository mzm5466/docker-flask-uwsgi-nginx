# 基础镜像
FROM python:2.7.15-alpine3.8

RUN mkdir /var/www
# 指定工作路径
WORKDIR /var/www
#设置时区和源
ENV TIME_ZONE Asia/Shanghai
#使用清华源
RUN echo "https://mirror.tuna.tsinghua.edu.cn/alpine/v3.8/main/" > /etc/apk/repositories

RUN apk add --no-cache -U tzdata \
    && ln -sf /usr/share/zoneinfo/${TIME_ZONE} /etc/localtime \ 
    && echo "${TIME_ZONE}" > /etc/timezone
# 拷贝安装python包清单
COPY requirements.txt ./

# 安装项目依赖包
RUN apk update && apk add \
        libuuid \
        pcre \
        mailcap \
        gcc \
        libc-dev \
        linux-headers \
        pcre-dev \
    && pip install --no-cache-dir -r requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple \
    && apk del \
        gcc \
        libc-dev \
        linux-headers \
    && rm -rf /tmp/*

#切换工作目录
WORKDIR /var/www/src

CMD ["uwsgi","--ini","/var/www/uwsgi.ini"]
