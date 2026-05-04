# Bilibili PCDN Rules for Nikki / Mihomo

B 站 PCDN / MCDN / P2P CDN 屏蔽规则。

用途：用于 OpenWrt Nikki / Mihomo / OpenClash 的 rule-provider。

## Raw 地址

```text
https://raw.githubusercontent.com/answerzx/bilibili-pcdn-rules/main/bilibili-pcdn.yaml
```

## 建议策略

建议将该规则集指向 `REJECT` 或 `REJECT-DROP`。

## 当前包含

- `mcdn.bilivideo.cn`
- `mcdn.bilivideo.com`
- `szbdyd.com`
- `v1d.szbdyd.com`
- `pcdn.biliapi.net`
- `ks-sh-tracker-02.biliapi.net`
- `*-pcdn-*.biliapi.net`
- `*pcdn*.biliapi.net`
- `stun*.chat.bilibili.com`
- `*-p2p-*.chat.bilibili.com`
- 社区规则中出现的 8 条 IPv4 tracker IP
- 社区规则中出现的 2 条 IPv6 tracker IP

## 刻意不包含

为避免误伤正常视频播放，暂不屏蔽：

- `*.bilivideo.com`
- `cn-*.bilivideo.com`
- `upos-sz-mirror*.bilivideo.com`
- 整个 `biliapi.net`
