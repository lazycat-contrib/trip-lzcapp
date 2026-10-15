# Trip - LazyCat App

[Trip](https://github.com/itskovacs/trip)（极简 POI 地图追踪与行程规划）的懒猫微服（LazyCat）打包。

## 模式

- **镜像模式（mirror）**：`ghcr.io/itskovacs/trip` 镜像经 `ghcr.1ms.run` 加速器拉取，`require_digest_match: true` 校验镜像内容与上游一致。
- **自动跟随上游**：每日检查上游 semver tag，发现新版本自动更新版本号与镜像、构建 LPK、发布商店。
- **喵喵商店发布**：仅私有商店（MiaoMiao private store），不发布官方商店。

## 说明

- 单容器 FastAPI + SQLite（数据卷 `/lzcapp/var/trip:/app/storage`）
- 上游镜像 tag 混用两段式（`1`、`1.50`）与三段式（`1.50.1`）；Action 配置将两段式映射为三段 SemVer（`1.50` → `1.50.0`）
- 首次打开创建账号（可选 OIDC，参考上游配置文档）
- 地图瓦片加载公网（OpenStreetMap 等由前端按需拉取）

## 所需 Secrets

| Secret | 说明 |
| --- | --- |
| `APPSTORE_URL` / `APPSTORE_TOKEN` | 喵喵商店 API 地址与发布令牌 |
| `APP_ID` | 可选 |
| `PRIVATE_STORE_GROUP_CODES` | 可选，私有分组码 |

## 许可

MIT（上游）
