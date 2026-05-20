# 3x-ui 网站屏蔽管理 TUI (x-ui-website-blocker)

`block.sh` —— 针对 [3x-ui](https://github.com/MHSanaei/3x-ui) 面板的网站/流量屏蔽管理工具，交互式菜单（TUI）。

## 用途

直接读写 3x-ui 的数据库 `x-ui.db`，向 Xray 的 routing 规则注入「黑洞（blackhole）」规则，按分类一键屏蔽对应网站/流量，无需手工编辑 JSON。

## 分类（可按需开启/关闭）

| 分类 | 说明 |
|---|---|
| speedtest | 测速网站（Speedtest / Fast / Cloudflare 等）|
| ipcheck | IP 检测站 |
| ads | 广告 |
| adult | 成人内容 |
| social | 社交 |
| tiktok | TikTok |
| streaming | 流媒体 |
| ai | AI 服务 |
| gambling | 博彩 |
| crypto | 加密货币 |

此外支持添加**自定义屏蔽域名**（`custom-block` 标签）。

## 使用方法

```bash
sudo bash block.sh
```

进入菜单后按分类切换开关，保存后写回数据库。可通过环境变量指定数据库路径：

```bash
XUI_DB=/etc/x-ui/x-ui.db sudo bash block.sh
```

## 依赖与环境

- 权限：**必须 root**
- 依赖：`jq`、`sqlite3`（脚本会尝试自动安装）
- 前置：已安装 3x-ui，且存在数据库 `/etc/x-ui/x-ui.db`

## 注意事项

- 直接修改面板数据库，**操作前建议先备份** `x-ui.db`
- 修改后通常需要重启 / 让 3x-ui 重载配置才生效
