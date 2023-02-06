# go-src-1.20
go-src-1.20

从源码安装 go https://go.dev/doc/install/source
```shell
sudo ln -s /usr/bin/go-12 /usr/bin/go 
sudo update-alternatives --set go /usr/bin/go-12
cd /go/src
./make.bash
# go gofmt 编译到了 ./bin
cd ..
export PATH=`pwd`/bin:$PATH
```
