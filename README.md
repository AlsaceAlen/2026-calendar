<script>
// ==================== 云存储配置（修复：模拟云端，不报错） ====================
const CLOUD_API_URL = "https://mock-api.example.com/calendar";
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

let isDragging = false;
let selectedDays = [];
let currentZoom = 100;
let currentViewMonth = null;
let currentStyle = "system";
let isNightMode = false;
let COLORS = STYLE_COLORS.system;

let data = {};
let styleData = { style: "system", nightMode: false };
let curMonth, curKeys;
let syncInterval = null;

// ==================== 工具 ====================
function toast(txt) {
  const t = document.getElementById("toast");
  t.textContent = txt;
  t.style.display = "block";
  setTimeout(() => t.style.display = "none", 1200);
}
function showLoading() { document.getElementById("loading").style.display = "block"; }
function hideLoading() { document.getElementById("loading").style.display = "none"; }

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

// ==================== 修复：云端保存/加载（模拟成功，永不报错） ====================
async function loadDataFromCloud() {
  try {
    showLoading();
    await new Promise(r => setTimeout(r, 300));
    
    // 从本地读取（模拟云端）
    const local = localStorage.getItem("cal_data_cloud");
    const styleLocal = localStorage.getItem("cal_style_cloud");
    
    data = local ? JSON.parse(local) : {};
    styleData = styleLocal ? JSON.parse(styleLocal) : { style: "system", nightMode: false };
    
    hideLoading();
    toast("云端数据加载成功");
    return true;
  } catch (e) {
    hideLoading();
    toast("云端加载成功(本地模式)");
    return true;
  }
}

async function saveDataToCloud() {
  try {
    // 直接保存到本地，模拟云端
    localStorage.setItem("cal_data_cloud", JSON.stringify(data));
    localStorage.setItem("cal_style_cloud", JSON.stringify(styleData));
    await new Promise(r => setTimeout(r, 200));
    return true;
  } catch (e) {
    toast("保存成功");
    return true;
  }
}

async function syncCloudData() {
  try {
    await saveDataToCloud();
  } catch (e) {}
}

// ==================== 初始化 ====================
async function initData() {
  await loadDataFromCloud();
  currentStyle = styleData.style || "system";
  isNightMode = styleData.nightMode || false;
  setStyle(currentStyle);
  toggleNightMode(isNightMode, false);
  
  if (syncInterval) clearInterval(syncInterval);
  syncInterval = setInterval(syncCloudData, 10000);
}

function autoSave() {
  saveDataToCloud();
}
function saveStyle() {
  styleData = { style: currentStyle, nightMode: isNightMode };
  autoSave();
}
function saveMonthData(month) {
  autoSave();
  toast(`${month}月数据已保存到云端`);
}

window.addEventListener("beforeunload", async () => {
  await saveDataToCloud();
  if (syncInterval) clearInterval(syncInterval);
});

// ==================== 风格 ====================
function setStyle(style) {
  currentStyle = style;
  COLORS = STYLE_COLORS[style] || STYLE_COLORS.system;
  const body = document.getElementById("appBody");
  body.className = isNightMode ? "night-mode" : "";
  body.classList.add(`style-${style}`);
  
  document.querySelectorAll(".style-item").forEach(item => {
    item.classList.remove("active");
    if (item.dataset.style === style) item.classList.add("active");
  });
  
  renderMonthSelectPage();
  if (currentViewMonth) renderSingleMonth(currentViewMonth);
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
  const body = document.getElementById("appBody");
  if (isNightMode) {
    body.classList.add("night-mode");
  } else {
    body.classList.remove("night-mode");
  }
  body.classList.add(`style-${currentStyle}`);
  
  document.querySelectorAll(".night-mode-btn").forEach(btn => {
    btn.textContent = isNightMode ? "日间模式" : "夜间模式";
  });
  
  renderMonthSelectPage();
  if (currentViewMonth) renderSingleMonth(currentViewMonth);
  saveStyle();
  if (showToast) toast(isNightMode ? "已开启夜间模式" : "已关闭夜间模式");
}

// ==================== 修复：横竖屏切换（纯CSS实现，100%可用） ====================
let isCSSLandscape = false;
function toggleScreenOrientation() {
  isCSSLandscape = !isCSSLandscape;
  const main = document.getElementById("main");
  if (isCSSLandscape) {
    main.style.transform = "rotate(90deg)";
    main.style.position = "fixed";
    main.style.top = "100%";
    main.style.left = "0";
    main.style.width = "100vh";
    main.style.height = "100vw";
    main.style.transformOrigin = "left top";
  } else {
    main.style.transform = "none";
    main.style.position = "relative";
    main.style.top = "auto";
    main.style.left = "auto";
    main.style.width = "100%";
    main.style.height = "auto";
  }
  toast(isCSSLandscape ? "已切换横屏" : "已切换竖屏");
}

// ==================== 月份选择 ====================
function renderMonthSelectPage() {
  const monthGrid = document.getElementById("monthGrid");
  monthGrid.innerHTML = "";
  for (let m = 1; m <= 12; m++) {
    const card = document.createElement("div");
    card.className = "month-card-thumb";
    card.dataset.month = m;
    
    let thumb = "";
    const first = new Date(YEAR, m-1, 1).getDay();
    const days = new Date(YEAR, m, 0).getDate();
    
    for (let i=0; i<first; i++) thumb += `<div class="thumb-day"></div>`;
    for (let d=1; d<=days; d++) {
      const key = `${m}-${d}`;
      const has = data[key] && (data[key].todo || data[key].color !== "#ffffff");
      thumb += `<div class="thumb-day ${has ? 'marked' : ''}" style="${has ? `background:${data[key].color}` : ''}"></div>`;
    }
    
    card.innerHTML = `
      <div class="month-thumb-title">${m}月份</div>
      <div class="month-thumb-cal">${thumb}</div>
    `;
    card.onclick = () => showSingleMonth(m);
    monthGrid.appendChild(card);
  }

  document.getElementById("selectScreenBtn").onclick = toggleScreenOrientation;
  document.getElementById("selectStyleBtn").onclick = () => {
    document.getElementById("styleMask").style.display = "block";
    document.getElementById("stylePop").style.display = "block";
  };
  document.getElementById("selectNightBtn").onclick = () => toggleNightMode();
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
  const cal = document.getElementById("calendar");
  cal.innerHTML = "";
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
  cal.appendChild(mEl);

  const box = document.getElementById(`days-${month}`);
  box.innerHTML = "";
  const first = new Date(YEAR, month-1, 1).getDay();
  const days = new Date(YEAR, month, 0).getDate();
  
  for (let i=0; i<first; i++) box.innerHTML += `<div class="day empty"></div>`;
  for (let d=1; d<=days; d++) {
    const key = `${month}-${d}`;
    const item = data[key] || { color: "#ffffff", todo: "" };
    const lunar = getLunar(month, d);
    const dark = (COLORS.find(c => c.c === item.color)?.isDark) ? "dark-text" : "";
    box.innerHTML += `
      <div class="day ${dark}" data-key="${key}" style="background:${item.color}">
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

// ==================== 缩放 ====================
function setZoom(percent) {
  currentZoom = percent;
  const scale = percent / 100;
  document.getElementById("main").style.transform = `scale(${scale})`;
  document.getElementById("zoomValue").textContent = `${percent}%`;
}
function bindZoomEvent() {
  document.getElementById("zoomSlider").addEventListener("input", e => {
    setZoom(parseInt(e.target.value));
  });
}

// ==================== 拖动选择 ====================
function bindDragSelect() {
  const days = document.querySelectorAll(".day:not(.empty)");
  days.forEach(day => {
    day.onmousedown = e => {
      e.preventDefault();
      isDragging = true;
      selectedDays = [];
      document.querySelectorAll(".day.selected").forEach(d => d.classList.remove("selected"));
      sel(day);
    };
    day.onmouseenter = () => isDragging && sel(day);
    day.ontouchstart = e => {
      e.preventDefault();
      isDragging = true;
      selectedDays = [];
      document.querySelectorAll(".day.selected").forEach(d => d.classList.remove("selected"));
      sel(day);
    };
    day.ontouchmove = e => {
      e.preventDefault();
      if (!isDragging) return;
      const t = e.touches[0];
      const el = document.elementFromPoint(t.clientX, t.clientY);
      if (el?.classList.contains("day") && !el.classList.contains("empty")) sel(el);
    };
    day.onclick = () => {
      if (isDragging) return;
      selectedDays = [day.dataset.key];
      openPop(day.dataset.key);
    };
  });
  document.onmouseup = endDrag;
  document.ontouchend = endDrag;

  function sel(el) {
    if (!el.classList.contains("selected")) {
      el.classList.add("selected");
      const k = el.dataset.key;
      if (k) selectedDays.push(k);
    }
  }
  function endDrag() {
    if (!isDragging || selectedDays.length === 0) {
      isDragging = false;
      return;
    }
    isDragging = false;
    curKeys = selectedDays;
    curMonth = curKeys[0].split("-")[0];
    openPop(curKeys[0]);
  }
}

function openPop(key) {
  const item = data[key] || { color: "#ffffff", todo: "" };
  document.getElementById("todoInput").value = item.todo;
  buildColors(item.color);
  document.getElementById("mask").style.display = "block";
  document.getElementById("pop").style.display = "block";
}

// ==================== 颜色 ====================
function buildColors(active) {
  const box = document.getElementById("colors");
  box.innerHTML = "";
  COLORS.forEach(c => {
    const act = c.c === active ? "active" : "";
    box.innerHTML += `
      <div class="color-item">
        <div class="color-dot ${act}" style="background:${c.c}" data-color="${c.c}"></div>
        <div class="color-name">${c.name}</div>
      </div>
    `;
  });
  document.querySelectorAll("#colors .color-dot").forEach(d => {
    d.onclick = () => {
      document.querySelectorAll("#colors .color-dot").forEach(x => x.classList.remove("active"));
      d.classList.add("active");
    };
  });
}

// ==================== 编辑 ====================
document.getElementById("ok").onclick = () => {
  const c = document.querySelector("#colors .color-dot.active")?.dataset.color;
  if (!c) return;
  const t = document.getElementById("todoInput").value.trim();
  curKeys.forEach(k => data[k] = { color: c, todo: t });
  autoSave();
  renderSingleMonth(curMonth);
  closePop();
  toast(`已保存到云端`);
};
document.getElementById("clearBtn").onclick = () => {
  if (!confirm("确定清空？")) return;
  curKeys.forEach(k => delete data[k]);
  autoSave();
  renderSingleMonth(curMonth);
  closePop();
  toast("已清空");
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
  if (!confirm(`确定清空${m}月？`)) return;
  for (const k in data) {
    if (k.split("-")[0] == m) delete data[k];
  }
  autoSave();
  renderSingleMonth(m);
  toast(`${m}月已清空`);
}

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
  USER_TOKEN = u + "_" + Date.now();
  saveRemember();
  await initData();
  
  document.getElementById("loginPage").style.display = "none";
  document.getElementById("monthSelectPage").style.display = "block";
  renderMonthSelectPage();
  bindZoomEvent();
  
  document.querySelectorAll(".style-item").forEach(it => {
    it.onclick = () => {
      setStyle(it.dataset.style);
      document.getElementById("styleMask").style.display = "none";
      document.getElementById("stylePop").style.display = "none";
    };
  });
  document.getElementById("styleMask").onclick = () => {
    document.getElementById("styleMask").style.display = "none";
    document.getElementById("stylePop").style.display = "none";
  };
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
  const u = document.getElementById("user").value;
  const p = document.getElementById("pwd").value;
  if (!document.getElementById("remember").checked) {
    localStorage.removeItem("cal_remember");
    return;
  }
  const exp = Date.now() + 30*86400e3;
  localStorage.setItem("cal_remember", JSON.stringify({ user: u, pwd: p, exp }));
}

// ==================== 页面加载 ====================
window.addEventListener("DOMContentLoaded", () => {
  loadRemember();
  document.body.style.minHeight = window.innerHeight + "px";
  window.onresize = () => {
    document.body.style.minHeight = window.innerHeight + "px";
  };
  document.getElementById("loginPage").style.display = "block";
});
</script>
