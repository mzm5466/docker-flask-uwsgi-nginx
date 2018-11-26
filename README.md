# Flask开发环境python2版本

## 起動
```
# make run
```
## 停止
```
# make stop
```

# 構成
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
