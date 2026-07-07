# Daimon的TCP重传检测

TCP SYN 重传检测脚本，支持三网、教育网和自定义 IP。无参数运行会进入交互菜单；带参数运行会直接开始检测。

## 运行

```bash
bash <(curl -fsSL https://raw.githubusercontent.com/daimon3332/TcpQuality/main/runTcpQuality.sh)
```

如果 GitHub Raw 返回 `429`，说明当前出口被 GitHub 临时限流；`curl -f` 会让下载失败而不是把错误页交给 Bash 执行。

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
bash <(curl -fsSL https://raw.githubusercontent.com/daimon3332/TcpQuality/main/runTcpQuality.sh) --三网
bash <(curl -fsSL https://raw.githubusercontent.com/daimon3332/TcpQuality/main/runTcpQuality.sh) --全部
bash <(curl -fsSL https://raw.githubusercontent.com/daimon3332/TcpQuality/main/runTcpQuality.sh) --教育 --福建
bash <(curl -fsSL https://raw.githubusercontent.com/daimon3332/TcpQuality/main/runTcpQuality.sh) --移动 --联通
bash <(curl -fsSL https://raw.githubusercontent.com/daimon3332/TcpQuality/main/runTcpQuality.sh) --IP 219.229.81.211
bash <(curl -fsSL https://raw.githubusercontent.com/daimon3332/TcpQuality/main/runTcpQuality.sh) --教育 --福建 --IPv4 --次数 30 --端口 80
```

默认会检测当前 VPS 可用的 IP 协议；如果显式指定 `--IPv4` 或 `--IPv6`，但当前 VPS 不支持该协议，脚本会提示并退出。教育网节点会优先解析域名，解析失败时再使用脚本内置 IP。

## 三网节点

| 省份 | 联通 IPv4 | 联通 IPv6 | 移动 IPv4 | 移动 IPv6 | 电信 IPv4 | 电信 IPv6 |
| --- | --- | --- | --- | --- | --- | --- |
| 河北 | he-cu-v4.ip.zstaticcdn.com | he-cu-v6.ip.zstaticcdn.com | he-cm-v4.ip.zstaticcdn.com | he-cm-v6.ip.zstaticcdn.com | he-ct-v4.ip.zstaticcdn.com | he-ct-v6.ip.zstaticcdn.com |
| 山西 | sx-cu-v4.ip.zstaticcdn.com | sx-cu-v6.ip.zstaticcdn.com | sx-cm-v4.ip.zstaticcdn.com | sx-cm-v6.ip.zstaticcdn.com | sx-ct-v4.ip.zstaticcdn.com | sx-ct-v6.ip.zstaticcdn.com |
| 辽宁 | ln-cu-v4.ip.zstaticcdn.com | ln-cu-v6.ip.zstaticcdn.com | ln-cm-v4.ip.zstaticcdn.com | ln-cm-v6.ip.zstaticcdn.com | ln-ct-v4.ip.zstaticcdn.com | ln-ct-v6.ip.zstaticcdn.com |
| 吉林 | jl-cu-v4.ip.zstaticcdn.com | jl-cu-v6.ip.zstaticcdn.com | jl-cm-v4.ip.zstaticcdn.com | jl-cm-v6.ip.zstaticcdn.com | jl-ct-v4.ip.zstaticcdn.com | jl-ct-v6.ip.zstaticcdn.com |
| 黑龙江 | hl-cu-v4.ip.zstaticcdn.com | hl-cu-v6.ip.zstaticcdn.com | hl-cm-v4.ip.zstaticcdn.com | hl-cm-v6.ip.zstaticcdn.com | hl-ct-v4.ip.zstaticcdn.com | hl-ct-v6.ip.zstaticcdn.com |
| 江苏 | js-cu-v4.ip.zstaticcdn.com | js-cu-v6.ip.zstaticcdn.com | js-cm-v4.ip.zstaticcdn.com | js-cm-v6.ip.zstaticcdn.com | js-ct-v4.ip.zstaticcdn.com | js-ct-v6.ip.zstaticcdn.com |
| 浙江 | zj-cu-v4.ip.zstaticcdn.com | zj-cu-v6.ip.zstaticcdn.com | zj-cm-v4.ip.zstaticcdn.com | zj-cm-v6.ip.zstaticcdn.com | zj-ct-v4.ip.zstaticcdn.com | zj-ct-v6.ip.zstaticcdn.com |
| 安徽 | ah-cu-v4.ip.zstaticcdn.com | ah-cu-v6.ip.zstaticcdn.com | ah-cm-v4.ip.zstaticcdn.com | ah-cm-v6.ip.zstaticcdn.com | ah-ct-v4.ip.zstaticcdn.com | ah-ct-v6.ip.zstaticcdn.com |
| 福建 | fj-cu-v4.ip.zstaticcdn.com | fj-cu-v6.ip.zstaticcdn.com | fj-cm-v4.ip.zstaticcdn.com | fj-cm-v6.ip.zstaticcdn.com | fj-ct-v4.ip.zstaticcdn.com | fj-ct-v6.ip.zstaticcdn.com |
| 江西 | jx-cu-v4.ip.zstaticcdn.com | jx-cu-v6.ip.zstaticcdn.com | jx-cm-v4.ip.zstaticcdn.com | jx-cm-v6.ip.zstaticcdn.com | jx-ct-v4.ip.zstaticcdn.com | jx-ct-v6.ip.zstaticcdn.com |
| 山东 | sd-cu-v4.ip.zstaticcdn.com | sd-cu-v6.ip.zstaticcdn.com | sd-cm-v4.ip.zstaticcdn.com | sd-cm-v6.ip.zstaticcdn.com | sd-ct-v4.ip.zstaticcdn.com | sd-ct-v6.ip.zstaticcdn.com |
| 河南 | ha-cu-v4.ip.zstaticcdn.com | ha-cu-v6.ip.zstaticcdn.com | ha-cm-v4.ip.zstaticcdn.com | ha-cm-v6.ip.zstaticcdn.com | ha-ct-v4.ip.zstaticcdn.com | ha-ct-v6.ip.zstaticcdn.com |
| 湖北 | hb-cu-v4.ip.zstaticcdn.com | hb-cu-v6.ip.zstaticcdn.com | hb-cm-v4.ip.zstaticcdn.com | hb-cm-v6.ip.zstaticcdn.com | hb-ct-v4.ip.zstaticcdn.com | hb-ct-v6.ip.zstaticcdn.com |
| 湖南 | hn-cu-v4.ip.zstaticcdn.com | hn-cu-v6.ip.zstaticcdn.com | hn-cm-v4.ip.zstaticcdn.com | hn-cm-v6.ip.zstaticcdn.com | hn-ct-v4.ip.zstaticcdn.com | hn-ct-v6.ip.zstaticcdn.com |
| 广东 | gd-cu-v4.ip.zstaticcdn.com | gd-cu-v6.ip.zstaticcdn.com | gd-cm-v4.ip.zstaticcdn.com | gd-cm-v6.ip.zstaticcdn.com | gd-ct-v4.ip.zstaticcdn.com | gd-ct-v6.ip.zstaticcdn.com |
| 海南 | hi-cu-v4.ip.zstaticcdn.com | hi-cu-v6.ip.zstaticcdn.com | hi-cm-v4.ip.zstaticcdn.com | hi-cm-v6.ip.zstaticcdn.com | hi-ct-v4.ip.zstaticcdn.com | hi-ct-v6.ip.zstaticcdn.com |
| 四川 | sc-cu-v4.ip.zstaticcdn.com | sc-cu-v6.ip.zstaticcdn.com | sc-cm-v4.ip.zstaticcdn.com | sc-cm-v6.ip.zstaticcdn.com | sc-ct-v4.ip.zstaticcdn.com | sc-ct-v6.ip.zstaticcdn.com |
| 贵州 | gz-cu-v4.ip.zstaticcdn.com | gz-cu-v6.ip.zstaticcdn.com | gz-cm-v4.ip.zstaticcdn.com | gz-cm-v6.ip.zstaticcdn.com | gz-ct-v4.ip.zstaticcdn.com | gz-ct-v6.ip.zstaticcdn.com |
| 云南 | yn-cu-v4.ip.zstaticcdn.com | yn-cu-v6.ip.zstaticcdn.com | yn-cm-v4.ip.zstaticcdn.com | yn-cm-v6.ip.zstaticcdn.com | yn-ct-v4.ip.zstaticcdn.com | yn-ct-v6.ip.zstaticcdn.com |
| 陕西 | sn-cu-v4.ip.zstaticcdn.com | sn-cu-v6.ip.zstaticcdn.com | sn-cm-v4.ip.zstaticcdn.com | sn-cm-v6.ip.zstaticcdn.com | sn-ct-v4.ip.zstaticcdn.com | sn-ct-v6.ip.zstaticcdn.com |
| 甘肃 | gs-cu-v4.ip.zstaticcdn.com | gs-cu-v6.ip.zstaticcdn.com | gs-cm-v4.ip.zstaticcdn.com | gs-cm-v6.ip.zstaticcdn.com | gs-ct-v4.ip.zstaticcdn.com | gs-ct-v6.ip.zstaticcdn.com |
| 青海 | qh-cu-v4.ip.zstaticcdn.com | qh-cu-v6.ip.zstaticcdn.com | qh-cm-v4.ip.zstaticcdn.com | qh-cm-v6.ip.zstaticcdn.com | qh-ct-v4.ip.zstaticcdn.com | qh-ct-v6.ip.zstaticcdn.com |
| 内蒙古 | nm-cu-v4.ip.zstaticcdn.com | nm-cu-v6.ip.zstaticcdn.com | nm-cm-v4.ip.zstaticcdn.com | nm-cm-v6.ip.zstaticcdn.com | nm-ct-v4.ip.zstaticcdn.com | nm-ct-v6.ip.zstaticcdn.com |
| 广西 | gx-cu-v4.ip.zstaticcdn.com | gx-cu-v6.ip.zstaticcdn.com | gx-cm-v4.ip.zstaticcdn.com | gx-cm-v6.ip.zstaticcdn.com | gx-ct-v4.ip.zstaticcdn.com | gx-ct-v6.ip.zstaticcdn.com |
| 西藏 | xz-cu-v4.ip.zstaticcdn.com | xz-cu-v6.ip.zstaticcdn.com | xz-cm-v4.ip.zstaticcdn.com | xz-cm-v6.ip.zstaticcdn.com | xz-ct-v4.ip.zstaticcdn.com | xz-ct-v6.ip.zstaticcdn.com |
| 宁夏 | nx-cu-v4.ip.zstaticcdn.com | nx-cu-v6.ip.zstaticcdn.com | nx-cm-v4.ip.zstaticcdn.com | nx-cm-v6.ip.zstaticcdn.com | nx-ct-v4.ip.zstaticcdn.com | nx-ct-v6.ip.zstaticcdn.com |
| 新疆 | xj-cu-v4.ip.zstaticcdn.com | xj-cu-v6.ip.zstaticcdn.com | xj-cm-v4.ip.zstaticcdn.com | xj-cm-v6.ip.zstaticcdn.com | xj-ct-v4.ip.zstaticcdn.com | xj-ct-v6.ip.zstaticcdn.com |
| 北京 | bj-cu-v4.ip.zstaticcdn.com | bj-cu-v6.ip.zstaticcdn.com | bj-cm-v4.ip.zstaticcdn.com | bj-cm-v6.ip.zstaticcdn.com | bj-ct-v4.ip.zstaticcdn.com | bj-ct-v6.ip.zstaticcdn.com |
| 天津 | tj-cu-v4.ip.zstaticcdn.com | tj-cu-v6.ip.zstaticcdn.com | tj-cm-v4.ip.zstaticcdn.com | tj-cm-v6.ip.zstaticcdn.com | tj-ct-v4.ip.zstaticcdn.com | tj-ct-v6.ip.zstaticcdn.com |
| 上海 | sh-cu-v4.ip.zstaticcdn.com | sh-cu-v6.ip.zstaticcdn.com | sh-cm-v4.ip.zstaticcdn.com | sh-cm-v6.ip.zstaticcdn.com | sh-ct-v4.ip.zstaticcdn.com | sh-ct-v6.ip.zstaticcdn.com |
| 重庆 | cq-cu-v4.ip.zstaticcdn.com | cq-cu-v6.ip.zstaticcdn.com | cq-cm-v4.ip.zstaticcdn.com | cq-cm-v6.ip.zstaticcdn.com | cq-ct-v4.ip.zstaticcdn.com | cq-ct-v6.ip.zstaticcdn.com |

## 教育网节点

| 省份   | 域名              | IPv4            | IPv6                             | 大学             |
| ------ | ----------------- | --------------- | -------------------------------- | ---------------- |
| 河北   | www.hebtu.edu.cn  | 202.206.100.34  | 2001:250:800:1::34               | 河北师范大学     |
| 山西   | www.tyut.edu.cn   | 202.207.240.104 | 2001:250:c01:5000:cacf:f068::    | 太原理工大学     |
| 辽宁   | www.dlut.edu.cn   | 202.118.66.66   | 2001:da8:a800:3::66              | 大连理工大学     |
| 吉林   | www.jlu.edu.cn    | 202.198.16.83   | 2001:da8:b000::80                | 吉林大学         |
| 黑龙江 | www.hit.edu.cn    | 202.118.254.135 | 2001:da8:b800:253::c0a8:3208     | 哈尔滨工业大学   |
| 江苏   | www.nju.edu.cn    | 202.119.32.7    | 2001:da8:1007::9999              | 南京大学         |
| 浙江   | www.hdu.edu.cn    | 210.32.32.181   | 2001:250:6402:106::102:36        | 杭州电子科技大学 |
| 安徽   | www.ustc.edu.cn   | 202.38.64.246   | 2001:da8:d800:642::248           | 中国科学技术大学 |
| 福建   | www.xmu.edu.cn    | 219.229.81.211  | 2001:da8:e800:251c::211          | 厦门大学         |
| 江西   | www.ncu.edu.cn    | 222.204.6.206   | 2001:250:6c00:60::4              | 南昌大学         |
| 山东   | www.sdu.edu.cn    | 202.194.7.118   | 2001:da8:7000:7:202:194:7:118    | 山东大学         |
| 河南   | www.zzu.edu.cn    | 202.196.64.48   | 2001:da8:5000:6c00::47           | 郑州大学         |
| 湖北   | www.whu.edu.cn    | 115.156.123.20  | 2001:250:4001:4::9               | 武汉大学         |
| 湖南   | www.hnu.edu.cn    | 202.197.98.24   | 2001:250:4402:51::9              | 湖南大学         |
| 广东   | www.sysu.edu.cn   | 202.116.64.8    | 2001:250:3002:10::8              | 中山大学         |
| 海南   | www.hainnu.edu.cn | 210.37.8.40     | 2001:250:3800:18::40             | 海南师范大学     |
| 四川   | www.scu.edu.cn    | 202.115.32.43   | 2001:250:2003::43                | 四川大学         |
| 贵州   | www.gzu.edu.cn    | 210.40.12.58    | 2001:250:2c00::60                | 贵州大学         |
| 云南   | www.ynu.edu.cn    | 113.55.13.95    | 2001:250:2800:0:28:0:13:95       | 云南大学         |
| 陕西   | www.xjtu.edu.cn   | 202.117.1.13    | 2001:250:1001:1::ca75:10d        | 西安交通大学     |
| 甘肃   | www.lzu.edu.cn    | 202.201.0.81    | 2001:da8:c000:2::2026            | 兰州大学         |
| 青海   | www.qhu.edu.cn    | 210.27.177.240  | 2001:250:1e01:1::240             | 青海大学         |
| 内蒙古 | www.imu.edu.cn    | 183.175.40.132  | 2001:da8:21d:c101::2             | 内蒙古大学       |
| 广西   | www.gxu.edu.cn    | 210.36.16.35    | 2001:250:3401:1::35              | 广西大学         |
| 西藏   | www.xzmu.edu.cn   | 202.200.16.13   | 2001:da8:4023:16::13             | 西藏民族大学     |
| 宁夏   | www.nxu.edu.cn    | 222.23.220.245  | 2001:250:1c00:1::245             | 宁夏大学         |
| 新疆   | www.xju.edu.cn    | 111.115.76.75   | 2001:250:1800:1997::4            | 新疆大学         |
| 北京   | www.pku.edu.cn    | 162.105.131.160 | 2001:da8:201:1138::a269:8a9e     | 北京大学         |
| 天津   | www.tju.edu.cn    | 202.113.2.198   | 2001:da8:a000:ab23::10           | 天津大学         |
| 上海   | www.sjtu.edu.cn   | 202.120.2.114   | 2001:da8:8000:6181:202:120:2:114 | 上海交通大学     |
| 重庆   | www.cqu.edu.cn    | 202.202.2.6     | 2001:da8:c800:100:caca:206::     | 重庆大学         |
