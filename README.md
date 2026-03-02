<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>2026轻奢行事历</title>
<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  font-family: "PingFang SC", "Microsoft YaHei", sans-serif;
}
body {
  background: #f7f5f2;
  padding: 12px;
}

/* 登录 */
.login-page {
  max-width: 380px;
  margin: 60px auto;
  background: #fff;
  border-radius: 20px;
  padding: 40px 30px;
  box-shadow: 0 8px 30px rgba(0,0,0,0.06);
}
.login-title {
  font-size: 24px;
  font-weight: 600;
  text-align: center;
  margin-bottom: 6px;
  color: #3b3b3b;
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
  border-color: #bfa999;
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
  background: #bfa999;
  color: #fff;
  border: none;
  border-radius: 14px;
  font-size: 15px;
  font-weight: 500;
}

/* 主界面 */
.calendar-container {
  display: none;
}
.header {
  text-align: center;
  padding: 20px 0;
  font-size: 18px;
  font-weight: 600;
  color: #444;
  position: relative;
}
.header::after {
  content: "";
  width: 30px;
  height: 3px;
  background: #bfa999;
  border-radius: 2px;
  position: absolute;
  bottom: 12px;
  left: 50%;
  transform: translateX(-50%);
}

/* 月份卡片 */
.month {
  background: #fff;
  border-radius: 16px;
  overflow: hidden;
  margin-bottom: 16px;
  box-shadow: 0 4px 12px rgba(0,0,0,0.04);
}
.month-head {
  padding: 14px 16px;
  background: #f9f7f5;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.month-title {
  font-size: 16px;
  font-weight: 600;
  color: #444;
}
.btn-clear-month {
  padding: 6px 10px;
  font-size: 12px;
  background: #e4d5c9;
  color: #6d5b54;
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
}
.day {
  aspect-ratio: 1/1.1;
  padding: 6px;
  border-right: 1px solid #f0ebe7;
  border-bottom: 1px solid #f0ebe7;
  position: relative;
}
.day:nth-child(7n) { border-right: none; }

.num {
  font-size: 15px;
  font-weight: 600;
  color: #333;
  margin-bottom: 2px;
}
.lunar {
  font-size: 10px;
  color: #bfa999;
  margin-left: 2px;
}
.todo {
  font-size: 15px;
  line-height: 1.3;
  color: #444;
  margin-top: 4px;
  word-break: break-all;
}

/* 轻奢色板 */
.color-panel {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
  margin-bottom: 16px;
}
.color-item {
  width: 36px;
  height: 36px;
  border-radius: 50%;
  cursor: pointer;
  border: 2px solid transparent;
}
.color-item.active {
  border-color: #bfa999;
}

/* 弹窗 */
.mask {
  position: fixed; inset:0; background:rgba(0,0,0,0.2);
  display: none;
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
}
.pop-title {
  font-size: 17px;
  font-weight: 600;
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
.btn-ok {
  background: #bfa999;
  color:#fff;
}
.btn-cancel {
  background: #f1eeeb;
  color:#666;
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
}
</style>
</head>
<body>

<!-- 登录 -->
<div class="login-page" id="loginPage">
  <div class="login-title">轻奢行事历</div>
  <div class="login-sub">2026 · 简约精致</div>
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
  <div class="header">2026 轻奢行事历</div>
  <div id="calendar"></div>
</div>

<!-- 弹窗 -->
<div class="mask" id="mask"></div>
<div class="pop" id="pop">
  <div class="pop-title">编辑待办</div>
  <div class="color-panel" id="colors"></div>
  <textarea class="pop-input" id="todoInput" placeholder="输入内容..."></textarea>
  <div class="pop-btns">
    <button class="btn-cancel" id="cancel">取消</button>
    <button class="btn-ok" id="ok">确定</button>
  </div>
</div>

<div class="toast" id="toast"></div>

<script>
// ==================== 配置 ====================
const YEAR = 2026;
const USER = "admin";
const PWD = "123456";
const COLORS = [
  "#f7f5f2","#e6e2df","#d9c8bc","#c4b8af","#bfa999",
  "#a89a8e","#8c7d70","#7a6b5f","#6d5b54","#5a4f47"
];

// ==================== 工具 ====================
function toast(txt){
  const t=document.getElementById("toast");
  t.textContent=txt; t.style.display="block";
  setTimeout(()=>t.style.display="none",1500);
}
function getLunar(month,day){
  const ld = [
    "","初一","初二","初三","初四","初五","初六","初七","初八","初九","初十",
    "十一","十二","十三","十四","十五","十六","十七","十八","十九","二十",
    "廿一","廿二","廿三","廿四","廿五","廿六","廿七","廿八","廿九","三十"
  ];
  const md=[0,31,28,31,30,31,30,31,31,30,31,30,31];
  let s=0;
  for(let i=1;i<month;i++)s+=md[i];
  const idx = (s+day+8)%30+1;
  return ld[idx]||"";
}

// ==================== 登录记忆 ====================
function loadRemember(){
  const d=localStorage.getItem("cal_remember");
  if(!d)return;
  const {user,pwd,exp}=JSON.parse(d);
  if(Date.now()>exp){localStorage.removeItem("cal_remember");return;}
  document.getElementById("user").value=user;
  document.getElementById("pwd").value=pwd;
  document.getElementById("remember").checked=true;
}
function saveRemember(){
  const user=document.getElementById("user").value;
  const pwd=document.getElementById("pwd").value;
  if(!document.getElementById("remember").checked){
    localStorage.removeItem("cal_remember");
    return;
  }
  const exp=Date.now()+30*24*60*60*1000;
  localStorage.setItem("cal_remember",JSON.stringify({user,pwd,exp}));
}

// ==================== 数据 ====================
let data = JSON.parse(localStorage.getItem("cal_data"))||{};
let curMonth, curKeys;

// ==================== 渲染 ====================
function render(){
  const cal=document.getElementById("calendar");
  cal.innerHTML="";
  for(let m=1;m<=12;m++){
    const mEl=document.createElement("div");
    mEl.className="month";
    mEl.innerHTML=`
      <div class="month-head">
        <div class="month-title">${m}月</div>
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
}

function renderMonth(m){
  const box=document.getElementById(`days-${m}`);
  box.innerHTML="";
  const first = new Date(YEAR,m-1,1).getDay();
  const days = new Date(YEAR,m,0).getDate();
  for(let i=0;i<first;i++)box.innerHTML+=`<div class="day"></div>`;
  for(let d=1;d<=days;d++){
    const key=`${m}-${d}`;
    const item=data[key]||{color:"#f7f5f2",todo:""};
    const lunar=getLunar(m,d);
    box.innerHTML+=`
      <div class="day" style="background:${item.color}" onclick="openEdit(${m},${d})">
        <div class="num">${d}<span class="lunar">${lunar}</span></div>
        <div class="todo">${item.todo}</div>
      </div>
    `;
  }
}

// ==================== 编辑 ====================
function openEdit(m,d){
  curMonth=m; curKeys=[`${m}-${d}`];
  const item=data[curKeys[0]]||{color:"#f7f5f2",todo:""};
  document.getElementById("todoInput").value=item.todo;
  buildColors(item.color);
  document.getElementById("mask").style.display="block";
  document.getElementById("pop").style.display="block";
}

function buildColors(active){
  const box=document.getElementById("colors");
  box.innerHTML="";
  COLORS.forEach(c=>{
    const el=document.createElement("div");
    el.className="color-item"+(c==active?" active":"");
    el.style.background=c;
    el.onclick=()=>{
      document.querySelectorAll(".color-item").forEach(i=>i.classList.remove("active"));
      el.classList.add("active");
    };
    box.appendChild(el);
  });
}

document.getElementById("ok").onclick=()=>{
  const c=document.querySelector(".color-item.active").style.backgroundColor;
  const t=document.getElementById("todoInput").value.trim();
  curKeys.forEach(k=>data[k]={color:c,todo:t});
  localStorage.setItem("cal_data",JSON.stringify(data));
  renderMonth(curMonth);
  closePop();
  toast("已保存");
};

document.getElementById("cancel").onclick=closePop;
function closePop(){
  document.getElementById("mask").style.display="none";
  document.getElementById("pop").style.display="none";
}

// ==================== 清空本月 ====================
function clearMonth(m){
  if(!confirm(`确定清空 ${m}月 所有内容？`))return;
  for(let k in data){
    if(k.split("-")[0]==m) delete data[k];
  }
  localStorage.setItem("cal_data",JSON.stringify(data));
  renderMonth(m);
  toast(`${m}月已清空`);
}

// ==================== 登录 ====================
document.getElementById("loginBtn").onclick=()=>{
  const u=document.getElementById("user").value;
  const p=document.getElementById("pwd").value;
  if(u==USER&&p==PWD){
    saveRemember();
    document.getElementById("loginPage").style.display="none";
    document.getElementById("main").style.display="block";
    render();
  }else{
    toast("账号或密码错误");
  }
};

window.onload=loadRemember;
</script>
</body>
</html>
