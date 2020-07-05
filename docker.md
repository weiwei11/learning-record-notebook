# docker

### 本机做成镜像
```bash
sudo tar -cpPf /media/ww/system.tar --directory=/ --exclude=proc --exclude=sys --exclude=dev --exclude=run --exclude=tmp --exclude=mnt --exclude=home/ww --exclude=media --exclude=boot /
cat /media/ww/system.tar | docker import - ww-shared-computer

docker images
docker run -it ww-shared-computer
```

