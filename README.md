# electricity-dashboard

匿名用电数据的静态看板镜像。

- 数据源：Cloudflare Worker 每小时采集结算（D1 存储）
- 本仓库由 GitHub Actions 每小时 :30 自动拉取 `/dashboard` 接口，经**字段白名单**过滤后提交 `data.json` 快照
- GitHub Pages 托管本仓库：看板首屏读取同源 `data.json`；更早历史的翻页/下钻回退到 Worker API（大陆不可达时优雅降级）
- 快照仅含匿名用电统计（时间/电量/余额/充值/状态），**不含**设备号、密钥或个人身份信息
- 提交身份为 `github-actions[bot]`（临时令牌，无长期凭据）
- `robots.txt` + `noindex` 阻止搜索引擎收录
