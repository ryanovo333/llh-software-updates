# llh 软件更新信息

这里只放**版本号和更新说明**，不放源代码，也不提供下载。
各个软件的「关于 → 检查更新」都来读这个仓库，用来判断有没有新版本。

## 当前版本

| 软件 | 版本 | 本次更新 | 详细日志 |
|---|---|---|---|
| 吸附制冷温控采集软件 | **v1.3.0** | 新增 macOS 与 Windows 双平台支持；主软件与连接助手统一版本号；支持 GitHub 云端双端打包 | [查看](CHANGELOG.md#吸附制冷温控采集软件-sorption-cooler-control) |
| 连接助手 | **v1.3.0** | 与主软件统一版本为 v1.3.0；新增 macOS 网卡静态IP/DHCP配置、跨平台诊断与串口排查 | [查看](CHANGELOG.md#连接助手) |
| 项目时间表 | **v0.6.0** | 新增 macOS 与 Windows 双平台支持；适配原生菜单与快捷键；跨平台路径兼容；补全高清图标 | [查看](CHANGELOG.md#项目时间表-project-timetable) |
| 尼康 NEF 批量 HDR 转档降噪工具 | **v1.1.0** | RAW基础去灰强化与原厂镜头矫正；光影色彩7大滑块；Auto Tone智能显影；LrC暗黑UI | [查看](CHANGELOG.md#尼康-nef-批量-hdr-转档降噪工具-nikon-nef-hdr-converter) |

> 上表由人工维护，机器读的是下面那份 `version.json`。改版本时两处都要改。

## 软件怎么找到自己的版本

所有软件读同一个文件，靠各自的 **key** 取自己那一段：

```
https://raw.githubusercontent.com/ryanovo333/llh-software-updates/main/version.json
```

```json
{
  "main_app":                { "name": "吸附制冷温控采集软件",     "version": "v0.9.7", "notes": "..." },
  "assistant":               { "name": "连接助手",                 "version": "v0.3.3", "notes": "..." },
  "project_timetable":       { "name": "项目时间表",               "version": "v0.4.0", "notes": "..." },
  "nikon_nef_hdr_converter": { "name": "尼康 NEF 批量 HDR 转档降噪工具", "version": "v1.0.0", "notes": "..." }
}
```

| key | 对应软件 |
|---|---|
| `main_app` | 吸附制冷温控采集软件 |
| `assistant` | 连接助手 |
| `project_timetable` | 项目时间表 |
| `nikon_nef_hdr_converter` | 尼康 NEF 批量 HDR 转档降噪工具 |

一个文件而不是每个软件一个文件，是因为检查更新只需要一次请求；
文件本身也就几百字节，再多几个软件也无所谓。

版本号带 `v` 前缀，比较前先剥掉，然后**逐段按数字比**
（`1.2.10` 比 `1.2.9` 新，按字符串比会得出相反的结论）。

## 加一个新软件

1. 在 `version.json` 里加一段，key 用小写加下划线
2. 在 `CHANGELOG.md` 顶部加一个 `## 软件名` 小节
3. 在本文件的表格里加一行
4. 软件那边把 key 和上面那个 raw 地址写进常量

## 发新版的顺序

1. 改软件源码里的版本号常量
2. 改这里的 `version.json`、`CHANGELOG.md` 和上面的表格，推送
3. 打包，私有仓库提交并打 tag

先推这里再打包，是为了避免出现「软件已经是新版、但检查更新说它落后」的尴尬。
