<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<meta name="format-detection" content="telephone=no, email=no">
<meta http-equiv="X-UA-Compatible" content="IE=edge">
<title>2026 全年行事历</title>
<style>
* {box-sizing: border-box; margin: 0; padding: 0; font-family: PingFang SC, Microsoft YaHei, sans-serif;}
body {background: #f4f4f4; padding: 10px 0; -webkit-user-select: none; user-select: none;}
.container {max-width: 100%; margin: 0 auto; background: #fff; border-radius: 10px; overflow: hidden;}
.header {text-align: center; padding: 14px 0; background: #fff; color: #333; font-size: 18px;}
.btns {display: flex; justify-content: center; gap: 10px; padding: 10px; background: #fff;}
button {padding: 8px 12px; border: none; border-radius: 6px; color: white; font-size: 14px; cursor: pointer;}
.btn-save {background: #007aff;}
.btn-reset {background: #ff3b30;}
.calendar {display: flex; flex-direction: column; gap: 15px; padding: 10px;}
.month {border: 1px solid #e5e5ea; border-radius: 10px; overflow: hidden;}
.month-top {
  background: #f2f2f7;
  padding: 8px 10px;
  text-align: center;
}
.month-cal-title {
  font-size: 14px;
  color: #666;
  margin-bottom: 4px;
}
.month-title {
  font-size: 16px;
  font-weight: bold;
  color: #333;
}
.week {display: grid; grid-template-columns: repeat(7, 1fr); background: #f7f7f7; font-size: 12px; color: #888;}
.week div {padding: 6px 0; text-align: center;}
.days {display: grid; grid-template-columns: repeat(7, 1fr); gap: 1px; background: #e5e5ea;}
.day {background: #fff; min-height: 54px; padding: 4px; position: relative; cursor: pointer; font-size: 12px;}
.day .num {font-weight: bold; font-size: 13px; margin-bottom: 2px;}
.day .todo {font-size: 10px; line-height: 1.2; overflow: hidden; max-height: 30px;}
.day.selected {outline: 2px solid #007aff;}
.day.dark .num, .day.dark .todo {color: #fff !important;}
.empty {background: #fafafa; cursor: default;}
.panel {position: fixed; bottom: 0; left: 0; right: 0; background: #fff; padding: 15px; border-top: 1px solid #ddd; display: none; z-index: 100;}
.panel h4 {margin-bottom: 10px; font-size: 16px;}
.color-row {display: flex; gap: 8px; margin-bottom: 10px; flex-wrap: wrap; justify-content: center;}
.color {width: 48px; height: 48px; border-radius: 6px; border: 2px solid #fff; display: flex; align-items: center; justify-content: center; color: #333; font-size: 12px; font-weight: bold; cursor: pointer;}
.color.dark-text {color: #fff;}
.color.active {border-color: #007aff;}
.todo-input {width: 100%; padding: 10px; border: 1px solid #ddd; border-radius: 6px; margin-bottom: 10px; font-size: 14px;}
.mask {position: fixed; top: 0; left: 0; right: 0; bottom: 0; background: rgba(0,0,0,0.3); display: none; z-index: 99;}
.toast {position: fixed; bottom: 80px; left: 50%; transform: translateX(-50%); background: rgba(0,0,0,0.7); color: #fff; padding: 8px 16px; border-radius: 4px; font-size: 14px; display: none; z-index: 101;}
</style>
</head>
<body>

<div class="container">
  <div class="header">2026 全年行事历</div>
  <div class="btns">
    <button class="btn-save" id="saveFile">保存最新日历</button>
    <button class="btn-reset" id="resetBtn">清空所有数据</button>
  </div>
  <div class="calendar" id="calendar"></div>
</div>

<div class="mask" id="mask"></div>
<div class="panel" id="panel">
  <h4>批量设置日期</h4>
  <div class="color-row">
    <div class="color" data-c="#FFE5E5" style="background: #FFE5E5;">蜜桃粉</div>
    <div class="color" data-c="#E5F0FF" style="background: #E5F0FF;">天空蓝</div>
    <div class="color" data-c="#E5FFE5" style="background: #E5FFE5;">薄荷绿</div>
    <div class="color" data-c="#FFF5E5" style="background: #FFF5E5;">芝士黄</div>
    <div class="color" data-c="#F5E5FF" style="background: #F5E5FF;">薰衣草紫</div>
    <div class="color dark-text" data-c="#FFB3E5" style="background: #FFB3E5;">樱花粉</div>
    <div class="color dark-text" data-c="#B3E5FF" style="background: #B3E5FF;">冰川蓝</div>
    <div class="color" data-c="#FFFFFF" style="background: #FFFFFF;">纯白色</div>
  </div>
  <input class="todo-input" id="todoText" placeholder="输入待办事项（如：出差）">
  <div style="display: flex; gap: 10px;">
    <button style="flex: 1; background: #007aff;" id="apply">确定</button>
    <button style="flex: 1; background: #ff3b30;" id="cancel">取消</button>
  </div>
</div>

<div class="toast" id="toast"></div>

<script>
const YEAR = 2026;
const monthNames = "1月,2月,3月,4月,5月,6月,7月,8月,9月,10月,11月,12月".split(",");
const weeks = "日,一,二,三,四,五,六".split(",");
const holidays = {"1-1":"元旦","2-16":"除夕","2-17":"春节","3-3":"元宵节","4-5":"清明","5-1":"劳动节","6-19":"端午","10-1":"国庆"};

let calendarData = JSON.parse(localStorage.getItem('CAL2026_WECHAT')) || {};
let isSelecting = false;
let selectedDays = [];
let currentColor = "#FFE5E5";

function isDarkColor(hex) {
  const colorMap = {
    "#FFB3E5": true,
    "#B3E5FF": true,
    "#FFFFFF": false
  };
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

    monthDiv.innerHTML = `
      <div class="month-top">
        <div class="month-cal-title">2026年行事历</div>
        <div class="month-title">${monthNames[month]}</div>
      </div>
      <div class="week">${weeks.map(day => `<div>${day}</div>`).join('')}</div>
    `;

    const daysDiv = document.createElement('div');
    daysDiv.className = 'days';

    for (let i = 0; i < firstDay; i++) {
      daysDiv.innerHTML += '<div class="day empty"></div>';
    }

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

function bindDayEvents() {
  const days = document.querySelectorAll('.day:not(.empty)');
  days.forEach(dayEl => {
    dayEl.addEventListener('mousedown', (e) => {
      e.preventDefault();
      startSelection(dayEl);
    });
    dayEl.addEventListener('mouseenter', () => {
      if (isSelecting) selectDay(dayEl);
    });

    dayEl.addEventListener('touchstart', (e) => {
      e.preventDefault();
      startSelection(dayEl);
    });
    dayEl.addEventListener('touchmove', (e) => {
      if (!isSelecting) return;
      const touch = e.touches[0];
      const target = document.elementFromPoint(touch.clientX, touch.clientY);
      if (target && target.classList.contains('day') && !target.classList.contains('empty')) {
        selectDay(target);
      }
    });

    dayEl.addEventListener('click', () => {
      if (!isSelecting) {
        selectedDays = [dayEl.dataset.key];
        showPanel();
      }
    });
  });

  document.addEventListener('mouseup', endSelection);
  document.addEventListener('touchend', endSelection);
}

function startSelection(dayEl) {
  isSelecting = true;
  selectedDays = [];
  selectDay(dayEl);
}

function selectDay(dayEl) {
  const key = dayEl.dataset.key;
  if (!selectedDays.includes(key)) {
    selectedDays.push(key);
    dayEl.classList.add('selected');
  }
}

function endSelection() {
  if (isSelecting && selectedDays.length > 0) {
    showPanel();
  }
  isSelecting = false;
  document.querySelectorAll('.day.selected').forEach(el => el.classList.remove('selected'));
}

function showPanel() {
  document.getElementById('panel').style.display = 'block';
  document.getElementById('mask').style.display = 'block';
  document.getElementById('todoText').value = '';
}

document.querySelectorAll('.color').forEach(colorEl => {
  colorEl.addEventListener('click', () => {
    document.querySelectorAll('.color').forEach(el => el.classList.remove('active'));
    colorEl.classList.add('active');
    currentColor = colorEl.dataset.c;
  });
});
document.querySelectorAll('.color')[0].classList.add('active');

document.getElementById('apply').addEventListener('click', () => {
  const todoText = document.getElementById('todoText').value.trim();
  if (selectedDays.length === 0) {
    showToast('请先选择日期');
    return;
  }

  selectedDays.forEach(key => {
    calendarData[key] = { color: currentColor, todo: todoText };
  });

  localStorage.setItem('CAL2026_WECHAT', JSON.stringify(calendarData));
  renderCalendar();
  closePanel();
  showToast('设置成功！');
});

document.getElementById('cancel').addEventListener('click', closePanel);
function closePanel() {
  document.getElementById('panel').style.display = 'none';
  document.getElementById('mask').style.display = 'none';
  selectedDays = [];
}

// 修复后的保存文件功能，避免了模板字符串嵌套问题
document.getElementById('saveFile').addEventListener('click', () => {
  const fullHTML = `<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<meta name="format-detection" content="telephone=no">
<title>2026 全年行事历（已同步）</title>
<style>
* {box-sizing: border-box; margin: 0; padding: 0; font-family: PingFang SC, Microsoft YaHei, sans-serif;}
body {background: #f4f4f4; padding: 10px 0; -webkit-user-select: none; user-select: none;}
.container {max-width: 100%; margin: 0 auto; background: #fff; border-radius: 10px; overflow: hidden;}
.header {text-align: center; padding: 14px 0; background: #fff; color: #333; font-size: 18px;}
.btns {display: flex; justify-content: center; gap: 10px; padding: 10px; background: #fff;}
button {padding: 8px 12px; border: none; border-radius: 6px; color: white; font-size: 14px; cursor: pointer;}
.btn-save {background: #007aff;}
.btn-reset {background: #ff3b30;}
.calendar {display: flex; flex-direction: column; gap: 15px; padding: 10px;}
.month {border: 1px solid #e5e5ea; border-radius: 10px; overflow: hidden;}
.month-top {background: #f2f2f7; padding: 8px 10px; text-align: center;}
.month-cal-title {font-size: 14px; color: #666; margin-bottom: 4px;}
.month-title {font-size: 16px; font-weight: bold; color: #333;}
.week {display: grid; grid-template-columns: repeat(7, 1fr); background: #f7f7f7; font-size: 12px; color: #888;}
.week div {padding: 6px 0; text-align: center;}
.days {display: grid; grid-template-columns: repeat(7, 1fr); gap: 1px; background: #e5e5ea;}
.day {background: #fff; min-height: 54px; padding: 4px; position: relative; cursor: pointer; font-size: 12px;}
.day .num {font-weight: bold; font-size: 13px; margin-bottom: 2px;}
.day .todo {font-size: 10px; line-height: 1.2; overflow: hidden; max-height: 30px;}
.day.selected {outline: 2px solid #007aff;}
.day.dark .num, .day.dark .todo {color: #fff !important;}
.empty {background: #fafafa; cursor: default;}
.panel {position: fixed; bottom: 0; left: 0; right: 0; background: #fff; padding: 15px; border-top: 1px solid #ddd; display: none; z-index: 100;}
.panel h4 {margin-bottom: 10px; font-size: 16px;}
.color-row {display: flex; gap: 8px; margin-bottom: 10px; flex-wrap: wrap; justify-content: center;}
.color {width: 48px; height: 48px; border-radius: 6px; border: 2px solid #fff; display: flex; align-items: center; justify-content: center; color: #333; font-size: 12px; font-weight: bold; cursor: pointer;}
.color.dark-text {color: #fff;}
.color.active {border-color: #007aff;}
.todo-input {width: 100%; padding: 10px; border: 1px solid #ddd; border-radius: 6px; margin-bottom: 10px; font-size: 14px;}
.mask {position: fixed; top: 0; left: 0; right: 0; bottom: 0; background: rgba(0,0,0,0.3); display: none; z-index: 99;}
.toast {position: fixed; bottom: 80px; left: 50%; transform: translateX(-50%); background: rgba(0,0,0,0.7); color: #fff; padding: 8px 16px; border-radius: 4px; font-size: 14px; display: none; z-index: 101;}
</style>
</head>
<body>
<div class="container">
  <div class="header">2026 全年行事历</div>
  <div class="btns">
    <button class="btn-save" id="saveFile">保存最新日历</button>
    <button class="btn-reset" id="resetBtn">清空所有数据</button>
  </div>
  <div class="calendar" id="calendar"></div>
</div>
<div class="mask" id="mask"></div>
<div class="panel" id="panel">
  <h4>批量设置日期</h4>
  <div class="color-row">
    <div class="color" data-c="#FFE5E5" style="background: #FFE5E5;">蜜桃粉</div>
    <div class="color" data-c="#E5F0FF" style="background: #E5F0FF;">天空蓝</div>
    <div class="color" data-c="#E5FFE5" style="background: #E5FFE5;">薄荷绿</div>
    <div class="color" data-c="#FFF5E5" style="background: #FFF5E5;">芝士黄</div>
    <div class="color" data-c="#F5E5FF" style="background: #F5E5FF;">薰衣草紫</div>
    <div class="color dark-text" data-c="#FFB3E5" style="background: #FFB3E5;">樱花粉</div>
    <div class="color dark-text" data-c="#B3E5FF" style="background: #B3E5FF;">冰川蓝</div>
    <div class="color" data-c="#FFFFFF" style="background: #FFFFFF;">纯白色</div>
  </div>
  <input class="todo-input" id="todoText" placeholder="输入待办事项（如：出差）">
  <div style="display: flex; gap: 10px;">
    <button style="flex: 1; background: #007aff;" id="apply">确定</button>
    <button style="flex: 1; background: #ff3b30;" id="cancel">取消</button>
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
let selectedDays = [];
let currentColor = "#FFE5E5";
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
    dayEl.addEventListener('mousedown', (e) => {
      e.preventDefault();
      startSelection(dayEl);
    });
    dayEl.addEventListener('mouseenter', () => {
      if (isSelecting) selectDay(dayEl);
    });
    dayEl.addEventListener('touchstart', (e) => {
      e.preventDefault();
      startSelection(dayEl);
    });
    dayEl.addEventListener('touchmove', (e) => {
      if (!isSelecting) return;
      const touch = e.touches[0];
      const target = document.elementFromPoint(touch.clientX, touch.clientY);
      if (target && target.classList.contains('day') && !target.classList.contains('empty')) {
        selectDay(target);
      }
    });
    dayEl.addEventListener('click', () => {
      if (!isSelecting) {
        selectedDays = [dayEl.dataset.key];
        showPanel();
      }
    });
  });
  document.addEventListener('mouseup', endSelection);
  document.addEventListener('touchend', endSelection);
}
function startSelection(dayEl) {
  isSelecting = true;
  selectedDays = [];
  selectDay(dayEl);
}
function selectDay(dayEl) {
  const key = dayEl.dataset.key;
  if (!selectedDays.includes(key)) {
    selectedDays.push(key);
    dayEl.classList.add('selected');
  }
}
function endSelection() {
  if (isSelecting && selectedDays.length > 0) {
    showPanel();
  }
  isSelecting = false;
  document.querySelectorAll('.day.selected').forEach(el => el.classList.remove('selected'));
}
function showPanel() {
  document.getElementById('panel').style.display = 'block';
  document.getElementById('mask').style.display = 'block';
  document.getElementById('todoText').value = '';
}
document.querySelectorAll('.color').forEach(colorEl => {
  colorEl.addEventListener('click', () => {
    document.querySelectorAll('.color').forEach(el => el.classList.remove('active'));
    colorEl.classList.add('active');
    currentColor = colorEl.dataset.c;
  });
});
document.querySelectorAll('.color')[0].classList.add('active');
document.getElementById('apply').addEventListener('click', () => {
  const todoText = document.getElementById('todoText').value.trim();
  if (selectedDays.length === 0) {
    showToast('请先选择日期');
    return;
  }
  selectedDays.forEach(key => {
    calendarData[key] = { color: currentColor, todo: todoText };
  });
  localStorage.setItem('CAL2026_WECHAT', JSON.stringify(calendarData));
  renderCalendar();
  closePanel();
  showToast('设置成功！');
});
document.getElementById('cancel').addEventListener('click', closePanel);
function closePanel() {
  document.getElementById('panel').style.display = 'none';
  document.getElementById('mask').style.display = 'none';
  selectedDays = [];
}
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
  a.download = `2026行事历_${new Date().toLocaleDateString().replace(/\//g, '-')}.html`;
  a.click();
  URL.revokeObjectURL(a.href);
  showToast('日历已保存到本地！');
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
</script>
</body>
</html>
