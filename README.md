# ELK Docker 安装

## 修改配置

> 在elasticsearch的docker版本文档中，官方提到了vm.max_map_count的值在生产环境最少要设置成262144。设置的方式有两种

1. 永久性的修改,在`/etc/sysctl.conf`文件中添加一行：

```shell
grep vm.max_map_count /etc/sysctl.conf # 查找当前的值。

vm.max_map_count=655360 # 修改或者新增
```

2. 正在运行的机器：

```shell
sysctl -w vm.max_map_count=655360
```
