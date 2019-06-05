# 基础镜像及作者
FROM centos
LABEL author='zjtachao/duhao:1.0'

# 基础环境设置
ENV LANG=C.UTF-8
# 安装gcc
RUN yum -y install gcc automake autoconf libtool make zlib* libffi-devel wget

# 添加python3.7环境
ENV PYTHON_VERSION=3.7.3
# 进入工作目录
WORKDIR /opt/install
# 复制安装文件到目标目录
# COPY ./Python-${PYTHON_VERSION}.tgz /opt/install
RUN wget https://www.python.org/ftp/python/${PYTHON_VERSION}/Python-${PYTHON_VERSION}.tgz
# 解压文件
RUN tar -zxvf Python-${PYTHON_VERSION}.tgz
# 进入解压好的目录
WORKDIR /opt/install/Python-${PYTHON_VERSION}
# 建立目标安装文件夹
RUN mkdir /usr/local/python3
# 配置安装路径
RUN ./configure --prefix=/usr/local/python3
# 编译和安装
RUN make
RUN make install
# 改变老版本的python2
#RUN mv /usr/bin/python /usr/bin/python2
# 建立新版本链接
RUN ln -s /usr/local/python3/bin/python3 /usr/bin/python3
# 查看是否安装完成
RUN python3 -V

# 返回
ENTRYPOINT [ "python3" ]