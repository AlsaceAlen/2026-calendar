<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>Vollure Rose 2026年度行事历</title>
<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  font-family: "PingFang SC", "Microsoft YaHei", sans-serif;
}
body {
  background: #faf8fd;
  padding: 0;
  position: relative;
  overflow-x: hidden;
  min-height: 100vh;
  transition: all 0.3s ease;
}

/* 基础风格变量 - 系统风格 */
:root {
  --bg-main: #faf8fd;
  --card-bg: #ffffff;
  --title-color: #444;
  --border-color: #f0ebe7;
  --btn-primary: #e99da9;
  --btn-secondary: #fce4e8;
  --text-secondary: #999;
  --watermark-opacity: 0%;
  --watermark-content: "";
  --shadow: 0 2px 8px rgba(0,0,0,0.05);
  --decor-pattern: none;
  --decor-color: transparent;
  --night-mode: 0;
}

/* 夜间模式变量 */
body.night-mode {
  --bg-main: #1a1a2e;
  --card-bg: #212134;
  --title-color: #e0e0e0;
  --border-color: #2d2d44;
  --btn-primary: #e99da9;
  --btn-secondary: #3a3a58;
  --text-secondary: #9090a5;
  --shadow: 0 2px 8px rgba(0,0,0,0.2);
  --night-mode: 1;
}

/* 1. 鎏金岁月风格（替代原轻奢）- 金色纹理+花纹装饰 */
.style-gilded {
  --bg-main: #f8f5f0;
  --card-bg: #ffffff;
  --title-color: #8b5a2b;
  --border-color: #f5eee0;
  --btn-primary: #d4af37;
  --btn-secondary: #f9f2e6;
  --text-secondary: #9d7a4a;
  --shadow: 0 3px 10px rgba(212, 175, 55, 0.1);
  --decor-pattern: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100' fill='%23d4af37' opacity='0.1'%3E%3Cpath d='M50 15L30 40h40L50 15zm0 70L30 60h40L50 85z'/%3E%3Ccircle cx='25' cy='25' r='5'/%3E%3Ccircle cx='75' cy='25' r='5'/%3E%3Ccircle cx='25' cy='75' r='5'/%3E%3Ccircle cx='75' cy='75' r='5'/%3E%3C/svg%3E");
  --decor-color: #d4af37;
}

/* 2. 蔷薇印记风格（替代原公司）- 玫瑰花纹+淡粉水印 */
.style-rosemark {
  --bg-main: #fef7fa;
  --card-bg: #ffffff;
  --title-color: #a64b60;
  --border-color: #fde4ec;
  --btn-primary: #e99da9;
  --btn-secondary: #fee9ef;
  --text-secondary: #b86b77;
  --watermark-opacity: 8%;
  --watermark-content: "Vollure Rose";
  --shadow: 0 2px 6px rgba(233, 157, 169, 0.1);
  --decor-pattern: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100' fill='%23e99da9' opacity='0.08'%3E%3Cpath d='M50 20c-10 0-15 8-20 15c-5-7-10-15-20-15c0 12 8 20 20 30c12-10 20-18 20-30zM50 80c10 0 15-8 20-15c5 7 10 15 20 15c0-12-8-20-20-30c-12 10-20 18-20 30z'/%3E%3C/svg%3E");
  --decor-color: #e99da9;
}

/* 3. 星钻流光风格（替代原玫瑰）- 碎钻纹理+渐变装饰 */
.style-stardiamond {
  --bg-main: #f5f0fa;
  --card-bg: #ffffff;
  --title-color: #6a5acd;
  --border-color: #ebe4f2;
  --btn-primary: #b19cd9;
  --btn-secondary: #f0e6fa;
  --text-secondary: #8068a8;
  --shadow: 0 3px 12px rgba(177, 156, 217, 0.15);
  --decor-pattern: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100' fill='%23b19cd9' opacity='0.1'%3E%3Cpolygon points='50 0, 61 35, 98 35, 68 57, 79 91, 50 70, 21 91, 32 57, 2 35, 39 35'/%3E%3C/svg%3E");
  --decor-color: #b19cd9;
}

/* 装饰花纹背景 - 应用到卡片和页面 */
body::after {
  content: var(--watermark-content);
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%) rotate(-15deg);
  font-size: 120px;
  font-weight: bold;
  color: #000;
  opacity: var(--watermark-opacity);
  pointer-events: none;
  z-index: 0;
  white-space: nowrap;
}

/* 风格装饰花纹 */
.month, .login-page, .month-select-page, .pop, .batch-pop, .style-pop {
  background-image: var(--decor-pattern);
  background-repeat: repeat;
  background-size: 150px;
  position: relative;
}

/* 装饰边框 - 非系统风格添加 */
.style-gilded .month, .style-rosemark .month, .style-stardiamond .month {
  border: 1px solid var(--decor-color);
}

/* 趣味装饰元素 - 随风格和夜间模式适配 */
.decoration-1 {
  position: fixed;
  top: 12px;
  left: 12px;
  width: 32px;
  height: 32px;
  background: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='%23e99da9'%3E%3Cpath d='M12 21.35l-1.45-1.32C5.4 15.36 2 12.28 2 8.5 2 5.42 4.42 3 7.5 3c1.74 0 3.41.81 4.5 2.09C13.09 3.81 14.76 3 16.5 3 19.58 3 22 5.42 22 8.5c0 3.78-3.4 6.86-8.55 11.54L12 21.35z'/%3E%3C/svg%3E") center no-repeat;
  background-size: contain;
  opacity: calc(0.6 - var(--night-mode) * 0.2);
  z-index: 1;
  animation: float 3s ease-in-out infinite;
}
.decoration-2 {
  position: fixed;
  bottom: 12px;
  right: 12px;
  width: 24px;
  height: 24px;
  background: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='%237a947f'%3E%3Cpath d='M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm0 18c-4.41 0-8-3.59-8-8s3.59-8 8-8 8 3.59 8 8-3.59 8-8 8zm-1-13h2v6h-2zm0 8h2v2h-2z'/%3E%3C/svg%3E") center no-repeat;
  background-size: contain;
  opacity: calc(0.6 - var(--night-mode) * 0.2);
  z-index: 1;
  animation: rotate 8s linear infinite;
}

/* 夜间模式专属装饰 */
.night-mode .decoration-1 {
  background: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='%23e99da9'%3E%3Cpath d='M20 15.31L23.31 12 20 8.69V4h-4.69L12 .69 8.69 4H4v4.69L.69 12 4 15.31V20h4.69L12 23.31 15.31 20H20v-4.69zM12 18c-3.31 0-6-2.69-6-6s2.69-6 6-6 6 2.69 6 6-2.69 6-6 6z'/%3E%3C/svg%3E") center no-repeat;
}
.night-mode .decoration-2 {
  background: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='%237a947f'%3E%3Cpath d='M12 3c-4.97 0-9 4.03-9 9s4.03 9 9 9c.83 0 1.5-.67 1.5-1.5 0-.39-.15-.74-.39-1.01-.23-.26-.38-.61-.38-.99 0-.83.67-1.5 1.5-1.5H16c2.76 0 5-2.24 5-5 0-4.42-4.03-8-9-8zm-5.5 9c-.83 0-1.5-.67-1.5-1.5S5.67 9 6.5 9 8 9.67 8 10.5 7.33 12 6.5 12zm3-4C8.67 8 8 7.33 8 6.5S8.67 5 9.5 5s1.5.67 1.5 1.5S10.33 8 9.5 8zm5 0c-.83 0-1.5-.67-1.5-1.5S13.67 5 14.5 5s1.5.67 1.5 1.5S15.33 8 14.5 8zm3 4c-.83 0-1.5-.67-1.5-1.5S16.67 9 17.5 9s1.5.67 1.5 1.5-.67 1.5-1.5 1.5z'/%3E%3C/svg%3E") center no-repeat;
}

@keyframes float {
  0% { transform: translateY(0px); }
  50% { transform: translateY(-8px); }
  100% { transform: translateY(0px); }
}
@keyframes rotate {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}

/* 加载状态样式 */
.loading {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 9999;
  text-align: center;
  color: var(--title-color);
}
.loading-spinner {
  width: 40px;
  height: 40px;
  border: 4px solid var(--border-color);
  border-top: 4px solid var(--btn-primary);
  border-radius: 50%;
  animation: spin 1s linear infinite;
  margin: 0 auto 10px;
}
@keyframes spin {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}

/* 登录页 - 全屏自适应 */
.login-page {
  max-width: 380px;
  width: 90%;
  margin: 0 auto;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background: var(--card-bg);
  border-radius: 20px;
  padding: 30px 24px;
  box-shadow: var(--shadow);
  animation: fadeIn 0.5s ease;
  z-index: 2;
  display: block !important; /* 确保移动端登录页默认显示 */
}
@keyframes fadeIn {
  from { opacity: 0; transform: translate(-50%, -45%) scale(0.95); }
  to { opacity: 1; transform: translate(-50%, -50%) scale(1); }
}
.login-title {
  font-size: 20px;
  font-weight: bold;
  text-align: center;
  margin-bottom: 4px;
  color: var(--title-color);
}
.login-sub {
  text-align: center;
  color: var(--text-secondary);
  margin-bottom: 24px;
  font-size: 13px;
}
.form-group {
  margin-bottom: 16px;
}
.form-group label {
  display: block;
  font-size: 12px;
  color: var(--text-secondary);
  margin-bottom: 4px;
}
.form-group input {
  width: 100%;
  padding: 10px 12px;
  border: 1px solid var(--border-color);
  border-radius: 10px;
  font-size: 14px;
  outline: none;
  background: var(--card-bg);
  color: var(--title-color);
}
.form-group input:focus {
  border-color: var(--btn-primary);
}
.remember {
  display: flex;
  align-items: center;
  gap: 4px;
  font-size: 12px;
  color: var(--text-secondary);
  margin-bottom: 20px;
}
.login-btn {
  width: 100%;
  padding: 11px;
  background: var(--btn-primary);
  color: #fff;
  border: none;
  border-radius: 12px;
  font-size: 14px;
  font-weight: 500;
  cursor: pointer;
}

/* 月份选择页面 - 全屏自适应 */
.month-select-page {
  display: none;
  animation: fadeIn 0.5s ease;
  position: relative;
  z-index: 2;
  width: 100%;
  height: 100vh;
  padding: 20px;
  background: var(--bg-main);
}
/* 月份选择页功能按钮栏 */
.month-select-actions {
  display: flex;
  justify-content: center;
  gap: 8px;
  margin-bottom: 20px;
  flex-wrap: wrap;
  padding: 0 10px;
}
.month-select-btn {
  padding: 6px 10px;
  font-size: 11px;
  background: var(--btn-secondary);
  color: var(--btn-primary);
  border: none;
  border-radius: 6px;
  cursor: pointer;
}
/* 夜间模式切换按钮 */
.night-mode-btn {
  background: var(--btn-secondary);
  color: var(--btn-primary);
  border: none;
  border-radius: 6px;
  padding: 6px 10px;
  font-size: 11px;
  cursor: pointer;
  margin-left: 8px;
}
.month-select-title {
  font-size: 22px;
  font-weight: bold;
  text-align: center;
  margin: 0 0 30px;
  color: var(--title-color);
}
/* 12个月网格：2行6列，全屏自适应 */
.month-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
  gap: 15px;
  width: 100%;
  max-width: 100%;
  padding: 0 10px;
}
@media (min-width: 768px) {
  .month-grid {
    grid-template-columns: repeat(6, 1fr);
    max-width: 800px;
    margin: 0 auto;
  }
}
/* 横屏适配 */
@media (orientation: landscape) and (max-width: 900px) {
  .month-grid {
    grid-template-columns: repeat(6, 1fr);
  }
  .month-card-thumb {
    padding: 10px 5px;
  }
}
/* 月份卡片缩略图 */
.month-card-thumb {
  background: var(--card-bg);
  border-radius: 12px;
  padding: 15px 10px;
  box-shadow: var(--shadow);
  cursor: pointer;
  text-align: center;
  transition: transform 0.2s ease;
}
.month-card-thumb:hover {
  transform: scale(1.05);
}
.month-thumb-title {
  font-size: 16px;
  font-weight: bold;
  color: var(--title-color);
  margin-bottom: 10px;
}
/* 月份缩略日历 */
.month-thumb-cal {
  display: grid;
  grid-template-columns: repeat(7, 1fr);
  gap: 2px;
}
.thumb-day {
  width: 100%;
  aspect-ratio: 1/1;
  border-radius: 3px;
  background: var(--border-color);
  font-size: 8px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.thumb-day.marked {
  border: 1px solid var(--btn-primary);
}

/* 主日历界面 - 全屏自适应 */
.calendar-container {
  display: none;
  animation: pageIn 0.6s ease;
  position: relative;
  z-index: 2;
  width: 100%;
  height: 100vh;
  padding: 10px;
  background: var(--bg-main);
  transform-origin: top center;
  overflow-y: auto;
}
@keyframes pageIn {
  from { opacity: 0; }
  to { opacity: 1; }
}
/* 缩放控制栏 */
.zoom-control {
  padding: 10px 12px;
  text-align: center;
  background: var(--card-bg);
  border-radius: 10px;
  margin: 0 auto 15px;
  max-width: 80%;
  box-shadow: var(--shadow);
}
.zoom-slider {
  width: 80%;
  margin: 10px auto;
  accent-color: var(--btn-primary);
}
.zoom-level {
  font-size: 12px;
  color: var(--text-secondary);
}

/* 月份卡片 - 全屏自适应 */
.month {
  background: var(--card-bg);
  border-radius: 14px;
  overflow: hidden;
  margin: 0 auto 20px;
  box-shadow: var(--shadow);
  width: 95%;
  max-width: 800px;
}
/* 横竖屏适配 */
@media (orientation: landscape) and (max-width: 900px) {
  .month {
    width: 98%;
    margin: 0 auto 10px;
  }
  .day {
    min-height: 60px !important;
  }
}
@media (max-width: 768px) {
  .month {
    width: 98%;
  }
}

.month-title {
  text-align: center;
  font-size: 15px;
  font-weight: bold;
  color: var(--title-color);
  padding: 12px 0;
  background: var(--card-bg);
  border-bottom: 1px solid var(--border-color);
}
/* 月份操作栏 - 取消批量设置按钮，调整布局 */
.month-head {
  padding: 8px 12px;
  background: var(--card-bg);
  display: flex;
  justify-content: space-between;
  gap: 6px;
  border-bottom: 1px solid var(--border-color);
  flex-wrap: wrap;
}
/* 左侧功能按钮组：返回+横竖屏+风格切换（取消批量设置） */
.month-func-group {
  display: flex;
  gap: 6px;
  flex-wrap: wrap;
}
/* 返回按钮 */
.btn-back {
  padding: 6px 10px;
  font-size: 11px;
  background: var(--border-color);
  color: var(--text-secondary);
  border: none;
  border-radius: 6px;
  cursor: pointer;
}
/* 功能按钮样式统一 */
.btn-screen, .btn-style, .btn-night {
  padding: 6px 10px;
  font-size: 11px;
  border: none;
  border-radius: 6px;
  cursor: pointer;
}
.btn-screen {
  background: #e8eef2;
  color: #7b9cb3;
}
.btn-style {
  background: var(--btn-secondary);
  color: var(--btn-primary);
}
.btn-night {
  background: var(--btn-secondary);
  color: var(--btn-primary);
}
/* 右侧操作按钮组：清空+保存 */
.month-actions {
  display: flex;
  gap: 8px;
}
.btn-clear-month, .btn-save-month {
  padding: 6px 10px;
  font-size: 11px;
  border: none;
  border-radius: 6px;
  cursor: pointer;
}
.btn-clear-month {
  background: var(--btn-secondary);
  color: var(--btn-primary);
}
.btn-save-month {
  background: var(--btn-primary);
  color: #ffffff;
}

.week {
  display: grid;
  grid-template-columns: repeat(7,1fr);
  background: var(--card-bg);
  padding: 6px 0;
  border-bottom: 1px solid var(--border-color);
}
.week > div {
  text-align: center;
  font-size: 11px;
  color: var(--text-secondary);
}

.days {
  display: grid;
  grid-template-columns: repeat(7,1fr);
  border-top: 1px solid var(--border-color);
  gap: 1px;
  background: var(--border-color);
  padding: 1px;
}

/* 日期框样式 - 取消滑动判定，全屏自适应 */
.day {
  width: 100%;
  aspect-ratio: 5/3;
  padding: 8px 6px;
  background: #fff;
  position: relative;
  cursor: pointer;
  border-radius: 6px;
  overflow: hidden;
  min-height: 60px;
}

/* 夜间模式日期框适配 */
.night-mode .day {
  background: var(--card-bg);
}
.night-mode .num, .night-mode .todo {
  color: var(--title-color) !important;
}
.night-mode .lunar {
  color: var(--text-secondary) !important;
}

/* 移动端日期框 - 横竖屏自适应 */
@media (max-width: 768px) {
  .day {
    aspect-ratio: auto;
    min-height: 90px;
    height: auto;
    padding: 10px 8px;
  }
  .todo {
    font-size: 14px !important;
    line-height: 1.4 !important;
    -webkit-line-clamp: unset !important;
    height: auto !important;
    top: 38px !important;
    bottom: 8px !important;
  }
}
@media (orientation: landscape) and (max-width: 900px) {
  .day {
    min-height: 70px !important;
    padding: 6px 4px !important;
  }
  .todo {
    font-size: 12px !important;
    top: 30px !important;
  }
}

/* 选中状态 */
.day.selected {
  border: 2px solid var(--btn-primary);
}
.day.dark-text .num, 
.day.dark-text .todo {
  color: #ffffff !important;
}
.night-mode .day.dark-text .num,
.night-mode .day.dark-text .todo {
  color: #ffffff !important;
}

/* 国历样式 */
.num {
  position: absolute;
  top: 6px;
  left: 6px;
  font-size: 18px;
  font-weight: bold;
  color: #333;
}

/* 农历样式：竖排+缩小 */
.lunar {
  position: absolute;
  top: 6px;
  right: 6px;
  font-size: 9px;
  color: #000000 !important;
  writing-mode: vertical-lr;
  text-orientation: upright;
  line-height: 1.2;
  width: 12px;
  text-align: center;
}

/* 待办事项 */
.todo {
  position: absolute;
  top: 32px;
  left: 6px;
  right: 6px;
  bottom: 6px;
  font-size: 14px;
  line-height: 1.3;
  color: #444;
  word-break: break-all;
  overflow: hidden;
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
}

/* 颜色面板 - 随风格变化 */
.color-panel {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 8px;
  margin-bottom: 14px;
}
.color-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 3px;
}
.color-dot {
  width: 32px;
  height: 32px;
  border-radius: 50%;
  cursor: pointer;
  border: 2px solid transparent;
}
.color-dot.active {
  border-color: var(--btn-primary);
}
.color-name {
  font-size: 10px;
  color: var(--text-secondary);
  text-align: center;
}

/* 弹窗 */
.mask {
  position: fixed; inset:0; background:rgba(0,0,0,0.25);
  display: none;
  z-index: 99;
}
.night-mode .mask {
  background: rgba(0,0,0,0.5);
}
.pop {
  position: fixed;
  top: 50%; left:50%;
  transform: translate(-50%,-50%);
  background:var(--card-bg);
  border-radius: 16px;
  padding: 20px;
  width: 88%;
  max-width: 340px;
  display: none;
  animation: popIn 0.3s ease;
  z-index: 100;
  box-shadow: var(--shadow);
}
@keyframes popIn {
  from { opacity:0; transform: translate(-50%,-45%) scale(0.95); }
  to { opacity:1; transform: translate(-50%,-50%) scale(1); }
}
.pop-title {
  font-size: 16px;
  font-weight: bold;
  margin-bottom: 14px;
  text-align: center;
  color: var(--title-color);
}
.pop-input {
  width: 100%;
  height: 70px;
  border: 1px solid var(--border-color);
  border-radius: 10px;
  padding: 8px 10px;
  font-size: 14px;
  margin-bottom: 14px;
  resize: none;
  outline: none;
  background: var(--card-bg);
  color: var(--title-color);
}
.pop-btns {
  display: flex;
  gap: 8px;
}
.pop-btns button {
  flex:1;
  padding: 9px;
  border-radius: 10px;
  border:none;
  font-size: 14px;
}
.btn-clear {
  background: var(--border-color);
  color:var(--text-secondary);
}
.btn-cancel {
  background: var(--border-color);
  color:var(--text-secondary);
}
.btn-ok {
  background: var(--btn-primary);
  color:#fff;
}

/* 批量设置待办弹窗 - 保留但不显示（取消批量功能） */
.batch-pop {
  display: none !important;
}
.batch-mask {
  display: none !important;
}

/* 风格选择弹窗 */
.style-pop {
  position: fixed;
  top: 50%; left:50%;
  transform: translate(-50%,-50%);
  background:var(--card-bg);
  border-radius: 16px;
  padding: 20px;
  width: 88%;
  max-width: 340px;
  display: none;
  animation: popIn 0.3s ease;
  z-index: 100;
  box-shadow: var(--shadow);
}
.style-title {
  font-size: 16px;
  font-weight: bold;
  margin-bottom: 20px;
  text-align: center;
  color: var(--title-color);
}
.style-item {
  padding: 12px;
  margin-bottom: 10px;
  border-radius: 10px;
  border: 1px solid var(--border-color);
  cursor: pointer;
  text-align: center;
  transition: all 0.2s ease;
}
.style-item.active {
  background: var(--btn-primary);
  color: #fff;
  border-color: var(--btn-primary);
}
.style-item:hover {
  background: var(--btn-secondary);
}

.toast {
  position: fixed;
  bottom: 40px;
  left:50%;
  transform: translateX(-50%);
  background: rgba(0,0,0,0.7);
  color:#fff;
  padding: 7px 12px;
  border-radius: 8px;
  font-size: 12px;
  display: none;
  z-index: 101;
}
.night-mode .toast {
  background: rgba(255,255,255,0.2);
  color: #fff;
}
</style>
</head>
<body id="appBody">
<!-- 加载状态 -->
<div class="loading" id="loading" style="display: none;">
  <div class="loading-spinner"></div>
  <div>加载中...</div>
</div>

<div class="decoration-1"></div>
<div class="decoration-2"></div>

<!-- 登录页 -->
<div class="login-page" id="loginPage">
  <div class="login-title">Vollure Rose</div>
  <div class="login-sub">2026年度行事历</div>
  <div class="form-group">
    <label>账号</label>
    <input id="user" type="text" placeholder="请输入账号">
  </div>
  <div class="form-group">
    <label>密码</label>
    <input id="pwd" type="password" placeholder="请输入密码">
  </div>
  <div class="remember">
    <input id="remember" type="checkbox">
    <label for="remember">记住密码30天</label>
  </div>
  <button class="login-btn" id="loginBtn">登录</button>
</div>

<!-- 月份选择页面 -->
<div class="month-select-page" id="monthSelectPage">
  <!-- 月份选择页功能按钮栏 -->
  <div class="month-select-actions">
    <button class="month-select-btn" id="selectScreenBtn">横竖屏切换</button>
    <button class="month-select-btn" id="selectStyleBtn">风格切换</button>
    <button class="night-mode-btn" id="selectNightBtn">夜间模式</button>
  </div>
  <div class="month-select-title">选择月份</div>
  <div class="month-grid" id="monthGrid"></div>
</div>

<!-- 主日历界面 -->
<div class="calendar-container" id="main">
  <!-- 缩放控制栏 -->
  <div class="zoom-control">
    <div class="zoom-level">当前缩放：<span id="zoomValue">100%</span></div>
    <input type="range" min="25" max="100" step="25" value="100" class="zoom-slider" id="zoomSlider">
  </div>
  <div id="calendar"></div>
</div>

<!-- 弹窗 -->
<div class="mask" id="mask"></div>
<div class="pop" id="pop">
  <div class="pop-title">编辑待办</div>
  <div class="color-panel" id="colors"></div>
  <textarea class="pop-input" id="todoInput" placeholder="输入内容..."></textarea>
  <div class="pop-btns">
    <button class="btn-clear" id="clearBtn">清除</button>
    <button class="btn-cancel" id="cancel">取消</button>
    <button class="btn-ok" id="ok">确定</button>
  </div>
</div>

<!-- 批量设置待办弹窗 - 保留但隐藏 -->
<div class="mask" id="batchMask"></div>
<div class="batch-pop" id="batchPop">
  <div class="batch-title">批量设置待办</div>
  <div class="batch-color-panel" id="batchColors"></div>
  <textarea class="batch-input" id="batchInput" placeholder="输入待办内容..."></textarea>
  <div class="batch-btns">
    <button class="btn-cancel" id="batchCancel">取消</button>
    <button class="btn-ok" id="batchOk">确定</button>
  </div>
</div>

<!-- 风格选择弹窗 -->
<div class="mask" id="styleMask"></div>
<div class="style-pop" id="stylePop">
  <div class="style-title">选择行事历风格</div>
  <div class="style-item active" data-style="system">系统风格</div>
  <div class="style-item" data-style="gilded">鎏金岁月</div>
  <div class="style-item" data-style="rosemark">蔷薇印记</div>
  <div class="style-item" data-style="stardiamond">星钻流光</div>
</div>

<div class="toast" id="toast"></div>

<script>
// ==================== 云存储配置 ====================
// 替换为你的云存储API地址（示例使用mock API，实际需替换为真实地址）
const CLOUD_API_URL = "https://your-api-domain.com/calendar";
// 用户标识（登录后生成）
let USER_TOKEN = "";

// ==================== 配置 ====================
const YEAR = 2026;
const USER = "rose001";
const PWD = "123456";

// 新风格对应的颜色配置
const STYLE_COLORS = {
  system: [
    { c: "#ffffff", name: "白色", isDark: false },
    { c: "#b86b77", name: "陈酒红", isDark: true },
    { c: "#7a947f", name: "暮光绿", isDark: true },
    { c: "#7b9cb3", name: "梦幻蓝", isDark: true },
    { c: "#949494", name: "冬日灰", isDark: true },
    { c: "#d49a6a", name: "伯爵橙", isDark: true },
    { c: "#e4b4b4", name: "奶茶粉", isDark: false },
    { c: "#f2d392", name: "香草黄", isDark: false },
    { c: "#f7c8d0", name: "泡沫粉", isDark: false }
  ],
  // 鎏金岁月 - 金色系
  gilded: [
    { c: "#ffffff", name: "象牙白", isDark: false },
    { c: "#d4af37", name: "黄金", isDark: true },
    { c: "#b8860b", name: "暗金", isDark: true },
    { c: "#ffd700", name: "亮金", isDark: true },
    { c: "#f0e68c", name: "卡其金", isDark: false },
    { c: "#deb887", name: "桃木金", isDark: false },
    { c: "#f5deb3", name: "小麦金", isDark: false },
    { c: "#fff8dc", name: "奶油金", isDark: false },
    { c: "#8b7355", name: "复古金", isDark: true }
  ],
  // 蔷薇印记 - 玫瑰粉系
  rosemark: [
    { c: "#ffffff", name: "本白", isDark: false },
    { c: "#e99da9", name: "玫瑰粉", isDark: true },
    { c: "#d87086", name: "深玫瑰", isDark: true },
    { c: "#f8e0e5", name: "浅粉", isDark: false },
    { c: "#f0c4ce", name: "柔粉", isDark: false },
    { c: "#e8a8b7", name: "粉金", isDark: true },
    { c: "#fdf0f3", name: "极浅粉", isDark: false },
    { c: "#f9e0e6", name: "淡粉", isDark: false },
    { c: "#a64b60", name: "酒红粉", isDark: true }
  ],
  // 星钻流光 - 紫蓝系
  stardiamond: [
    { c: "#ffffff", name: "透白", isDark: false },
    { c: "#b19cd9", name: "浅紫钻", isDark: true },
    { c: "#9370db", name: "深紫钻", isDark: true },
    { c: "#87cefa", name: "浅蓝钻", isDark: false },
    { c: "#4169e1", name: "宝蓝钻", isDark: true },
    { c: "#e6e6fa", name: "淡紫钻", isDark: false },
    { c: "#d8bfd8", name: "藕紫钻", isDark: false },
    { c: "#6a5acd", name: "暗紫钻", isDark: true },
    { c: "#f0e6fa", name: "柔紫钻", isDark: false }
  ]
};

// 全局变量
let isDragging = false;
let selectedDays = [];
let currentZoom = 100;
let currentViewMonth = null;
let currentStyle = "system"; // 默认系统风格
let isNightMode = false; // 夜间模式状态
let COLORS = STYLE_COLORS.system;

let data = {}; // 不再从本地存储初始化，改为从云端加载
let styleData = { style: "system", nightMode: false };
let curMonth, curKeys;
let syncInterval = null;

// ==================== 工具函数 ====================
function toast(txt) {
  const t = document.getElementById("toast");
  t.textContent = txt;
  t.style.display = "block";
  setTimeout(() => t.style.display = "none", 1200);
}

function showLoading() {
  document.getElementById("loading").style.display = "block";
}

function hideLoading() {
  document.getElementById("loading").style.display = "none";
}

function getLunar(month, day) {
  const ld = [
    "", "初一", "初二", "初三", "初四", "初五", "初六", "初七", "初八", "初九", "初十",
    "十一", "十二", "十三", "十四", "十五", "十六", "十七", "十八", "十九", "二十",
    "廿一", "廿二", "廿三", "廿四", "廿五", "廿六", "廿七", "廿八", "廿九", "三十"
  ];
  const md = [0,31,28,31,30,31,30,31,31,30,31,30,31];
  let sum = 0;
  for (let i=1; i<month; i++) sum += md[i];
  const idx = (sum + day + 8) % 30 + 1;
  return ld[idx] || "";
}

// ==================== 云存储API封装 ====================
/**
 * 从云端加载日历数据
 */
async function loadDataFromCloud() {
  try {
    showLoading();
    // 实际项目中替换为真实的API请求
    const response = await fetch(`${CLOUD_API_URL}/load?user=${USER_TOKEN}`, {
      method: "GET",
      headers: {
        "Content-Type": "application/json",
        "Authorization": `Bearer ${USER_TOKEN}`
      }
    });
    
    if (!response.ok) throw new Error("加载失败");
    const result = await response.json();
    
    // 兼容mock数据和真实数据
    data = result.data || {};
    styleData = result.style || { style: "system", nightMode: false };
    
    hideLoading();
    toast("云端数据加载成功");
    return true;
  } catch (error) {
    hideLoading();
    // 云端加载失败时，使用本地备份（降级方案）
    const localBackup = JSON.parse(localStorage.getItem("cal_data_backup")) || {};
    data = localBackup;
    toast("云端加载失败，使用本地备份数据");
    return false;
  }
}

/**
 * 保存数据到云端
 */
async function saveDataToCloud() {
  try {
    // 同时保存到本地作为备份
    localStorage.setItem("cal_data_backup", JSON.stringify(data));
    
    // 实际项目中替换为真实的API请求
    const response = await fetch(`${CLOUD_API_URL}/save`, {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
        "Authorization": `Bearer ${USER_TOKEN}`
      },
      body: JSON.stringify({
        user: USER_TOKEN,
        data: data,
        style: styleData
      })
    });
    
    if (!response.ok) throw new Error("保存失败");
    return true;
  } catch (error) {
    toast("云端保存失败，已保存到本地备份");
    return false;
  }
}

/**
 * 同步云端数据
 */
async function syncCloudData() {
  try {
    const response = await fetch(`${CLOUD_API_URL}/sync?user=${USER_TOKEN}`, {
      method: "GET",
      headers: {
        "Authorization": `Bearer ${USER_TOKEN}`
      }
    });
    
    if (!response.ok) throw new Error("同步失败");
    const result = await response.json();
    
    if (JSON.stringify(data) !== JSON.stringify(result.data)) {
      data = result.data;
      renderMonthSelectPage();
      if (currentViewMonth) {
        renderSingleMonth(currentViewMonth);
      }
      toast("云端数据已同步");
    }
  } catch (error) {
    // 同步失败不提示，避免打扰用户
  }
}

// ==================== 初始化函数 ====================
async function initData() {
  // 1. 加载云端数据
  await loadDataFromCloud();
  
  // 2. 初始化风格和夜间模式
  currentStyle = styleData.style || "system";
  isNightMode = styleData.nightMode || false;
  setStyle(currentStyle);
  toggleNightMode(isNightMode, false); // 初始化不提示
  
  // 3. 启动云端同步定时器
  if (syncInterval) clearInterval(syncInterval);
  syncInterval = setInterval(syncCloudData, 10000); // 每10秒同步一次
}

// ==================== 保存函数重写 ====================
function autoSave() {
  // 异步保存到云端，不阻塞UI
  saveDataToCloud();
}

function saveStyle() {
  // 风格数据随主数据一起保存到云端
  styleData = {
    style: currentStyle,
    nightMode: isNightMode
  };
  autoSave();
}

function saveMonthData(month) {
  autoSave();
  toast(`${month}月数据已保存到云端`);
}

window.addEventListener("beforeunload", async () => {
  // 页面关闭前确保数据保存到云端
  await saveDataToCloud();
  if (syncInterval) clearInterval(syncInterval);
});

// ==================== 风格切换 ====================
function setStyle(style) {
  currentStyle = style;
  COLORS = STYLE_COLORS[style] || STYLE_COLORS.system;
  
  // 移除所有风格类
  document.getElementById("appBody").className = isNightMode ? "night-mode" : "";
  // 添加当前风格类
  document.getElementById("appBody").classList.add(`style-${style}`);
  
  // 更新风格选择弹窗选中状态
  document.querySelectorAll(".style-item").forEach(item => {
    item.classList.remove("active");
    if (item.dataset.style === style) {
      item.classList.add("active");
    }
  });
  
  // 刷新界面
  renderMonthSelectPage();
  if (currentViewMonth) {
    renderSingleMonth(currentViewMonth);
  }
  
  saveStyle();
  toast(`已切换为${getStyleName(style)}`);
}

function getStyleName(style) {
  const names = {
    system: "系统风格",
    gilded: "鎏金岁月",
    rosemark: "蔷薇印记",
    stardiamond: "星钻流光"
  };
  return names[style] || "系统风格";
}

// ==================== 夜间模式 ====================
function toggleNightMode(forceMode, showToast = true) {
  isNightMode = forceMode !== undefined ? forceMode : !isNightMode;
  
  // 更新样式类
  if (isNightMode) {
    document.getElementById("appBody").classList.add("night-mode");
  } else {
    document.getElementById("appBody").classList.remove("night-mode");
  }
  
  // 保持风格类
  document.getElementById("appBody").classList.add(`style-${currentStyle}`);
  
  // 更新按钮文字
  document.querySelectorAll(".night-mode-btn").forEach(btn => {
    btn.textContent = isNightMode ? "日间模式" : "夜间模式";
  });
  
  // 刷新界面
  renderMonthSelectPage();
  if (currentViewMonth) {
    renderSingleMonth(currentViewMonth);
  }
  
  saveStyle();
  if (showToast) {
    toast(isNightMode ? "已开启夜间模式" : "已关闭夜间模式");
  }
}

// ==================== 月份选择页面 ====================
function renderMonthSelectPage() {
  const monthGrid = document.getElementById("monthGrid");
  monthGrid.innerHTML = "";
  
  for (let m = 1; m <= 12; m++) {
    const monthCard = document.createElement("div");
    monthCard.className = "month-card-thumb";
    monthCard.dataset.month = m;
    
    let thumbCalHtml = "";
    const firstDay = new Date(YEAR, m-1, 1).getDay();
    const daysInMonth = new Date(YEAR, m, 0).getDate();
    
    for (let i=0; i<firstDay; i++) {
      thumbCalHtml += `<div class="thumb-day"></div>`;
    }
    
    for (let d=1; d<=daysInMonth; d++) {
      const key = `${m}-${d}`;
      const hasMark = data[key] && (data[key].todo || data[key].color !== "#ffffff");
      const dayClass = hasMark ? "thumb-day marked" : "thumb-day";
      thumbCalHtml += `<div class="${dayClass}" style="${hasMark ? `background:${data[key].color || '#ffffff'}` : ''}"></div>`;
    }
    
    monthCard.innerHTML = `
      <div class="month-thumb-title">${m}月份</div>
      <div class="month-thumb-cal">${thumbCalHtml}</div>
    `;
    
    monthCard.addEventListener("click", () => {
      showSingleMonth(m);
    });
    
    monthGrid.appendChild(monthCard);
  }
  
  // 绑定月份选择页的功能按钮
  document.getElementById("selectScreenBtn").onclick = toggleScreenOrientation;
  document.getElementById("selectStyleBtn").onclick = () => {
    document.getElementById("styleMask").style.display = "block";
    document.getElementById("stylePop").style.display = "block";
  };
  document.getElementById("selectNightBtn").onclick = () => {
    toggleNightMode();
  };
}

function showSingleMonth(month) {
  currentViewMonth = month;
  document.getElementById("monthSelectPage").style.display = "none";
  document.getElementById("main").style.display = "block";
  renderSingleMonth(month);
  setZoom(100);
  document.getElementById("zoomSlider").value = 100;
  document.getElementById("zoomValue").textContent = "100%";
}

function renderSingleMonth(month) {
  const calendar = document.getElementById("calendar");
  calendar.innerHTML = "";
  
  const mEl = document.createElement("div");
  mEl.className = "month";
  mEl.innerHTML = `
    <div class="month-title">Vollure Rose 2026年度行事历-${month}月份</div>
    <div class="month-head">
      <div class="month-func-group">
        <button class="btn-back" onclick="backToMonthSelect()">返回</button>
        <button class="btn-screen" onclick="toggleScreenOrientation()">横竖屏</button>
        <button class="btn-style" onclick="openStylePop()">风格切换</button>
        <button class="btn-night" onclick="toggleNightMode()">${isNightMode ? '日间模式' : '夜间模式'}</button>
      </div>
      <div class="month-actions">
        <button class="btn-clear-month" onclick="clearMonth(${month})">清空本月</button>
        <button class="btn-save-month" onclick="saveMonthData(${month})">保存本月</button>
      </div>
    </div>
    <div class="week">
      <div>日</div><div>一</div><div>二</div><div>三</div><div>四</div><div>五</div><div>六</div>
    </div>
    <div class="days" id="days-${month}"></div>
  `;
  calendar.appendChild(mEl);
  
  const box = document.getElementById(`days-${month}`);
  box.innerHTML = "";
  const first = new Date(YEAR, month-1, 1).getDay();
  const days = new Date(YEAR, month, 0).getDate();
  
  for (let i=0; i<first; i++) {
    box.innerHTML += `<div class="day empty"></div>`;
  }
  
  for (let d=1; d<=days; d++) {
    const key = `${month}-${d}`;
    const item = data[key] || { color: "#ffffff", todo: "" };
    const lunar = getLunar(month, d);
    const colorConfig = COLORS.find(c => c.c === item.color) || { isDark: false };
    const darkClass = colorConfig.isDark ? "dark-text" : "";
    
    box.innerHTML += `
      <div class="day ${darkClass}" data-key="${key}" style="background:${item.color}">
        <div class="num">${d}</div>
        <div class="lunar">${lunar}</div>
        <div class="todo">${item.todo}</div>
      </div>
    `;
  }
  
  bindDragSelect();
}

function backToMonthSelect() {
  document.getElementById("main").style.display = "none";
  document.getElementById("monthSelectPage").style.display = "block";
  renderMonthSelectPage();
}

// ==================== 缩放功能 ====================
function setZoom(percent) {
  currentZoom = percent;
  const scale = percent / 100;
  document.getElementById("main").style.transform = `scale(${scale})`;
  document.getElementById("zoomValue").textContent = `${percent}%`;
}

function bindZoomEvent() {
  const slider = document.getElementById("zoomSlider");
  slider.addEventListener("input", (e) => {
    const value = parseInt(e.target.value);
    setZoom(value);
  });
}

// ==================== 拖动选中功能（取消移动端滑动判定） ====================
function bindDragSelect() {
  const allDays = document.querySelectorAll(".day:not(.empty)");
  
  // 鼠标端
  allDays.forEach(day => {
    day.addEventListener("mousedown", (e) => {
      e.preventDefault();
      isDragging = true;
      selectedDays = [];
      document.querySelectorAll(".day.selected").forEach(d => d.classList.remove("selected"));
      selectDay(day);
    });

    day.addEventListener("mouseenter", () => {
      if (isDragging) {
        selectDay(day);
      }
    });
  });

  // 移动端：取消滑动判定，完全恢复拖动多选
  allDays.forEach(day => {
    day.addEventListener("touchstart", (e) => {
      e.preventDefault(); // 取消默认行为
      isDragging = true;
      selectedDays = [];
      document.querySelectorAll(".day.selected").forEach(d => d.classList.remove("selected"));
      selectDay(day);
    });

    day.addEventListener("touchmove", (e) => {
      e.preventDefault(); // 取消默认行为
      if (isDragging) {
        const touch = e.touches[0];
        const target = document.elementFromPoint(touch.clientX, touch.clientY);
        if (target && target.classList.contains("day") && !target.classList.contains("empty")) {
          selectDay(target);
        }
      }
    });
  });

  // 通用结束处理
  document.addEventListener("mouseup", endDrag);
  document.addEventListener("touchend", endDrag);

  function selectDay(day) {
    if (!day.classList.contains("selected")) {
      day.classList.add("selected");
      const key = day.dataset.key;
      if (key && !selectedDays.includes(key)) {
        selectedDays.push(key);
      }
    }
  }

  function endDrag() {
    if (isDragging && selectedDays.length > 0) {
      isDragging = false;
      curMonth = selectedDays[0].split("-")[0];
      curKeys = selectedDays;
      const firstKey = selectedDays[0];
      const item = data[firstKey] || { color: "#ffffff", todo: "" };
      document.getElementById("todoInput").value = item.todo;
      buildColors(item.color);
      document.getElementById("mask").style.display = "block";
      document.getElementById("pop").style.display = "block";
    }
    isDragging = false;
  }

  // 单机/单点
  allDays.forEach(day => {
    day.addEventListener("click", () => {
      if (!isDragging) {
        selectedDays = [day.dataset.key];
        curMonth = day.dataset.key.split("-")[0];
        curKeys = selectedDays;
        const item = data[day.dataset.key] || { color: "#ffffff", todo: "" };
        document.getElementById("todoInput").value = item.todo;
        buildColors(item.color);
        document.getElementById("mask").style.display = "block";
        document.getElementById("pop").style.display = "block";
      }
    });
  });
}

// ==================== 颜色面板构建 ====================
function buildColors(activeColor, targetId = "colors") {
  const box = document.getElementById(targetId);
  box.innerHTML = "";
  COLORS.forEach(item => {
    const isActive = item.c === activeColor;
    const html = `
      <div class="color-item">
        <div class="color-dot ${isActive ? 'active' : ''}" style="background:${item.c}" data-color="${item.c}"></div>
        <div class="color-name">${item.name}</div>
      </div>
    `;
    box.innerHTML += html;
  });

  document.querySelectorAll(`#${targetId} .color-dot`).forEach(dot => {
    dot.onclick = () => {
      document.querySelectorAll(`#${targetId} .color-dot`).forEach(d => d.classList.remove("active"));
      dot.classList.add("active");
    };
  });
}

// ==================== 编辑功能 ====================
document.getElementById("ok").onclick = () => {
  const activeDot = document.querySelector("#colors .color-dot.active");
  if (!activeDot) return;
  const color = activeDot.dataset.color;
  const todo = document.getElementById("todoInput").value.trim();
  
  curKeys.forEach(k => {
    data[k] = { color, todo };
  });
  
  autoSave();
  renderSingleMonth(curMonth);
  bindDragSelect();
  closePop();
  toast(`已保存${curKeys.length}个日期到云端`);
};

document.getElementById("clearBtn").onclick = () => {
  if (!confirm("确定清空选中日期的内容？")) return;
  curKeys.forEach(k => delete data[k]);
  autoSave();
  renderSingleMonth(curMonth);
  bindDragSelect();
  closePop();
  toast(`已清空${curKeys.length}个日期`);
};

document.getElementById("cancel").onclick = closePop;
document.getElementById("mask").onclick = closePop;

function closePop() {
  document.getElementById("mask").style.display = "none";
  document.getElementById("pop").style.display = "none";
  document.querySelectorAll(".day.selected").forEach(d => d.classList.remove("selected"));
  selectedDays = [];
}

// ==================== 清空本月 ====================
function clearMonth(m) {
  if (!confirm(`确定清空 ${m}月 所有内容？`)) return;
  for (let k in data) {
    if (k.split("-")[0] == m) delete data[k];
  }
  autoSave();
  renderSingleMonth(m);
  bindDragSelect();
  toast(`${m}月已清空`);
}

// ==================== 横竖屏切换 - 解决授权问题 ====================
function toggleScreenOrientation() {
  // 方案1：不调用需要授权的API，改为提示用户手动旋转设备
  const currentOrientation = window.innerWidth > window.innerHeight ? "横屏" : "竖屏";
  const targetOrientation = currentOrientation === "横屏" ? "竖屏" : "横屏";
  
  // 友好提示，引导用户手动操作
  toast(`请手动将设备旋转为${targetOrientation}模式`);
}

// ==================== 风格弹窗 ====================
function openStylePop() {
  document.getElementById("styleMask").style.display = "block";
  document.getElementById("stylePop").style.display = "block";
}

// ==================== 登录 ====================
document.getElementById("loginBtn").onclick = async () => {
  const u = document.getElementById("user").value.trim();
  const p = document.getElementById("pwd").value.trim();
  
  if (u !== USER || p !== PWD) {
    toast("账号或密码错误");
    return;
  }
  
  // 生成用户标识（实际项目中使用后端返回的token）
  USER_TOKEN = `${u}_${Date.now()}`;
  
  // 保存记住密码
  saveRemember();
  
  // 初始化数据（从云端加载）
  await initData();
  
  // 显示页面
  document.getElementById("loginPage").style.display = "none";
  document.getElementById("monthSelectPage").style.display = "block";
  
  // 渲染页面
  renderMonthSelectPage();
  bindZoomEvent();
  
  // 绑定风格选择事件
  document.querySelectorAll(".style-item").forEach(item => {
    item.addEventListener("click", () => {
      setStyle(item.dataset.style);
      document.getElementById("styleMask").style.display = "none";
      document.getElementById("stylePop").style.display = "none";
    });
  });
  
  document.getElementById("styleMask").addEventListener("click", () => {
    document.getElementById("styleMask").style.display = "none";
    document.getElementById("stylePop").style.display = "none";
  });
};

function loadRemember() {
  const d = localStorage.getItem("cal_remember");
  if (!d) return;
  const { user, pwd, exp } = JSON.parse(d);
  if (Date.now() > exp) {
    localStorage.removeItem("cal_remember");
    return;
  }
  document.getElementById("user").value = user;
  document.getElementById("pwd").value = pwd;
  document.getElementById("remember").checked = true;
}

function saveRemember() {
  const user = document.getElementById("user").value;
  const pwd = document.getElementById("pwd").value;
  if (!document.getElementById("remember").checked) {
    localStorage.removeItem("cal_remember");
    return;
  }
  const exp = Date.now() + 30 * 24 * 60 * 60 * 1000;
  localStorage.setItem("cal_remember", JSON.stringify({ user, pwd, exp }));
}

// ==================== 页面加载 - 修复移动端空白问题 ====================
window.addEventListener("DOMContentLoaded", () => {
  // 确保页面元素加载完成后再执行操作
  loadRemember();
  
  // 移动端适配：强制设置body高度
  document.body.style.minHeight = `${window.innerHeight}px`;
  
  // 监听窗口大小变化，实时适配
  window.addEventListener("resize", () => {
    document.body.style.minHeight = `${window.innerHeight}px`;
    if (currentViewMonth) {
      renderSingleMonth(currentViewMonth);
    }
    renderMonthSelectPage();
  });
  
  // 确保登录页默认显示
  document.getElementById("loginPage").style.display = "block";
});

// 兼容移动端触摸事件
document.addEventListener("touchstart", function() {}, { passive: false });
document.addEventListener("touchmove", function() {}, { passive: false });
</script>
</body>
</html>
