# Clash-RuleSet-Mod

Private Rules for Clash Meta — 域名与 IP 分家处理，按代理组合并规则集。

## 目录结构

```
├── rules/
│   ├── domain/                # 域名规则源文件（可单独编辑）
│   │   ├── AdBlock.yaml       #   广告拦截（清理版）
│   │   ├── Common.yaml        #   常用服务合集（Google+GitHub+Telegram+Twitter+Spotify）
│   │   ├── Custom.yaml        #   自定义个人规则
│   │   ├── Gemini.yaml
│   │   ├── Microsoft.yaml
│   │   ├── ...
│   │
│   └── mrs/                   # 预编译 .mrs 规则集（仅 5 个）
│       ├── AdBlock.mrs
│       ├── Common.mrs
│       ├── Custom.mrs
│       ├── Gemini.mrs
│       └── Microsoft.mrs
│
└── config-example.yaml
```

## 合并逻辑

| RULE-SET | 代理组 | 来源 |
|----------|--------|------|
| AdBlock | REJECT | AdBlock.yaml |
| Custom | 常用服务 | Custom.yaml |
| Common | 常用服务 | Google + GitHub + Telegram + Twitter + Spotify |
| Gemini | Gemini | Gemini.yaml |
| Microsoft | 微软服务 | Microsoft.yaml |

## 本地编译

```bash
for name in AdBlock Custom Common Gemini Microsoft; do
  mihomo convert-ruleset domain yaml "rules/domain/${name}.yaml" "rules/mrs/${name}.mrs"
done
```
