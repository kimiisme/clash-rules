# Clash 分流规则订阅

自用 / 可分享的 Clash Meta（Mihomo）规则集。推送到 GitHub 后，用 raw 链接在客户端里订阅即可。

## 规则列表

| 文件 | 用途 | 建议策略 |
|------|------|----------|
| [rules/private.txt](rules/private.txt) | 局域网 / 私有 IP | DIRECT |
| [rules/reject.txt](rules/reject.txt) | 广告与追踪 | REJECT |
| [rules/ai.txt](rules/ai.txt) | ChatGPT / Claude / Gemini 等 | PROXY |
| [rules/telegram.txt](rules/telegram.txt) | Telegram | PROXY |
| [rules/apple.txt](rules/apple.txt) | Apple / iCloud | DIRECT 或 PROXY |
| [rules/google.txt](rules/google.txt) | Google / YouTube | PROXY |
| [rules/gfw.txt](rules/gfw.txt) | 常见被墙站点 | PROXY |
| [rules/direct.txt](rules/direct.txt) | 国内常用域名 | DIRECT |
| [rules/proxy.txt](rules/proxy.txt) | 常见海外服务 | PROXY |

## 订阅地址

把下面链接填进 Clash Meta 的 `rule-providers`（`type: http`，`behavior: classical`，`format: text`）：

```text
https://raw.githubusercontent.com/kimiisme/clash-rules/main/rules/private.txt
https://raw.githubusercontent.com/kimiisme/clash-rules/main/rules/reject.txt
https://raw.githubusercontent.com/kimiisme/clash-rules/main/rules/ai.txt
https://raw.githubusercontent.com/kimiisme/clash-rules/main/rules/telegram.txt
https://raw.githubusercontent.com/kimiisme/clash-rules/main/rules/apple.txt
https://raw.githubusercontent.com/kimiisme/clash-rules/main/rules/google.txt
https://raw.githubusercontent.com/kimiisme/clash-rules/main/rules/gfw.txt
https://raw.githubusercontent.com/kimiisme/clash-rules/main/rules/direct.txt
https://raw.githubusercontent.com/kimiisme/clash-rules/main/rules/proxy.txt
```

完整示例见 [examples/clash-meta.yaml](examples/clash-meta.yaml)。

## 怎么用

1. 在客户端配置里加上对应的 `rule-providers` 和 `rules`（可直接参考示例）。
2. 需要改规则时，编辑 `rules/*.txt`，然后 `git push`。
3. 客户端按 `interval`（示例为 86400 秒）自动更新；也可手动「更新规则」。

规则格式示例：

```text
DOMAIN-SUFFIX,example.com
DOMAIN-KEYWORD,ads
IP-CIDR,10.0.0.0/8,no-resolve
```

## 维护

- 只改你真正需要的域名，避免盲目堆规则。
- `reject` 里关键词较宽，若误杀可删掉对应行或把该域名加到 `direct`。
- 国内 / 海外策略以你的实际网络为准，示例分组可按需改名、增减。

## License

MIT
