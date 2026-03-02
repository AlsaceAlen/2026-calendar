<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<!-- 微信内置浏览器核心适配 -->
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<meta name="format-detection" content="telephone=no, email=no">
<meta http-equiv="X-UA-Compatible" content="IE=edge">
<title>2026 趣味行事历</title>
<style>
/* 全局样式重置+基础美化 */
* {box-sizing: border-box; margin: 0; padding: 0; font-family: PingFang SC, Microsoft YaHei, sans-serif;}
body {
  background: linear-gradient(120deg, #fdfbfb 0%, #ebedee 100%);
  padding: 10px 0;
  -webkit-user-select: none; 
  user-select: none;
  min-height: 100vh;
}
.container {
  max-width: 100%;
  margin: 0 auto;
  background: #fff;
  border-radius: 16px;
  overflow: hidden;
  box-shadow: 0 8px 24px rgba(0,0,0,0.08);
  margin: 10px;
}
/* 顶部标题美化 */
.header {
  text-align: center;
  padding: 20px 0;
  background: linear-gradient(90deg, #ff9a9e 0%, #fad0c4 99%, #fad0c4 100%);
  color: #fff;
  font-size: 20px;
  font-weight: bold;
  position: relative;
}
.header::after {
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
/* 日期格子 */
.days {
  display: grid;
  grid-template-columns: repeat(7, 1fr);
  gap: 1px;
  background: #f0f0f0;
}
.day {
  background: #fff;
  min-height: 60px;
  padding: 6px;
  position: relative;
  cursor: pointer;
  font-size: 12px;
  transition: all 0.2s ease;
}
.day:hover, .day:active {
  background: #f8f9fa;
}
.day .num {
  font-weight: bold;
  font-size: 14px;
  margin-bottom: 4px;
  color: #333;
}
.day .todo {
  font-size: 11px;
  line-height: 1.3;
  overflow: hidden;
  max-height: 36px;
  color: #555;
}
.day.empty {
  background: #fafafa;
  cursor: default;
}
/* 深色背景文字反白 */
.day.dark .num, .day.dark .todo {
  color: #fff !important;
}
/* 编辑弹窗样式（核心优化） */
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
.decoration {
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

<div class="container">
  <div class="header">
    <div class="decoration"></div>
    2026 趣味行事历
  </div>
  <div class="btns">
    <button class="btn-save" id="saveFile">保存最新日历</button>
    <button class="btn-reset" id="resetBtn">清空所有数据</button>
  </div>
  <div class="calendar" id="calendar"></div>
</div>

<!-- 遮罩层（点击空白处关闭弹窗） -->
<div class="mask" id="mask"></div>
<!-- 编辑弹窗（核心优化） -->
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
  </div>
</div>

<div class="toast" id="toast"></div>

<script>
const YEAR = 2026;
const monthNames = "1月,2月,3月,4月,5月,6月,7月,8月,9月,10月,11月,12月".split(",");
const weeks = "日,一,二,三,四,五,六".split(",");
const holidays = {"1-1":"元旦","2-16":"除夕","2-17":"春节","3-3":"元宵节","4-5":"清明","5-1":"劳动节","6-19":"端午","10-1":"国庆"};

// 存储数据：兼容微信内置浏览器
let calendarData = JSON.parse(localStorage.getItem('CAL2026_WECHAT')) || {};
let currentDateKey = ''; // 当前编辑的日期key

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
  }

  bindDayEvents();
}

// 绑定日期事件：仅点击触发（取消滑动选中）
function bindDayEvents() {
  const days = document.querySelectorAll('.day:not(.empty)');
  days.forEach(dayEl => {
    // 仅点击触发编辑窗口，取消所有滑动/ hover 选中逻辑
    dayEl.addEventListener('click', () => {
      currentDateKey = dayEl.dataset.key;
      openEditPanel();
    });
    // 移动端触屏点击兼容
    dayEl.addEventListener('touchend', (e) => {
      e.preventDefault();
      currentDateKey = dayEl.dataset.key;
      openEditPanel();
    });
  });
}

// 打开编辑面板（核心优化：清空输入框+默认白色）
function openEditPanel() {
  const panel = document.getElementById('panel');
  const mask = document.getElementById('mask');
  const todoInput = document.getElementById('todoText');
  const colorDots = document.querySelectorAll('.color-dot');

  // 1. 清空输入框，不留存上一次文字
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
  currentDateKey = '';
}

// 颜色选择事件（圆形色块）
document.querySelectorAll('.color-dot').forEach(dot => {
  dot.addEventListener('click', () => {
    document.querySelectorAll('.color-dot').forEach(d => d.classList.remove('active'));
    dot.classList.add('active');
  });
});

// 点击空白处（遮罩层）关闭面板
document.getElementById('mask').addEventListener('click', closeEditPanel);
// 阻止面板内点击触发遮罩关闭
document.getElementById('panel').addEventListener('click', (e) => {
  e.stopPropagation();
});

// 确定保存
document.getElementById('apply').addEventListener('click', () => {
  if (!currentDateKey) return;
  
  // 获取选中的颜色和输入的文字
  const selectedColor = document.querySelector('.color-dot.active').dataset.c;
  const todoText = document.getElementById('todoText').value.trim();
  
  // 保存数据
  calendarData[currentDateKey] = { color: selectedColor, todo: todoText };
  localStorage.setItem('CAL2026_WECHAT', JSON.stringify(calendarData));
  
  // 重新渲染+关闭面板
  renderCalendar();
  closeEditPanel();
  showToast('保存成功！');
});

// 保存日历文件
document.getElementById('saveFile').addEventListener('click', () => {
  const fullHTML = `<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<meta name="format-detection" content="telephone=no">
<title>2026 趣味行事历（已同步）</title>
<style>
* {box-sizing: border-box; margin: 0; padding: 0; font-family: PingFang SC, Microsoft YaHei, sans-serif;}
body {background: linear-gradient(120deg, #fdfbfb 0%, #ebedee 100%); padding: 10px 0; -webkit-user-select: none; user-select: none; min-height: 100vh;}
.container {max-width: 100%; margin: 0 auto; background: #fff; border-radius: 16px; overflow: hidden; box-shadow: 0 8px 24px rgba(0,0,0,0.08); margin: 10px;}
.header {text-align: center; padding: 20px 0; background: linear-gradient(90deg, #ff9a9e 0%, #fad0c4 99%, #fad0c4 100%); color: #fff; font-size: 20px; font-weight: bold; position: relative;}
.header::after {content: ''; display: block; width: 60px; height: 4px; background: #fff; border-radius: 2px; margin: 8px auto 0;}
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
.days {display: grid; grid-template-columns: repeat(7, 1fr); gap: 1px; background: #f0f0f0;}
.day {background: #fff; min-height: 60px; padding: 6px; position: relative; cursor: pointer; font-size: 12px; transition: all 0.2s ease;}
.day:hover, .day:active {background: #f8f9fa;}
.day .num {font-weight: bold; font-size: 14px; margin-bottom: 4px; color: #333;}
.day .todo {font-size: 11px; line-height: 1.3; overflow: hidden; max-height: 36px; color: #555;}
.day.empty {background: #fafafa; cursor: default;}
.day.dark .num, .day.dark .todo {color: #fff !important;}
.mask {position: fixed; top: 0; left: 0; right: 0; bottom: 0; background: rgba(0,0,0,0.5); display: none; z-index: 99; backdrop-filter: blur(2px);}
.panel {position: fixed; top: 50%; left: 50%; transform: translate(-50%, -50%); background: #fff; padding: 24px; border-radius: 16px; width: 90%; max-width: 400px; display: none; z-index: 100; box-shadow: 0 8px 32px rgba(0,0,0,0.15); animation: popup 0.3s ease;}
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
.toast {position: fixed; bottom: 30px; left: 50%; transform: translateX(-50%); background: rgba(0,0,0,0.7); color: #fff; padding: 10px 20px; border-radius: 20px; font-size: 14px; display: none; z-index: 101; animation: fadeIn 0.3s ease;}
@keyframes fadeIn {from {opacity: 0; bottom: 20px;} to {opacity: 1; bottom: 30px;}}
.decoration {position: absolute; top: 10px; left: 10px; width: 30px; height: 30px; background: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='%23fff'%3E%3Cpath d='M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm0 18c-4.41 0-8-3.59-8-8s3.59-8 8-8 8 3.59 8 8-3.59 8-8 8zm-1-13h2v6h-2zm0 8h2v2h-2z'/%3E%3C/svg%3E") center no-repeat; background-size: 24px; opacity: 0.8;}
</style>
</head>
<body>
<div class="container">
  <div class="header">
    <div class="decoration"></div>
    2026 趣味行事历
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
  </div>
</div>
<div class="toast" id="toast"></div>
<script>
const YEAR = 2026;
const monthNames = "1月,2月,3月,4月,5月,6月,7月,8月,9月,10月,11月,12月".split(",");
const weeks = "日,一,二,三,四,五,六".split(",");
const holidays = {"1-1":"元旦","2-16":"除夕","2-17":"春节","3-3":"元宵节","4-5":"清明","5-1":"劳动节","6-19":"端午","10-1":"国庆"};
let calendarData = ${JSON.stringify(calendarData)};
let currentDateKey = '';
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
  }
  bindDayEvents();
}
function bindDayEvents() {
  const days = document.querySelectorAll('.day:not(.empty)');
  days.forEach(dayEl => {
    dayEl.addEventListener('click', () => {
      currentDateKey = dayEl.dataset.key;
      openEditPanel();
    });
    dayEl.addEventListener('touchend', (e) => {
      e.preventDefault();
      currentDateKey = dayEl.dataset.key;
      openEditPanel();
    });
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
  currentDateKey = '';
}
document.querySelectorAll('.color-dot').forEach(dot => {
  dot.addEventListener('click', () => {
    document.querySelectorAll('.color-dot').forEach(d => d.classList.remove('active'));
    dot.classList.add('active');
  });
});
document.getElementById('mask').addEventListener('click', closeEditPanel);
document.getElementById('panel').addEventListener('click', (e) => {
  e.stopPropagation();
});
document.getElementById('apply').addEventListener('click', () => {
  if (!currentDateKey) return;
  const selectedColor = document.querySelector('.color-dot.active').dataset.c;
  const todoText = document.getElementById('todoText').value.trim();
  calendarData[currentDateKey] = { color: selectedColor, todo: todoText };
  localStorage.setItem('CAL2026_WECHAT', JSON.stringify(calendarData));
  renderCalendar();
  closeEditPanel();
  showToast('保存成功！');
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
  a.download = `2026趣味行事历_${new Date().toLocaleDateString().replace(/\//g, '-')}.html`;
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

// 首次渲染
renderCalendar();
</script>
</body>
</html>
