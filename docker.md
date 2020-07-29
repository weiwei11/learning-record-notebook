d# docker

### 本机做成镜像
```bash
sudo tar --exclude=/proc --exclude=/sys --exclude=/media --exclude=/run --exclude=/tmp --exclude=/home -czf /media/system.tar.gz /

cat /media/ww/system.tar | docker import - shared-computer

docker images
docker run -it ww-shared-computer
```

### 更改镜像默认存储位置
1. 首先停止docker服务
```bash
sudo service docker stop
```

2. 进入 docker.service.d中，docker.service.d 如果没有请自行创建；
```bash
cd etc/systemd/system/docker.service.d
```
3. 修改 docker-overlay.conf 文件，如果没有请自行创建；
```bash
sudo vim docker-overlay.conf 
```
4. 在文件中添加内容
```
[Service]
ExecStart=
ExecStart=/usr/bin/dockerd --graph="/media/yujuan/deepinData/docker" --storage-driver=overlay
```
5. 重启docker
```bash
systemctl daemon-reload
sudo service docker start
```
6. 查看docker 信息，确认是否已经修改成功
```bash
sudo docker info
```

### docker添加管理员权限
```bash
sudo groupadd docker
sudo gpasswd -a <你的用户名> docker
sudo service docker restart
```

### 主机与容器间复制文件
```bash
sudo docker cp --help
```

### 查看GPU设备
```bash
ls -la /dev | grep nvidia
```

### docker 实验
1. 
```bash
sudo docker run -it --name deke --device /dev/nvidia0:/dev/nvidia0 --device /dev/nvidia1:/dev/nvidia1 --device /dev/nvidiactl:/dev/nvidiactl --device /dev/nvidia-modeset:/dev/nvidia-modeset --device /dev/nvidia-uvm:/dev/nvidia-uvm --device /dev/nvidia-uvm-tools:/dev/nvidia-uvm-tools -e DISPLAY=$DISPLAY --net=host -v /media/deke/DATA_03/code/pvnet_cpp:/home/deke/code/pvnet_cpp -v /home/deke/lib:/home/deke/lib -v /home/deke/app:/home/deke/app -P deke-shared-computer /bin/bash
```

2. solve problem
  1. [docker use gpu](https://stackoverflow.com/questions/25185405/using-gpu-from-a-docker-container#:~:text=Using%20GPU%20from%20a%20docker%20containe                    r%3F%201%20Environment.,CUDA%20driver.%20...%2010%20Run%20your%20image.%20)
  2. [docker failed to initialize nvml: unknown error](https://stackoverflow.com/questions/25185405/using-gpu-from-a-docker-container#:~:text=Using%20GPU%20from%20a%20docker%20container%3F%201%20Environment.,CUDA%20driver.%20...%2010%20Run%20your%20image.%20)
  3. [Running GUI apps with Docker](http://fabiorehm.com/blog/2014/09/11/running-gui-apps-with-docker/)
  4. ```Unable to init server: Could not connect: Connection refused

	(1:66): Gtk-WARNING **: 14:14:03.644: cannot open display:```
  [solve link](https://stackoverflow.com/questions/38249629/inside-a-docker-container-error-cannot-open-display-localhost11-0)
  5. ```(1:15): dbind-WARNING **: 14:29:13.629: Couldn't register with accessibility bus: An AppArmor policy prevents this sender from sending this message to this recipient; type="method_call", sender="(null)" (inactive) interface="org.freedesktop.DBus" member="Hello" error name="(unset)" requested_reply="0" destination="org.freedesktop.DBus" (bus)```
  [solve link](https://unix.stackexchange.com/questions/532585/getting-dbind-warnings-about-registering-with-the-accessibility-bus)
