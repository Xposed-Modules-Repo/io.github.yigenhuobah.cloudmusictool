# 云音乐工具箱 (CloudMusicTool)

网易云音乐 Android 客户端的 LSPosed 体验优化模块：去广告、精简界面、收敛弹窗、隐私加固、ABTest 实验控制。

## 2.0.0 架构升级

- **Profile / MountSpec / MountResolver**：134 个挂载点集中到 `Profile9608`，支持多候选类名、参数/返回类型校验、DexKit 结构/锚点兜底。
- **版本门禁**：versionCode + `ProfileRegistry`；未适配版本按 `allowUnsupported` best-effort，按功能降级。
- **健康度**：状态卡显示 installed/expected，critical 挂载点失败时标记降级。
- **check-mounts v2**：从 Profile 自动生成，断言 versionCode、类/方法、参数/返回类型。

## 功能

**广告拦截（默认开启）**：开屏、运营弹窗、更新弹窗、首页信息流、评论区、播放页、音频贴片/播客、广告上报与外跳、搜索广告、广告预加载。

**界面净化（默认开启）**：首页模块、顶部频道真实删除、底部导航、启动延迟、引导气泡/评分/VIP 弹窗、自动播放、头像挂件、播放页提示、搜索热词、播客/AI DJ、小组件/推送、歌词页推广。

**隐私（默认关闭）**：OAID、日志写盘、启动任务黑名单、APM、统计上报、剪贴板、启动任务编排。

**实验（默认只读）**：只读观测 ABTest 命中；22 个体验 key 可单 key 强开；黑名单 key 禁止；一键恢复。

## 兼容性

| 项 | 值 |
|---|---|
| 目标应用 | `com.netease.cloudmusic` 9.6.08 |
| Xposed API | libxposed API 102 |
| 系统要求 | Android 10+（minSdk 29） |

## 已知限制

- 仅承诺 9.6.08；新增版本 = 新增 Profile 分片 + 跑 check-mounts，不承诺任意版本自动兼容。
- UI-04 侧栏抽屉暂不支持。
- 部分新功能已注册但未自然触发验证；实验强开可能导致界面异常，可一键恢复默认。
- 不触碰 VIP/付费/版权/地区、青少年模式、登录/Cookie/风控。

源码与完整文档：<https://github.com/yigenhuobah/cloudmusictool>

仅供学习研究和个人设备使用，与网易官方无任何关联。
