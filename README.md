# AECAEA 谱面索引仓（meta）

本仓只放**索引与安装包**，不放谱面本体：

| 文件 | 用途 |
|---|---|
| `enc-manifest.json` | 全量谱面清单：明文名 / 大小 / MD5 / 密文名，以及每条记录所属分片仓 `part` |
| `latest.json` | App 内置更新清单（versionCode / versionName / apk 路径） |
| `release/app-release.apk` | 当前发布包 |
| `README.md` | 本说明 |

谱面密文按体积分片存放在 `aeca-charts-1`、`aeca-charts-2` 两个仓的 `enc/` 目录，
清单顶层 `parts` 数组给出分片仓名（顺序对应 `part` 从 1 开始）。
单个 GitHub 仓超过 50MB 会被 jsDelivr 拒绝（`Package size exceeded the configured limit of 50 MB`），
分片后每仓约 25MB，留出后续新增谱面的余量。
