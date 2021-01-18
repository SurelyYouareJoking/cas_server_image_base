# 打包单点登录服务运行环境

# 应用程序
## 打包镜像
cmd 进入 ~/cas_server/bin
docker build -t cas_server:2.1.1  --rm=true .

## 需要映射目录
- /data/static 静态文件目录   需要映射本地目录
- /data/logs 日志文件目录   需要映射本地目录
- /data/apps  应用程序目录    需要映射本地目录
- /data/tmp 进程等临时文件
- /data/conf 配置文件
- /data/package 工具目录

## 需要映射端口
- 8000 单点服务 ...
- 8001 预留 ...
- 8002 预留 ...

## 运行镜像 生成容器（本地测试）
docker run  -dit --name cas:1.1（容器名称）  -p 服务器映射端口:8000 -p 服务器映射端口:8001 -v 服务器映射目录:/data/apps  -v 服务器映射目录:/data/static  -v 服务器映射目录:/data/logs cas_server:2.1.1（镜像名称）

## 导出镜像
docker save cas_server:2.1.1 > E:\hup\Angel\cas_server2.1.1.tar

## 导入镜像
docker load < 镜像路径
docker load < cas_server2.1.1.tar

## 进入容器
docker exec -it cas:1.1  bash

## 需要完善
- requirements.txt 完善依赖的库列表
- nginx.conf 完善nginx.conf配置文件
- 启动时映射代码目录，映射端口
- 本地测试完成上传服务器