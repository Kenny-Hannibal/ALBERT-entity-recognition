# 声明基础镜像版本，选择pytorch官方镜像
FROM pytorch/pytorch:1.3-cuda10.1-cudnn7-runtime

# 声明维护者
MAINTAINER old-wang <old-wang@gmail.com>

# 首先拷贝requirements.txt进docker
COPY ./requirements.txt /requirements.txt
# 安装python依赖（如果安装较慢，请更换国内pip源：-i https://pypi.douban.com/simple/）
RUN pip install -r /requirements.txt

# 将所有代码添加进去
COPY . /data/app

# 设置默认的工作目录
WORKDIR /data/app

# 设置系统编码为utf-8，防止中文乱码
ENV LANG C.UTF-8

# 设置暴露8000端口
EXPOSE 8000

# CMD启动http服务，（也可以选择启动rpc服务，或者两个同时启动）
CMD cd /data/app/scripts && sh start_http_server.sh
