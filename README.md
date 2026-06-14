# shellcrashyaml

基于当前 ShellCrash 实际需求整理的一份 **Mihomo / 订阅转换后端模板 YAML**。

## 文件

- `subconverter-shellcrash-needs.yaml`

## 设计目标

- 适配 **订阅转换后端** 使用，不直接内置具体节点
- 保留当前 ShellCrash 的核心路由需求
- 风格参考 `666OS/YYDS` 的 `Pro_cn.yaml`

## 当前策略

- `🤖 AI 服务`：美国优先
- `📲 Telegram`：新加坡优先
- `🎯 国内流量`：默认直连
- 其他流量：走 `🚀 节点选择`
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
