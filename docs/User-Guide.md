# PMem Common

PMem common package includes native libraries and JNI interface for Intel Optane PMem.

## Prerequisites

Below libraries need to be installed in the machine

- [Memkind](http://memkind.github.io/memkind/)

- [Vmemcache](https://github.com/pmem/vmemcache)

###  memkind installation

The memkind library depends on `libnuma` at the runtime, so it must already exist in the worker node system. Build the latest memkind lib from source:

```
git clone -b v1.10.1 https://github.com/memkind/memkind
cd memkind
./autogen.sh
./configure
make
make install
``` 
### vmemcache installation

To build vmemcache library from source, you can (for RPM-based linux as example):
```
git clone https://github.com/pmem/vmemcache
cd vmemcache
mkdir build
cd build
cmake .. -DCMAKE_INSTALL_PREFIX=/usr -DCPACK_GENERATOR=rpm
make package
sudo rpm -i libvmemcache*.rpm
```

## Building

```
git clone -b <tag-version> https://github.com/oap-project/pmem-common.git
cd pmem-common
mvn clean package -Ppersistent-memory,vmemcache
```
