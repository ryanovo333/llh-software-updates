# llh-software-updates

llh 开发的实验室软件的**版本信息**。

这个仓库里**只有版本号和更新日志**,没有源代码,也不提供软件下载。
软件里的"检查更新"会来读 [`version.json`](version.json),比对一下本地版本,
告诉用户有没有新版本 —— 仅此而已,不会自动下载或安装任何东西。

拿新版本请直接找开发者。

## 当前版本

| 软件 | 版本 |
|---|---|
| 吸附制冷温控采集软件 (Sorption Cooler Control) | v0.7.3 |
| 连接助手 | v0.2 |

完整的更新日志见 [CHANGELOG.md](CHANGELOG.md)。

## `version.json` 的格式

```json
{
  "<组件key>": {
    "name": "显示名称",
    "version": "v0.7.1",
    "notes": "一句话说明这个版本更新了什么"
  }
}
```

组件 key 由软件那边决定,目前是 `main_app`(主软件)和 `assistant`(连接助手)。
以后加新软件就在这里多加一个 key。
