# ycy-sync

异次元:云同步（com.wsw.cospsync）的版本更新信息仓库。

## 文件

- `update.json`：App 启动时读取的版本信息
- `RELEASE.md`：发版步骤模板

## update.json 字段

| 字段 | 说明 |
|---|---|
| versionCode | 必须大于当前安装版本才会提示 |
| versionName | 展示用版本号 |
| force | 是否强制更新，当前固定 false |
| title | 弹窗标题 |
| changelog | 更新内容，`\n` 换行 |
| githubUrl | GitHub Release APK 直链 |
| lanzouUrl | 蓝奏云备用链接 |
| publishedAt | 发布日期 |

## 读取地址

App 会依次尝试：

1. `https://raw.githubusercontent.com/MagicalLogic/ycy-sync/main/update.json`
2. `https://cdn.jsdelivr.net/gh/MagicalLogic/ycy-sync@main/update.json`

## 发版流程

1. 构建新 APK
2. GitHub 建 Release，tag 如 `v1028`，上传 APK
3. 蓝奏云上传同一 APK，复制分享链接
4. 修改 `update.json`：
   - `versionCode` 改成新版本
   - `versionName`
   - `changelog`
   - `githubUrl` 填 Release APK 直链
   - `lanzouUrl` 填蓝奏云链接
   - `publishedAt`
5. 提交 `update.json`
6. 旧版 App 下次启动即可看到更新提示

## 注意

- `versionCode` 必须严格大于旧版
- GitHub Release 直链格式：
  `https://github.com/MagicalLogic/ycy-sync/releases/download/v1028/ycy-sync-v1028.apk`
- 蓝奏云链接可能带提取码，App 只负责打开链接
- 仓库必须是 Public，raw 地址才能匿名读取
