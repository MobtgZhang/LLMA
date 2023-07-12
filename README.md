# 大模型环境配置教程

部署docker环境

我这里使用的是Debian
```bash
distribution=$(. /etc/os-release;echo $ID$VERSION_ID) \
   && curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add - \
   && curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | sudo tee /etc/apt/sources.list.d/nvidia-docker.list
```

然后更新源，安装`nvidia-docker-toolkit`

```bash
apt-get update
apt-get install -y nvidia-docker2
```
重启，并且完成安装
```bash
sudo systemctl restart docker
```
拉取对应的docker镜像，如下所示

```bash
sudo docker pull nvidia/cuda:11.7.1-base-ubuntu22.04
```

创建容器

```bash
sudo docker build -t nvidia/cuda:11.7.1-base-ubuntu22.04 .
```