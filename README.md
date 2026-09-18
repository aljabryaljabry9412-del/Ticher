<!doctype html>
<html lang="ar" dir="rtl">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1,maximum-scale=5">
<meta name="theme-color" content="#172554">
<meta name="mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-title" content="سجل المدرس">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
<title>سجل المدرس</title>

<link rel="apple-touch-icon" href="https://aljabryaljabry9412-del.github.io/Ticher/icon.jpeg?v=3">
<link rel="icon" type="image/jpeg" href="https://aljabryaljabry9412-del.github.io/Ticher/icon.jpeg?v=3">

<style>
@font-face{font-family:NaskhLocal;src:local("Noto Naskh Arabic"),local("Noto Naskh Arabic UI"),local("Traditional Arabic")}
:root{--navy:#172554;--blue:#2563eb;--bg:#f1f5f9;--card:#fff;--line:#cbd5e1;--red:#dc2626;--green:#15803d;--text:#0f172a}
*{box-sizing:border-box}body{margin:0;background:var(--bg);color:var(--text);font-family:Tahoma,Arial,sans-serif}
header{background:linear-gradient(135deg,#172554,#1d4ed8);color:white;padding:18px 22px;position:sticky;top:0;z-index:20;box-shadow:0 3px 15px #0002}
header h1{font-family:NaskhLocal,"Noto Naskh Arabic",serif;font-size:34px;margin:0 0 6px}
.header-meta{opacity:.9}.wrap{max-width:1600px;margin:auto;padding:18px}
.tabs{display:flex;gap:8px;overflow:auto;padding-bottom:8px}.tabs button{white-space:nowrap;border:0;border-radius:12px;padding:11px 16px;background:#e2e8f0;color:#0f172a;font-weight:bold;cursor:pointer}.tabs button.active{background:var(--navy);color:white}
.card{background:var(--card);border:1px solid var(--line);border-radius:16px;padding:18px;margin-bottom:16px;box-shadow:0 2px 10px #0000000a}
.grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:12px}.field label{display:block;font-weight:bold;margin-bottom:6px}.field input,.field select,.field textarea{width:100%;padding:10px;border:1px solid #94a3b8;border-radius:99px;background:white;font-size:16px}
button,.btn{border:0;border-radius:10px;padding:10px 14px;cursor:pointer;font-weight:bold}.primary{background:var(--blue);color:#fff}.danger{background:#fee2e2;color:#991b1b}.secondary{background:#e2e8f0}.success{background:#dcfce7;color:#166534}
.actions{display:flex;gap:8px;flex-wrap:wrap;margin-top:12px}.muted{color:#64748b}.section-title{font-size:21px;margin:0 0 12px}.hidden{display:none!important}
.header-action-row{display:flex;align-items:center;justify-content:space-between;gap:10px;margin-bottom:12px}.header-action-row .section-title{margin:0}
.action-select{-webkit-appearance:none;-moz-appearance:none;appearance:none;width:38px!important;min-width:38px!important;height:38px;padding:0;border:1px solid var(--blue);border-radius:8px;background:#eff6ff;color:var(--blue);font-weight:bold;font-size:20px;cursor:pointer;outline:none;text-align:center;text-align-last:center}
.stage-tabs,.class-tabs{display:flex;gap:7px;flex-wrap:wrap}.stage-item,.class-item{display:flex;gap:3px;align-items:center}
.stage-item button,.class-item button{background:#e2e8f0;color:#0f172a}
.stage-item.active-stage button,.class-item.active-class button{background:var(--blue)!important;color:white!important}
.table-wrap{overflow:auto;max-height:65vh;border:1px solid var(--line);border-radius:12px;background:white}
table{border-collapse:separate;border-spacing:0;min-width:1750px;width:max-content}th,td{border-left:1px solid var(--line);border-bottom:1px solid var(--line);padding:4px;text-align:center;white-space:nowrap;background:white}th{background:#e2e8f0;font-weight:bold;position:sticky;top:0;z-index:4}
.sticky-seq{position:sticky;right:0;z-index:7;width:32px!important;min-width:32px!important;max-width:32px!important;padding-left:2px!important;padding-right:2px!important}.sticky-name{position:sticky;right:32px;z-index:6;min-width:180px}th.sticky-name,th.sticky-seq{background:#cbd5e1}
td input{width:48px;border:1px solid #cbd5e1;border-radius:6px;padding:4px 2px;text-align:center;font-size:15px}.name-input{width:170px!important}
.low{color:var(--red)!important;font-weight:bold}.calc{font-weight:bold}.summary{font-weight:bold}.summary td{background:#f8fafc}.summary-label{font-size:13px}.goodtxt{color:var(--green)}.badtxt{color:var(--red)}
.daily-box{text-align:center;max-width:650px;margin:20px auto}.daily-name{font-size:32px;font-family:NaskhLocal,"Noto Naskh Arabic",serif;margin:15px}.daily-grade{font-size:30px;width:160px!important;text-align:center}.progress{height:10px;background:#e2e8f0;border-radius:20px;overflow:hidden}.progress>div{height:100%;background:var(--blue)}
.att-name{font-size:30px;text-align:center;font-family:NaskhLocal,"Noto Naskh Arabic",serif;margin:20px}.att-buttons{display:flex;justify-content:center;gap:15px}.att-buttons button{font-size:22px;min-width:130px}.present{background:#dcfce7;color:#166534}.absent{background:#fee2e2;color:#991b1b}
.report-list{padding:0;list-style:none}.report-list li{padding:7px 10px;border-radius:7px;margin:3px 0}.report-present li{background:#dcfce7;color:#166534}.report-absent li{background:#fee2e2;color:#991b1b}
.photo-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(150px,1fr));gap:10px}.photo-grid img{width:100%;height:130px;object-fit:cover;border-radius:10px;border:1px solid var(--line)}
.modal{position:fixed;inset:0;background:#0008;display:flex;align-items:center;justify-content:center;z-index:100;padding:20px}.modal>div{background:white;border-radius:16px;padding:20px;max-width:850px;width:100%;max-height:90vh;overflow:auto}
.search-card .student-search-row{display:flex;gap:8px;align-items:center}.student-search-row input{flex:1;min-width:0;padding:11px 12px;border:1px solid #94a3b8;border-radius:99px;background:white;font-size:16px}.student-search-results{margin-top:14px}.search-result{border:1px solid var(--line);border-radius:12px;padding:12px;margin-top:10px;background:#f8fafc}.search-result h3{margin:0 0 8px;color:var(--navy)}.search-meta{color:#64748b;font-size:14px;margin-bottom:10px}.search-grades{display:grid;grid-template-columns:repeat(auto-fit,minmax(145px,1fr));gap:7px}.search-grade{background:white;border:1px solid #e2e8f0;border-radius:8px;padding:7px;text-align:center}.search-grade b{display:block;font-size:13px;color:#475569;margin-bottom:3px}.search-notes{margin-top:10px;padding:9px;background:#fff;border-radius:8px;border-right:4px solid var(--blue);white-space:pre-wrap}.search-empty{padding:12px;border-radius:10px;background:#fee2e2;color:#991b1b;font-weight:bold}
.print-area{display:none}
@media print{body{background:white}.no-print,header,.tabs,.actions,.card:not(.print-card){display:none!important}.print-area{display:block!important}.print-card{display:block!important;border:0;box-shadow:none;padding:0}table{min-width:0;width:100%;font-size:9px}th,td{padding:3px}.table-wrap{overflow:visible;max-height:none;border:0}}
@media(max-width:700px){header h1{font-size:27px}.wrap{padding:10px}.card{padding:12px}.sticky-seq{width:28px!important;min-width:28px!important;max-width:28px!important}.sticky-name{min-width:135px;right:28px}.name-input{width:125px!important}}
</style>
</head>
<body>
<header><h1>سجل المدرس</h1><div class="header-meta" id="headerMeta">المدرسة • المدرس • المادة</div></header>
<div class="wrap">
<div class="tabs no-print">
<button type="button" id="btn-home" onclick="showTab('home')" class="active">الرئيسية</button>
<button type="button" id="btn-students" onclick="showTab('students')">أسماء الطلاب</button>
<button type="button" id="btn-daily" onclick="showTab('daily')">الاختبار اليومي</button>
<button type="button" id="btn-attendance" onclick="showTab('attendance')">سجل الحضور</button>
<button type="button" id="btn-absence" onclick="showTab('absence')">سجل الغياب</button>
<button type="button" id="btn-backup" onclick="showTab('backup')">النسخ الاحتياطي</button>
</div>
<section id="home" class="tab">
<div class="card"><h2 class="section-title">بيانات السجل</h2><div class="grid">
<div class="field"><label>اسم المدرسة</label><input id="school"></div><div class="field"><label>اسم المدرس</label><input id="teacher"></div><div class="field"><label>اسم المادة</label><input id="subject"></div>
</div><div class="actions"><button class="primary" onclick="saveMeta()">حفظ البيانات</button></div></div>
<div class="card search-card"><h2 class="section-title">البحث عن طالب</h2><div class="student-search-row"><input id="studentSearchInput" type="search" placeholder="اكتب اسم الطالب" autocomplete="off" onkeydown="if(event.key==='Enter')searchStudent()"><button class="primary" onclick="searchStudent()">بحث</button></div><div id="studentSearchResults" class="student-search-results hidden"></div></div>

<div class="card">
  <div class="header-action-row">
    <h2 class="section-title">المراحل الدراسية</h2>
    <select class="action-select" onchange="handleStageAction(this)">
      <option value="" selected disabled>⋮</option>
      <option value="add">+ إضافة مرحلة جديدة</option>
      <option value="rename">✏️ تعديل المرحلة الحالية</option>
      <option value="delete">🗑️ حذف المرحلة الحالية</option>
    </select>
  </div>
  <div id="stageTabs" class="stage-tabs"></div>
</div>

<div class="card" id="stageCard">
  <div class="header-action-row">
    <h2 class="section-title">الشعبة في المرحلة: <span id="stageTitle"></span></h2>
    <select class="action-select" onchange="handleClassAction(this)">
      <option value="" selected disabled>⋮</option>
      <option value="add">+ إضافة شعبة جديدة</option>
      <option value="rename">✏️ تعديل الشعبة الحالية</option>
      <option value="delete">🗑️ حذف الشعبة الحالية</option>
    </select>
  </div>
  <div id="classTabs" class="class-tabs"></div>
  <p class="muted" style="margin-top:10px;">الشعبة اختيارية؛ يمكنك إبقاؤها باسم افتراضي أو تعديلها.</p>
</div>

</section>
<section id="students" class="tab hidden"><div class="card"><div class="actions no-print"><button class="primary" onclick="addStudent()">+ إضافة طالب</button><button class="secondary" onclick="importStudents()">استيراد أسماء من TXT / DOC / DOCX</button><input id="studentFile" type="file" accept=".txt,.doc,.docx" class="hidden" onchange="readStudentFile(this)"><button class="secondary" onclick="printGrades('all')">طباعة جميع الأعمدة</button><button class="secondary" onclick="printGrades('summary')">طباعة المعدلات فقط</button><button class="secondary" onclick="openPrintColumns()">تخصيص الطباعة</button></div><div id="studentsTitle" class="muted"></div><div class="table-wrap" id="gradeWrap"></div></div></section>
<section id="daily" class="tab hidden"><div class="card daily-box"><h2 class="section-title">الاختبار اليومي</h2><div id="dailyStatus" class="muted"></div><div class="progress"><div id="dailyProgress" style="width:0%"></div></div><div id="dailyName" class="daily-name">—</div><input id="dailyGrade" class="daily-grade" type="number" min="0" max="100" step="1" inputmode="numeric" placeholder="0 - 100"><div class="actions" style="justify-content:center"><button class="primary" onclick="saveDailyGrade()">حفظ والانتقال للاسم التالي</button><button class="secondary" onclick="nextDailyOnly()">الاسم التالي</button></div></div></section>
<section id="attendance" class="tab hidden"><div class="card daily-box"><h2 class="section-title">سجل الحضور</h2><div class="muted" id="attDate"></div><div id="attName" class="att-name">—</div><div class="att-buttons"><button class="present" onclick="markAttendance(true)">حاضر</button><button class="absent" onclick="markAttendance(false)">غائب</button></div><div class="actions" style="justify-content:center"><button class="secondary" onclick="attendanceBack()">العودة إلى الخلف</button><button class="danger" onclick="cancelAttendance()">إلغاء الجلسة</button></div><div id="attReport" class="hidden"></div></div></section>
<section id="absence" class="tab hidden"><div class="card"><h2 class="section-title">سجل الغياب</h2><div class="grid no-print"><div class="field"><label>اختر التاريخ</label><input id="absenceDate" type="date" onchange="renderAbsence()"></div></div><div class="actions no-print"><button class="primary" onclick="renderAbsence()">عرض السجل</button><button class="secondary" onclick="openCamera()">تصوير وإضافة صورة</button><button class="secondary" onclick="pickPhoto()">اختيار صورة من الجهاز</button><input id="photoFile" type="file" accept="image/*" class="hidden" onchange="savePhotoFromFile(this)"><button class="secondary" onclick="printAbsence('all')">طباعة الحاضرين والغائبين</button><button class="secondary" onclick="printAbsence('absent')">طباعة الغائبين</button><button class="secondary" onclick="printAbsence('present')">طباعة الحاضرين</button></div><div id="absenceContent"></div></div></section>
<section id="backup" class="tab hidden"><div class="card"><h2 class="section-title">النسخ الاحتياطي والاستعادة</h2><p>يعمل السجل محلياً داخل الجهاز باستخدام التخزين المحلي، ويمكنك حفظ نسخة JSON واستعادتها لاحقاً حتى لا تضيع البيانات عند مسح بيانات المتصفح.</p><div class="actions"><button class="primary" onclick="exportJSON()">تصدير البيانات كملف JSON</button><button class="secondary" onclick="document.getElementById('jsonFile').click()">استيراد ملف سابق</button><input id="jsonFile" type="file" accept=".json,application/json" class="hidden" onchange="importJSON(this)"></div></div></section>
</div>
<div id="nameModal" class="modal hidden no-print"><div style="max-width:520px"><h2 id="nameModalTitle">إضافة</h2><div class="field"><label id="nameModalLabel">الاسم</label><input id="nameModalInput" autocomplete="off"></div><div class="actions"><button class="primary" onclick="submitNameModal()">حفظ</button><button class="secondary" onclick="closeModal('nameModal')">إلغاء</button></div></div></div>
<div id="printColumnsModal" class="modal hidden no-print"><div><h2>اختيار أعمدة الطباعة</h2><div id="columnChecks"></div><div class="actions"><button class="primary" onclick="printCustom()">طباعة</button><button class="secondary" onclick="closeModal('printColumnsModal')">إلغاء</button></div></div></div>
<div id="cameraModal" class="modal hidden no-print"><div><h2>التقاط صورة</h2><video id="video" autoplay playsinline style="width:100%;max-height:60vh"></video><div class="actions"><button class="primary" onclick="capturePhoto()">التقاط</button><button class="secondary" onclick="closeCamera()">إغلاق</button></div></div></div>
<div id="printArea" class="print-area print-card"></div>
<script>
const KEY="teacherRegisterV1";
const arabicDigits=s=>String(s).replace(/\d/g,d=>"٠١٢٣٤٥٦٧٨٩"[d]);
const latinDigits=s=>String(s).replace(/[٠-٩]/g,d=>"٠١٢٣٤٥٦٧٨٩".indexOf(d));
const uid=()=>Date.now().toString(36)+Math.random().toString(36).slice(2,8);
let db=loadDB(),currentStage=0,currentClass=0,dailyOrder=[],dailyIndex=0,attSession=null,stream=null;

function blankClass(name="الشعبة ١"){return{id:uid(),name,students:[],attendance:{},photos:{},daily:{}}}
function blankStage(name="المرحلة ١"){return{id:uid(),name,classes:[blankClass()]}}
function defaultDB(){return{meta:{school:"",teacher:"",subject:""},stages:[blankStage()]}}
function loadDB(){try{return JSON.parse(localStorage.getItem(KEY))||defaultDB()}catch(e){return defaultDB()}}
function saveDB(){localStorage.setItem(KEY,JSON.stringify(db));updateHeader()}
function currentStageObj(){return db.stages[currentStage]||db.stages[0]}
function currentClassObj(){
  let stage=currentStageObj();
  if(!stage.classes[currentClass]) currentClass=0;
  return stage.classes[currentClass]||stage.classes[0];
}
function confirmAction(msg){return confirm(msg+"\n\nلا يمكن التراجع عن هذا الإجراء.")}
function updateHeader(){document.getElementById("headerMeta").textContent=[db.meta.school||"اسم المدرسة",db.meta.teacher||"اسم المدرس",db.meta.subject||"اسم المادة"].join(" • ")}
function normalizeSearchName(v){return String(v||"").trim().toLowerCase().replace(/[أإآٱ]/g,"ا").replace(/ى/g,"ي").replace(/ة/g,"ه").replace(/[ًٌٍَُِّْـ]/g,"").replace(/\s+/g," ")}

function searchStudent(){
  const input=document.getElementById("studentSearchInput"),box=document.getElementById("studentSearchResults");
  const q=normalizeSearchName(input.value);
  if(!q){box.classList.remove("hidden");box.innerHTML='<div class="search-empty">اكتب اسم الطالب أولاً.</div>';return}
  const results=[];
  db.stages.forEach(stage=>stage.classes.forEach(cls=>cls.students.forEach(s=>{
    if(normalizeSearchName(s.name).includes(q)){calc(s);results.push({stage:stage.name,className:cls.name,student:s})}
  })));
  box.classList.remove("hidden");
  if(!results.length){box.innerHTML='<div class="search-empty">لم يتم العثور على طالب بهذا الاسم.</div>';return}
  box.innerHTML='<div class="muted">تم العثور على '+arabicDigits(results.length)+' نتيجة</div>'+results.map(r=>{
    const s=r.student;
    const gradeHtml=fields.map(f=>`<div class="search-grade"><b>${f[1]}</b><span>${s[f[0]]===""||s[f[0]]==null?"—":arabicDigits(s[f[0]])}</span></div>`).join("");
    return `<div class="search-result"><h3>${esc(s.name)}</h3><div class="search-meta">المرحلة: ${esc(r.stage)} — الشعبة: ${esc(r.className)}</div><div class="search-grades">${gradeHtml}</div><div class="search-notes"><b>الملاحظات:</b><br>${s.notes?esc(s.notes):'<span class="muted">لا توجد ملاحظات.</span>'}</div></div>`
  }).join("")
}

function saveMeta(){
  db.meta.school=document.getElementById("school").value.trim();
  db.meta.teacher=document.getElementById("teacher").value.trim();
  db.meta.subject=document.getElementById("subject").value.trim();
  saveDB();
  alert("تم حفظ البيانات");
}

function init(){
  document.getElementById("school").value=db.meta.school;
  document.getElementById("teacher").value=db.meta.teacher;
  document.getElementById("subject").value=db.meta.subject;
  renderStages();
  renderStudents();
  resetDaily();
  updateHeader();
}

function showTab(id){
  const target=document.getElementById(id);
  if(!target)return;
  document.querySelectorAll(".tab").forEach(x=>x.classList.add("hidden"));
  target.classList.remove("hidden");
  
  document.querySelectorAll(".tabs button").forEach(b=>{
    if(b.id === "btn-" + id){
      b.classList.add("active");
    } else {
      b.classList.remove("active");
    }
  });

  if(id==="students")renderStudents();
  if(id==="daily")resetDaily();
  if(id==="absence")renderAbsence();
  if(id==="attendance"){attSession=null;startAttendance();}
}

function renderStages(){
  let el=document.getElementById("stageTabs");
  if(!db.stages || db.stages.length === 0) db.stages = [blankStage()];
  if(currentStage >= db.stages.length) currentStage = 0;
  
  el.innerHTML=db.stages.map((s,i)=>`<span class="stage-item ${i===currentStage?'active-stage':''}"><button type="button" onclick="selectStage(${i})">${esc(s.name)}</button></span>`).join("");
  selectStage(currentStage);
}

function selectStage(i){
  currentStage=i;
  if(!db.stages[currentStage]) currentStage = 0;
  document.querySelectorAll(".stage-item").forEach((el,idx)=>{
    if(idx===i)el.classList.add("active-stage");else el.classList.remove("active-stage")
  });
  let stageObj = currentStageObj();
  if(stageObj){
    document.getElementById("stageTitle").textContent=stageObj.name;
    if(!stageObj.classes || stageObj.classes.length === 0) stageObj.classes = [blankClass()];
    if(currentClass >= stageObj.classes.length) currentClass = 0;
    
    let el=document.getElementById("classTabs");
    el.innerHTML=stageObj.classes.map((c,j)=>`<span class="class-item ${j===currentClass?'active-class':''}"><button type="button" onclick="selectClass(${j})">${esc(c.name)}</button></span>`).join("");
    selectClass(currentClass);
  }
}

function selectClass(i){
  currentClass=i;
  let stageObj = currentStageObj();
  if(stageObj && stageObj.classes){
    if(currentClass >= stageObj.classes.length) currentClass = 0;
    document.querySelectorAll(".class-item").forEach((el,idx)=>{
      if(idx===i)el.classList.add("active-class");else el.classList.remove("active-class")
    });
    document.getElementById("stageTitle").textContent=stageObj.name;
  }
  renderStudents();
  resetDaily();
}

function handleStageAction(sel){
  const val = sel.value;
  sel.value = "";
  if(val === "add") addStage();
  else if(val === "rename") renameCurrentStage();
  else if(val === "delete") deleteCurrentStage();
}

function handleClassAction(sel){
  const val = sel.value;
  sel.value = "";
  if(val === "add") addClass();
  else if(val === "rename") renameCurrentClass();
  else if(val === "delete") deleteCurrentClass();
}

let nameModalAction=null;
function openNameModal(title,label,value,action){
  document.getElementById("nameModalTitle").textContent=title;
  document.getElementById("nameModalLabel").textContent=label;
  const input=document.getElementById("nameModalInput");
  input.value=value||"";
  nameModalAction=action;
  document.getElementById("nameModal").classList.remove("hidden");
  setTimeout(()=>{input.focus();input.select()},50)
}

function submitNameModal(){
  const input=document.getElementById("nameModalInput");
  const n=input.value.trim();
  if(!n){alert("يرجى كتابة الاسم.");input.focus();return}
  const action=nameModalAction;
  closeModal("nameModal");
  nameModalAction=null;
  if(action)action(n)
}

function addStage(){
  openNameModal("إضافة مرحلة دراسية","اسم المرحلة","المرحلة "+arabicDigits(db.stages.length+1),n=>{
    db.stages.push(blankStage(n));
    currentStage=db.stages.length-1;
    currentClass=0;
    saveDB();
    renderStages();
  })
}

function renameCurrentStage(){
  const st=currentStageObj();
  openNameModal("تعديل المرحلة","اسم المرحلة",st.name,n=>{
    st.name=n;
    saveDB();
    renderStages();
  })
}

function deleteCurrentStage(){
  if(db.stages.length===1){alert("يجب أن تبقى مرحلة واحدة على الأقل.");return}
  if(confirmAction("هل تريد حذف المرحلة الحالية وكل شعبها وطلابها؟")){
    db.stages.splice(currentStage,1);
    currentStage=Math.max(0,currentStage-1);
    currentClass=0;
    saveDB();
    renderStages();
  }
}

function addClass(){
  const a=currentStageObj().classes;
  openNameModal("إضافة شعبة","اسم الشعبة","الشعبة "+arabicDigits(a.length+1),n=>{
    a.push(blankClass(n));
    currentClass=a.length-1;
    saveDB();
    renderStages();
  })
}

function renameCurrentClass(){
  const c=currentClassObj();
  openNameModal("تعديل الشعبة","اسم الشعبة",c.name,n=>{
    c.name=n;
    saveDB();
    renderStages();
  })
}

function deleteCurrentClass(){
  const a=currentStageObj().classes;
  if(a.length===1){alert("يجب أن تبقى شعبة واحدة على الأقل.");return}
  if(confirmAction("هل تريد حذف الشعبة الحالية وجميع طلابها ودرجاتها؟")){
    a.splice(currentClass,1);
    currentClass=Math.max(0,currentClass-1);
    saveDB();
    renderStages();
  }
}

const fields=[["oral1a","شفهي ١"],["month1a","درجة الشهر ١"],["oral2a","شفهي ٢"],["month2a","درجة الشهر ٢"],["avg1","معدل الفصل الأول"],["mid","درجة نصف السنة"],["oral1b","شفهي ١"],["month1b","درجة الشهر ١"],["oral2b","شفهي ٢"],["month2b","درجة الشهر ٢"],["avg2","معدل الفصل الثاني"],["annual","السعي السنوي"]];

function blankStudent(name){
  let s={id:uid(),name,notes:""};
  fields.forEach(f=>{if(!["avg1","avg2","annual"].includes(f[0]))s[f[0]]=""});
  return s;
}

function sortStudents(){
  let cls = currentClassObj();
  if(cls && cls.students) {
    cls.students.sort((a,b)=>a.name.localeCompare(b.name,"ar"));
  }
}

function addStudent(){
  let n=prompt("اسم الطالب:");
  if(!n||!n.trim())return;
  currentClassObj().students.push(blankStudent(n.trim()));
  sortStudents();
  saveDB();
  renderStudents();
}

function importStudents(){document.getElementById("studentFile").click()}

async function readStudentFile(input){
  let f=input.files[0];
  if(!f)return;
  try{
    let text=await f.text();
    let names=text.split(/\r?\n/).map(x=>x.trim()).filter(Boolean);
    if(!names.length)throw 0;
    names.forEach(n=>{if(!currentClassObj().students.some(s=>s.name===n))currentClassObj().students.push(blankStudent(n))});
    sortStudents();
    saveDB();
    renderStudents();
    alert("تم استيراد "+arabicDigits(names.length)+" اسماً.");
  }catch(e){
    alert("تعذر قراءة الملف. استخدم ملف نصي TXT.");
  }
  input.value="";
}

function validGrade(v){return v!==""&&Number.isFinite(Number(v))&&Number(v)>=0&&Number(v)<=100}
function num(v){return v===""?0:Number(v)}
function round10(x){return Math.round(x*10)/10}
function calc(s){
  s.avg1=Math.round((num(s.oral1a)+num(s.month1a)+num(s.oral2a)+num(s.month2a))/4);
  s.avg2=Math.round((num(s.oral1b)+num(s.month1b)+num(s.oral2b)+num(s.month2b))/4);
  s.annual=Math.round((num(s.avg1)+num(s.mid)+num(s.avg2))/3);
}

function renderStudents(){
  let c=currentClassObj();
  if(!c) return;
  sortStudents();
  document.getElementById("studentsTitle").textContent=`${c.name} — ${c.students.length?arabicDigits(c.students.length):"٠"} طالب`;
  c.students.forEach(calc);
  let head=`<tr><th class="sticky-seq">ت</th><th class="sticky-name">اسم الطالب</th>${fields.map(f=>`<th>${f[1]}</th>`).join("")}<th>ملاحظات</th></tr>`;
  let rows=c.students.map((s,i)=>`<tr><td class="sticky-seq">${arabicDigits(i+1)}</td><td class="sticky-name"><input class="name-input" value="${escAttr(s.name)}" onchange="editName('${s.id}',this.value)"></td>${fields.map(f=>{let k=f[0],v=s[k]?? "";let disabled=["avg1","avg2","annual"].includes(k);return `<td><input ${disabled?"readonly":""} type="text" inputmode="decimal" autocomplete="off" value="${v===""?"":arabicDigits(v)}" class="${validGrade(v)&&Number(v)<50?"low":""}" onchange="editGrade('${s.id}','${k}',this.value,this)"></td>`}).join("")}<td><textarea rows="2" onchange="editNotes('${s.id}',this.value)">${esc(s.notes||"")}</textarea></td></tr>`).join("");
  let sums=summaryRows(c.students);
  document.getElementById("gradeWrap").innerHTML=`<table><thead>${head}</thead><tbody>${rows}</tbody><tfoot>${sums}</tfoot></table>`;
}

function editName(id,v){let s=findStudent(id);if(!v.trim())return alert("لا يمكن ترك الاسم فارغاً.");s.name=v.trim();sortStudents();saveDB();renderStudents()}
function editGrade(id,k,v,input){v=latinDigits(v).trim();if(v!==""&&(isNaN(v)||Number(v)<0||Number(v)>100)){alert("الدرجة يجب أن تكون بين ٠ و ١٠٠ فقط.");input.value="";return}let s=findStudent(id);s[k]=v===""?"":Number(v);calc(s);saveDB();renderStudents()}
function editNotes(id,v){findStudent(id).notes=v;saveDB()}
function findStudent(id){return currentClassObj().students.find(s=>s.id===id)}
function summaryRows(students){let cols=["avg1","mid","avg2","annual"];return cols.map(k=>{let pass=students.filter(s=>num(s[k])>=50).length,fail=students.length-pass,pct=students.length?round10(pass/students.length*100):0;return `<tr class="summary"><td colspan="2"></td>${fields.map(f=>f[0]===k?`<td><span class="summary-label goodtxt">الناجحون: ${arabicDigits(pass)}<br><span class="badtxt">الراسبون: ${arabicDigits(fail)}</span><br>النسبة: ${arabicDigits(pct)}٪</span></td>`:`<td></td>`).join("")}<td></td></tr>`}.join("")}

function resetDaily(){let st=currentClassObj().students;dailyOrder=shuffle([...st]);dailyIndex=0;renderDaily()}
function shuffle(a){for(let i=a.length-1;i>0;i--){let j=Math.floor(Math.random()*(i+1));[a[i],a[j]]=[a[j],a[i]]}return a}
function renderDaily(){let st=currentClassObj().students;if(!st.length){document.getElementById("dailyName").textContent="لا توجد أسماء";return}if(dailyIndex>=dailyOrder.length){document.getElementById("dailyName").textContent="اكتملت الدورة";document.getElementById("dailyStatus").textContent="تم المرور على جميع الطلاب.";return}let s=dailyOrder[dailyIndex],c=currentClassObj();let done=st.filter(x=>x.oral1a!=="").length;document.getElementById("dailyName").textContent=s.name;document.getElementById("dailyGrade").value="";document.getElementById("dailyStatus").textContent=`الطالب ${arabicDigits(dailyIndex+1)} من ${arabicDigits(dailyOrder.length)}`;document.getElementById("dailyProgress").style.width=(dailyIndex/dailyOrder.length*100)+"%"}
function saveDailyGrade(){let s=dailyOrder[dailyIndex],v=latinDigits(document.getElementById("dailyGrade").value).trim();if(v===""||isNaN(v)||Number(v)<0||Number(v)>100)return alert("أدخل درجة من ٠ إلى ١٠٠.");let c=currentClassObj();if(s.oral1a==="")s.oral1a=Number(v);else if(s.oral2a==="")s.oral2a=Number(v);else if(c.students.every(x=>x.oral1a!=="")&&s.oral1b==="")s.oral1b=Number(v);else if(c.students.every(x=>x.oral1b!=="")&&s.oral2b==="")s.oral2b=Number(v);else return alert("اكتملت حقول الشفهي لهذا الطالب.");calc(s);saveDB();dailyIndex++;if(dailyIndex>=dailyOrder.length){dailyOrder=shuffle([...c.students]);dailyIndex=0}renderDaily()}
function nextDailyOnly(){if(dailyOrder.length){dailyIndex=(dailyIndex+1)%dailyOrder.length;renderDaily()}}

function startAttendance(){if(!attSession){let c=currentClassObj();if(!c.students.length){document.getElementById("attName").textContent="لا توجد أسماء";return}attSession={date:new Date().toISOString(),index:0,results:[],order:[...c.students]};}document.getElementById("attDate").textContent="تاريخ التسجيل: "+formatDate(new Date(attSession.date));renderAtt()}
function renderAtt(){if(attSession.index>=attSession.order.length)return finishAttendance();document.getElementById("attName").textContent=attSession.order[attSession.index].name}
function markAttendance(present){if(!attSession)return;let s=attSession.order[attSession.index];attSession.results.push({id:s.id,present,time:new Date().toISOString()});if(!present){s.notes=(s.notes?s.notes+"\n":"")+`غائب — ${formatDateTime(new Date())}`}saveDB();attSession.index++;renderAtt()}
function attendanceBack(){if(!attSession||attSession.index===0)return;attSession.index--;attSession.results.pop();renderAtt()}
function cancelAttendance(){if(confirmAction("هل تريد إلغاء جلسة الحضور الحالية؟")){attSession=null;document.getElementById("attReport").classList.add("hidden")}}
function finishAttendance(){let c=currentClassObj(),present=attSession.results.filter(x=>x.present),abs=attSession.results.filter(x=>!x.present);c.attendance[dateKey(attSession.date)]={date:attSession.date,results:attSession.results};saveDB();let names=id=>c.students.find(s=>s.id===id)?.name||"";document.getElementById("attName").textContent="اكتمل التسجيل";document.querySelector(".att-buttons").style.display="none";let box=document.getElementById("attReport");box.classList.remove("hidden");box.innerHTML=`<h3>تقرير الحضور</h3><p class="goodtxt">الحاضرون: ${arabicDigits(present.length)}</p><ul class="report-list report-present">${present.map(x=>`<li>${esc(names(x.id))}</li>`).join("")}</ul><p class="badtxt">الغائبون: ${arabicDigits(abs.length)}</p><ul class="report-list report-absent">${abs.map(x=>`<li>${esc(names(x.id))}</li>`).join("")}</ul>`;attSession=null}

function dateKey(iso){return new Date(iso).toISOString().slice(0,10)}
function formatDate(d){return d.toLocaleDateString("ar-IQ",{year:"numeric",month:"long",day:"numeric"})}
function formatDateTime(d){return d.toLocaleString("ar-IQ",{year:"numeric",month:"2-digit",day:"2-digit",hour:"2-digit",minute:"2-digit"})}

function renderAbsence(){let date=document.getElementById("absenceDate").value;if(!date){date=new Date().toISOString().slice(0,10);document.getElementById("absenceDate").value=date}let c=currentClassObj(),rec=c.attendance[date],el=document.getElementById("absenceContent");if(!rec){el.innerHTML="<p class='muted'>لا يوجد سجل لهذا التاريخ.</p>";return}let names=id=>c.students.find(s=>s.id===id)?.name||"";let p=rec.results.filter(x=>x.present),a=rec.results.filter(x=>!x.present);let photos=c.photos[date]||[];el.innerHTML=`<div class="card"><h3>${esc(db.meta.school||"")} — ${esc(db.meta.subject||"")} — ${esc(currentStageObj().name)}</h3><h3>تاريخ السجل: ${formatDate(new Date(rec.date))}</h3><p class="goodtxt">الحاضرون: ${arabicDigits(p.length)}</p><ul class="report-list report-present">${p.map(x=>`<li>${esc(names(x.id))}</li>`).join("")}</ul><p class="badtxt">الغائبون: ${arabicDigits(a.length)}</p><ul class="report-list report-absent">${a.map(x=>`<li>${esc(names(x.id))}</li>`).join("")}</ul><h3>الصور</h3><div class="photo-grid">${photos.map(src=>`<img src="${src}">`).join("")||"<span class='muted'>لا توجد صور.</span>"}</div></div>`}
function pickPhoto(){document.getElementById("photoFile").click()}
function savePhotoFromFile(input){let f=input.files[0];if(!f)return;let r=new FileReader();r.onload=()=>addPhoto(r.result);r.readAsDataURL(f);input.value=""}
function addPhoto(src){let date=document.getElementById("absenceDate").value||new Date().toISOString().slice(0,10),c=currentClassObj();c.photos[date]??=[];c.photos[date].push(src);saveDB();renderAbsence()}
async function openCamera(){try{stream=await navigator.mediaDevices.getUserMedia({video:{facingMode:"environment"}});document.getElementById("video").srcObject=stream;document.getElementById("cameraModal").classList.remove("hidden")}catch(e){alert("تعذر فتح الكاميرا.")}}
function capturePhoto(){let v=document.getElementById("video"),can=document.createElement("canvas");can.width=v.videoWidth;can.height=v.videoHeight;can.getContext("2d").drawImage(v,0,0);addPhoto(can.toDataURL("image/jpeg",.82));closeCamera()}
function closeCamera(){if(stream)stream.getTracks().forEach(t=>t.stop());stream=null;closeModal("cameraModal")}
function closeModal(id){document.getElementById(id).classList.add("hidden")}

function exportJSON(){let blob=new Blob([JSON.stringify(db,null,2)],{type:"application/json"}),a=document.createElement("a");a.href=URL.createObjectURL(blob);a.download=`سجل-المدرس-${new Date().toISOString().slice(0,10)}.json`;a.click();URL.revokeObjectURL(a.href)}
function importJSON(input){let f=input.files[0];if(!f)return;let r=new FileReader();r.onload=()=>{try{let x=JSON.parse(r.result);if(!x.meta||!Array.isArray(x.stages))throw 0;if(confirmAction("استيراد الملف سيستبدل البيانات الحالية. هل تريد المتابعة؟")){db=x;currentStage=0;currentClass=0;saveDB();init();alert("تمت الاستعادة بنجاح.")}}catch(e){alert("ملف JSON غير صالح.")}};r.readAsText(f);input.value=""}

function printGrades(mode){let cols=mode==="summary"?["name","avg1","mid","avg2","annual"]:["name",...fields.map(x=>x[0])];buildPrintGrades(cols)}
function openPrintColumns(){let el=document.getElementById("columnChecks");el.innerHTML=`<label><input type="checkbox" data-col="name" checked disabled> اسم الطالب</label><br>`+fields.map(f=>`<label><input type="checkbox" data-col="${f[0]}" checked> ${f[1]}</label><br>`).join("");document.getElementById("printColumnsModal").classList.remove("hidden")}
function printCustom(){let cols=[...document.querySelectorAll("#columnChecks input:checked")].map(x=>x.dataset.col);closeModal("printColumnsModal");buildPrintGrades(cols)}
function buildPrintGrades(cols){let c=currentClassObj();let title=`${db.meta.school||""} — ${db.meta.teacher||""} — ${db.meta.subject||""} — ${currentStageObj().name} — ${c.name}`;let labels={name:"اسم الطالب"};fields.forEach(f=>labels[f[0]]=f[1]);let html=`<h2 style="text-align:center">${esc(title)}</h2><table><thead><tr>${cols.map(k=>`<th>${labels[k]}</th>`).join("")}</tr></thead><tbody>${c.students.map((s,i)=>{calc(s);return `<tr>${cols.map(k=>`<td>${k==="name"?esc(s.name):arabicDigits(s[k]??"")}</td>`).join("")}</tr>`}).join("")}</tbody></table>`;document.getElementById("printArea").innerHTML=html;window.print()}
function printAbsence(kind){let date=document.getElementById("absenceDate").value,c=currentClassObj(),rec=c.attendance[date];if(!rec)return alert("لا يوجد سجل لهذا التاريخ.");let names=id=>c.students.find(s=>s.id===id)?.name||"";let arr=rec.results.filter(x=>kind==="all"||kind===(x.present?"present":"absent")),photos=c.photos[date]||[];let html=`<h2 style="text-align:center">${esc(db.meta.school||"")} — ${esc(db.meta.teacher||"")} — ${esc(db.meta.subject||"")}</h2><h3 style="text-align:center">${esc(currentStageObj().name)} — ${esc(c.name)} — ${formatDate(new Date(rec.date))}</h3><table><thead><tr><th>الاسم</th><th>الحالة</th><th>الوقت</th></tr></thead><tbody>${arr.map(x=>`<tr><td>${esc(names(x.id))}</td><td>${x.present?"حاضر":"غائب"}</td><td>${formatDateTime(new Date(x.time))}</td></tr>`).join("")}</tbody></table>${photos.length?`<h3>الصور</h3><div>${photos.map(x=>`<img src="${x}" style="max-width:45%;max-height:220px;margin:5px">`).join("")}</div>`:""}`;document.getElementById("printArea").innerHTML=html;window.print()}

function esc(s){return String(s??"").replace(/[&<>"']/g,m=>({"&":"&amp;","<":"&lt;",">":"&quot;","'":"&#39;"}[m]))}
function escAttr(s){return esc(s).replace(/"/g,"&quot;")}

init();
document.getElementById("nameModalInput").addEventListener("keydown",e=>{e.key==="Enter"&&submitNameModal();e.key==="Escape"&&closeModal("nameModal")});
</script>
</body>
</html>
