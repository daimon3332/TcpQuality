# TcpQuality

## 使用方法

默认检测三网，每个节点发送 60 个包，并行数为 31：

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

仅检测 CERNET IPv4 和 CERNET2 IPv6：

```bash
bash <(curl -sL https://raw.githubusercontent.com/ibsgss/TcpQuality/main/runTcpQuality.sh) --cernet
```

检测三网、CERNET 和 CERNET2：

```bash
bash <(curl -sL https://raw.githubusercontent.com/ibsgss/TcpQuality/main/runTcpQuality.sh) --all
```

设置并行节点数，例如 16：

```bash
bash <(curl -sL https://raw.githubusercontent.com/ibsgss/TcpQuality/main/runTcpQuality.sh) -p 16
```

## 支持参数

- `-h`、`--help`：显示帮助信息并退出。
- `-c NUM`、`--count NUM`：设置每个节点的发包数量，`NUM` 必须是大于 0 的整数。
- `-p NUM`、`--parallel NUM`：设置并行节点数，范围为 1–31，默认 31。
- `--cernet`：仅检测 CERNET IPv4 和 CERNET2 IPv6。
- `--all`：检测三网、CERNET 和 CERNET2。

脚本仅检测本机可用的 IP 协议；缺少 IPv4 或 IPv6 时会自动跳过对应节点。发送 TCP SYN 探测包通常需要使用 `root` 用户运行。
