# protobuf

下载https://github.com/google/protobuf/releases ##Source code (zip)##
./autogen.sh
./configure
make
make check
make install
1
2
3
4
5
6

卸载

which protoc 
rm /usr/local/bin/protoc

rm /usr/local/lib/libproto*

rm -R /usr/local/include/google/protobuf