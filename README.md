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
  padding: 10px;
  position: relative;
}

/* 趣味装饰元素 */
.decoration-1 {
  position: fixed;
  top: 20px;
  left: 20px;
  width: 40px;
  height: 40px;
  background: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='%23e99da9'%3E%3Cpath d='M12 21.35l-1.45-1.32C5.4 15.36 2 12.28 2 8.5 2 5.42 4.42 3 7.5 3c1.74 0 3.41.81 4.5 2.09C13.09 3.81 14.76 3 16.5 3 19.58 3 22 5.42 22 8.5c0 3.78-3.4 6.86-8.55 11.54L12 21.35z'/%3E%3C/svg%3E") center no-repeat;
  background-size: contain;
  opacity: 0.6;
  z-index: 1;
  animation: float 3s ease-in-out infinite;
}
.decoration-2 {
  position: fixed;
  bottom: 20px;
  right: 20px;
  width: 30px;
  height: 30px;
  background: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='%237a947f'%3E%3Cpath d='M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm0 18c-4.41 0-8-3.59-8-8s3.59-8 8-8 8 3.59 8 8-3.59 8-8 8zm-1-13h2v6h-2zm0 8h2v2h-2z'/%3E%3C/svg%3E") center no-repeat;
  background-size: contain;
  opacity: 0.6;
  z-index: 1;
  animation: rotate 8s linear infinite;
}
@keyframes float {
  0% { transform: translateY(0px); }
  50% { transform: translateY(-10px); }
  100% { transform: translateY(0px); }
}
@keyframes rotate {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}

/* 登录页 */
.login-page {
  max-width: 380px;
  margin: 70px auto;
  background: #fff;
  border-radius: 24px;
  padding: 40px 30px;
  box-shadow: 0 6px 20px rgba(0,0,0,0.08);
  animation: fadeIn 0.5s ease;
  position: relative;
  z-index: 2;
}
@keyframes fadeIn {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}
.login-title {
  font-size: 22px;
  font-weight: bold;
  text-align: center;
  margin-bottom: 6px;
  color: #333;
}
.login-sub {
  text-align: center;
  color: #999;
  margin-bottom: 30px;
  font-size: 14px;
}
.form-group {
  margin-bottom: 20px;
}
.form-group label {
  display: block;
  font-size: 13px;
  color: #666;
  margin-bottom: 6px;
}
.form-group input {
  width: 100%;
  padding: 12px 14px;
  border: 1px solid #e6e2df;
  border-radius: 12px;
  font-size: 15px;
  outline: none;
}
.form-group input:focus {
  border-color: #e99da9;
}
.remember {
  display: flex;
  align-items: center;
  gap: 6px;
  font-size: 13px;
  color: #666;
  margin-bottom: 24px;
}
.login-btn {
  width: 100%;
  padding: 13px;
  background: #e99da9;
  color: #fff;
  border: none;
  border-radius: 14px;
  font-size: 15px;
  font-weight: 500;
}

/* 主界面 */
.calendar-container {
  display: none;
  animation: pageIn 0.6s ease;
  position: relative;
  z-index: 2;
}
@keyframes pageIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

/* 月份卡片 */
.month {
  background: #fff;
  border-radius: 16px;
  overflow: hidden;
  margin-bottom: 22px;
  box-shadow: 0 3px 10px rgba(0,0,0,0.05);
}
/* 月份标题：上方居中 */
.month-title {
  text-align: center;
  font-size: 16px;
  font-weight: bold;
  color: #444;
  padding: 14px 0;
  background: #fdfafc;
}
.month-head {
  padding: 8px 16px;
  background: #fdfafc;
  display: flex;
  justify: flex-end;
}
.btn-clear-month {
  padding: 6px 10px;
  font-size: 12px;
  background: #fce4e8;
  color: #c96f7d;
  border: none;
  border-radius: 8px;
}

.week {
  display: grid;
  grid-template-columns: repeat(7,1fr);
  background: #fdfcfb;
  padding: 8px 0;
}
.week > div {
  text-align: center;
  font-size: 12px;
  color: #999;
}

.days {
  display: grid;
  grid-template-columns: repeat(7,1fr);
  border-top: 1px solid #f0ebe7;
  gap: 2px;
  background: #f0ebe7;
  padding: 2px;
}
/* 日期框：圆角矩形 + 5:3比例 */
.day {
  width: 100%;
  aspect-ratio: 5/3;
  padding: 8px 6px;
  background: #fff;
  position: relative;
  cursor: pointer;
  border-radius: 8px;
  overflow: hidden;
}
/* 选中状态样式 */
.day.selected {
  border: 2px solid #e99da9;
}
/* 深色背景文字变白 */
.day.dark-text .num, 
.day.dark-text .todo {
  color: #ffffff !important;
}
/* 国历（左上角，字号+3） */
.num {
  position: absolute;
  top: 6px;
  left: 6px;
  font-size: 18px;
  font-weight: bold;
  color: #333;
}
/* 农历（右上角，黑色） */
.lunar {
  position: absolute;
  top: 6px;
  right: 6px;
  font-size: 10px;
  color: #000000 !important;
}
/* 待办事项：与国历空隙加大 */
.todo {
  position: absolute;
  top: 36px;
  left: 6px;
  right: 6px;
  bottom: 4px;
  font-size: 15px;
  line-height: 1.3;
  color: #444;
  word-break: break-all;
  overflow: hidden;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
}

/* 颜色面板 3行3列 */
.color-panel {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 10px;
  margin-bottom: 16px;
}
.color-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 4px;
}
.color-dot {
  width: 36px;
  height: 36px;
  border-radius: 50%;
  cursor: pointer;
  border: 2px solid transparent;
}
.color-dot.active {
  border-color: #e99da9;
}
.color-name {
  font-size: 11px;
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
  border-radius: 18px;
  padding: 24px;
  width: 86%;
  max-width: 360px;
  display: none;
  animation: popIn 0.3s ease;
  z-index: 100;
}
@keyframes popIn {
  from { opacity:0; transform: translate(-50%,-45%) scale(0.95); }
  to { opacity:1; transform: translate(-50%,-50%) scale(1); }
}
.pop-title {
  font-size: 17px;
  font-weight: bold;
  margin-bottom: 16px;
  text-align: center;
}
.pop-input {
  width: 100%;
  height: 80px;
  border: 1px solid #e6e2df;
  border-radius: 12px;
  padding: 10px 12px;
  font-size: 15px;
  margin-bottom: 16px;
  resize: none;
  outline: none;
}
.pop-btns {
  display: flex;
  gap: 10px;
}
.pop-btns button {
  flex:1;
  padding: 11px;
  border-radius: 12px;
  border:none;
  font-size: 15px;
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
  bottom: 60px;
  left:50%;
  transform: translateX(-50%);
  background: rgba(0,0,0,0.7);
  color:#fff;
  padding: 8px 14px;
  border-radius: 10px;
  font-size: 13px;
  display: none;
  z-index: 101;
}
</style>
</head>
<body>
<!-- 趣味装饰 -->
<div class="decoration-1"></div>
<div class="decoration-2"></div>

<!-- 登录 -->
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

<!-- 日历 -->
<div class="calendar-container" id="main">
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

<div class="toast" id="toast"></div>

<script>
// ==================== 配置 ====================
const YEAR = 2026;
const USER = "rose001";
const PWD = "123456";

// 颜色配置（新增深色标记）
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

// ==================== 工具 ====================
function toast(txt) {
  const t = document.getElementById("toast");
  t.textContent = txt;
  t.style.display = "block";
  setTimeout(() => t.style.display = "none", 1500);
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

// ==================== 数据 ====================
let data = JSON.parse(localStorage.getItem("cal_data")) || {};
let curMonth, curKeys;

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
  // 绑定拖动选中事件
  bindDragSelect();
}

function renderMonth(m) {
  const box = document.getElementById(`days-${m}`);
  box.innerHTML = "";
  const first = new Date(YEAR, m-1, 1).getDay();
  const days = new Date(YEAR, m, 0).getDate();
  
  // 填充月初空白
  for (let i=0; i<first; i++) {
    box.innerHTML += `<div class="day empty"></div>`;
  }
  
  // 填充日期
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

  // 移动端触屏
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

  // 结束拖动
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

  // 单击日期
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

// 确定保存
document.getElementById("ok").onclick = () => {
  const activeDot = document.querySelector(".color-dot.active");
  if (!activeDot) return;
  const color = activeDot.dataset.color;
  const todo = document.getElementById("todoInput").value.trim();
  
  curKeys.forEach(k => {
    data[k] = { color, todo };
  });
  
  localStorage.setItem("cal_data", JSON.stringify(data));
  renderMonth(curMonth);
  bindDragSelect();
  closePop();
  toast(`已为${curKeys.length}个日期保存内容`);
};

// 清除当前选中日期内容
document.getElementById("clearBtn").onclick = () => {
  if (!confirm("确定清空选中日期的内容？")) return;
  curKeys.forEach(k => {
    delete data[k];
  });
  localStorage.setItem("cal_data", JSON.stringify(data));
  renderMonth(curMonth);
  bindDragSelect();
  closePop();
  toast(`已清空${curKeys.length}个日期内容`);
};

// 取消
document.getElementById("cancel").onclick = closePop;

// 点击遮罩关闭
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
  localStorage.setItem("cal_data", JSON.stringify(data));
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
    document.getElementById("loginPage").style.display = "none";
    document.getElementById("main").style.display = "block";
    render();
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
