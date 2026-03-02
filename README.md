<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<!-- 微信内置浏览器核心适配 -->
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<meta name="format-detection" content="telephone=no, email=no">
<meta http-equiv="X-UA-Compatible" content="IE=edge">
<title>vollure rose 2026年行事历</title>
<style>
/* 全局样式重置+基础美化 */
* {box-sizing: border-box; margin: 0; padding: 0; font-family: PingFang SC, Microsoft YaHei, sans-serif;}
body {
  background: linear-gradient(120deg, #fdfbfb 0%, #ebedee 100%);
  padding: 10px 0;
  -webkit-user-select: none; 
  user-select: none;
  min-height: 100vh;
  touch-action: pan-y; /* 仅允许垂直滑动，防止触发拖动选中 */
}

/* 登录页面样式（核心新增） */
.login-page {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  padding: 20px;
}
.login-header {
  text-align: center;
  margin-bottom: 40px;
}
.login-title {
  font-size: 28px;
  font-weight: bold;
  background: linear-gradient(90deg, #ff9a9e 0%, #fad0c4 99%, #d685ad 100%);
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
  margin-bottom: 8px;
}
.login-subtitle {
  font-size: 16px;
  color: #666;
}
/* 趣味装饰元素 */
.login-decoration {
  width: 80px;
  height: 80px;
  margin: 0 auto 20px;
  background: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='%23ff9a9e'%3E%3Cpath d='M12 21.35l-1.45-1.32C5.4 15.36 2 12.28 2 8.5 2 5.42 4.42 3 7.5 3c1.74 0 3.41.81 4.5 2.09C13.09 3.81 14.76 3 16.5 3 19.58 3 22 5.42 22 8.5c0 3.78-3.4 6.86-8.55 11.54L12 21.35z'/%3E%3C/svg%3E") center no-repeat;
  background-size: contain;
  opacity: 0.8;
  animation: float 3s ease-in-out infinite;
}
@keyframes float {
  0% {transform: translateY(0px);}
  50% {transform: translateY(-10px);}
  100% {transform: translateY(0px);}
}

/* 登录表单样式 */
.login-form {
  background: #fff;
  padding: 30px;
  border-radius: 20px;
  box-shadow: 0 8px 32px rgba(0,0,0,0.1);
  width: 100%;
  max-width: 400px;
}
.form-group {
  margin-bottom: 20px;
}
.form-label {
  display: block;
  font-size: 14px;
  color: #666;
  margin-bottom: 8px;
}
.form-input {
  width: 100%;
  padding: 14px 16px;
  border: 1px solid #e0e0e0;
  border-radius: 12px;
  font-size: 16px;
  transition: all 0.2s ease;
}
.form-input:focus {
  outline: none;
  border-color: #ff9a9e;
  box-shadow: 0 0 0 3px rgba(255,154,158,0.1);
}
/* 记住密码样式 */
.remember-wrap {
  display: flex;
  align-items: center;
  gap: 8px;
  margin-bottom: 15px;
}
.remember-checkbox {
  width: 18px;
  height: 18px;
  accent-color: #ff9a9e;
  cursor: pointer;
}
.remember-label {
  font-size: 14px;
  color: #666;
  cursor: pointer;
}
.login-btn {
  width: 100%;
  padding: 14px;
  border: none;
  border-radius: 12px;
  background: linear-gradient(90deg, #ff9a9e 0%, #fad0c4 99%, #d685ad 100%);
  color: #fff;
  font-size: 16px;
  font-weight: bold;
  cursor: pointer;
  transition: all 0.2s ease;
  margin-top: 10px;
}
.login-btn:active {
  transform: scale(0.98);
}
.error-tip {
  color: #ff3b30;
  font-size: 12px;
  margin-top: 8px;
  display: none;
}

/* 日历主界面（默认隐藏） */
.calendar-container {
  display: none;
  max-width: 100%;
  margin: 0 auto;
  background: #fff;
  border-radius: 16px;
  overflow: hidden;
  box-shadow: 0 8px 24px rgba(0,0,0,0.08);
  margin: 10px;
}
/* 顶部标题美化 */
.calendar-header {
  text-align: center;
  padding: 20px 0;
  background: linear-gradient(90deg, #ff9a9e 0%, #fad0c4 99%, #d685ad 100%);
  color: #fff;
  font-size: 20px;
  font-weight: bold;
  position: relative;
}
.calendar-header::after {
  content: '';
  display: block;
  width: 60px;
  height: 4px;
  background: #fff;
  border-radius: 2px;
  margin: 8px auto 0;
}
/* 按钮栏美化 */
.btns {
  display: flex;
  justify-content: center;
  gap: 12px;
  padding: 15px 10px;
  background: #fff;
}
button {
  padding: 10px 20px;
  border: none;
  border-radius: 20px;
  color: white;
  font-size: 14px;
  cursor: pointer;
  box-shadow: 0 4px 8px rgba(0,0,0,0.1);
  transition: all 0.2s ease;
}
button:active {
  transform: scale(0.95);
}
.btn-save {
  background: linear-gradient(90deg, #667eea 0%, #764ba2 100%);
}
.btn-reset {
  background: linear-gradient(90deg, #fa709a 0%, #fee140 100%);
}
/* 日历主体样式 */
.calendar {
  display: flex;
  flex-direction: column;
  gap: 20px;
  padding: 10px 15px;
}
.month {
  border: 1px solid #f0f0f0;
  border-radius: 12px;
  overflow: hidden;
  background: #fff;
  box-shadow: 0 2px 8px rgba(0,0,0,0.05);
}
/* 月份标题栏 */
.month-top {
  background: #f8f9fa;
  padding: 12px 10px;
  text-align: center;
  border-bottom: 1px solid #f0f0f0;
}
.month-cal-title {
  font-size: 14px;
  color: #999;
  margin-bottom: 4px;
}
.month-title {
  font-size: 18px;
  font-weight: bold;
  color: #333;
}
/* 星期栏 */
.week {
  display: grid;
  grid-template-columns: repeat(7, 1fr);
  background: #f8f9fa;
  font-size: 12px;
  color: #666;
}
.week div {
  padding: 8px 0;
  text-align: center;
  font-weight: bold;
}
/* 日期格子（核心：支持合并显示） */
.days {
  display: grid;
  grid-template-columns: repeat(7, 1fr);
  gap: 1px;
  background: #f0f0f0;
  position: relative;
}
.day {
  background: #fff;
  min-height: 60px;
  padding: 6px;
  position: relative;
  cursor: pointer;
  font-size: 12px;
  transition: all 0.2s ease;
  z-index: 1; /* 默认层级 */
}
.day:hover, .day:active {
  background: #f8f9fa;
}
.day .num {
  font-weight: bold;
  font-size: 14px;
  margin-bottom: 4px;
  color: #333;
  z-index: 2;
  position: relative;
}
.day .todo {
  font-size: 11px;
  line-height: 1.3;
  overflow: hidden;
  max-height: 36px;
  color: #555;
  z-index: 2;
  position: relative;
}
/* 合并待办的样式（仅合并待办，保留日期） */
.merge-todo {
  position: absolute;
  background: inherit;
  border-radius: 8px;
  padding: 4px;
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 3;
  box-shadow: 0 1px 3px rgba(0,0,0,0.1);
  /* 调整位置，不遮挡日期 */
  top: 20px !important;
  height: calc(100% - 20px) !important;
}
.day.empty {
  background: #fafafa;
  cursor: default;
}
/* 深色背景文字反白 */
.day.dark .num, .day.dark .todo,
.day.dark .merge-todo {
  color: #fff !important;
}
/* 选中状态 */
.day.selected {
  background: #e5f0ff;
  border: 2px solid #667eea;
}
/* 编辑弹窗样式 */
.mask {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0,0,0,0.5);
  display: none;
  z-index: 99;
  backdrop-filter: blur(2px);
}
.panel {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background: #fff;
  padding: 24px;
  border-radius: 16px;
  width: 90%;
  max-width: 400px;
  display: none;
  z-index: 100;
  box-shadow: 0 8px 32px rgba(0,0,0,0.15);
  animation: popup 0.3s ease;
}
/* 弹窗动画 */
@keyframes popup {
  from {
    opacity: 0;
    transform: translate(-50%, -45%);
  }
  to {
    opacity: 1;
    transform: translate(-50%, -50%);
  }
}
.panel h4 {
  margin-bottom: 20px;
  font-size: 18px;
  color: #333;
  text-align: center;
  font-weight: bold;
}
/* 颜色选择区（圆形+两行对齐+文字在下） */
.color-row-wrap {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 15px 10px;
  margin-bottom: 20px;
}
.color-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 6px;
}
.color-dot {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  border: 3px solid #fff;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
  cursor: pointer;
  transition: all 0.2s ease;
}
.color-dot.active {
  border-color: #667eea;
  transform: scale(1.1);
}
.color-name {
  font-size: 12px;
  color: #666;
}
/* 输入框（初始3行高度） */
.todo-input {
  width: 100%;
  padding: 12px;
  border: 1px solid #e0e0e0;
  border-radius: 10px;
  margin-bottom: 20px;
  font-size: 14px;
  min-height: 84px; /* 约3行文字高度 */
  resize: none;
  line-height: 1.4;
}
/* 按钮组 */
.btn-group {
  display: flex;
  gap: 10px;
}
.btn-group button {
  flex: 1;
  padding: 12px 0;
  border-radius: 10px;
  font-size: 16px;
}
.btn-confirm {
  background: linear-gradient(90deg, #667eea 0%, #764ba2 100%);
}
.btn-cancel {
  background: #e0e0e0;
  color: #666;
}
/* 提示框 */
.toast {
  position: fixed;
  bottom: 30px;
  left: 50%;
  transform: translateX(-50%);
  background: rgba(0,0,0,0.7);
  color: #fff;
  padding: 10px 20px;
  border-radius: 20px;
  font-size: 14px;
  display: none;
  z-index: 101;
  animation: fadeIn 0.3s ease;
}
@keyframes fadeIn {
  from {opacity: 0; bottom: 20px;}
  to {opacity: 1; bottom: 30px;}
}
/* 趣味装饰 */
.calendar-decoration {
  position: absolute;
  top: 10px;
  left: 10px;
  width: 30px;
  height: 30px;
  background: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='%23fff'%3E%3Cpath d='M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm0 18c-4.41 0-8-3.59-8-8s3.59-8 8-8 8 3.59 8 8-3.59 8-8 8zm-1-13h2v6h-2zm0 8h2v2h-2z'/%3E%3C/svg%3E") center no-repeat;
  background-size: 24px;
  opacity: 0.8;
}
</style>
</head>
<body>
<!-- 登录页面（默认显示） -->
<div class="login-page" id="loginPage">
  <div class="login-header">
    <div class="login-decoration"></div>
    <h1 class="login-title">vollure rose</h1>
    <p class="login-subtitle">2026年行事历</p>
  </div>
  <div class="login-form">
    <div class="form-group">
      <label class="form-label">登录账号</label>
      <input type="text" class="form-input" id="username" placeholder="请输入账号">
      <div class="error-tip" id="userError">账号格式错误</div>
    </div>
    <div class="form-group">
      <label class="form-label">登录密码</label>
      <input type="password" class="form-input" id="password" placeholder="请输入密码">
      <div class="error-tip" id="pwdError">密码错误</div>
    </div>
    <!-- 新增记住密码功能 -->
    <div class="remember-wrap">
      <input type="checkbox" class="remember-checkbox" id="rememberPwd">
      <label class="remember-label" for="rememberPwd">记住密码（30天）</label>
    </div>
    <button class="login-btn" id="loginBtn">登录</button>
  </div>
</div>

<!-- 日历主界面（默认隐藏） -->
<div class="calendar-container" id="calendarContainer">
  <div class="calendar-header">
    <div class="calendar-decoration"></div>
    vollure rose 2026年行事历
  </div>
  <div class="btns">
    <button class="btn-save" id="saveFile">保存最新日历</button>
    <button class="btn-reset" id="resetBtn">清空所有数据</button>
  </div>
  <div class="calendar" id="calendar"></div>
</div>

<!-- 遮罩层（点击空白处关闭弹窗） -->
<div class="mask" id="mask"></div>
<!-- 编辑弹窗 -->
<div class="panel" id="panel">
  <h4>编辑日期事项</h4>
  <!-- 颜色选择：圆形+两行+文字在下 -->
  <div class="color-row-wrap">
    <div class="color-item">
      <div class="color-dot active" data-c="#FFFFFF" style="background: #FFFFFF;"></div>
      <div class="color-name">纯白色</div>
    </div>
    <div class="color-item">
      <div class="color-dot" data-c="#FFE5E5" style="background: #FFE5E5;"></div>
      <div class="color-name">蜜桃粉</div>
    </div>
    <div class="color-item">
      <div class="color-dot" data-c="#E5F0FF" style="background: #E5F0FF;"></div>
      <div class="color-name">天空蓝</div>
    </div>
    <div class="color-item">
      <div class="color-dot" data-c="#E5FFE5" style="background: #E5FFE5;"></div>
      <div class="color-name">薄荷绿</div>
    </div>
    <div class="color-item">
      <div class="color-dot" data-c="#FFF5E5" style="background: #FFF5E5;"></div>
      <div class="color-name">芝士黄</div>
    </div>
    <div class="color-item">
      <div class="color-dot" data-c="#F5E5FF" style="background: #F5E5FF;"></div>
      <div class="color-name">薰衣草紫</div>
    </div>
    <div class="color-item">
      <div class="color-dot" data-c="#FFB3E5" style="background: #FFB3E5;"></div>
      <div class="color-name">樱花粉</div>
    </div>
    <div class="color-item">
      <div class="color-dot" data-c="#B3E5FF" style="background: #B3E5FF;"></div>
      <div class="color-name">冰川蓝</div>
    </div>
  </div>
  <!-- 输入框：初始3行高度 -->
  <textarea class="todo-input" id="todoText" placeholder="输入待办事项（如：出差、开会）"></textarea>
  <!-- 按钮组 -->
  <div class="btn-group">
    <button class="btn-confirm" id="apply">确定</button>
    <button class="btn-cancel" id="cancel">取消</button>
  </div>
</div>

<div class="toast" id="toast"></div>

<script>
// 登录相关配置
const CORRECT_USERNAME = "vollurerose001";
const CORRECT_PASSWORD = "linguiying";
const REMEMBER_DAYS = 30; // 记住密码有效期（天）

// ========== 新增：记住密码功能 ==========
// 读取记住的密码
function loadRememberedPwd() {
  const rememberData = JSON.parse(localStorage.getItem('CAL2026_REMEMBER_PWD')) || {};
  // 检查是否过期
  if (rememberData.expireTime && new Date().getTime() < rememberData.expireTime) {
    document.getElementById('username').value = rememberData.username || '';
    document.getElementById('password').value = rememberData.password || '';
    document.getElementById('rememberPwd').checked = true;
  } else {
    // 过期则清除
    localStorage.removeItem('CAL2026_REMEMBER_PWD');
  }
}

// 保存记住的密码
function saveRememberedPwd(username, password) {
  const expireTime = new Date().getTime() + REMEMBER_DAYS * 24 * 60 * 60 * 1000;
  localStorage.setItem('CAL2026_REMEMBER_PWD', JSON.stringify({
    username: username,
    password: password,
    expireTime: expireTime
  }));
}

// 页面加载时读取记住的密码
window.addEventListener('load', loadRememberedPwd);

// 登录逻辑
document.getElementById('loginBtn').addEventListener('click', function() {
  const username = document.getElementById('username').value.trim();
  const password = document.getElementById('password').value.trim();
  const rememberPwd = document.getElementById('rememberPwd').checked;
  const userError = document.getElementById('userError');
  const pwdError = document.getElementById('pwdError');
  
  // 重置错误提示
  userError.style.display = 'none';
  pwdError.style.display = 'none';
  
  // 验证账号
  if (username !== CORRECT_USERNAME) {
    userError.textContent = "账号错误，请输入正确的账号";
    userError.style.display = 'block';
    return;
  }
  
  // 验证密码
  if (password !== CORRECT_PASSWORD) {
    pwdError.textContent = "密码错误，请输入正确的密码";
    pwdError.style.display = 'block';
    return;
  }
  
  // 记住密码
  if (rememberPwd) {
    saveRememberedPwd(username, password);
  } else {
    localStorage.removeItem('CAL2026_REMEMBER_PWD');
  }
  
  // 登录成功：隐藏登录页，显示日历页
  document.getElementById('loginPage').style.display = 'none';
  document.getElementById('calendarContainer').style.display = 'block';
  showToast('登录成功！');
  
  // 首次渲染日历
  renderCalendar();
});

// 日历核心逻辑
const YEAR = 2026;
const monthNames = "1月,2月,3月,4月,5月,6月,7月,8月,9月,10月,11月,12月".split(",");
const weeks = "日,一,二,三,四,五,六".split(",");
const holidays = {"1-1":"元旦","2-16":"除夕","2-17":"春节","3-3":"元宵节","4-5":"清明","5-1":"劳动节","6-19":"端午","10-1":"国庆"};

// 存储数据：兼容微信内置浏览器
let calendarData = JSON.parse(localStorage.getItem('CAL2026_WECHAT')) || {};
// 多选相关变量
let isSelecting = false; // 是否正在拖动选择
let selectedDateKeys = []; // 选中的日期key
let startDayEl = null; // 拖动起始元素
let isDragging = false; // 是否真的在拖动（区分点击和拖动）
let isScrolling = false; // 新增：是否正在滑动页面

// ========== 新增：滑动状态检测 ==========
// 检测页面滑动状态
function initScrollDetection() {
  const calendarContainer = document.getElementById('calendarContainer');
  
  // 移动端触摸滑动检测
  let touchStartY = 0;
  let touchMoveY = 0;
  
  calendarContainer.addEventListener('touchstart', (e) => {
    touchStartY = e.touches[0].clientY;
    // 开始触摸，标记可能要滑动
    isScrolling = true;
    // 清除之前的延迟判断
    clearTimeout(window.scrollCheckTimer);
  });
  
  calendarContainer.addEventListener('touchmove', (e) => {
    touchMoveY = e.touches[0].clientY;
    // 有垂直移动，判定为滑动中
    if (Math.abs(touchMoveY - touchStartY) > 5) {
      isScrolling = true;
    }
  });
  
  calendarContainer.addEventListener('touchend', () => {
    // 滑动结束后，延迟200ms判定为停止滑动（避免快速点击误判）
    window.scrollCheckTimer = setTimeout(() => {
      isScrolling = false;
    }, 200);
  });
  
  // 鼠标滚轮滑动检测
  calendarContainer.addEventListener('wheel', (e) => {
    if (Math.abs(e.deltaY) > 0) {
      isScrolling = true;
      // 滑动停止后延迟判定
      clearTimeout(window.scrollCheckTimer);
      window.scrollCheckTimer = setTimeout(() => {
        isScrolling = false;
      }, 200);
    }
  });
}

// 判断是否需要文字反白
function isDarkColor(hex) {
  const colorMap = {
    "#FFB3E5": true, // 樱花粉
    "#B3E5FF": true, // 冰川蓝
    "#FFFFFF": false
  };
  return colorMap[hex] || false;
}

// 显示提示框
function showToast(text) {
  const toast = document.getElementById('toast');
  toast.textContent = text;
  toast.style.display = 'block';
  setTimeout(() => toast.style.display = 'none', 1500);
}

// 检测连续日期（同行列）
function getContinuousDays(monthEl) {
  const dayEls = monthEl.querySelectorAll('.day:not(.empty)');
  const continuousGroups = [];
  let currentGroup = [];

  // 遍历所有日期，按行分组（7个为一行）
  const rows = [];
  let currentRow = [];
  dayEls.forEach((el, index) => {
    currentRow.push(el);
    if ((index + 1) % 7 === 0) {
      rows.push(currentRow);
      currentRow = [];
    }
  });
  if (currentRow.length > 0) rows.push(currentRow);

  // 检查每行内的连续相同待办
  rows.forEach(row => {
    currentGroup = [row[0]];
    for (let i = 1; i < row.length; i++) {
      const prevEl = row[i-1];
      const currEl = row[i];
      const prevKey = prevEl.dataset.key;
      const currKey = currEl.dataset.key;
      const prevData = calendarData[prevKey] || { todo: '', color: '#FFFFFF' };
      const currData = calendarData[currKey] || { todo: '', color: '#FFFFFF' };

      // 同行列、待办相同、颜色相同 → 加入当前组
      if (prevData.todo && prevData.todo === currData.todo && prevData.color === currData.color) {
        currentGroup.push(currEl);
      } else {
        if (currentGroup.length > 1) {
          continuousGroups.push(currentGroup);
        }
        currentGroup = [currEl];
      }
    }
    if (currentGroup.length > 1) {
      continuousGroups.push(currentGroup);
    }
  });

  return continuousGroups;
}

// 渲染合并待办（仅合并待办，保留日期）
function renderMergeTodos(monthEl) {
  // 先清除已有的合并待办
  monthEl.querySelectorAll('.merge-todo').forEach(el => el.remove());
  
  const continuousGroups = getContinuousDays(monthEl);
  const daysContainer = monthEl.querySelector('.days');

  continuousGroups.forEach(group => {
    if (group.length < 2) return;

    // 获取组内第一个和最后一个元素的位置
    const firstEl = group[0];
    const lastEl = group[group.length - 1];
    const firstRect = firstEl.getBoundingClientRect();
    const lastRect = lastEl.getBoundingClientRect();
    const containerRect = daysContainer.getBoundingClientRect();

    // 计算合并待办的位置和尺寸（避开日期数字区域）
    const top = firstRect.top - containerRect.top;
    const left = firstRect.left - containerRect.left;
    const width = lastRect.right - firstRect.left;
    const height = firstRect.height;

    // 创建合并待办元素
    const mergeEl = document.createElement('div');
    mergeEl.className = 'merge-todo';
    mergeEl.style.top = `${top}px`;
    mergeEl.style.left = `${left}px`;
    mergeEl.style.width = `${width}px`;
    mergeEl.style.height = `${height}px`;
    mergeEl.style.background = calendarData[firstEl.dataset.key].color;
    mergeEl.textContent = calendarData[firstEl.dataset.key].todo;

    // 隐藏组内每个元素的单独待办（保留日期）
    group.forEach(el => {
      el.querySelector('.todo').style.display = 'none';
      // 确保日期数字始终显示
      el.querySelector('.num').style.display = 'block';
    });

    daysContainer.appendChild(mergeEl);
  });
}

// 渲染日历
function renderCalendar() {
  const calendarEl = document.getElementById('calendar');
  calendarEl.innerHTML = '';

  for (let month = 0; month < 12; month++) {
    const firstDay = new Date(YEAR, month, 1).getDay();
    const daysInMonth = new Date(YEAR, month + 1, 0).getDate();
    const monthDiv = document.createElement('div');
    monthDiv.className = 'month';

    // 月份标题栏
    monthDiv.innerHTML = `
      <div class="month-top">
        <div class="month-cal-title">2026年行事历</div>
        <div class="month-title">${monthNames[month]}</div>
      </div>
      <div class="week">${weeks.map(day => `<div>${day}</div>`).join('')}</div>
    `;

    // 日期格子容器
    const daysDiv = document.createElement('div');
    daysDiv.className = 'days';

    // 填充月初空白
    for (let i = 0; i < firstDay; i++) {
      daysDiv.innerHTML += '<div class="day empty"></div>';
    }

    // 填充日期
    for (let day = 1; day <= daysInMonth; day++) {
      const dateKey = `${month + 1}-${day}`;
      const dateData = calendarData[dateKey] || { color: '#FFFFFF', todo: '' };
      const isDark = isDarkColor(dateData.color) ? 'dark' : '';
      const holidayText = holidays[dateKey] ? `<br><span style="color:#ff3b30">${holidays[dateKey]}</span>` : '';

      daysDiv.innerHTML += `
        <div class="day ${isDark}" data-key="${dateKey}" style="background:${dateData.color}">
          <div class="num">${day}</div>
          <div class="todo">${dateData.todo}${holidayText}</div>
        </div>
      `;
    }

    monthDiv.appendChild(daysDiv);
    calendarEl.appendChild(monthDiv);

    // 渲染合并待办
    renderMergeTodos(monthDiv);
  }

  // 初始化滑动检测
  initScrollDetection();
  // 绑定日期事件
  bindDayEvents();
}

// 绑定日期事件：仅当页面停止滑动时触发点击/拖动
function bindDayEvents() {
  const days = document.querySelectorAll('.day:not(.empty)');
  const mask = document.getElementById('mask');
  const panel = document.getElementById('panel');

  days.forEach(dayEl => {
    // 鼠标端拖动选中（增加滑动状态判断）
    dayEl.addEventListener('mousedown', (e) => {
      // 滑动中，不触发任何操作
      if (isScrolling) return;
      
      e.preventDefault();
      isSelecting = true;
      isDragging = false;
      startDayEl = dayEl;
      selectedDateKeys = [dayEl.dataset.key];
      // 清除所有选中状态
      document.querySelectorAll('.day.selected').forEach(el => el.classList.remove('selected'));
      dayEl.classList.add('selected');
    });

    dayEl.addEventListener('mousemove', (e) => {
      // 滑动中或未开始选择，不触发
      if (isScrolling || !isSelecting) return;
      
      isDragging = true;
      const target = document.elementFromPoint(e.clientX, e.clientY);
      if (target && target.classList.contains('day') && !target.classList.contains('empty')) {
        const key = target.dataset.key;
        if (!selectedDateKeys.includes(key)) {
          selectedDateKeys.push(key);
          target.classList.add('selected');
        }
      }
    });

    // 移动端触屏拖动选中（增加滑动状态判断）
    dayEl.addEventListener('touchstart', (e) => {
      // 滑动中，不触发任何操作
      if (isScrolling) return;
      
      e.preventDefault();
      isSelecting = true;
      isDragging = false;
      startDayEl = dayEl;
      selectedDateKeys = [dayEl.dataset.key];
      document.querySelectorAll('.day.selected').forEach(el => el.classList.remove('selected'));
      dayEl.classList.add('selected');
    });

    dayEl.addEventListener('touchmove', (e) => {
      // 滑动中或未开始选择，不触发
      if (isScrolling || !isSelecting) return;
      
      isDragging = true;
      const touch = e.touches[0];
      const target = document.elementFromPoint(touch.clientX, touch.clientY);
      if (target && target.classList.contains('day') && !target.classList.contains('empty')) {
        const key = target.dataset.key;
        if (!selectedDateKeys.includes(key)) {
          selectedDateKeys.push(key);
          target.classList.add('selected');
        }
      }
    });

    // 点击/拖动结束
    dayEl.addEventListener('mouseup', handleSelectEnd);
    dayEl.addEventListener('touchend', handleSelectEnd);
  });

  // 全局结束选择
  document.addEventListener('mouseup', handleSelectEnd);
  document.addEventListener('touchend', handleSelectEnd);

  // 处理选择结束逻辑
  function handleSelectEnd() {
    if (!isSelecting) return;
    isSelecting = false;

    // 拖动选中 → 打开编辑面板
    if (isDragging && selectedDateKeys.length > 0) {
      openEditPanel();
    } 
    // 纯点击 → 打开编辑面板
    else if (!isDragging && startDayEl) {
      openEditPanel();
    }

    // 重置状态
    isDragging = false;
    startDayEl = null;
  }

  // 点击空白处关闭面板
  mask.addEventListener('click', () => {
    closeEditPanel();
    // 清除选中状态
    document.querySelectorAll('.day.selected').forEach(el => el.classList.remove('selected'));
    selectedDateKeys = [];
  });

  // 阻止面板内点击触发遮罩关闭
  panel.addEventListener('click', (e) => {
    e.stopPropagation();
  });
}

// 打开编辑面板（清空输入框+默认白色）
function openEditPanel() {
  const panel = document.getElementById('panel');
  const mask = document.getElementById('mask');
  const todoInput = document.getElementById('todoText');
  const colorDots = document.querySelectorAll('.color-dot');

  // 1. 清空输入框
  todoInput.value = '';
  // 2. 颜色默认选中白色
  colorDots.forEach(dot => dot.classList.remove('active'));
  document.querySelector('.color-dot[data-c="#FFFFFF"]').classList.add('active');
  
  // 显示面板和遮罩
  panel.style.display = 'block';
  mask.style.display = 'block';
}

// 关闭编辑面板
function closeEditPanel() {
  document.getElementById('panel').style.display = 'none';
  document.getElementById('mask').style.display = 'none';
  // 清除选中状态
  document.querySelectorAll('.day.selected').forEach(el => el.classList.remove('selected'));
  selectedDateKeys = [];
}

// 颜色选择事件（圆形色块）
document.querySelectorAll('.color-dot').forEach(dot => {
  dot.addEventListener('click', () => {
    document.querySelectorAll('.color-dot').forEach(d => d.classList.remove('active'));
    dot.classList.add('active');
  });
});

// 取消按钮事件
document.getElementById('cancel').addEventListener('click', closeEditPanel);

// 确定保存
document.getElementById('apply').addEventListener('click', () => {
  if (selectedDateKeys.length === 0) return;
  
  // 获取选中的颜色和输入的文字
  const selectedColor = document.querySelector('.color-dot.active').dataset.c;
  const todoText = document.getElementById('todoText').value.trim();
  
  // 保存数据
  selectedDateKeys.forEach(key => {
    calendarData[key] = { color: selectedColor, todo: todoText };
  });
  localStorage.setItem('CAL2026_WECHAT', JSON.stringify(calendarData));
  
  // 重新渲染+关闭面板
  renderCalendar();
  closeEditPanel();
  showToast(`已为${selectedDateKeys.length}个日期保存事项！`);
});

// 保存日历文件
document.getElementById('saveFile').addEventListener('click', () => {
  const fullHTML = `<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<meta name="format-detection" content="telephone=no">
<title>vollure rose 2026年行事历（已同步）</title>
<style>
* {box-sizing: border-box; margin: 0; padding: 0; font-family: PingFang SC, Microsoft YaHei, sans-serif;}
body {background: linear-gradient(120deg, #fdfbfb 0%, #ebedee 100%); padding: 10px 0; -webkit-user-select: none; user-select: none; min-height: 100vh; touch-action: pan-y;}
.container {max-width: 100%; margin: 0 auto; background: #fff; border-radius: 16px; overflow: hidden; box-shadow: 0 8px 24px rgba(0,0,0,0.08); margin: 10px;}
.calendar-header {text-align: center; padding: 20px 0; background: linear-gradient(90deg, #ff9a9e 0%, #fad0c4 99%, #d685ad 100%); color: #fff; font-size: 20px; font-weight: bold; position: relative;}
.calendar-header::after {content: ''; display: block; width: 60px; height: 4px; background: #fff; border-radius: 2px; margin: 8px auto 0;}
.btns {display: flex; justify-content: center; gap: 12px; padding: 15px 10px; background: #fff;}
button {padding: 10px 20px; border: none; border-radius: 20px; color: white; font-size: 14px; cursor: pointer; box-shadow: 0 4px 8px rgba(0,0,0,0.1); transition: all 0.2s ease;}
button:active {transform: scale(0.95);}
.btn-save {background: linear-gradient(90deg, #667eea 0%, #764ba2 100%);}
.btn-reset {background: linear-gradient(90deg, #fa709a 0%, #fee140 100%);}
.calendar {display: flex; flex-direction: column; gap: 20px; padding: 10px 15px;}
.month {border: 1px solid #f0f0f0; border-radius: 12px; overflow: hidden; background: #fff; box-shadow: 0 2px 8px rgba(0,0,0,0.05);}
.month-top {background: #f8f9fa; padding: 12px 10px; text-align: center; border-bottom: 1px solid #f0f0f0;}
.month-cal-title {font-size: 14px; color: #999; margin-bottom: 4px;}
.month-title {font-size: 18px; font-weight: bold; color: #333;}
.week {display: grid; grid-template-columns: repeat(7, 1fr); background: #f8f9fa; font-size: 12px; color: #666;}
.week div {padding: 8px 0; text-align: center; font-weight: bold;}
.days {display: grid; grid-template-columns: repeat(7, 1fr); gap: 1px; background: #f0f0f0; position: relative;}
.day {background: #fff; min-height: 60px; padding: 6px; position: relative; cursor: pointer; font-size: 12px; transition: all 0.2s ease; z-index: 1;}
.day:hover, .day:active {background: #f8f9fa;}
.day .num {font-weight: bold; font-size: 14px; margin-bottom: 4px; color: #333; z-index: 2; position: relative;}
.day .todo {font-size: 11px; line-height: 1.3; overflow: hidden; max-height: 36px; color: #555; z-index: 2; position: relative;}
.merge-todo {position: absolute; background: inherit; border-radius: 8px; padding: 4px; display: flex; align-items: center; justify-content: center; z-index: 3; box-shadow: 0 1px 3px rgba(0,0,0,0.1); top: 20px !important; height: calc(100% - 20px) !important;}
.day.empty {background: #fafafa; cursor: default;}
.day.dark .num, .day.dark .todo, .day.dark .merge-todo {color: #fff !important;}
.day.selected {background: #e5f0ff; border: 2px solid #667eea;}
.mask {position: fixed; top: 0; left: 0; right: 0; bottom: 0; background: rgba(0,0,0,0.5); display: none; z-index: 99; backdrop-filter: blur(2px);}
.panel {position: fixed; top: 50%; left: 50%; transform: translate(-50%, -50%); background: #fff; padding: 30px; border-radius: 16px; width: 90%; max-width: 400px; display: none; z-index: 100; box-shadow: 0 8px 32px rgba(0,0,0,0.15); animation: popup 0.3s ease;}
@keyframes popup {from {opacity: 0; transform: translate(-50%, -45%);} to {opacity: 1; transform: translate(-50%, -50%);}}
.panel h4 {margin-bottom: 20px; font-size: 18px; color: #333; text-align: center; font-weight: bold;}
.color-row-wrap {display: grid; grid-template-columns: repeat(4, 1fr); gap: 15px 10px; margin-bottom: 20px;}
.color-item {display: flex; flex-direction: column; align-items: center; gap: 6px;}
.color-dot {width: 40px; height: 40px; border-radius: 50%; border: 3px solid #fff; box-shadow: 0 2px 4px rgba(0,0,0,0.1); cursor: pointer; transition: all 0.2s ease;}
.color-dot.active {border-color: #667eea; transform: scale(1.1);}
.color-name {font-size: 12px; color: #666;}
.todo-input {width: 100%; padding: 12px; border: 1px solid #e0e0e0; border-radius: 10px; margin-bottom: 20px; font-size: 14px; min-height: 84px; resize: none; line-height: 1.4;}
.btn-group {display: flex; gap: 10px;}
.btn-group button {flex: 1; padding: 12px 0; border-radius: 10px; font-size: 16px;}
.btn-confirm {background: linear-gradient(90deg, #667eea 0%, #764ba2 100%);}
.btn-cancel {background: #e0e0e0; color: #666;}
.toast {position: fixed; bottom: 30px; left: 50%; transform: translateX(-50%); background: rgba(0,0,0,0.7); color: #fff; padding: 10px 20px; border-radius: 20px; font-size: 14px; display: none; z-index: 101; animation: fadeIn 0.3s ease;}
@keyframes fadeIn {from {opacity: 0; bottom: 20px;} to {opacity: 1; bottom: 30px;}}
.calendar-decoration {position: absolute; top: 10px; left: 10px; width: 30px; height: 30px; background: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='%23fff'%3E%3Cpath d='M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm0 18c-4.41 0-8-3.59-8-8s3.59-8 8-8 8 3.59 8 8-3.59 8-8 8zm-1-13h2v6h-2zm0 8h2v2h-2z'/%3E%3C/svg%3E") center no-repeat; background-size: 24px; opacity: 0.8;}
</style>
</head>
<body>
<div class="container">
  <div class="calendar-header">
    <div class="calendar-decoration"></div>
    vollure rose 2026年行事历
  </div>
  <div class="btns">
    <button class="btn-save" id="saveFile">保存最新日历</button>
    <button class="btn-reset" id="resetBtn">清空所有数据</button>
  </div>
  <div class="calendar" id="calendar"></div>
</div>
<div class="mask" id="mask"></div>
<div class="panel" id="panel">
  <h4>编辑日期事项</h4>
  <div class="color-row-wrap">
    <div class="color-item">
      <div class="color-dot active" data-c="#FFFFFF" style="background: #FFFFFF;"></div>
      <div class="color-name">纯白色</div>
    </div>
    <div class="color-item">
      <div class="color-dot" data-c="#FFE5E5" style="background: #FFE5E5;"></div>
      <div class="color-name">蜜桃粉</div>
    </div>
    <div class="color-item">
      <div class="color-dot" data-c="#E5F0FF" style="background: #E5F0FF;"></div>
      <div class="color-name">天空蓝</div>
    </div>
    <div class="color-item">
      <div class="color-dot" data-c="#E5FFE5" style="background: #E5FFE5;"></div>
      <div class="color-name">薄荷绿</div>
    </div>
    <div class="color-item">
      <div class="color-dot" data-c="#FFF5E5" style="background: #FFF5E5;"></div>
      <div class="color-name">芝士黄</div>
    </div>
    <div class="color-item">
      <div class="color-dot" data-c="#F5E5FF" style="background: #F5E5FF;"></div>
      <div class="color-name">薰衣草紫</div>
    </div>
    <div class="color-item">
      <div class="color-dot" data-c="#FFB3E5" style="background: #FFB3E5;"></div>
      <div class="color-name">樱花粉</div>
    </div>
    <div class="color-item">
      <div class="color-dot" data-c="#B3E5FF" style="background: #B3E5FF;"></div>
      <div class="color-name">冰川蓝</div>
    </div>
  </div>
  <textarea class="todo-input" id="todoText" placeholder="输入待办事项（如：出差、开会）"></textarea>
  <div class="btn-group">
    <button class="btn-confirm" id="apply">确定</button>
    <button class="btn-cancel" id="cancel">取消</button>
  </div>
</div>
<div class="toast" id="toast"></div>
<script>
const YEAR = 2026;
const monthNames = "1月,2月,3月,4月,5月,6月,7月,8月,9月,10月,11月,12月".split(",");
const weeks = "日,一,二,三,四,五,六".split(",");
const holidays = {"1-1":"元旦","2-16":"除夕","2-17":"春节","3-3":"元宵节","4-5":"清明","5-1":"劳动节","6-19":"端午","10-1":"国庆"};
let calendarData = ${JSON.stringify(calendarData)};
let isSelecting = false;
let selectedDateKeys = [];
let startDayEl = null;
let isDragging = false;
let isScrolling = false;

function isDarkColor(hex) {
  const colorMap = {"#FFB3E5":true,"#B3E5FF":true,"#FFFFFF":false};
  return colorMap[hex] || false;
}

function showToast(text) {
  const toast = document.getElementById('toast');
  toast.textContent = text;
  toast.style.display = 'block';
  setTimeout(() => toast.style.display = 'none', 1500);
}

function getContinuousDays(monthEl) {
  const dayEls = monthEl.querySelectorAll('.day:not(.empty)');
  const continuousGroups = [];
  let currentGroup = [];
  const rows = [];
  let currentRow = [];
  dayEls.forEach((el, index) => {
    currentRow.push(el);
    if ((index + 1) % 7 === 0) {
      rows.push(currentRow);
      currentRow = [];
    }
  });
  if (currentRow.length > 0) rows.push(currentRow);

  rows.forEach(row => {
    currentGroup = [row[0]];
    for (let i = 1; i < row.length; i++) {
      const prevEl = row[i-1];
      const currEl = row[i];
      const prevKey = prevEl.dataset.key;
      const currKey = currEl.dataset.key;
      const prevData = calendarData[prevKey] || { todo: '', color: '#FFFFFF' };
      const currData = calendarData[currKey] || { todo: '', color: '#FFFFFF' };

      if (prevData.todo && prevData.todo === currData.todo && prevData.color === currData.color) {
        currentGroup.push(currEl);
      } else {
        if (currentGroup.length > 1) {
          continuousGroups.push(currentGroup);
        }
        currentGroup = [currEl];
      }
    }
    if (currentGroup.length > 1) {
      continuousGroups.push(currentGroup);
    }
  });

  return continuousGroups;
}

function renderMergeTodos(monthEl) {
  monthEl.querySelectorAll('.merge-todo').forEach(el => el.remove());
  const continuousGroups = getContinuousDays(monthEl);
  const daysContainer = monthEl.querySelector('.days');

  continuousGroups.forEach(group => {
    if (group.length < 2) return;
    const firstEl = group[0];
    const lastEl = group[group.length - 1];
    const firstRect = firstEl.getBoundingClientRect();
    const lastRect = lastEl.getBoundingClientRect();
    const containerRect = daysContainer.getBoundingClientRect();

    const top = firstRect.top - containerRect.top;
    const left = firstRect.left - containerRect.left;
    const width = lastRect.right - firstRect.left;
    const height = firstRect.height;

    const mergeEl = document.createElement('div');
    mergeEl.className = 'merge-todo';
    mergeEl.style.top = \`\${top}px\`;
    mergeEl.style.left = \`\${left}px\`;
    mergeEl.style.width = \`\${width}px\`;
    mergeEl.style.height = \`\${height}px\`;
    mergeEl.style.background = calendarData[firstEl.dataset.key].color;
    mergeEl.textContent = calendarData[firstEl.dataset.key].todo;

    group.forEach(el => {
      el.querySelector('.todo').style.display = 'none';
      el.querySelector('.num').style.display = 'block';
    });

    daysContainer.appendChild(mergeEl);
  });
}

function initScrollDetection() {
  const calendarContainer = document.getElementById('calendarContainer');
  let touchStartY = 0;
  let touchMoveY = 0;
  
  calendarContainer.addEventListener('touchstart', (e) => {
    touchStartY = e.touches[0].clientY;
    isScrolling = true;
    clearTimeout(window.scrollCheckTimer);
  });
  
  calendarContainer.addEventListener('touchmove', (e) => {
    touchMoveY = e.touches[0].clientY;
    if (Math.abs(touchMoveY - touchStartY) > 5) {
      isScrolling = true;
    }
  });
  
  calendarContainer.addEventListener('touchend', () => {
    window.scrollCheckTimer = setTimeout(() => {
      isScrolling = false;
    }, 200);
  });
  
  calendarContainer.addEventListener('wheel', (e) => {
    if (Math.abs(e.deltaY) > 0) {
      isScrolling = true;
      clearTimeout(window.scrollCheckTimer);
      window.scrollCheckTimer = setTimeout(() => {
        isScrolling = false;
      }, 200);
    }
  });
}

function renderCalendar() {
  const calendarEl = document.getElementById('calendar');
  calendarEl.innerHTML = '';

  for (let month = 0; month < 12; month++) {
    const firstDay = new Date(YEAR, month, 1).getDay();
    const daysInMonth = new Date(YEAR, month + 1, 0).getDate();
    const monthDiv = document.createElement('div');
    monthDiv.className = 'month';

    monthDiv.innerHTML = \`
      <div class="month-top">
        <div class="month-cal-title">2026年行事历</div>
        <div class="month-title">\${monthNames[month]}</div>
      </div>
      <div class="week">\${weeks.map(day => \`<div>\${day}</div>\`).join('')}</div>
    \`;

    const daysDiv = document.createElement('div');
    daysDiv.className = 'days';

    for (let i = 0; i < firstDay; i++) {
      daysDiv.innerHTML += '<div class="day empty"></div>';
    }

    for (let day = 1; day <= daysInMonth; day++) {
      const dateKey = \`\${month + 1}-\${day}\`;
      const dateData = calendarData[dateKey] || { color: '#FFFFFF', todo: '' };
      const isDark = isDarkColor(dateData.color) ? 'dark' : '';
      const holidayText = holidays[dateKey] ? \`<br><span style="color:#ff3b30">\${holidays[dateKey]}</span>\` : '';

      daysDiv.innerHTML += \`
        <div class="day \${isDark}" data-key="\${dateKey}" style="background:\${dateData.color}">
          <div class="num">\${day}</div>
          <div class="todo">\${dateData.todo}\${holidayText}</div>
        </div>
      \`;
    }

    monthDiv.appendChild(daysDiv);
    calendarEl.appendChild(monthDiv);
    renderMergeTodos(monthDiv);
  }

  initScrollDetection();
  bindDayEvents();
}

function bindDayEvents() {
  const days = document.querySelectorAll('.day:not(.empty)');
  const mask = document.getElementById('mask');
  const panel = document.getElementById('panel');

  days.forEach(dayEl => {
    dayEl.addEventListener('mousedown', (e) => {
      if (isScrolling) return;
      
      e.preventDefault();
      isSelecting = true;
      isDragging = false;
      startDayEl = dayEl;
      selectedDateKeys = [dayEl.dataset.key];
      document.querySelectorAll('.day.selected').forEach(el => el.classList.remove('selected'));
      dayEl.classList.add('selected');
    });

    dayEl.addEventListener('mousemove', (e) => {
      if (isScrolling || !isSelecting) return;
      
      isDragging = true;
      const target = document.elementFromPoint(e.clientX, e.clientY);
      if (target && target.classList.contains('day') && !target.classList.contains('empty')) {
        const key = target.dataset.key;
        if (!selectedDateKeys.includes(key)) {
          selectedDateKeys.push(key);
          target.classList.add('selected');
        }
      }
    });

    dayEl.addEventListener('touchstart', (e) => {
      if (isScrolling) return;
      
      e.preventDefault();
      isSelecting = true;
      isDragging = false;
      startDayEl = dayEl;
      selectedDateKeys = [dayEl.dataset.key];
      document.querySelectorAll('.day.selected').forEach(el => el.classList.remove('selected'));
      dayEl.classList.add('selected');
    });

    dayEl.addEventListener('touchmove', (e) => {
      if (isScrolling || !isSelecting) return;
      
      isDragging = true;
      const touch = e.touches[0];
      const target = document.elementFromPoint(touch.clientX, touch.clientY);
      if (target && target.classList.contains('day') && !target.classList.contains('empty')) {
        const key = target.dataset.key;
        if (!selectedDateKeys.includes(key)) {
          selectedDateKeys.push(key);
          target.classList.add('selected');
        }
      }
    });

    dayEl.addEventListener('mouseup', handleSelectEnd);
    dayEl.addEventListener('touchend', handleSelectEnd);
  });

  document.addEventListener('mouseup', handleSelectEnd);
  document.addEventListener('touchend', handleSelectEnd);

  function handleSelectEnd() {
    if (!isSelecting) return;
    isSelecting = false;

    if (isDragging && selectedDateKeys.length > 0) {
      openEditPanel();
    } else if (!isDragging && startDayEl) {
      openEditPanel();
    }

    isDragging = false;
    startDayEl = null;
  }

  mask.addEventListener('click', () => {
    closeEditPanel();
    document.querySelectorAll('.day.selected').forEach(el => el.classList.remove('selected'));
    selectedDateKeys = [];
  });

  panel.addEventListener('click', (e) => {
    e.stopPropagation();
  });
}

function openEditPanel() {
  const panel = document.getElementById('panel');
  const mask = document.getElementById('mask');
  const todoInput = document.getElementById('todoText');
  const colorDots = document.querySelectorAll('.color-dot');

  todoInput.value = '';
  colorDots.forEach(dot => dot.classList.remove('active'));
  document.querySelector('.color-dot[data-c="#FFFFFF"]').classList.add('active');
  
  panel.style.display = 'block';
  mask.style.display = 'block';
}

function closeEditPanel() {
  document.getElementById('panel').style.display = 'none';
  document.getElementById('mask').style.display = 'none';
  document.querySelectorAll('.day.selected').forEach(el => el.classList.remove('selected'));
  selectedDateKeys = [];
}

document.querySelectorAll('.color-dot').forEach(dot => {
  dot.addEventListener('click', () => {
    document.querySelectorAll('.color-dot').forEach(d => d.classList.remove('active'));
    dot.classList.add('active');
  });
});

document.getElementById('cancel').addEventListener('click', closeEditPanel);

document.getElementById('apply').addEventListener('click', () => {
  if (selectedDateKeys.length === 0) return;
  
  const selectedColor = document.querySelector('.color-dot.active').dataset.c;
  const todoText = document.getElementById('todoText').value.trim();
  
  selectedDateKeys.forEach(key => {
    calendarData[key] = { color: selectedColor, todo: todoText };
  });
  localStorage.setItem('CAL2026_WECHAT', JSON.stringify(calendarData));
  
  renderCalendar();
  closeEditPanel();
  showToast(\`已为\${selectedDateKeys.length}个日期保存事项！\`);
});

document.getElementById('saveFile').addEventListener('click', () => {
  showToast('此功能在独立文件中可用');
});

document.getElementById('resetBtn').addEventListener('click', () => {
  if (confirm('确定要清空所有日历数据吗？')) {
    calendarData = {};
    localStorage.removeItem('CAL2026_WECHAT');
    renderCalendar();
    showToast('数据已清空！');
  }
});

renderCalendar();
<\/script>
</body>
</html>`;

  const blob = new Blob([fullHTML], { type: 'text/html; charset=utf-8' });
  const a = document.createElement('a');
  a.href = URL.createObjectURL(blob);
  a.download = `vollure rose 2026行事历_${new Date().toLocaleDateString().replace(/\//g, '-')}.html`;
  a.click();
  URL.revokeObjectURL(a.href);
  showToast('日历已保存到本地！');
});

// 清空数据
document.getElementById('resetBtn').addEventListener('click', () => {
  if (confirm('确定要清空所有日历数据吗？')) {
    calendarData = {};
    localStorage.removeItem('CAL2026_WECHAT');
    renderCalendar();
    showToast('数据已清空！');
  }
});
</script>
</body>
</html>
