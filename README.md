# Daimon的TCP重传检测

TCP SYN 重传检测脚本，支持三网、教育网和自定义 IP。无参数运行会进入交互菜单；带参数运行会直接开始检测。

## 运行

```bash
bash <(curl -sL https://raw.githubusercontent.com/daimon3332/TcpQuality/main/runTcpQuality.sh)
```

## 参数

- `--三网`：测试移动、联通、电信。
- `--全部`：测试三网和教育网。
- `--教育`：测试教育网。
- `--移动`：测试移动，可与 `--联通`、`--电信` 组合。
- `--联通`：测试联通，可与 `--移动`、`--电信` 组合。
- `--电信`：测试电信，可与 `--移动`、`--联通` 组合。
- `--福建`：只测试福建教育网节点，需配合 `--教育` 或 `--全部` 使用。
- `--IPv4`：只测试 IPv4。
- `--IPv6`：只测试 IPv6。
- `--IP IP`：只测试指定 IP。
- `--端口 NUM`：设置 TCP 目标端口，默认 `80`。
- `--次数 NUM`：设置每节点探测次数，默认 `30`。
- `--并发 NUM`：设置并行节点数，默认 `16`。

## 示例

```bash
bash <(curl -sL https://raw.githubusercontent.com/daimon3332/TcpQuality/main/runTcpQuality.sh) --三网
bash <(curl -sL https://raw.githubusercontent.com/daimon3332/TcpQuality/main/runTcpQuality.sh) --全部
bash <(curl -sL https://raw.githubusercontent.com/daimon3332/TcpQuality/main/runTcpQuality.sh) --教育 --福建
bash <(curl -sL https://raw.githubusercontent.com/daimon3332/TcpQuality/main/runTcpQuality.sh) --移动 --联通
bash <(curl -sL https://raw.githubusercontent.com/daimon3332/TcpQuality/main/runTcpQuality.sh) --IP 219.229.81.211
bash <(curl -sL https://raw.githubusercontent.com/daimon3332/TcpQuality/main/runTcpQuality.sh) --教育 --福建 --IPv4 --次数 30 --端口 80
```

默认会检测当前 VPS 可用的 IP 协议；如果显式指定 `--IPv4` 或 `--IPv6`，但当前 VPS 不支持该协议，脚本会提示并退出。教育网节点会优先解析域名，解析失败时再使用脚本内置 IP。
