# Bilibili PCDN Rules for Nikki / Mihomo

B 站 PCDN / MCDN / P2P CDN 屏蔽规则。

适用于：

- OpenWrt Nikki
- Mihomo / Clash.Meta
- OpenClash
- 其他支持 `classical + text` 规则集的客户端

## 正确规则地址

请使用这个：

```text
https://raw.githubusercontent.com/answerzx/bilibili-pcdn-rules/main/bilibili-pcdn-classical.list
```

## 正确格式

这是 **classical text list**，不是 YAML payload。

对应配置：

```yaml
behavior: classical
format: text
```

如果你的配置里有类似锚点：

```yaml
rule-anchor:
  ip: &ip {type: http, interval: 86400, behavior: ipcidr, format: mrs}
  domain: &domain {type: http, interval: 86400, behavior: domain, format: mrs}
  class: &class {type: http, interval: 86400, behavior: classical, format: text}
```

那本规则集应该使用 `*class`。

## Nikki / Mihomo 引用示例

```yaml
rule-providers:
  bilibili-pcdn:
    <<: *class
    url: "https://raw.githubusercontent.com/answerzx/bilibili-pcdn-rules/main/bilibili-pcdn-classical.list"
    path: ./ruleset/bilibili-pcdn-classical.list
```

规则引用：

```yaml
rules:
  - RULE-SET,bilibili-pcdn,REJECT
```

如果你的客户端支持，也可以使用：

```yaml
rules:
  - RULE-SET,bilibili-pcdn,REJECT-DROP
```

## 文件内容格式示例

```text
# Bilibili PCDN 补充列表

# B 站 MCDN / PCDN 视频节点
DOMAIN-SUFFIX,mcdn.bilivideo.cn
DOMAIN-SUFFIX,mcdn.bilivideo.com
DOMAIN-SUFFIX,szbdyd.com
DOMAIN,v1d.szbdyd.com

# B 站 PCDN Tracker / 控制域名
DOMAIN,pcdn.biliapi.net
DOMAIN,ks-sh-tracker-02.biliapi.net
```

注意：

- 文件后缀是 `.list`
- 文件格式是纯文本
- 没有 `payload:`
- 没有 YAML 数组前缀 `-`
- 每条规则单独一行

## 当前包含

域名规则：

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

IP 规则：

- 社区规则中出现的 8 条 IPv4 tracker IP
- 社区规则中出现的 2 条 IPv6 tracker IP

## 刻意不包含

为避免误伤正常视频播放，暂不屏蔽：

- `*.bilivideo.com`
- `cn-*.bilivideo.com`
- `upos-sz-mirror*.bilivideo.com`
- 整个 `biliapi.net`

## 历史文件说明

仓库中可能保留旧文件用于兼容或追溯，但推荐使用：

```text
bilibili-pcdn-classical.list
```

不要优先使用旧的 `.yaml` 版本。
