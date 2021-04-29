##### \* LEGAL NOTICE: Your use of this software and any required dependent software (the "Software Package") is subject to the terms and conditions of the software license agreements for the Software Package, which may also include notices, disclaimers, or license terms for third party or open source software included in or with the Software Package, and your use indicates your acceptance of all such terms. Please refer to the "TPP.txt" or other similarly-named text file included with the Software Package for additional details.

##### \* Optimized Analytics Package for Spark* Platform is under Apache 2.0 (https://www.apache.org/licenses/LICENSE-2.0).

# PMem Common

PMem Common package includes native libraries and JNI interface for Intel Optane PMem.

## Online Documentation

You can find the all the PMem Common documents on the [project web page](https://oap-project.github.io/pmem-common/).

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
