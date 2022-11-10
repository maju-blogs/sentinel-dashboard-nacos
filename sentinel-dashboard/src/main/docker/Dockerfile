#使用的基础镜像
FROM yangqiyong/jdk:1.8.0

#作者信息
MAINTAINER yangqiyong "yangqiyong@vip.qq.com"

RUN rm -f /etc/localtime   \
&& ln -sv /usr/share/zoneinfo/Asia/Shanghai /etc/localtime  \
&& echo "Asia/Shanghai" > /etc/timezone \

#创建目录
RUN mkdir -p /opt/itlong/

#创建用户组及用户；这里是以root用户执行
RUN groupadd itlong
RUN useradd -g itlong itlong

#把当前目录下的应用添加到镜像
ADD --chown=itlong:itlong sentinel-dashboard.jar /opt/itlong/sentinel-dashboard.jar

#普通用户
USER itlong

#暴露服务端口
EXPOSE 18889

#启动时运行服务
ENTRYPOINT ["java","-jar","-Xmx512m","-Xms512m","-Dfile.encoding=utf-8","-Dlog4j2.formatMsgNoLookups=true","/opt/itlong/sentinel-dashboard.jar"]
