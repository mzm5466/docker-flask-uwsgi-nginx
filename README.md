# Flask开发环境 基于Alpine:3.8基础镜像

## 启动
```
# make run
```
## 停止
```
# make stop
```

# 目录
```
.
├── Makefile  #启动器
├── README.md  
├── app       #后台
│   ├── Dockerfile
│   ├── requirements.txt
│   ├── src
│   │   ├── run.py
│   │   ├── test.log
│   └── uwsgi.ini
├── docker-compose.yml
└── nginx    #前端
    ├── Dockerfile
    └── nginx.conf
```
