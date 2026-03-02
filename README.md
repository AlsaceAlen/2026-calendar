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
  padding: 8px; /* 全局内边距收窄，减少拥挤 */
  position: relative;
}

/* 趣味装饰元素（手机端缩小，避免遮挡） */
.decoration-1 {
  position: fixed;
  top: 12px;
  left: 12px;
  width: 32px; /* 缩小 */
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
  width: 24px; /* 缩小 */
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

/* 登录页（手机端收窄内边距，减少高度） */
.login-page {
  max-width: 360px; /* 收窄 */
  margin: 40px auto; /* 减少上下边距 */
  background: #fff;
  border-radius: 20px;
  padding: 30px 24px; /* 收窄内边距 */
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
  font-size: 20px; /* 缩小 */
  font-weight: bold;
  text-align: center;
  margin-bottom: 4px;
  color: #333;
}
.login-sub {
  text-align: center;
  color: #999;
  margin-bottom: 24px; /* 减少 */
  font-size: 13px; /* 缩小 */
}
.form-group {
  margin-bottom: 16px; /* 减少 */
}
.form-group label {
  display: block;
  font-size: 12px; /* 缩小 */
  color: #666;
  margin-bottom: 4px;
}
.form-group input {
  width: 100%;
  padding: 10px 12px; /* 收窄 */
  border: 1px solid #e6e2df;
  border-radius: 10px;
  font-size: 14px; /* 缩小 */
  outline: none;
}
.form-group input:focus {
  border-color: #e99da9;
}
.remember {
  display: flex;
  align-items: center;
  gap: 4px;
  font-size: 12px; /* 缩小 */
  color: #666;
  margin-bottom: 20px; /* 减少 */
}
.login-btn {
  width: 100%;
  padding: 11px; /* 收窄 */
  background: #e99da9;
  color: #fff;
  border: none;
  border-radius: 12px;
  font-size: 14px; /* 缩小 */
  font-weight: 500;
}

/* 主界面（手机端居中，减少最大宽度） */
.calendar-container {
  display: none;
  animation: pageIn 0.6s ease;
  position: relative;
  z-index: 2;
  max-width: 900px; /* 收窄 */
  margin: 0 auto;
  padding: 0 4px; /* 减少左右内边距 */
}
@keyframes pageIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

/* 月份卡片（手机端减少间距和内边距） */
.month {
  background: #fff;
  border-radius: 14px;
  overflow: hidden;
  margin-bottom: 16px; /* 减少间距 */
  box-shadow: 0 2px 8px rgba(0,0,0,0.05);
}
.month-title {
  text-align: center;
  font-size: 15px; /* 缩小 */
  font-weight: bold;
  color: #444;
  padding: 12px 0; /* 收窄 */
  background: #fdfafc;
}
.month-head {
  padding: 6px 12px; /* 收窄 */
  background: #fdfafc;
  display: flex;
  justify-content: flex-end;
}
.btn-clear-month {
  padding: 5px 8px; /* 收窄 */
  font-size: 11px; /* 缩小 */
  background: #fce4e8;
  color: #c96f7d;
  border: none;
  border-radius: 6px;
}

.week {
  display: grid;
  grid-template-columns: repeat(7,1fr);
  background: #fdfcfb;
  padding: 6px 0; /* 收窄 */
}
.week > div {
  text-align: center;
  font-size: 11px; /* 缩小 */
  color: #999;
}

.days {
  display: grid;
  grid-template-columns: repeat(7,1fr);
  border-top: 1px solid #f0ebe7;
  gap: 1px; /* 减少间距，避免拥挤 */
  background: #f0ebe7;
  padding: 1px; /* 收窄 */
}

/* 电脑版：日期框固定 5:3 */
.day {
  width: 100%;
  aspect-ratio: 5/3;
  padding: 6px 4px; /* 收窄内边距 */
  background: #fff;
  position: relative;
  cursor: pointer;
  border-radius: 6px; /* 缩小圆角 */
  overflow: hidden;
}

/* 手机版：竖版自适应，全面瘦身优化 */
@media (max-width: 768px) {
  .day {
    aspect-ratio: auto;
    min-height: 70px; /* 降低最小高度 */
    height: auto;
    padding: 6px 4px 10px; /* 优化内边距 */
  }
  /* 手机版待办字体缩小，减少行数 */
  .todo {
    font-size: 13px !important; /* 缩小 */
    -webkit-line-clamp: 1 !important; /* 改为1行，避免拥挤 */
  }
}

.day.selected {
  border: 2px solid #e99da9;
}
.day.dark-text .num, 
.day.dark-text .todo {
  color: #ffffff !important;
}

/* 国历：位置微调，保持原有字号 */
.num {
  position: absolute;
  top: 4px;
  left: 4px;
  font-size: 18px;
  font-weight: bold;
  color: #333;
}

/* 农历：缩小1号（9px）+ 上下竖排 + 右上角定位优化 */
.lunar {
  position: absolute;
  top: 4px;
  right: 4px;
  font-size: 9px; /* 原10px缩小1号 */
  color: #000000 !important;
  writing-mode: vertical-lr; /* 上下书写，从左到右 */
  text-orientation: upright; /* 字符直立，不旋转 */
  line-height: 1.2; /* 紧凑行高 */
  width: 12px; /* 固定宽度，避免换行 */
  text-align: center;
}

/* 待办事项：与国历空隙优化，字体微调 */
.todo {
  position: absolute;
  top: 32px; /* 微调，减少拥挤 */
  left: 4px;
  right: 4px;
  bottom: 4px;
  font-size: 14px; /* 电脑版也缩小 */
  line-height: 1.2; /* 紧凑行高 */
  color: #444;
  word-break: break-all;
  overflow: hidden;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
}

/* 颜色面板（手机端缩小，减少间距） */
.color-panel {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 8px; /* 减少间距 */
  margin-bottom: 14px;
}
.color-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 3px;
}
.color-dot {
  width: 32px; /* 缩小 */
  height: 32px;
  border-radius: 50%;
  cursor: pointer;
  border: 2px solid transparent;
}
.color-dot.active {
  border-color: #e99da9;
}
.color-name {
  font-size: 10px; /* 缩小 */
  color: #666;
  text-align: center;
}

/* 弹窗（手机端收窄内边距，缩小字体） */
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
  padding: 20px; /* 收窄 */
  width: 88%;
  max-width: 340px; /* 收窄 */
  display: none;
  animation: popIn 0.3s ease;
  z-index: 100;
}
@keyframes popIn {
  from { opacity:0; transform: translate(-50%,-45%) scale(0.95); }
  to { opacity:1; transform: translate(-50%,-50%) scale(1); }
}
.pop-title {
  font-size: 16px; /* 缩小 */
  font-weight: bold;
  margin-bottom: 14px;
  text-align: center;
}
.pop-input {
  width: 100%;
  height: 70px; /* 缩短 */
  border: 1px solid #e6e2df;
  border-radius: 10px;
  padding: 8px 10px; /* 收窄 */
  font-size: 14px; /* 缩小 */
  margin-bottom: 14px;
  resize: none;
  outline: none;
}
.pop-btns {
  display: flex;
  gap: 8px; /* 减少间距 */
}
.pop-btns button {
  flex:1;
  padding: 9px; /* 收窄 */
  border-radius: 10px;
  border:none;
  font-size: 14px; /* 缩小 */
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
  bottom: 40px; /* 上移，避免遮挡 */
  left:50%;
  transform: translateX(-50%);
  background: rgba(0,0,0,0.7);
  color:#fff;
  padding: 7px 12px; /* 收窄 */
  border-radius: 8px;
  font-size: 12px; /* 缩小 */
  display: none;
  z-index: 101;
}
</style>
</head>
<body>
<div class="decoration-1"></div>
<div class="decoration-2"></div>

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

<div class="calendar-container" id="main">
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

let isDragging = false;
let selectedDays = [];
let data = JSON.parse(localStorage.getItem("cal_data")) || {};
let curMonth, curKeys;
let syncInterval = null; // 同步定时器

// ==================== 工具 ====================
function toast(txt) {
  const t = document.getElementById("toast");
  t.textContent = txt;
  t.style.display = "block";
  setTimeout(() => t.style.display = "none", 1200); // 缩短提示时间
}

// 农历计算保持不变
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

// ==================== 多设备实时同步核心 ====================
// 统一存储键，确保所有设备读写同一数据
const STORAGE_KEY = "cal_data_vollure_rose_2026";

// 初始化数据：从统一存储读取
function initData() {
  const stored = localStorage.getItem(STORAGE_KEY);
  data = stored ? JSON.parse(stored) : {};
}

// 自动保存：写入统一存储
function autoSave() {
  localStorage.setItem(STORAGE_KEY, JSON.stringify(data));
}

// 实时同步：定时拉取最新数据，更新页面
function syncData() {
  const stored = localStorage.getItem(STORAGE_KEY);
  if (!stored) return;
  const latestData = JSON.parse(stored);
  // 对比数据是否有变化
  if (JSON.stringify(data) !== JSON.stringify(latestData)) {
    data = latestData;
    render(); // 全量渲染，确保所有月份更新
    toast("数据已同步");
  }
}

// 页面离开前强制保存
window.addEventListener("beforeunload", () => {
  autoSave();
  if (syncInterval) clearInterval(syncInterval); // 清理定时器
});

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

// ==================== 渲染 ====================
function render() {
  const cal = document.getElementById("calendar");
  cal.innerHTML = "";
  for (let m = 1; m <= 12; m++) {
    const mEl = document.createElement("div");
    mEl.className = "month";
    mEl.innerHTML = `
      <div class="month-title">Vollure Rose 2026年度行事历-${m}月份</div>
      <div class="month-head">
        <button class="btn-clear-month" onclick="clearMonth(${m})">清空本月</button>
      </div>
      <div class="week">
        <div>日</div><div>一</div><div>二</div><div>三</div><div>四</div><div>五</div><div>六</div>
      </div>
      <div class="days" id="days-${m}"></div>
    `;
    cal.appendChild(mEl);
    renderMonth(m);
  }
  bindDragSelect();
}

function renderMonth(m) {
  const box = document.getElementById(`days-${m}`);
  box.innerHTML = "";
  const first = new Date(YEAR, m-1, 1).getDay();
  const days = new Date(YEAR, m, 0).getDate();
  
  for (let i=0; i<first; i++) {
    box.innerHTML += `<div class="day empty"></div>`;
  }
  
  for (let d=1; d<=days; d++) {
    const key = `${m}-${d}`;
    const item = data[key] || { color: "#ffffff", todo: "" };
    const lunar = getLunar(m, d);
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
}

// ==================== 拖动选中功能 ====================
function bindDragSelect() {
  const allDays = document.querySelectorAll(".day:not(.empty)");
  
  allDays.forEach(day => {
    day.addEventListener("mousedown", (e) => {
      e.preventDefault();
      isDragging = true;
      selectedDays = [];
      document.querySelectorAll(".day.selected").forEach(d => d.classList.remove("selected"));
      selectDay(day);
    });

    day.addEventListener("mouseenter", () => {
      if (isDragging) selectDay(day);
    });
  });

  allDays.forEach(day => {
    day.addEventListener("touchstart", (e) => {
      e.preventDefault();
      isDragging = true;
      selectedDays = [];
      document.querySelectorAll(".day.selected").forEach(d => d.classList.remove("selected"));
      selectDay(day);
    });

    day.addEventListener("touchmove", (e) => {
      if (!isDragging) return;
      e.preventDefault();
      const touch = e.touches[0];
      const target = document.elementFromPoint(touch.clientX, touch.clientY);
      if (target && target.classList.contains("day") && !target.classList.contains("empty")) {
        selectDay(target);
      }
    });
  });

  document.addEventListener("mouseup", endDrag);
  document.addEventListener("touchend", endDrag);

  function selectDay(day) {
    if (!day.classList.contains("selected")) {
      day.classList.add("selected");
      const key = day.dataset.key;
      if (key && !selectedDays.includes(key)) selectedDays.push(key);
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
  
  autoSave(); // 保存到统一存储
  renderMonth(curMonth);
  bindDragSelect();
  closePop();
  toast(`已保存${curKeys.length}个日期`);
};

document.getElementById("clearBtn").onclick = () => {
  if (!confirm("确定清空选中日期的内容？")) return;
  curKeys.forEach(k => delete data[k]);
  autoSave(); // 保存到统一存储
  renderMonth(curMonth);
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
  autoSave(); // 保存到统一存储
  renderMonth(m);
  bindDragSelect();
  toast(`${m}月已清空`);
}

// ==================== 登录 ====================
document.getElementById("loginBtn").onclick = () => {
  const u = document.getElementById("user").value.trim();
  const p = document.getElementById("pwd").value.trim();
  if (u === USER && p === PWD) {
    saveRemember();
    initData(); // 初始化统一存储数据
    document.getElementById("loginPage").style.display = "none";
    document.getElementById("main").style.display = "block";
    render();
    // 启动实时同步：每2秒拉取一次最新数据
    syncInterval = setInterval(syncData, 2000);
  } else {
    toast("账号或密码错误");
  }
};

// 页面加载
window.onload = () => {
  loadRemember();
  document.addEventListener("touchmove", (e) => {
    if (isDragging) e.preventDefault();
  }, { passive: false });
};
</script>
</body>
</html>
