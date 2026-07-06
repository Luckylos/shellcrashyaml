# shellcrashyaml

基于当前 ShellCrash 实际需求整理的一份 **Mihomo / 订阅转换后端模板 YAML**。

## 文件

- `subconverter-shellcrash-needs.yaml`：标准版，包含 `🤖 AI 服务`、`📲 Telegram`、`🎯 国内流量` 三类独立分流
- `subconverter-shellcrash-needs-ai-tg-only.yaml`：额外版，仅单独分离 `🤖 AI 服务` 与 `📲 Telegram`，不单独划分中国大陆流量

## 设计目标

- 适配 **订阅转换后端** 使用，不直接内置具体节点
- 保留当前 ShellCrash 的核心路由需求
- 风格参考 `666OS/YYDS` 的 `Pro_cn.yaml`
- 地区节点支持“手动指定优先，失效后同地区自动回退”
- 未匹配到已知地区关键字的节点统一归入 `其余地区`

## 当前策略

### 标准版 `subconverter-shellcrash-needs.yaml`

- `🤖 AI 服务`：美国优先
- `📲 Telegram`：新加坡优先
- `🎯 国内流量`：默认直连
- 其他流量：走 `🚀 节点选择`
- 未命中港/日/新/美筛选规则的节点：归入 `其余地区`
- 私网/本地地址：强制直连
- DNS：`fake-ip + 0.0.0.0:1053 + 阿里/腾讯 DoH`

### 额外版 `subconverter-shellcrash-needs-ai-tg-only.yaml`

- `🤖 AI 服务`：美国优先
- `📲 Telegram`：新加坡优先
- 不单独划分中国大陆流量
- 其他流量：统一走 `🚀 节点选择`
- 未命中港/日/新/美筛选规则的节点：归入 `其余地区`
- 私网/本地地址：强制直连
- DNS：`fake-ip + 0.0.0.0:1053 + 阿里/腾讯 DoH`

## 说明

这份 YAML 主要表达：

1. 策略组结构
2. 区域分组筛选规则
3. 规则集与路由意图
4. DNS 行为

具体节点应由订阅转换后端注入，或由上游订阅提供。

## 参考

- https://raw.githubusercontent.com/666OS/YYDS/refs/heads/main/mihomo/config/cn/Pro_cn.yaml
