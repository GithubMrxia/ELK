# ELK Docker 安装


## 流程

1. `filebeat` 日志收集，输出到 `redis`
2. `logstash` 从 `redis` 拉取缓存的日志，进行日志处理，并输出到 `elasticseach`
3. `Kibana`:用于日志展示的可视化工具

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

## 配置

### 配置 `.env`

- 如果修改 `ELASTIC_PASSWORD` 值，需要同时调整 `logstash` 和 `kibana` 配置的密码

1. 复制 `.env.example` 改名为 `.env`

2. 调整配置

### `filebeat` 配置

1. 增加 `filebeat/config/filebeat.yml`
2.  在 `filebeat/config/inputs.d` 下增加日志配置

### `logstash` 增加日志配置

1. 在 `logstash/pipeline/` 下增加日志配置

### `kibana` 增加日志配置

1. 增加`kibana/config/kibana.yml`
