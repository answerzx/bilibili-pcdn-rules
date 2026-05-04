# Bilibili PCDN Rules for Nikki / Mihomo

保守版 B 站 PCDN / MCDN / P2P CDN 屏蔽规则。

用途：用于 OpenWrt Nikki / Mihomo / OpenClash 的 rule-provider。

## Raw 地址

```text
https://raw.githubusercontent.com/answerzx/bilibili-pcdn-rules/main/bilibili-pcdn.yaml
```

## 建议策略

建议将该规则集指向 `REJECT` 或 `REJECT-DROP`。

## 说明

规则刻意不屏蔽以下正常 CDN，避免影响播放：

- `*.bilivideo.com`
- `cn-*.bilivideo.com`
- `upos-sz-mirror*.bilivideo.com`
- 整个 `biliapi.net`

如果直播互动/聊天室异常，可尝试注释 `chat.bilibili.com` 相关规则。
