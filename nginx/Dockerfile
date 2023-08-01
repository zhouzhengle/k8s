# Base image
FROM centos:7

# 将nginx源代码加入镜像
ADD nginx-1.24.0.tar.gz /usr/local/src/

# 安装编译器
RUN yum install -y gcc gcc-c++ make openssl-devel lsof
RUN useradd -s /sbin/nologin -M nginx

# 指定工作目录
WORKDIR /usr/local/src/nginx-1.24.0/

# 编译nginx
RUN ./configure --prefix=/usr/local/nginx --user=nginx --group=nginx --with-http_ssl_module --with-http_stub_status_module && make && make install
RUN echo "daemon off;" >> /usr/local/nginx/conf/nginx.conf

# 设置环境变量
ENV PATH /usr/local/nginx/sbin:$PATH

# 暴露80端口
EXPOSE 8080

# 容器默认启动命令
ENTRYPOINT ["nginx"]