# Clash / Quantumult X 分流规则订阅

自用 / 可分享的分流规则集。支持 **Clash Meta（Mihomo）** 与 **Quantumult X**。

仓库：https://github.com/kimiisme/clash-rules

## 规则列表

| 规则 | 用途 | 建议策略 | Clash | QuanX |
|------|------|----------|-------|-------|
| private | 局域网 / 私有 IP | DIRECT | [rules/](rules/private.txt) | [quanx/](quanx/private.list) |
| reject | 广告与追踪 | REJECT | [rules/](rules/reject.txt) | [quanx/](quanx/reject.list) |
| ibkr-direct | 盈透中国站 | DIRECT | [rules/](rules/ibkr-direct.txt) | [quanx/](quanx/ibkr-direct.list) |
| ibkr | 盈透证券海外 | TRADING | [rules/](rules/ibkr.txt) | [quanx/](quanx/ibkr.list) |
| tos | Thinkorswim / Schwab | TRADING | [rules/](rules/tos.txt) | [quanx/](quanx/tos.list) |
| ai | ChatGPT / Claude 等 | PROXY | [rules/](rules/ai.txt) | [quanx/](quanx/ai.list) |
| telegram | Telegram | PROXY | [rules/](rules/telegram.txt) | [quanx/](quanx/telegram.list) |
| apple | Apple / iCloud | DIRECT | [rules/](rules/apple.txt) | [quanx/](quanx/apple.list) |
| google | Google / YouTube | PROXY | [rules/](rules/google.txt) | [quanx/](quanx/google.list) |
| gfw | 常见被墙站点 | PROXY | [rules/](rules/gfw.txt) | [quanx/](quanx/gfw.list) |
| direct | 国内常用域名 | DIRECT | [rules/](rules/direct.txt) | [quanx/](quanx/direct.list) |
| proxy | 常见海外服务 | PROXY | [rules/](rules/proxy.txt) | [quanx/](quanx/proxy.list) |

## Clash Meta 订阅

`rule-providers`：`type: http`，`behavior: classical`，`format: text`

```text
https://raw.githubusercontent.com/kimiisme/clash-rules/main/rules/private.txt
https://raw.githubusercontent.com/kimiisme/clash-rules/main/rules/reject.txt
https://raw.githubusercontent.com/kimiisme/clash-rules/main/rules/ibkr-direct.txt
https://raw.githubusercontent.com/kimiisme/clash-rules/main/rules/ibkr.txt
https://raw.githubusercontent.com/kimiisme/clash-rules/main/rules/tos.txt
https://raw.githubusercontent.com/kimiisme/clash-rules/main/rules/ai.txt
https://raw.githubusercontent.com/kimiisme/clash-rules/main/rules/telegram.txt
https://raw.githubusercontent.com/kimiisme/clash-rules/main/rules/apple.txt
https://raw.githubusercontent.com/kimiisme/clash-rules/main/rules/google.txt
https://raw.githubusercontent.com/kimiisme/clash-rules/main/rules/gfw.txt
https://raw.githubusercontent.com/kimiisme/clash-rules/main/rules/direct.txt
https://raw.githubusercontent.com/kimiisme/clash-rules/main/rules/proxy.txt
```

完整示例：[examples/clash-meta.yaml](examples/clash-meta.yaml)

## Quantumult X 订阅

在配置的 `[filter_remote]` 中添加（可用 `force-policy` 指定策略组）：

```text
https://raw.githubusercontent.com/kimiisme/clash-rules/main/quanx/private.list, tag=Private, force-policy=direct, update-interval=86400, opt-parser=true, enabled=true
https://raw.githubusercontent.com/kimiisme/clash-rules/main/quanx/reject.list, tag=Reject, force-policy=reject, update-interval=86400, opt-parser=true, enabled=true
https://raw.githubusercontent.com/kimiisme/clash-rules/main/quanx/ibkr-direct.list, tag=IBKR-CN, force-policy=direct, update-interval=86400, opt-parser=true, enabled=true
https://raw.githubusercontent.com/kimiisme/clash-rules/main/quanx/ibkr.list, tag=IBKR, force-policy=TRADING, update-interval=86400, opt-parser=true, enabled=true
https://raw.githubusercontent.com/kimiisme/clash-rules/main/quanx/tos.list, tag=TOS, force-policy=TRADING, update-interval=86400, opt-parser=true, enabled=true
https://raw.githubusercontent.com/kimiisme/clash-rules/main/quanx/ai.list, tag=AI, force-policy=PROXY, update-interval=86400, opt-parser=true, enabled=true
https://raw.githubusercontent.com/kimiisme/clash-rules/main/quanx/telegram.list, tag=Telegram, force-policy=PROXY, update-interval=86400, opt-parser=true, enabled=true
https://raw.githubusercontent.com/kimiisme/clash-rules/main/quanx/apple.list, tag=Apple, force-policy=direct, update-interval=86400, opt-parser=true, enabled=true
https://raw.githubusercontent.com/kimiisme/clash-rules/main/quanx/google.list, tag=Google, force-policy=PROXY, update-interval=86400, opt-parser=true, enabled=true
https://raw.githubusercontent.com/kimiisme/clash-rules/main/quanx/gfw.list, tag=GFW, force-policy=PROXY, update-interval=86400, opt-parser=true, enabled=true
https://raw.githubusercontent.com/kimiisme/clash-rules/main/quanx/direct.list, tag=Direct, force-policy=direct, update-interval=86400, opt-parser=true, enabled=true
https://raw.githubusercontent.com/kimiisme/clash-rules/main/quanx/proxy.list, tag=Proxy, force-policy=PROXY, update-interval=86400, opt-parser=true, enabled=true
```

完整示例：[examples/quantumultx.conf](examples/quantumultx.conf)

请先在 `[policy]` 里建好 `PROXY`、`TRADING` 等策略组；`force-policy` 里的名字要和策略组一致。

## 维护

1. 优先改 `rules/*.txt`（Clash 源），再同步生成 `quanx/*.list`。
2. `git push` 后客户端按 `update-interval` / `interval` 自动更新。
3. `reject` 关键词较宽，误杀时删掉对应行或加到 `direct`。

## License

MIT
