哔哩哔哩首页清爽化规则集

> 基于 uBlock Origin 的静态规则，移除广告、推广卡片、杂乱模块，并注入现代化样式，让 B 站首页回归纯粹的视频推荐体验。

## ✨ 特性

- 隐藏顶部横幅、轮播图等干扰元素
- 屏蔽“国创”“课堂”“直播”“活动”“番剧”等分区推广卡片（仅保留普通视频卡片）
- 重构顶部导航栏：毛玻璃效果、精简冗余入口（保留收藏/历史/消息/动态）
- 滚动条隐藏

## 📦 使用条件

- 浏览器已安装 **uBlock Origin** 扩展（[官方安装地址](https://ublockorigin.com/)）
- 使用深色模式
- 仅适用于 **Bilibili 桌面版网页**（`www.bilibili.com`），主要作用于首页（`/`）
- 规则基于当前页面结构编写（2026年5月），如遇页面改版可能需要微调选择器

## 🎯 生效作用域

- **域名**：`www.bilibili.com`
- **影响的组件**：
  - 顶部导航栏（毛玻璃背景）
  - 首页轮播图（隐藏）
  - 推荐流中的分区卡片（隐藏）
  - 悬浮窗（背景、位置、圆角）
  - 滚动条（可选隐藏）

## 🙏 致谢

感谢 [uBlock Origin](https://github.com/gorhill/uBlock) 项目及其开发者，提供了强大的内容过滤与样式注入能力。

---

## 📝 最终规则（请手工粘贴至 uBlock Origin 自定义静态规则）

> 以下为完整规则。请复制全部内容，打开 uBlock Origin 仪表盘 → “自定义静态规则” → 粘贴 → 应用更改。

```plaintext
! ====================================================
! Bilibili 首页 - 最终稳定版（含卡片偏移修复）
! ====================================================

! ---------- 1. 隐藏顶部横幅 ----------
www.bilibili.com##.bili-header__banner


! ---------- 3. 隐藏轮播图 ----------
www.bilibili.com##.recommended-swipe

! ---------- 4. 屏蔽所有分区推广卡片 ----------
www.bilibili.com##.floor-single-card

! ---------- 5. 隐藏其他杂项 ----------
www.bilibili.com##.adblock-tips
www.bilibili.com##.act-now.activity-m-v1
www.bilibili.com##.recommend-list-v1
www.bilibili.com##footer
www.bilibili.com##.bili-footer
www.bilibili.com##.footer

! ---------- 6. 修复外边距穿透 ----------
www.bilibili.com##.large-header:style(border-top: 1px solid transparent !important;)

! ---------- 7. 主导航栏毛玻璃 ----------
www.bilibili.com##.bili-header__bar:style(background: rgba(15, 15, 15, 0.7) !important;)
www.bilibili.com##.bili-header__bar:style(backdrop-filter: blur(12px) !important;)
www.bilibili.com##.bili-header__bar:style(border-bottom: 1px solid rgba(255, 255, 255, 0.08) !important;)

! ---------- 8. 滚动后固定频道栏毛玻璃 ----------
www.bilibili.com##.header-channel:style(background: rgba(15, 15, 15, 0.7) !important;)
www.bilibili.com##.header-channel:style(backdrop-filter: blur(12px) !important;)
www.bilibili.com##.header-channel:style(border-bottom: 1px solid rgba(255, 255, 255, 0.08) !important;)


! ---------- 9. 修复频道栏被导航栏遮挡 ----------
www.bilibili.com##.bili-header__channel:style(margin-top: 60px !important;)

! ---------- 10. 隐藏滚动条（可选） ----------
www.bilibili.com##html:style(scrollbar-width: none !important;)
www.bilibili.com##body:style(scrollbar-width: none !important;)
www.bilibili.com##html::-webkit-scrollbar:style(display: none !important;)
www.bilibili.com##body::-webkit-scrollbar:style(display: none !important;)

! ---------- 11. 悬浮窗：纯色半透明背景 ----------
www.bilibili.com##.v-popover:style(background: rgba(0, 0, 0, 0.8) !important;)
www.bilibili.com##.v-popover:style(border-radius: 16px !important;)
www.bilibili.com##.v-popover:style(border: 1px solid rgba(255, 255, 255, 0.1) !important;)
www.bilibili.com##.v-popover:style(box-shadow: 0 8px 20px rgba(0, 0, 0, 0.3) !important;)
! 清除所有子元素的背景，防止覆盖
www.bilibili.com##.v-popover *:style(background: transparent !important; background-color: transparent !important;)
www.bilibili.com##.v-popover-content:style(background: transparent !important;)

! 修复前几个个卡片 margin-top 为0导致的偏移问题
www.bilibili.com##.feed-card:style(margin-top: 40px !important;)
www.bilibili.com##.roll-btn.primary-btn:style(margin-top: 40px !important;)

