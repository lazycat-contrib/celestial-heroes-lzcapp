# celestial-heroes-lzcapp

[星阵归途 / Celestial Heroes](https://github.com/coracoo/Celestial) 的 LazyCat LPK 打包 —— 3D 柏青哥娘化武将弹珠游戏（纯静态站）。

## 形态

- 纯静态：Vite 构建 `dist/`（含 three.js + Rapier 物理引擎）
- 发布目标：**仅喵喵商店**
  - 产物约 300+ MB，绝大部分是立绘分层素材（`art/layers` 218 个 PNG）
  - 该体积不适合走官方商店上传与审核流程，因此只发社区商店
- 仅 PC 平台：`unsupported_platforms: [ios, android, tvos]`
- 存档导出/导入接入文件选择器拦截

## 版本策略

上游没有 release tag 和镜像，只有 main 分支，按每日 patch 递增自动跟版。

## 结构

- `package.yml` — LPK v2 包元数据 + 平台限制
- `lzc-manifest.yml` — 静态文件直出 + 文件选择器注入
- `lzc-build.yml` — `build.sh` + `contentdir: ./dist`
- `build.sh` — 拉上游 main → `npm ci && npm run build` → 拷贝 `dist/`
- `.github/lazycat-action.yml` — 仅私有商店
- `.github/workflows/lazycat.yml` — 每日构建 + 发布喵喵商店
