# ceph-container-build

ceph cainter build

## env
docker > 23.0.0



# chinese / 中文
通过容器编译ceph

## 环境
docker > 23.0.0

## 创建容器环境


OS_VERSION 获取 https://hub.docker.com/_/ubuntu/tags
GIT_REF 获取 https://docs.ceph.com/en/latest/releases/#active-releases

构建:
```
docker build   --build-arg OS_VERSION="jammy" \
 --build-arg GIT_URL="https://github.com/ceph/ceph" \
 --build-arg GIT_REF="quincy" \
--tag myrepo/ceph-builder:jammy-quincy ./
```


编译:
```
docker run -ti \
  --storage-opt size=100G \
  -v "/path/to/ceph:/ceph" \
  --entrypoint=/bin/bash \
  popperized/ceph-builder:jammy-bionic
# 
cd ceph
./do_cmake.sh
```
需要注意的是 编译ceph 需要 50G磁盘空间, 所以加一个参数`--storage-opt size=100G`
