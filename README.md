# TcpQuality

## 使用方法

直接运行（默认每个节点发送 60 个包）：

```bash
bash <(curl -sL https://raw.githubusercontent.com/ibsgss/TcpQuality/main/runTcpQuality.sh)
```

查看帮助：

```bash
bash <(curl -sL https://raw.githubusercontent.com/ibsgss/TcpQuality/main/runTcpQuality.sh) -h
```

指定每个节点的发包数量，例如 100 个包：

```bash
bash <(curl -sL https://raw.githubusercontent.com/ibsgss/TcpQuality/main/runTcpQuality.sh) -c 100
```

## 支持参数

- `-h`、`--help`：显示帮助信息并退出。
- `-c NUM`、`--count NUM`：设置每个节点的发包数量，`NUM` 必须是大于 0 的整数。

发送 TCP SYN 探测包通常需要使用 `root` 用户运行。
