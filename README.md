<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>انقلاب اسلامی</title>
<style>
  *{margin:0;padding:0;box-sizing:border-box;font-family:Tahoma,sans-serif}
  body{background:#f4f6f9;color:#333;line-height:1.8}
  header{background:linear-gradient(135deg,#1a3a5c,#2e5a88);color:#fff;padding:2rem;text-align:center}
  header h1{font-size:2rem;margin-bottom:.4rem}
  .container{max-width:1100px;margin:2rem auto;padding:0 1.5rem}
  .card{background:#fff;border-radius:12px;box-shadow:0 4px 15px rgba(0,0,0,.08);padding:2rem;margin-bottom:2rem}
  .card h2{color:#1a3a5c;border-bottom:3px solid #2e5a88;padding-bottom:.5rem;margin-bottom:1.2rem;font-size:1.15rem}
  .card p{white-space:pre-wrap;text-align:justify;margin-bottom:1rem}
  .media{display:flex;flex-wrap:wrap;gap:1rem;justify-content:center}
  .media>div{background:#eef2f7;border-radius:8px;padding:.6rem;text-align:center;flex:1 1 250px;max-width:340px}
  .media img,.media video{max-width:100%;border-radius:6px;display:block}
  .sources{list-style:disc;padding-right:1.5rem}
  .sources li{margin-bottom:.6rem}
  .comments textarea,.comments input{width:100%;padding:.8rem;border:1px solid #ccc;border-radius:6px;font-family:inherit;margin-bottom:.6rem}
  .comments textarea{min-height:100px}
  .btn{background:#2e5a88;color:#fff;border:none;padding:.7rem 2rem;border-radius:6px;cursor:pointer;font-family:inherit;font-size:1rem}
  .btn:hover{background:#1a3a5c}
  .btn.danger{background:#c0392b}
  .btn.small{padding:.4rem 1rem;font-size:.85rem}
  .comment-item{background:#f8f9fb;border-right:4px solid #2e5a88;padding:.7rem;border-radius:6px;margin-top:.6rem;font-size:.95rem}
  footer{background:#1a3a5c;color:#ddd;text-align:center;padding:2rem;margin-top:3rem}
  .authors{color:#fff;font-weight:bold;margin-top:.4rem}
  .admin-link{position:fixed;bottom:20px;left:20px;background:#333;color:#fff;padding:10px 15px;border-radius:50px;text-decoration:none;font-size:.85rem;opacity:.75;cursor:pointer;border:none}
  .admin-link:hover{opacity:1}
  .overlay{position:fixed;inset:0;background:rgba(0,0,0,.6);display:none;justify-content:center;align-items:center;z-index:999;padding:1rem}
  .overlay.show{display:flex}
  .modal{background:#fff;border-radius:12px;padding:2rem;width:100%;max-width:420px;box-shadow:0 8px 30px rgba(0,0,0,.3);position:relative}
  .modal h3{color:#1a3a5c;text-align:center;margin-bottom:1.2rem}
  .modal input{width:100%;padding:.7rem;margin:.4rem 0;border:1px solid #ccc;border-radius:6px;box-sizing:border-box;font-family:inherit}
  .modal .btn{width:100%;margin-top:.6rem}
  .close-x{position:absolute;top:.7rem;left:.9rem;font-size:1.4rem;cursor:pointer;color:#888;background:none;border:none;line-height:1}
  .msg{padding:.6rem;border-radius:6px;font-size:.9rem;text-align:center;display:none;margin-top:.6rem}
  .ok{background:#d4edda;color:#155724;display:block}
  .err{background:#f8d7da;color:#721c24;display:block}
  .admin-wrap{max-width:950px;margin:auto}
  .admin-head{display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:.5rem}
  .admin-head h1{font-size:1.4rem;color:#1a3a5c}
  .tabs{display:flex;gap:.5rem;margin-bottom:1rem;flex-wrap:wrap}
  .tab{padding:.5rem 1rem;background:#eef2f7;border:none;border-radius:6px;cursor:pointer;font-family:inherit}
  .tab.active{background:#2e5a88;color:#fff}
  .tab-content{display:none}
  .tab-content.active{display:block}
  label{display:block;font-size:.9rem;color:#555;margin-top:.5rem}
  #galleryAdmin .item{border:1px solid #ddd;border-radius:8px;padding:.6rem;text-align:center;background:#fafbfc;display:flex;flex-direction:column;gap:.4rem}
  #galleryAdmin img,#galleryAdmin video{max-width:100%;border-radius:6px;max-height:150px}
  .pending-comment{background:#fff8e1;border-right:4px solid #f0ad4e;padding:.7rem;border-radius:6px;margin-top:.6rem;font-size:.9rem}
  .pending-comment .actions{display:flex;gap:.5rem;margin-top:.4rem}
</style>
</head>
<body>

<div id="siteView">
  <header>
    <h1 id="siteTitle">انقلاب اسلامی</h1>
    <p>موسس، پشتوانه، چرایی، موانع و مباحث دینی</p>
  </header>
  <div class="container">
    <div class="card"><h2>موسس و پشتوانه</h2><p id="founder"></p></div>
    <div class="card"><h2>چرایی و موانع</h2><p id="why"></p></div>
    <div class="card"><h2>مباحث دینی</h2><p id="religion"></p></div>
    <div class="card"><h2>رسانه</h2><div class="media" id="mediaPublic"></div></div>
    <div class="card comments">
      <h2>نظرات و پیشنهادات</h2>
      <input id="cName" placeholder="نام شما (اختیاری)">
      <textarea id="cText" placeholder="نظر یا پیشنهاد خود را بنویسید..."></textarea>
      <button class="btn" id="cBtn">ارسال نظر</button>
      <div id="cList"></div>
    </div>
    <div class="card"><h2>منابع</h2><ul class="sources" id="sources"></ul></div>
  </div>
  <button class="admin-link" id="openAuthBtn">ورود ادمین</button>
  <footer>
    <p>تمامی حقوق محفوظ است.</p>
    <p class="authors">نوشته شده توسط: علی عبداله نیا و پرهام حسام پور</p>
  </footer>
</div>

<div id="adminView" class="container" style="display:none">
  <div class="admin-wrap">
    <div class="admin-head card">
      <h1>پنل مدیریت</h1>
      <div>
        <span id="who" style="color:#666;font-size:.9rem;margin-left:.7rem"></span>
        <button class="btn danger small" id="logoutBtn">خروج</button>
      </div>
    </div>
    <div class="tabs">
      <button class="tab active" data-tab="content">محتوا</button>
      <button class="tab" data-tab="media">رسانه</button>
      <button class="tab" data-tab="comments">نظرات</button>
      <button class="tab" data-tab="account">حساب ادمین</button>
    </div>

    <div class="card tab-content active" id="tab-content">
      <h2>ویرایش محتوای سایت</h2>
      <label>عنوان سایت</label><input id="f_title">
      <label>موسس و پشتوانه</label><textarea id="f_founder" rows="4"></textarea>
      <label>چرایی و موانع</label><textarea id="f_why" rows="4"></textarea>
      <label>مباحث دینی</label><textarea id="f_religion" rows="4"></textarea>
      <label>منابع (هر خط یک منبع)</label><textarea id="f_sources" rows="5"></textarea>
      <button class="btn" id="saveContentBtn">ذخیره محتوا</button>
      <div id="m_content" class="msg"></div>
    </div>

    <div class="card tab-content" id="tab-media">
      <h2>افزودن عکس / ویدیو</h2>
      <label>آپلود فایل</label><input type="file" id="fileInput" accept="image/*,video/*">
      <button class="btn" id="uploadBtn">آپلود و افزودن</button>
      <div style="text-align:center;color:#888;margin:.8rem 0">— یا —</div>
      <label>افزودن با لینک</label>
      <input id="urlInput" placeholder="https://example.com/image.jpg">
      <select id="urlType"><option value="image">عکس</option><option value="video">ویدیو</option></select>
      <button class="btn" id="addUrlBtn">افزودن لینک</button>
      <div id="m_media" class="msg"></div>
      <h2 style="margin-top:1.5rem">رسانه‌های موجود</h2>
      <div class="media" id="galleryAdmin"></div>
    </div>

    <div class="card tab-content" id="tab-comments">
      <h2>در انتظار تأیید</h2><div id="pendingComments"></div>
      <h2 style="margin-top:1.5rem">تأیید شده</h2><div id="approvedComments"></div>
    </div>

    <div class="card tab-content" id="tab-account">
      <h2>تغییر نام کاربری و رمز ادمین</h2>
      <label>نام کاربری جدید</label><input id="newUser" placeholder="admin">
      <label>رمز جدید (حداقل ۶ کاراکتر)</label><input type="password" id="newPass">
      <button class="btn" id="changeCredBtn">ذخیره تغییرات</button>
      <div id="m_account" class="msg"></div>
    </div>
  </div>
</div>

<div class="overlay" id="authOverlay">
  <div class="modal">
    <button class="close-x" id="closeAuth">×</button>
    <h3>ورود ادمین</h3>
    <input id="loginUser" placeholder="نام کاربری">
    <input id="loginPass" type="password" placeholder="رمز عبور">
    <button class="btn" id="loginBtn">ورود</button>
    <div id="m_login" class="msg"></div>
  </div>
</div>

<script>
/* ============================================================
   تنظیمات ادمین پیش‌فرض — قابل تغییر از داخل پنل
   نام کاربری: admin
   رمز: Admin@1403
   ============================================================ */
const DEFAULT_ADMIN = { username: "admin", password: "Admin@1403" };

/* ============================================================
   ذخیره‌سازی محلی (localStorage) — بدون نیاز به سرور/Firebase
   ============================================================ */
const KEY = {
  admin:   "site_admin_cred",
  content: "site_content",
  media:   "site_media",
  comments:"site_comments",
  session: "site_session"
};

function getAdmin(){
  try { return JSON.parse(localStorage.getItem(KEY.admin)) || {...DEFAULT_ADMIN}; }
  catch { return {...DEFAULT_ADMIN}; }
}
function setAdmin(a){ localStorage.setItem(KEY.admin, JSON.stringify(a)); }

function getArr(k){
  try { return JSON.parse(localStorage.getItem(k)) || []; }
  catch { return []; }
}
function setArr(k,v){ localStorage.setItem(k, JSON.stringify(v)); }

function getContent(){
  try { return JSON.parse(localStorage.getItem(KEY.content)) || {
    title:"انقلاب اسلامی",
    founder:"",
    why:"",
    religion:"",
    sources:""
  }; } catch { return {}; }
}
function setContent(c){ localStorage.setItem(KEY.content, JSON.stringify(c)); }

const $ = id => document.getElementById(id);
function showMsg(id, text, ok=true){
  const e = $(id);
  e.textContent = text;
  e.className = "msg " + (ok ? "ok" : "err");
  if(ok) setTimeout(()=>{ if(e.textContent===text) e.className="msg"; }, 4000);
}
function esc(s){ return (s||"").replace(/[<>&"]/g, c=>({'<':'&lt;','>':'&gt;','&':'&amp;','"':'&quot;'}[c])); }

/* ============ ورود ادمین ============ */
$("openAuthBtn").onclick = ()=>{
  if(localStorage.getItem(KEY.session) === "1"){ showAdmin(); }
  else { $("authOverlay").classList.add("show"); }
};
$("closeAuth").onclick = ()=> $("authOverlay").classList.remove("show");

$("loginBtn").onclick = ()=>{
  const u = $("loginUser").value.trim();
  const p = $("loginPass").value;
  const a = getAdmin();
  if(u === a.username && p === a.password){
    localStorage.setItem(KEY.session, "1");
    $("authOverlay").classList.remove("show");
    $("m_login").className = "msg";
    $("loginUser").value = ""; $("loginPass").value = "";
    showAdmin();
  } else {
    showMsg("m_login", "نام کاربری یا رمز اشتباه است.", false);
  }
};

$("logoutBtn").onclick = ()=>{
  localStorage.removeItem(KEY.session);
  $("adminView").style.display = "none";
  $("siteView").style.display = "block";
  loadPublic();
};

function showAdmin(){
  $("siteView").style.display = "none";
  $("adminView").style.display = "block";
  const a = getAdmin();
  $("who").textContent = "ادمین: " + a.username;
  loadAdminAll();
}

/* ============ سایت عمومی ============ */
function loadPublic(){
  const c = getContent();
  $("siteTitle").textContent = c.title || "انقلاب اسلامی";
  $("founder").textContent  = c.founder || "";
  $("why").textContent      = c.why || "";
  $("religion").textContent = c.religion || "";
  const ul = $("sources"); ul.innerHTML = "";
  (c.sources||"").split("\n").filter(Boolean).forEach(s=>{
    const li = document.createElement("li"); li.textContent = s; ul.appendChild(li);
  });

  const md = $("mediaPublic"); md.innerHTML = "";
  getArr(KEY.media).slice().sort((a,b)=>b.createdAt-a.createdAt).forEach(m=>{
    const div = document.createElement("div");
    div.innerHTML = m.type==="image"
      ? `<img src="${esc(m.url)}" alt="">`
      : `<video src="${esc(m.url)}" controls></video>`;
    md.appendChild(div);
  });

  const list = $("cList"); list.innerHTML = "";
  getArr(KEY.comments).filter(c=>c.approved).sort((a,b)=>b.createdAt-a.createdAt).forEach(c=>{
    const div = document.createElement("div");
    div.className = "comment-item";
    div.textContent = (c.name||"ناشناس") + ": " + c.text;
    list.appendChild(div);
  });
}

$("cBtn").onclick = ()=>{
  const text = $("cText").value.trim();
  const name = $("cName").value.trim();
  if(!text) return alert("متن نظر خالی است.");
  const arr = getArr(KEY.comments);
  arr.push({ id: Date.now()+"_"+Math.random(), text, name, approved:false, createdAt: Date.now() });
  setArr(KEY.comments, arr);
  $("cText").value = "";
  alert("نظر ثبت شد و پس از تأیید ادمین نمایش داده می‌شود.");
};

/* ============ تب‌های پنل ============ */
document.querySelectorAll(".tab").forEach(t=>{
  t.onclick = ()=>{
    document.querySelectorAll(".tab").forEach(x=>x.classList.remove("active"));
    document.querySelectorAll(".tab-content").forEach(x=>x.classList.remove("active"));
    t.classList.add("active");
    $("tab-" + t.dataset.tab).classList.add("active");
  };
});

function loadAdminAll(){
  loadContentAdmin();
  loadMediaAdmin();
  loadCommentsAdmin();
  const a = getAdmin();
  $("newUser").value = a.username;
}

/* محتوا */
function loadContentAdmin(){
  const c = getContent();
  $("f_title").value    = c.title || "";
  $("f_founder").value  = c.founder || "";
  $("f_why").value      = c.why || "";
  $("f_religion").value = c.religion || "";
  $("f_sources").value  = c.sources || "";
}
$("saveContentBtn").onclick = ()=>{
  setContent({
    title: $("f_title").value,
    founder: $("f_founder").value,
    why: $("f_why").value,
    religion: $("f_religion").value,
    sources: $("f_sources").value,
    updatedAt: Date.now()
  });
  showMsg("m_content", "محتوا ذخیره شد ✅", true);
};

/* رسانه */
function loadMediaAdmin(){
  const md = $("galleryAdmin"); md.innerHTML = "";
  getArr(KEY.media).slice().sort((a,b)=>b.createdAt-a.createdAt).forEach(m=>{
    const div = document.createElement("div");
    div.className = "item";
    div.innerHTML = (m.type==="image"
      ? `<img src="${esc(m.url)}" alt="">`
      : `<video src="${esc(m.url)}" controls></video>`)
      + `<div style="font-size:.8rem;color:#777;word-break:break-all">${esc(m.name||"")}</div>`;
    const del = document.createElement("button");
    del.className = "btn danger small";
    del.textContent = "حذف";
    del.onclick = ()=>{
      if(!confirm("حذف شود؟")) return;
      setArr(KEY.media, getArr(KEY.media).filter(x=>x.id !== m.id));
      loadMediaAdmin();
    };
    div.appendChild(del);
    md.appendChild(div);
  });
}

$("uploadBtn").onclick = ()=>{
  const f = $("fileInput").files[0];
  if(!f) return showMsg("m_media", "اول یک فایل انتخاب کن.", false);
  if(f.size > 4 * 1024 * 1024){
    return showMsg("m_media", "حجم فایل زیاد است (حداکثر ۴ مگابایت). برای فایل بزرگ‌تر از «افزودن با لینک» استفاده کن.", false);
  }
  const reader = new FileReader();
  reader.onload = ()=>{
    const arr = getArr(KEY.media);
    arr.push({
      id: Date.now()+"_"+Math.random(),
      url: reader.result,
      type: f.type.startsWith("video") ? "video" : "image",
      name: f.name,
      createdAt: Date.now()
    });
    setArr(KEY.media, arr);
    showMsg("m_media", "آپلود شد ✅", true);
    $("fileInput").value = "";
    loadMediaAdmin();
  };
  reader.readAsDataURL(f);
};

$("addUrlBtn").onclick = ()=>{
  const url = $("urlInput").value.trim();
  if(!url) return showMsg("m_media", "لینک را وارد کن.", false);
  const arr = getArr(KEY.media);
  arr.push({
    id: Date.now()+"_"+Math.random(),
    url, type: $("urlType").value,
    name: url.split("/").pop(),
    createdAt: Date.now()
  });
  setArr(KEY.media, arr);
  showMsg("m_media", "لینک اضافه شد ✅", true);
  $("urlInput").value = "";
  loadMediaAdmin();
};

/* نظرات */
function loadCommentsAdmin(){
  const pend = $("pendingComments"), appr = $("approvedComments");
  pend.innerHTML = ""; appr.innerHTML = "";
  const all = getArr(KEY.comments).sort((a,b)=>b.createdAt-a.createdAt);
  all.forEach(c=>{
    const wrap = document.createElement("div");
    if(c.approved){
      wrap.className = "comment-item";
      wrap.innerHTML = `<div><b>${esc(c.name||"ناشناس")}</b>: ${esc(c.text)}</div>`;
      const del = document.createElement("button");
      del.className = "btn danger small"; del.style.marginTop=".4rem"; del.textContent="حذف";
      del.onclick = ()=>{
        if(!confirm("حذف شود؟")) return;
        setArr(KEY.comments, getArr(KEY.comments).filter(x=>x.id !== c.id));
        loadCommentsAdmin();
      };
      wrap.appendChild(del);
      appr.appendChild(wrap);
    } else {
      wrap.className = "pending-comment";
      wrap.innerHTML = `<div><b>${esc(c.name||"ناشناس")}</b>: ${esc(c.text)}</div>`;
      const actions = document.createElement("div");
      actions.className = "actions";
      const ok = document.createElement("button");
      ok.className="btn small"; ok.textContent="تأیید";
      ok.onclick = ()=>{
        const arr = getArr(KEY.comments).map(x=> x.id===c.id ? {...x, approved:true} : x);
        setArr(KEY.comments, arr);
        loadCommentsAdmin();
      };
      const del = document.createElement("button");
      del.className="btn danger small"; del.textContent="حذف";
      del.onclick = ()=>{
        if(!confirm("حذف شود؟")) return;
        setArr(KEY.comments, getArr(KEY.comments).filter(x=>x.id !== c.id));
        loadCommentsAdmin();
      };
      actions.appendChild(ok); actions.appendChild(del);
      wrap.appendChild(actions);
      pend.appendChild(wrap);
    }
  });
  if(!pend.children.length) pend.innerHTML = '<div style="color:#888;font-size:.9rem">نظر جدیدی در انتظار تأیید نیست.</div>';
  if(!appr.children.length) appr.innerHTML = '<div style="color:#888;font-size:.9rem">هنوز نظری تأیید نشده.</div>';
}

/* تغییر نام کاربری و رمز */
$("changeCredBtn").onclick = ()=>{
  const u = $("newUser").value.trim();
  const p = $("newPass").value;
  if(!u) return showMsg("m_account", "نام کاربری را وارد کن.", false);
  if(p && p.length < 6) return showMsg("m_account", "رمز حداقل ۶ کاراکتر.", false);
  const a = getAdmin();
  setAdmin({ username: u, password: p ? p : a.password });
  $("who").textContent = "ادمین: " + u;
  $("newPass").value = "";
  showMsg("m_account", "ذخیره شد ✅ (نام کاربری: " + u + ")", true);
};

/* شروع */
if(localStorage.getItem(KEY.session) === "1"){ showAdmin(); }
else { loadPublic(); }
</script>
</body>
</html>
