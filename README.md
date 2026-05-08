! ====================================================
! Bilibili 首页 - 优化重构版（极简毛玻璃风格）
! ====================================================

! ---------- 1. 隐藏广告、推广、无用杂项及页脚 ----------
! 使用逗号分隔合并隐藏规则，提升匹配效率
www.bilibili.com##.bili-header__banner, .recommended-swipe, .floor-single-card, .adblock-tips, .act-now.activity-m-v1, .recommend-list-v1, footer, .bili-footer, .footer

! ---------- 2. 修复外边距穿透 (BFC) ----------
www.bilibili.com##.large-header:style(border-top: 1px solid transparent !important;)

! ---------- 3. 主导航栏 & 频道栏 毛玻璃效果 ----------
! 合并 background, filter 和 border，减少注入次数
www.bilibili.com##.bili-header__bar, .header-channel:style(background: rgba(15, 15, 15, 0.7) !important; backdrop-filter: blur(12px) !important; border-bottom: 1px solid rgba(255, 255, 255, 0.08) !important;)

! ---------- 4. 修复频道栏被导航栏遮挡 ----------
www.bilibili.com##.bili-header__channel:style(margin-top: 60px !important;)

! ---------- 5. 隐藏全局滚动条 ----------
www.bilibili.com##html, body:style(scrollbar-width: none !important;)
www.bilibili.com##html::-webkit-scrollbar, body::-webkit-scrollbar:style(display: none !important;)

! ---------- 6. 悬浮窗：纯色半透明背景 ----------
! 移除了暴力的 * 选择器，改为仅调整父级，并确保内容区透明
www.bilibili.com##.v-popover:style(background: rgba(0, 0, 0, 0.8) !important; border-radius: 16px !important; border: 1px solid rgba(255, 255, 255, 0.1) !important; box-shadow: 0 8px 20px rgba(0, 0, 0, 0.3) !important;)
www.bilibili.com##.v-popover-content:style(background: transparent !important;)

! ---------- 7. 修复首页卡片网格顶部偏移 ----------
! 方案A：不使用 margin，改用给整个 Feed 容器加 padding（推荐，不破坏 Grid）
www.bilibili.com##.container:style(padding-top: 40px !important;)
! （如果方案A无效，使用方案B：仅针对前两排的元素加 margin，假设一排5个卡片）
! www.bilibili.com##.feed-card:nth-child(-n+10):style(margin-top: 40px !important;)
www.bilibili.com##.roll-btn.primary-btn:style(margin-top: 40px !important;)
