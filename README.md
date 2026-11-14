<!DOCTYPE html>
<html lang="th">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>BANGSAEN42-2026 · Command Center</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Sarabun:wght@400;500;700;800&display=swap" rel="stylesheet">
<style>
:root{--bg:#0a0f1e;--p1:#111933;--p2:#17213f;--bd:#26325a;--tx:#e8ecf8;--mut:#8b97bd;--ac:#38bdf8;
--red:#ef4444;--yel:#facc15;--grn:#22c55e;--oth:#64748b}
*{box-sizing:border-box}
html{scroll-behavior:smooth}
body{margin:0;background:radial-gradient(1200px 600px at 80% -10%,#16224a 0,transparent 60%),var(--bg);color:var(--tx);
font-family:'Sarabun',system-ui,-apple-system,'Segoe UI',sans-serif;font-size:15px;min-height:100vh}
.top{display:flex;flex-wrap:wrap;gap:12px;align-items:center;justify-content:space-between;padding:14px 22px;border-bottom:1px solid var(--bd);background:rgba(10,15,30,.85);backdrop-filter:blur(8px);position:sticky;top:0;z-index:10}
.brand{display:flex;align-items:center;gap:12px}
.logo{width:38px;height:38px;border-radius:10px;background:linear-gradient(135deg,var(--red),#f97316);display:grid;place-items:center;font-weight:800;font-size:20px}
.brand h1{margin:0;font-size:19px;letter-spacing:.3px}
.brand small{color:var(--mut)}
.right{display:flex;gap:10px;align-items:center;flex-wrap:wrap}
#clock{font-variant-numeric:tabular-nums;font-size:20px;font-weight:700;color:var(--ac)}
.st{color:var(--mut);font-size:13px;display:flex;align-items:center;gap:6px;max-width:420px}
.dot{width:9px;height:9px;border-radius:50%;background:var(--oth);flex:none}
.dot.ok{background:var(--grn);box-shadow:0 0 8px var(--grn)}.dot.err{background:var(--red);box-shadow:0 0 8px var(--red)}
button{font:inherit;color:var(--tx);background:var(--p2);border:1px solid var(--bd);border-radius:8px;padding:6px 12px;cursor:pointer}
button:hover{border-color:var(--ac)}
button.on{background:var(--ac);color:#06202e;border-color:var(--ac);font-weight:700}
main{max-width:1560px;margin:0 auto;padding:18px 22px 40px}
.kpis{display:grid;grid-template-columns:repeat(auto-fit,minmax(170px,1fr));gap:12px;margin-bottom:16px}
.kpi{background:var(--p1);border:1px solid var(--bd);border-top:4px solid var(--oth);border-radius:12px;padding:12px 16px}
.kpi b{display:block;font-size:38px;line-height:1.05;font-weight:800;font-variant-numeric:tabular-nums}
.kpi span{color:var(--mut);font-size:13px}
.kpi.r{border-top-color:var(--red)}.kpi.r b{color:var(--red)}
.kpi.y{border-top-color:var(--yel)}.kpi.y b{color:var(--yel)}
.kpi.g{border-top-color:var(--grn)}.kpi.g b{color:var(--grn)}
.kpi.t{border-top-color:var(--ac)}
.panel{background:var(--p1);border:1px solid var(--bd);border-radius:12px;padding:14px 16px}
.panel h2{margin:0 0 10px;font-size:15px;color:var(--mut);font-weight:700;letter-spacing:.4px;text-transform:uppercase}
.pies{display:grid;grid-template-columns:repeat(auto-fit,minmax(380px,1fr));gap:14px;margin-bottom:16px}
.pie{display:flex;gap:18px;align-items:center;flex-wrap:wrap;min-height:190px}
.pie svg{width:190px;height:190px;flex:none;filter:drop-shadow(0 6px 14px rgba(0,0,0,.45))}
.pie svg path,.pie svg circle{stroke:var(--p1);stroke-width:2}
.leg{flex:1;min-width:190px;font-size:14px}
.leg div{display:flex;align-items:center;gap:8px;padding:4px 6px;border-radius:6px}
.leg div[data-t]{cursor:pointer}.leg div[data-t]:hover{background:var(--p2)}
.leg i{width:12px;height:12px;border-radius:3px;flex:none}
.leg .t{flex:1;overflow:hidden;text-overflow:ellipsis;white-space:nowrap}
.leg b{font-variant-numeric:tabular-nums;white-space:nowrap}
.sec{display:flex;justify-content:space-between;align-items:baseline;flex-wrap:wrap;gap:6px;margin:6px 0 10px}
.sec h2{margin:0;font-size:17px}.sec .mut{color:var(--mut);font-size:13px}
.hosp{display:grid;grid-template-columns:repeat(auto-fill,minmax(300px,1fr));gap:12px;margin-bottom:20px}
.hc{background:var(--p1);border:1px solid var(--bd);border-radius:12px;padding:14px 16px;cursor:pointer;transition:.15s}
.hc:hover{border-color:var(--ac);transform:translateY(-2px)}
.hc h3{margin:0;font-size:17px;line-height:1.25}
.hc .tot{display:flex;align-items:baseline;gap:6px;margin:6px 0 10px}
.hc .tot b{font-size:34px;font-weight:800;font-variant-numeric:tabular-nums}.hc .tot span{color:var(--mut);font-size:13px}
.chips{display:flex;gap:8px;margin-bottom:10px}
.chip{flex:1;text-align:center;border-radius:8px;padding:6px 0;font-weight:800;font-size:20px;background:var(--p2);border:1px solid var(--bd)}
.chip small{display:block;font-size:11px;font-weight:500;color:var(--mut)}
.chip.r{color:var(--red);border-color:rgba(239,68,68,.5)}.chip.y{color:var(--yel);border-color:rgba(250,204,21,.45)}.chip.g{color:var(--grn);border-color:rgba(34,197,94,.45)}
.last{font-size:13px;color:var(--mut);display:flex;justify-content:space-between;gap:8px;padding:3px 0;border-top:1px dashed var(--bd)}
.last.red{color:var(--tx);font-size:14px;border-top:1px solid var(--bd);padding-top:7px}
.last b{color:var(--tx);font-weight:700;text-align:right}.last.red b{color:var(--red)}
.empty{color:var(--mut);padding:18px;text-align:center}
.bar{display:flex;flex-wrap:wrap;gap:10px;margin-bottom:12px;align-items:center}
input,select{font:inherit;color:var(--tx);background:var(--p2);border:1px solid var(--bd);border-radius:8px;padding:7px 11px}
input[type=search]{flex:1;min-width:240px}
input:focus,select:focus{outline:none;border-color:var(--ac)}
.seg{display:flex;gap:6px;flex-wrap:wrap}
.wrap{overflow:auto;max-height:66vh;border-radius:10px;border:1px solid var(--bd)}
table{border-collapse:collapse;width:100%}
th,td{padding:9px 11px;text-align:left;vertical-align:top;border-bottom:1px solid var(--bd)}
th{position:sticky;top:0;background:var(--p2);color:var(--mut);font-size:12px;text-transform:uppercase;letter-spacing:.4px;white-space:nowrap;z-index:1}
tbody tr{cursor:pointer;border-left:5px solid var(--oth)}
tbody tr.r{border-left-color:var(--red)}tbody tr.y{border-left-color:var(--yel)}tbody tr.g{border-left-color:var(--grn)}
tbody tr:hover{background:var(--p2)}
.bd{display:inline-block;min-width:56px;text-align:center;padding:2px 9px;border-radius:999px;font-size:12px;font-weight:800;color:#fff}
.bd.r{background:var(--red)}.bd.y{background:var(--yel);color:#2b2200}.bd.g{background:var(--grn);color:#052e12}.bd.o{background:var(--oth)}
.clip{max-width:280px}.mut{color:var(--mut);font-size:12px}
.foot{color:var(--mut);font-size:12px;margin-top:8px}
#overlay{position:fixed;inset:0;background:rgba(0,0,0,.55);display:none;z-index:30}
#drawer{position:fixed;top:0;right:0;height:100%;width:min(540px,100%);background:var(--p1);border-left:1px solid var(--bd);transform:translateX(100%);transition:transform .2s;z-index:31;overflow:auto;padding:16px 18px}
body.open #overlay{display:block}body.open #drawer{transform:none}
#drawer dl{display:grid;grid-template-columns:150px 1fr;gap:6px 12px;margin:12px 0 0}
#drawer dt{color:var(--mut);font-size:12px}#drawer dd{margin:0;white-space:pre-wrap;word-break:break-word}
.dh{display:flex;justify-content:space-between;align-items:center;gap:10px}
@media print{body{background:#fff;color:#000}.top button,.bar,#drawer,#overlay{display:none!important}.top{position:static;background:#fff}
.panel,.kpi,.hc{background:#fff;border-color:#bbb}.wrap{max-height:none;overflow:visible}th{background:#eee;color:#333}.kpi b,.hc .tot b{color:#000}}
</style>
</head>
<body>
<div class="top">
  <div class="brand"><div class="logo">+</div>
    <div><h1>BANGSAEN42-2026 · Medical Command Center</h1><small>Realtime จาก Medical Record &amp; Referral Form</small></div></div>
  <div class="right">
    <div class="st"><span class="dot" id="dot"></span><span id="status">กำลังโหลด…</span></div>
    <div id="clock">--:--:--</div>
    <button id="btnRefresh">รีเฟรช</button>
    <button id="btnAuto" class="on">Auto 30s</button>
    <button id="btnPdf">PDF</button>
  </div>
</div>

<main>
  <div class="kpis" id="kpis"></div>

  <div class="pies">
    <div class="panel"><h2>เคสแดง / เหลือง / เขียว</h2><div class="pie" id="pieTri"></div></div>
    <div class="panel"><h2>สัดส่วนตาม Diagnosis</h2><div class="pie" id="pieDx"></div></div>
  </div>

  <div class="sec"><h2>🏥 โรงพยาบาลที่รับเคสส่งต่อ</h2><span class="mut" id="hospMeta"></span></div>
  <div class="hosp" id="hospGrid"></div>

  <div class="sec" id="logTop"><h2>📋 Patient log</h2><span class="mut">คลิกแถวเพื่อดูรายละเอียดทั้งหมด</span></div>
  <div class="panel">
    <div class="bar">
      <input type="search" id="q" placeholder="ค้นหา: ชื่อ, BIB, อาการ, จุดเกิดเหตุ, Dx, ร.พ., ผู้กรอก …">
      <div class="seg" id="segTri"></div>
      <select id="fHosp"><option value="">ทุก ร.พ. / disposition</option></select>
      <button id="btnClear">ล้างตัวกรอง</button>
    </div>
    <div class="wrap"><table><thead id="logHead"></thead><tbody id="logBody"></tbody></table></div>
    <div class="foot" id="logFoot"></div>
  </div>
</main>

<div id="overlay"></div>
<aside id="drawer"></aside>

<script>
/* ===== CONFIG ===== */
const SHEET_ID   = '1RZyc-IEYDtgFkGkqBODJK8NpG8oTddDnpNLK1-Uwh0Y';
const SHEET_NAME = 'Form Responses 1';
const REFRESH_MS = 30000;
const HOSPITAL_RE = /ร\.?พ\.?|โรงพยาบาล|hospital|hosp\b|รพ/i;
const LOG_LIMIT = 500;
/* ================== */

let headers = [], recs = [], C = {}, auto = true, timer = null;
const F = {tri:'', hosp:''};
const $ = id => document.getElementById(id);
const esc = s => String(s ?? '').replace(/[&<>"']/g, c => ({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[c]));
const pad = n => String(n).padStart(2,'0');
const fmtT = d => d ? `${pad(d.getDate())}/${pad(d.getMonth()+1)} ${pad(d.getHours())}:${pad(d.getMinutes())}` : '–';
const TL = {r:'แดง', y:'เหลือง', g:'เขียว', o:'อื่นๆ'};

function ago(d){
  if(!d) return '';
  const m = Math.round((Date.now() - d.getTime())/60000);
  if(m < 1) return 'เมื่อสักครู่';
  if(m < 60) return m + ' นาทีที่แล้ว';
  const h = Math.floor(m/60); if(h < 24) return h + ' ชม. ' + (m%60) + ' น. ที่แล้ว';
  return Math.floor(h/24) + ' วันที่แล้ว';
}
function triageKey(s){
  const t = (s||'').toLowerCase();
  if(/red|แดง/.test(t)) return 'r';
  if(/yellow|เหลือง/.test(t)) return 'y';
  if(/green|เขียว/.test(t)) return 'g';
  return 'o';
}
function maskId(s){ s = String(s||''); return s.length > 4 ? '•'.repeat(s.length-4) + s.slice(-4) : s; }
function colIdx(...keys){ return headers.findIndex(h => keys.some(k => h.toLowerCase().includes(k.toLowerCase()))); }

function toDate(cell, base){
  if(!cell || cell.v == null || cell.v === '') return null;
  const v = cell.v;
  if(typeof v === 'string' && v.startsWith('Date(')){
    const n = v.match(/\d+/g).map(Number);
    return new Date(n[0], n[1], n[2], n[3]||0, n[4]||0, n[5]||0);
  }
  if(Array.isArray(v)){
    const d = base ? new Date(base) : new Date();
    d.setHours(v[0]||0, v[1]||0, v[2]||0, 0); d._t = true; return d;
  }
  if(typeof v === 'string'){
    const m = v.trim().match(/^(\d{1,2})[:.](\d{2})(?:[:.](\d{2}))?$/);
    if(m){ const d = base ? new Date(base) : new Date(); d.setHours(+m[1], +m[2], +(m[3]||0), 0); d._t = true; return d; }
    const t = Date.parse(v); if(!isNaN(t)) return new Date(t);
  }
  return null;
}

async function load(){
  $('status').textContent = 'กำลังโหลด…';
  try{
    const url = `https://docs.google.com/spreadsheets/d/${SHEET_ID}/gviz/tq?tqx=out:json&headers=1&sheet=${encodeURIComponent(SHEET_NAME)}&_=${Date.now()}`;
    const res = await fetch(url, {cache:'no-store'});
    if(!res.ok) throw new Error('HTTP ' + res.status);
    const txt = await res.text();
    const json = JSON.parse(txt.substring(txt.indexOf('{'), txt.lastIndexOf('}')+1));
    if(json.status === 'error') throw new Error((json.errors||[]).map(e => e.detailed_message || e.message).join('; '));
    const t = json.table;
    let rows = t.rows.map(r => (r.c||[]).map(c => c ? {v:c.v, f:c.f} : null));
    headers = t.cols.map(c => (c.label||'').trim());
    if(headers.every(h => !h) && rows.length){ headers = rows[0].map(c => c ? String(c.v ?? '') : ''); rows = rows.slice(1); }
    build(rows); renderAll();
    $('dot').className = 'dot ok';
    $('status').textContent = `อัปเดต ${new Date().toLocaleTimeString('th-TH')} · ${recs.length} เคส`;
  }catch(e){
    $('dot').className = 'dot err';
    $('status').textContent = 'โหลดไม่สำเร็จ: ' + e.message + ' (ตรวจว่าชีตแชร์แบบ Anyone with the link และชื่อ tab ถูกต้อง)';
  }
}

function build(rows){
  C = {
    ts: colIdx('timestamp'), tri: colIdx('triage'), rec: colIdx('record time'), bib: colIdx('bib'),
    name: colIdx('patient full name'), sex: colIdx('sex'), age: colIdx('age (years)'),
    loc: colIdx('incident location'), cc: colIdx('chief complaint'), dx: colIdx('provisional diagnosis'),
    dt: colIdx('disposition time'), dc: colIdx('disposition choice'), nid: colIdx('national id'),
    ref: colIdx('กรณีที่ refer','refer')
  };
  const disp = c => c ? (c.f ?? (c.v == null ? '' : String(c.v))) : '';
  recs = rows.filter(r => r.some(c => c && c.v != null && c.v !== '')).map((r, i) => {
    const base = C.ts >= 0 ? toDate(r[C.ts]) : null;
    const g = k => C[k] >= 0 ? disp(r[C[k]]) : '';
    let evt = (C.dt >= 0 && toDate(r[C.dt], base)) || (C.rec >= 0 && toDate(r[C.rec], base)) || base;
    if(evt && evt._t && base){
      const dh = (evt - base)/36e5;
      if(dh < -12) evt = new Date(evt.getTime() + 864e5); else if(dh > 12) evt = new Date(evt.getTime() - 864e5);
    }
    const dispV = g('dc').trim(), hosp = g('ref').replace(/\s+/g,' ').trim();
    const dest = hosp || (/refer|ส่งต่อ|นำส่ง/i.test(dispV) ? dispV + ' (ไม่ระบุ ร.พ.)' : dispV);
    const o = { i, cells: r.map(disp), tri: triageKey(g('tri')), bib: g('bib'), name: g('name'), sex: g('sex'), age: g('age'),
      loc: g('loc'), cc: g('cc'), dx: g('dx'), dispT: g('dt'), disp: dispV, hosp, dest, evt, ts: base };
    o.isRef = !!hosp || HOSPITAL_RE.test(dispV);
    o.hay = o.cells.join(' | ').toLowerCase();
    return o;
  });
  recs.sort((a,b) => (b.ts||0) - (a.ts||0));
}

/* ---------- pie ---------- */
const PAL = ['#38bdf8','#a78bfa','#f472b6','#34d399','#fb923c','#2dd4bf','#e879f9'];
function pie(el, items, clickable){
  const tot = items.reduce((a,b) => a + b.value, 0);
  if(!tot){ el.innerHTML = '<span class="mut">ยังไม่มีข้อมูล</span>'; return; }
  const cx = 95, cy = 95, R = 88; let a0 = -Math.PI/2, svg = '';
  const pt = a => `${(cx + R*Math.cos(a)).toFixed(2)} ${(cy + R*Math.sin(a)).toFixed(2)}`;
  const live = items.filter(x => x.value > 0);
  live.forEach(x => {
    const fr = x.value/tot;
    if(fr > 0.9999){ svg += `<circle cx="${cx}" cy="${cy}" r="${R}" fill="${x.color}"><title>${esc(x.label)}: ${x.value}</title></circle>`; return; }
    const a1 = a0 + fr*2*Math.PI;
    svg += `<path d="M${cx} ${cy} L${pt(a0)} A${R} ${R} 0 ${fr > 0.5 ? 1 : 0} 1 ${pt(a1)} Z" fill="${x.color}"><title>${esc(x.label)}: ${x.value} (${(fr*100).toFixed(1)}%)</title></path>`;
    a0 = a1;
  });
  el.innerHTML = `<svg viewBox="0 0 190 190" role="img">${svg}</svg><div class="leg">` +
    live.map(x => `<div title="${esc(x.label)}" ${clickable && x.key ? `data-t="${x.key}"` : ''}><i style="background:${x.color}"></i><span class="t">${esc(x.label)}</span><b>${x.value} · ${(x.value*100/tot).toFixed(1)}%</b></div>`).join('') +
    `<div class="mut" style="margin-top:4px">รวม ${tot} เคส</div></div>`;
}

/* ---------- render ---------- */
function count(list){ const c = {r:0,y:0,g:0,o:0}; list.forEach(x => c[x.tri]++); return c; }

function renderKpis(){
  const c = count(recs), ref = recs.filter(r => r.isRef).length;
  $('kpis').innerHTML =
    `<div class="kpi t"><b>${recs.length}</b><span>เคสทั้งหมด</span></div>
     <div class="kpi r"><b>${c.r}</b><span>แดง</span></div>
     <div class="kpi y"><b>${c.y}</b><span>เหลือง</span></div>
     <div class="kpi g"><b>${c.g}</b><span>เขียว</span></div>
     <div class="kpi"><b>${ref}</b><span>ส่งต่อ ร.พ. แล้ว</span></div>
     <div class="kpi"><b>${recs.filter(r => !r.dest).length}</b><span>ยังไม่มี disposition</span></div>`;
}

function renderPies(){
  const c = count(recs);
  pie($('pieTri'), [
    {label:'แดง', value:c.r, color:'#ef4444', key:'r'}, {label:'เหลือง', value:c.y, color:'#facc15', key:'y'},
    {label:'เขียว', value:c.g, color:'#22c55e', key:'g'}, {label:'อื่นๆ / ไม่ระบุ', value:c.o, color:'#64748b', key:'o'}], true);
  const m = new Map();
  recs.forEach(r => {
    const raw = (r.dx || '').replace(/\s+/g,' ').trim(), k = raw ? raw.toLowerCase() : '(ไม่ระบุ)';
    if(!m.has(k)) m.set(k, {label: raw || 'ไม่ระบุ Dx', value:0}); m.get(k).value++;
  });
  let arr = [...m.values()].sort((a,b) => b.value - a.value);
  const TOP = 7;
  if(arr.length > TOP + 1){ const rest = arr.slice(TOP).reduce((s,x) => s + x.value, 0); arr = arr.slice(0, TOP).concat([{label:'อื่นๆ', value:rest}]); }
  pie($('pieDx'), arr.map((x,i) => ({...x, color: x.label === 'อื่นๆ' ? '#64748b' : PAL[i % PAL.length]})), false);
}

function renderHosp(){
  const H = new Map();
  recs.filter(r => r.isRef).forEach(r => {
    const k = r.dest;
    if(!H.has(k)) H.set(k, {n:k, r:0, y:0, g:0, o:0, lr:null, ly:null, lg:null});
    const h = H.get(k); h[r.tri]++;
    const f = {r:'lr', y:'ly', g:'lg'}[r.tri];
    if(f && r.evt && (!h[f] || r.evt > h[f])) h[f] = r.evt;
  });
  const tot = h => h.r + h.y + h.g + h.o;
  const arr = [...H.values()].sort((a,b) => tot(b) - tot(a) || (b.lr||0) - (a.lr||0));
  const nonRef = recs.filter(r => !r.isRef && r.dest).length, pend = recs.filter(r => !r.dest).length;
  $('hospMeta').textContent = `${arr.length} ร.พ. · ส่งต่อรวม ${recs.filter(r => r.isRef).length} เคส · ไม่ได้ส่งต่อ/อื่นๆ ${nonRef} · ยังไม่ระบุ ${pend}`;
  const last = (cls, label, n, d) => `<div class="last ${cls}"><span>${label}</span><b>${n ? fmtT(d) + ' · ' + ago(d) : 'ยังไม่เคยรับ'}</b></div>`;
  $('hospGrid').innerHTML = arr.map(h => `<div class="hc" data-d="${esc(h.n)}">
      <h3>${esc(h.n)}</h3>
      <div class="tot"><b>${tot(h)}</b><span>เคสที่รับแล้ว</span></div>
      <div class="chips"><div class="chip r">${h.r}<small>แดง</small></div><div class="chip y">${h.y}<small>เหลือง</small></div><div class="chip g">${h.g}<small>เขียว</small></div></div>
      ${last('red', 'รับเคสแดงล่าสุด', h.r, h.lr)}
      ${last('', 'เคสเหลืองล่าสุด', h.y, h.ly)}
      ${last('', 'เคสเขียวล่าสุด', h.g, h.lg)}
    </div>`).join('') || '<div class="empty panel" style="grid-column:1/-1">ยังไม่มีเคสที่ส่งต่อไป ร.พ.</div>';
}

function renderSeg(){
  const c = count(recs);
  const b = (k, t, n) => `<button data-t="${k}" class="${F.tri === k ? 'on' : ''}">${t}${n != null ? ' ' + n : ''}</button>`;
  $('segTri').innerHTML = b('', 'ทั้งหมด', recs.length) + b('r','แดง',c.r) + b('y','เหลือง',c.y) + b('g','เขียว',c.g) + b('o','อื่นๆ',c.o);
}
function renderHospSelect(){
  const sel = $('fHosp'), vals = [...new Set(recs.map(r => r.dest).filter(Boolean))].sort();
  sel.innerHTML = '<option value="">ทุก ร.พ. / disposition</option>' + vals.map(v => `<option value="${esc(v)}">${esc(v)}</option>`).join('');
  if(!vals.includes(F.hosp)) F.hosp = '';
  sel.value = F.hosp;
}

function filtered(){
  const q = $('q').value.trim().toLowerCase().split(/\s+/).filter(Boolean);
  return recs.filter(r => (!F.tri || r.tri === F.tri) && (!F.hosp || r.dest === F.hosp) && q.every(w => r.hay.includes(w)));
}
function renderLog(){
  const list = filtered(), shown = list.slice(0, LOG_LIMIT);
  $('logHead').innerHTML = '<tr><th>เวลา</th><th>Triage</th><th>BIB</th><th>ชื่อ</th><th>เพศ/อายุ</th><th>จุดเกิดเหตุ</th><th>อาการสำคัญ</th><th>Dx</th><th>ส่งต่อ / Disposition</th></tr>';
  $('logBody').innerHTML = shown.map(r => `<tr class="${r.tri}" data-i="${r.i}">
    <td>${fmtT(r.ts)}</td><td><span class="bd ${r.tri}">${TL[r.tri]}</span></td><td>${esc(r.bib)}</td><td>${esc(r.name)}</td>
    <td>${esc(r.sex)} ${esc(r.age)}</td><td class="clip">${esc(r.loc)}</td><td class="clip">${esc(r.cc)}</td><td class="clip">${esc(r.dx)}</td>
    <td>${r.dest ? '<b>' + esc(r.hosp || r.dest) + '</b>' : '<span class="mut">–</span>'}<div class="mut">${esc(r.hosp ? r.disp : '')} ${esc(r.dispT)}</div></td></tr>`).join('')
    || '<tr><td colspan="9" class="empty">ไม่พบข้อมูล</td></tr>';
  $('logFoot').textContent = `แสดง ${shown.length} จาก ${list.length} เคสที่ตรงเงื่อนไข (ทั้งหมด ${recs.length})` + (list.length > LOG_LIMIT ? ` · แสดง ${LOG_LIMIT} เคสล่าสุด ใช้ช่องค้นหาเพื่อจำกัด` : '');
}
function renderAll(){ renderKpis(); renderPies(); renderHosp(); renderSeg(); renderHospSelect(); renderLog(); }

function openDrawer(i){
  const r = recs.find(x => x.i == i); if(!r) return;
  const rows = headers.map((h, k) => {
    let v = r.cells[k] ?? ''; if(!v) return '';
    if(k === C.nid) v = maskId(v);
    return `<dt>${esc(h)}</dt><dd>${esc(v)}</dd>`;
  }).join('');
  $('drawer').innerHTML = `<div class="dh"><div><span class="bd ${r.tri}">${TL[r.tri]}</span> <b style="font-size:17px">${esc(r.name || 'ไม่ระบุชื่อ')}</b><div class="mut">BIB ${esc(r.bib)}</div></div><button id="dClose">ปิด</button></div><dl>${rows}</dl>`;
  document.body.classList.add('open');
}
function closeDrawer(){ document.body.classList.remove('open'); }
function goLog(){ $('logTop').scrollIntoView({behavior:'smooth'}); }
function schedule(){ clearInterval(timer); if(auto) timer = setInterval(load, REFRESH_MS); }

/* ---------- events ---------- */
$('btnRefresh').onclick = load;
$('btnAuto').onclick = e => { auto = !auto; e.target.classList.toggle('on', auto); e.target.textContent = 'Auto 30s' + (auto ? '' : ' (ปิด)'); schedule(); };
$('btnPdf').onclick = () => window.print();
$('btnClear').onclick = () => { $('q').value = ''; F.tri = ''; F.hosp = ''; renderSeg(); renderHospSelect(); renderLog(); };
$('q').addEventListener('input', renderLog);
$('fHosp').addEventListener('change', e => { F.hosp = e.target.value; renderLog(); });
$('segTri').addEventListener('click', e => { const b = e.target.closest('button'); if(!b) return; F.tri = b.dataset.t; renderSeg(); renderLog(); });
$('pieTri').addEventListener('click', e => { const d = e.target.closest('[data-t]'); if(!d) return; F.tri = d.dataset.t; renderSeg(); renderLog(); goLog(); });
$('hospGrid').addEventListener('click', e => { const c = e.target.closest('.hc'); if(!c) return; F.hosp = c.dataset.d; F.tri = ''; renderSeg(); renderHospSelect(); renderLog(); goLog(); });
$('logBody').addEventListener('click', e => { const tr = e.target.closest('tr'); if(tr && tr.dataset.i != null) openDrawer(tr.dataset.i); });
$('drawer').addEventListener('click', e => { if(e.target.id === 'dClose') closeDrawer(); });
$('overlay').addEventListener('click', closeDrawer);
document.addEventListener('keydown', e => { if(e.key === 'Escape') closeDrawer(); });
setInterval(() => { $('clock').textContent = new Date().toLocaleTimeString('th-TH', {hour12:false}); }, 1000);
setInterval(() => { if(recs.length) renderHosp(); }, 60000);

load(); schedule();
</script>
</body>
</html>
