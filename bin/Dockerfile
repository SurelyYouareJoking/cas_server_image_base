FROM ubuntu:16.04

ADD sources.list /etc/apt/sources.list

RUN apt-get update -y && apt-get install -y gcc python-pip python-dev build-essential vim supervisor nginx

RUN mkdir -p /data/package /data/conf /data/tmp /data/apps /data/static /data/logs

# pip 工具目录
# /data/static 静态文件目录   需要映射本地目录
# /data/logs 日志文件目录   需要映射本地目录
# /data/apps  应用程序目录    需要映射本地目录
# /data/tmp 进程等临时文件
# /data/conf 配置文件
# /data/package 工具目录

# 配置文件
WORKDIR /data
COPY ./conf/ /data/conf/

RUN pip install -r /data/conf/requirements.txt

# 8000 单点服务 ...
# 8001 预留 ...
# 8002 预留 ...
EXPOSE 8000 8001 8002

CMD ["/usr/bin/supervisord", "-n"]

