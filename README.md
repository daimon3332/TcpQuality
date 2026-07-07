# Daimon的TCP重传检测

TCP SYN 重传检测脚本，支持三网节点和教育网节点。无参数运行会进入交互菜单；带参数运行会直接开始检测。

## 运行

```bash
bash <(curl -sL https://raw.githubusercontent.com/daimon3332/TcpQuality/main/runTcpQuality.sh)
```

## 常用参数

- `--three`：只测试三网。
- `--all`：测试三网和教育网。
- `--edu`：只测试教育网。
- `--cm`：测试移动。
- `--cu`：测试联通。
- `--ct`：测试电信。
- `-fujian`：只测试福建教育网节点，配合 `--edu` 或 `--all` 使用。
- `-4`、`-v4`：只测试 IPv4。
- `-6`、`-v6`：只测试 IPv6。
- `--port NUM`：设置 TCP 目标端口，默认 `80`。
- `-c NUM`、`--count NUM`：设置每节点探测次数，默认 `30`。
- `-p NUM`、`--parallel NUM`：设置并行节点数，默认 `16`。

## 示例

测试教育网全部可用协议：

```bash
bash <(curl -sL https://raw.githubusercontent.com/daimon3332/TcpQuality/main/runTcpQuality.sh) --edu
```

测试三网和教育网：

```bash
bash <(curl -sL https://raw.githubusercontent.com/daimon3332/TcpQuality/main/runTcpQuality.sh) --all
```

测试福建教育网：

```bash
bash <(curl -sL https://raw.githubusercontent.com/daimon3332/TcpQuality/main/runTcpQuality.sh) --edu -fujian
```

测试移动+联通：

```bash
bash <(curl -sL https://raw.githubusercontent.com/daimon3332/TcpQuality/main/runTcpQuality.sh) --cm --cu
```

只测试福建教育网 IPv4：

```bash
bash <(curl -sL https://raw.githubusercontent.com/daimon3332/TcpQuality/main/runTcpQuality.sh) --edu -fujian -v4
```

指定端口和次数：

```bash
bash <(curl -sL https://raw.githubusercontent.com/daimon3332/TcpQuality/main/runTcpQuality.sh) --edu -fujian --port 80 -c 30
```

默认会检测当前 VPS 可用的 IP 协议；如果显式指定 `-v4` 或 `-v6`，但当前 VPS 不支持该协议，脚本会提示并退出。
