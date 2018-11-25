# 基础镜像
FROM alpine:3.8

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

RUN apk add --no-cache python3-dev gcc libc-dev linux-headers
#安装python
RUN apk add --no-cache python3 && \
    python3 -m ensurepip && \
    rm -r /usr/lib/python*/ensurepip && \
    pip3 install --upgrade pip setuptools && \
    if [ ! -e /usr/bin/pip ]; then ln -s pip3 /usr/bin/pip ; fi && \
    if [[ ! -e /usr/bin/python ]]; then ln -sf /usr/bin/python3 /usr/bin/python; fi && \
    rm -r /root/.cache
# 拷贝安装python包清单
COPY requirements.txt ./

# 安装项目依赖包
RUN pip3 install --no-cache-dir -r requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple
#切换工作目录
WORKDIR /var/www/src

CMD ["uwsgi","--ini","/var/www/uwsgi.ini"]
