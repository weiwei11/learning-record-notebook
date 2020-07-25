# docker

### 本机做成镜像
```bash
sudo tar -cpPf /media/ww/system.tar --directory=/ --exclude=proc --exclude=sys --exclude=dev --exclude=run --exclude=tmp --exclude=mnt --exclude=home/ww --exclude=media --exclude=boot /
cat /media/ww/system.tar | docker import - ww-shared-computer

docker images
docker run -it ww-shared-computer
```

### 更改镜像默认存储位置
1. 首先停止docker服务

sudo service docker stop；

2. 进入 docker.service.d中，docker.service.d 如果没有请自行创建；

cd etc/systemd/system/docker.service.d

3. 修改 docker-overlay.conf 文件，如果没有请自行创建；

sudo vim docker-overlay.conf 

4. 在文件中添加内容

[Service]
ExecStart=
ExecStart=/usr/bin/dockerd --graph="/media/yujuan/deepinData/docker" --storage-driver=overlay

5. 重启docker

systemctl daemon-reload
sudo service docker start

6. 查看docker 信息，确认是否已经修改成功

sudo docker info

### docker添加管理员权限
sudo groupadd docker
sudo gpasswd -a <你的用户名> docker
sudo service docker restart

