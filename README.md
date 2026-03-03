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
  padding: 8px;
  position: relative;
  overflow-x: hidden;
}

/* 趣味装饰元素 */
.decoration-1 {
  position: fixed;
  top: 12px;
  left: 12px;
  width: 32px;
  height: 32px;
  background: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='%23e99da9'%3E%3Cpath d='M12 21.35l-1.45-1.32C5.4 15.36 2 12.28 2 8.5 2 5.42 4.42 3 7.5 3c1.74 0 3.41.81 4.5 2.09C13.09 3.81 14.76 3 16.5 3 19.58 3 22 5.42 22 8.5c0 3.78-3.4 6.86-8.55 11.54L12 21.35z'/%3E%3C/svg%3E") center no-repeat;
  background-size: contain;
  opacity: 0.6;
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
  opacity: 0.6;
  z-index: 1;
  animation: rotate 8s linear infinite;
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

/* 登录页 */
.login-page {
  max-width: 360px;
  margin: 40px auto;
  background: #fff;
  border-radius: 20px;
  padding: 30px 24px;
  box-shadow: 0 4px 16px rgba(0,0,0,0.08);
  animation: fadeIn 0.5s ease;
  position: relative;
  z-index: 2;
}
@keyframes fadeIn {
  from { opacity: 0; transform: translateY(16px); }
  to { opacity: 1; transform: translateY(0); }
}
.login-title {
  font-size: 20px;
  font-weight: bold;
  text-align: center;
  margin-bottom: 4px;
  color: #333;
}
.login-sub {
  text-align: center;
  color: #999;
  margin-bottom: 24px;
  font-size: 13px;
}
.form-group {
  margin-bottom: 16px;
}
.form-group label {
  display: block;
  font-size: 12px;
  color: #666;
  margin-bottom: 4px;
}
.form-group input {
  width: 100%;
  padding: 10px 12px;
  border: 1px solid #e6e2df;
  border-radius: 10px;
  font-size: 14px;
  outline: none;
}
.form-group input:focus {
  border-color: #e99da9;
}
.remember {
  display: flex;
  align-items: center;
  gap: 4px;
  font-size: 12px;
  color: #666;
  margin-bottom: 20px;
}
.login-btn {
  width: 100%;
  padding: 11px;
  background: #e99da9;
  color: #fff;
  border: none;
  border-radius: 12px;
  font-size: 14px;
  font-weight: 500;
}

/* 新增：月份选择页面 */
.month-select-page {
  display: none;
  animation: fadeIn 0.5s ease;
  position: relative;
  z-index: 2;
  max-width: 90%;
  margin: 40px auto;
  padding: 20px;
}
.month-select-title {
  font-size: 22px;
  font-weight: bold;
  text-align: center;
  margin-bottom: 30px;
  color: #333;
}
/* 12个月网格：2行6列，满屏自适应 */
.month-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
  gap: 15px;
  max-width: 100%;
}
@media (min-width: 768px) {
  .month-grid {
    grid-template-columns: repeat(6, 1fr); /* 电脑端固定6列 */
  }
}
/* 月份卡片缩略图 */
.month-card-thumb {
  background: #fff;
  border-radius: 12px;
  padding: 15px 10px;
  box-shadow: 0 2px 8px rgba(0,0,0,0.05);
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
  color: #444;
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
  background: #f0ebe7;
  font-size: 8px;
  display: flex;
  align-items: center;
  justify-content: center;
}
/* 有标记的日期显示对应色块 */
.thumb-day.marked {
  border: 1px solid #e99da9;
}

/* 主日历界面 - 新增缩放控制栏 */
.calendar-container {
  display: none;
  animation: pageIn 0.6s ease;
  position: relative;
  z-index: 2;
  width: 100%;
  max-width: none;
  margin: 0 auto;
  padding: 0 4px;
  transform-origin: top center; /* 缩放原点：顶部居中 */
}
/* 缩放控制栏 */
.zoom-control {
  padding: 10px 12px;
  text-align: center;
  background: #fff;
  border-radius: 10px;
  margin: 0 auto 15px;
  max-width: 80%;
  box-shadow: 0 2px 8px rgba(0,0,0,0.05);
}
.zoom-slider {
  width: 80%;
  margin: 10px auto;
  accent-color: #e99da9;
}
.zoom-level {
  font-size: 12px;
  color: #666;
}

@keyframes pageIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

/* 月份卡片 - 手机端占屏幕4/5宽度 */
.month {
  background: #fff;
  border-radius: 14px;
  overflow: hidden;
  margin: 0 auto 20px;
  box-shadow: 0 2px 8px rgba(0,0,0,0.05);
  width: 95%;
  max-width: 800px;
}
@media (max-width: 768px) {
  .month {
    width: 80%;
    margin: 0 auto 25px;
  }
}

.month-title {
  text-align: center;
  font-size: 15px;
  font-weight: bold;
  color: #444;
  padding: 12px 0;
  background: #fdfafc;
}
/* 月份操作栏：返回+清空+保存按钮 */
.month-head {
  padding: 8px 12px;
  background: #fdfafc;
  display: flex;
  justify-content: space-between;
  gap: 8px;
}
/* 返回按钮 - 靠左 */
.btn-back {
  padding: 6px 10px;
  font-size: 11px;
  background: #f1eeeb;
  color: #666;
  border: none;
  border-radius: 6px;
  cursor: pointer;
}
/* 清空+保存按钮容器 - 靠右 */
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
  background: #fce4e8;
  color: #c96f7d;
}
.btn-save-month {
  background: #e99da9;
  color: #ffffff;
}

.week {
  display: grid;
  grid-template-columns: repeat(7,1fr);
  background: #fdfcfb;
  padding: 6px 0;
}
.week > div {
  text-align: center;
  font-size: 11px;
  color: #999;
}

.days {
  display: grid;
  grid-template-columns: repeat(7,1fr);
  border-top: 1px solid #f0ebe7;
  gap: 1px;
  background: #f0ebe7;
  padding: 1px;
}

/* 日期框样式 - 恢复拖动多选 + 适配待办显示 */
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

/* 手机端日期框 */
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

/* 选中状态样式恢复 */
.day.selected {
  border: 2px solid #e99da9;
}
.day.dark-text .num, 
.day.dark-text .todo {
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

/* 颜色面板 */
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
  border-color: #e99da9;
}
.color-name {
  font-size: 10px;
  color: #666;
  text-align: center;
}

/* 弹窗 */
.mask {
  position: fixed; inset:0; background:rgba(0,0,0,0.25);
  display: none;
  z-index: 99;
}
.pop {
  position: fixed;
  top: 50%; left:50%;
  transform: translate(-50%,-50%);
  background:#fff;
  border-radius: 16px;
  padding: 20px;
  width: 88%;
  max-width: 340px;
  display: none;
  animation: popIn 0.3s ease;
  z-index: 100;
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
}
.pop-input {
  width: 100%;
  height: 70px;
  border: 1px solid #e6e2df;
  border-radius: 10px;
  padding: 8px 10px;
  font-size: 14px;
  margin-bottom: 14px;
  resize: none;
  outline: none;
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
  background: #f1eeeb;
  color:#666;
}
.btn-cancel {
  background: #f1eeeb;
  color:#666;
}
.btn-ok {
  background: #e99da9;
  color:#fff;
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
</style>
</head>
<body>
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

<!-- 新增：月份选择页面 -->
<div class="month-select-page" id="monthSelectPage">
  <div class="month-select-title">选择月份</div>
  <div class="month-grid" id="monthGrid"></div>
</div>

<!-- 主日历界面 -->
<div class="calendar-container" id="main">
  <!-- 新增：缩放控制栏 -->
  <div class="zoom-control">
    <div class="zoom-level">当前缩放：<span id="zoomValue">100%</span></div>
    <input type="range" min="25" max="100" step="25" value="100" class="zoom-slider" id="zoomSlider">
  </div>
  <div id="calendar"></div>
</div>

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

<div class="toast" id="toast"></div>

<script>
// ==================== 配置 ====================
const YEAR = 2026;
const USER = "rose001";
const PWD = "123456";

const COLORS = [
  { c: "#ffffff", name: "白色", isDark: false },
  { c: "#b86b77", name: "陈酒红", isDark: true },
  { c: "#7a947f", name: "暮光绿", isDark: true },
  { c: "#7b9cb3", name: "梦幻蓝", isDark: true },
  { c: "#949494", name: "冬日灰", isDark: true },
  { c: "#d49a6a", name: "伯爵橙", isDark: true },
  { c: "#e4b4b4", name: "奶茶粉", isDark: false },
  { c: "#f2d392", name: "香草黄", isDark: false },
  { c: "#f7c8d0", name: "泡沫粉", isDark: false }
];

// 拖动选中相关变量
let isDragging = false;
let selectedDays = [];
let touchStartX = 0;
let touchStartY = 0;
const SWIPE_THRESHOLD = 10;

// 缩放相关变量
let currentZoom = 100; // 默认100%
let currentViewMonth = null; // 当前显示的月份

let data = JSON.parse(localStorage.getItem("cal_data_vollure_rose_2026")) || {};
let curMonth, curKeys;
let syncInterval = null;

// ==================== 工具 ====================
function toast(txt) {
  const t = document.getElementById("toast");
  t.textContent = txt;
  t.style.display = "block";
  setTimeout(() => t.style.display = "none", 1200);
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

// ==================== 多设备同步 ====================
const STORAGE_KEY = "cal_data_vollure_rose_2026";

function initData() {
  const stored = localStorage.getItem(STORAGE_KEY);
  data = stored ? JSON.parse(stored) : {};
}

function autoSave() {
  localStorage.setItem(STORAGE_KEY, JSON.stringify(data));
}

// 手动保存本月数据
function saveMonthData(month) {
  autoSave();
  toast(`${month}月数据已手动保存`);
}

function syncData() {
  const stored = localStorage.getItem(STORAGE_KEY);
  if (!stored) return;
  const latestData = JSON.parse(stored);
  if (JSON.stringify(data) !== JSON.stringify(latestData)) {
    data = latestData;
    // 更新月份选择页面的缩略图
    renderMonthSelectPage();
    // 如果当前在日历页面，更新当前月份
    if (currentViewMonth) {
      renderSingleMonth(currentViewMonth);
    }
    toast("数据已同步");
  }
}

window.addEventListener("beforeunload", () => {
  autoSave();
  if (syncInterval) clearInterval(syncInterval);
});

// ==================== 新增：月份选择页面 ====================
// 渲染月份选择页面（12个月缩略图）
function renderMonthSelectPage() {
  const monthGrid = document.getElementById("monthGrid");
  monthGrid.innerHTML = "";
  
  for (let m = 1; m <= 12; m++) {
    const monthCard = document.createElement("div");
    monthCard.className = "month-card-thumb";
    monthCard.dataset.month = m;
    
    // 构建月份缩略日历
    let thumbCalHtml = "";
    const firstDay = new Date(YEAR, m-1, 1).getDay();
    const daysInMonth = new Date(YEAR, m, 0).getDate();
    
    // 填充月初空白
    for (let i=0; i<firstDay; i++) {
      thumbCalHtml += `<div class="thumb-day"></div>`;
    }
    
    // 填充日期（显示有标记的日期色块）
    for (let d=1; d<=daysInMonth; d++) {
      const key = `${m}-${d}`;
      const hasMark = data[key] && (data[key].todo || data[key].color !== "#ffffff");
      const dayClass = hasMark ? "thumb-day marked" : "thumb-day";
      thumbCalHtml += `<div class="${dayClass}" style="${hasMark ? `background:${data[key].color || '#ffffff'}` : ''}"></div>`;
    }
    
    // 月份卡片内容
    monthCard.innerHTML = `
      <div class="month-thumb-title">${m}月份</div>
      <div class="month-thumb-cal">${thumbCalHtml}</div>
    `;
    
    // 点击月份卡片进入对应月份详情
    monthCard.addEventListener("click", () => {
      showSingleMonth(m);
    });
    
    monthGrid.appendChild(monthCard);
  }
}

// 显示单个月份详情
function showSingleMonth(month) {
  currentViewMonth = month;
  // 隐藏月份选择页，显示日历页
  document.getElementById("monthSelectPage").style.display = "none";
  document.getElementById("main").style.display = "block";
  // 渲染单个月份
  renderSingleMonth(month);
  // 重置缩放
  setZoom(100);
  document.getElementById("zoomSlider").value = 100;
  document.getElementById("zoomValue").textContent = "100%";
}

// 渲染单个月份
function renderSingleMonth(month) {
  const calendar = document.getElementById("calendar");
  calendar.innerHTML = "";
  
  const mEl = document.createElement("div");
  mEl.className = "month";
  mEl.innerHTML = `
    <div class="month-title">Vollure Rose 2026年度行事历-${month}月份</div>
    <div class="month-head">
      <button class="btn-back" onclick="backToMonthSelect()">返回</button>
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
  
  // 渲染日期
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
  
  // 绑定拖动选中事件
  bindDragSelect();
}

// 返回月份选择页面
function backToMonthSelect() {
  document.getElementById("main").style.display = "none";
  document.getElementById("monthSelectPage").style.display = "block";
  // 刷新月份缩略图（同步最新数据）
  renderMonthSelectPage();
}

// ==================== 新增：缩放功能 ====================
function setZoom(percent) {
  currentZoom = percent;
  const scale = percent / 100;
  document.getElementById("main").style.transform = `scale(${scale})`;
  document.getElementById("zoomValue").textContent = `${percent}%`;
}

// 绑定缩放滑块事件
function bindZoomEvent() {
  const slider = document.getElementById("zoomSlider");
  slider.addEventListener("input", (e) => {
    const value = parseInt(e.target.value);
    setZoom(value);
  });
}

// ==================== 登录记忆 ====================
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

// ==================== 恢复：拖动选中功能 ====================
function bindDragSelect() {
  const allDays = document.querySelectorAll(".day:not(.empty)");
  
  // 鼠标端：恢复完整拖动多选
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

  // 移动端：恢复拖动多选 + 滑动判定
  allDays.forEach(day => {
    day.addEventListener("touchstart", (e) => {
      touchStartX = e.touches[0].clientX;
      touchStartY = e.touches[0].clientY;
      isDragging = true; // 恢复默认拖动状态
      selectedDays = [];
      document.querySelectorAll(".day.selected").forEach(d => d.classList.remove("selected"));
      selectDay(day);
    });

    day.addEventListener("touchmove", (e) => {
      const touchX = e.touches[0].clientX;
      const touchY = e.touches[0].clientY;
      const diffX = Math.abs(touchX - touchStartX);
      const diffY = Math.abs(touchY - touchStartY);
      
      // 滑动阈值判定：超过则取消拖动
      if (diffX > SWIPE_THRESHOLD || diffY > SWIPE_THRESHOLD) {
        isDragging = false;
        return;
      }
      
      // 恢复拖动多选
      if (isDragging) {
        const target = document.elementFromPoint(touchX, touchY);
        if (target && target.classList.contains("day") && !target.classList.contains("empty")) {
          selectDay(target);
        }
      }
    });
  });

  // 通用结束拖动处理
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

  // 单机/单点日期
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

// ==================== 编辑功能 ====================
function buildColors(activeColor) {
  const box = document.getElementById("colors");
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

  document.querySelectorAll(".color-dot").forEach(dot => {
    dot.onclick = () => {
      document.querySelectorAll(".color-dot").forEach(d => d.classList.remove("active"));
      dot.classList.add("active");
    };
  });
}

document.getElementById("ok").onclick = () => {
  const activeDot = document.querySelector(".color-dot.active");
  if (!activeDot) return;
  const color = activeDot.dataset.color;
  const todo = document.getElementById("todoInput").value.trim();
  
  curKeys.forEach(k => {
    data[k] = { color, todo };
  });
  
  autoSave();
  renderSingleMonth(curMonth); // 刷新当前月份
  bindDragSelect();
  closePop();
  toast(`已保存${curKeys.length}个日期`);
};

document.getElementById("clearBtn").onclick = () => {
  if (!confirm("确定清空选中日期的内容？")) return;
  curKeys.forEach(k => delete data[k]);
  autoSave();
  renderSingleMonth(curMonth); // 刷新当前月份
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
  renderSingleMonth(m); // 刷新当前月份
  bindDragSelect();
  toast(`${m}月已清空`);
}

// ==================== 登录 ====================
document.getElementById("loginBtn").onclick = () => {
  const u = document.getElementById("user").value.trim();
  const p = document.getElementById("pwd").value.trim();
  if (u === USER && p === PWD) {
    saveRemember();
    initData();
    // 隐藏登录页，显示月份选择页
    document.getElementById("loginPage").style.display = "none";
    document.getElementById("monthSelectPage").style.display = "block";
    // 渲染月份选择页面
    renderMonthSelectPage();
    // 绑定缩放事件
    bindZoomEvent();
    // 启动实时同步
    syncInterval = setInterval(syncData, 2000);
  } else {
    toast("账号或密码错误");
  }
};

// 页面加载
window.onload = () => {
  loadRemember();
  document.addEventListener("touchmove", (e) => {}, { passive: true });
};
</script>
</body>
</html>
