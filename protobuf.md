# protobuf

## 安装

1. 下载源代码 https://github.com/google/protobuf/releases
2. 运行命令：
```bash
./autogen.sh
./configure 
make 
make check 
make install
```

## 卸载

```bash
which protoc rm /usr/local/bin/protoc
rm /usr/local/lib/libproto*
rm -R /usr/local/include/google/protobuf
```