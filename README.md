# -<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<meta name="referrer" content="no-referrer">
<title>굴다리 현행화 조사 지도</title>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/leaflet/1.9.4/leaflet.min.css" onerror="this.onerror=null;this.href='https://cdn.jsdelivr.net/npm/leaflet@1.9.4/dist/leaflet.min.css';">
<script src="https://cdnjs.cloudflare.com/ajax/libs/leaflet/1.9.4/leaflet.min.js" onerror="this.onerror=null;var s=document.createElement('script');s.src='https://cdn.jsdelivr.net/npm/leaflet@1.9.4/dist/leaflet.min.js';document.head.appendChild(s);"></script>
<style>
@import url('https://cdn.jsdelivr.net/gh/orioncactus/pretendard@v1.3.9/dist/web/variable/pretendardvariable-dynamic-subset.min.css');
*{box-sizing:border-box}
html,body{margin:0;height:100%}
body{display:flex;flex-direction:column;height:100dvh;overflow:hidden;background:#f1f5f9;color:#1e293b;font-family:'Pretendard Variable',Pretendard,'Malgun Gothic',sans-serif;font-size:12px}
button,input,select{font-family:inherit;font-size:12px}
button{cursor:pointer}
header{height:46px;background:#0f172a;color:#fff;display:flex;align-items:center;justify-content:space-between;gap:8px;padding:0 10px;flex-shrink:0;box-shadow:0 2px 6px #0004;z-index:30;overflow-x:auto;white-space:nowrap}
header .logo{background:#2563eb;border-radius:8px;padding:5px 7px;font-size:14px}
header b{font-size:14px;font-weight:700}
.badge{background:#3b82f633;color:#bfdbfe;border:1px solid #60a5fa80;border-radius:99px;padding:2px 10px;font-weight:700;font-size:11px}
.tools{height:44px;background:#fff;border-bottom:1px solid #e2e8f0;display:flex;align-items:center;gap:8px;padding:0 10px;flex-shrink:0;overflow-x:auto;white-space:nowrap;z-index:20}
.btn{border:0;border-radius:8px;padding:6px 10px;font-weight:700;background:#f1f5f9;color:#334155;border:1px solid #cbd5e1}
.btn:hover{background:#e2e8f0}
.btn.pri{background:#2563eb;color:#fff;border-color:#2563eb}.btn.pri:hover{background:#1d4ed8}
.btn.on{background:#dc2626;border-color:#dc2626;color:#fff}
.btn.dk{background:#1e293b;color:#e2e8f0;border-color:#475569}
.chip{display:flex;align-items:center;gap:6px;background:#f8fafc;border:1px solid #cbd5e1;border-radius:8px;padding:4px 8px;font-weight:700}
.chip select,.chip input{border:0;background:transparent;outline:0;font-weight:700;color:#1e293b}
.chip input{width:150px}
.cnt{margin-left:auto;font-weight:700;color:#475569}
.cnt b{color:#2563eb}
main{flex:1;position:relative;min-height:0}
#mapView,#tableView{position:absolute;inset:0}
#map{width:100%;height:100%}
#tableView{display:none;flex-direction:column;background:#fff}
#tableView .top{padding:8px 12px;border-bottom:1px solid #e2e8f0;display:flex;gap:8px;align-items:center}
#tableView .wrap{flex:1;overflow:auto}
table{border-collapse:collapse;width:100%}
th{position:sticky;top:0;background:#1e293b;color:#fff;padding:8px;text-align:center;font-size:11px}
td{border-bottom:1px solid #e2e8f0;padding:7px 8px;text-align:center}
tbody tr{cursor:pointer}tbody tr:hover{background:#eff6ff}
td.l{text-align:left;font-weight:700}
.tag{display:inline-block;padding:2px 9px;border-radius:99px;font-weight:700;font-size:11px}
.t0{background:#e2e8f0;color:#475569}.t1{background:#dbeafe;color:#1d4ed8}.t2{background:#d1fae5;color:#047857}
footer{height:38px;background:#e2e8f0;border-top:1px solid #cbd5e1;display:flex;align-items:center;justify-content:space-between;padding:0 8px;flex-shrink:0;z-index:30;overflow-x:auto;white-space:nowrap}
.tab{border:0;background:transparent;padding:8px 14px;font-weight:700;color:#64748b;border-top:3px solid transparent}
.tab.act{background:#fff;color:#1d4ed8;border-top-color:#2563eb}
.st{display:flex;align-items:center;gap:6px;background:#fff;border:1px solid #cbd5e1;border-radius:99px;padding:2px 10px;font-weight:600}
.dot{width:8px;height:8px;border-radius:50%;background:#10b981;display:inline-block}
/* 핀 */
.pinw{position:relative;width:28px;height:34px}
.pin{position:absolute;left:2px;top:0;width:24px;height:24px;border-radius:50% 50% 50% 0;transform:rotate(-45deg);border:2px solid #fff;box-shadow:0 2px 6px #0006}
.pin i{position:absolute;inset:0;transform:rotate(45deg);display:flex;align-items:center;justify-content:center;color:#fff;font-style:normal;font-weight:800;font-size:11px}
.pinw.sel .pin{box-shadow:0 0 0 4px #facc1599,0 2px 6px #0006}
.pthumb{display:block;width:96px;height:72px;object-fit:cover;border-radius:4px;margin-bottom:3px}
.pnoimg{display:flex;align-items:center;justify-content:center;width:96px;height:40px;background:#f1f5f9;color:#94a3b8;border-radius:4px;margin-bottom:3px;font-size:10px}
.mode{display:flex;background:#f1f5f9;border:1px solid #cbd5e1;border-radius:8px;padding:2px;gap:2px}
.mode button{border:0;background:transparent;border-radius:6px;padding:4px 9px;font-weight:700;color:#475569}
.mode button.on{background:#1e293b;color:#fff}
.plab{position:absolute;left:30px;top:2px;background:#fffffff2;border:1px solid #94a3b8;border-radius:6px;padding:1px 6px;font-weight:700;font-size:11px;white-space:nowrap;box-shadow:0 1px 3px #0003}
.leaflet-custom-pin{background:transparent;border:0}
#guide{display:none;position:absolute;top:12px;left:50%;transform:translateX(-50%);z-index:1000;background:#2563eb;color:#fff;border:2px solid #fff;border-radius:99px;padding:8px 16px;font-weight:700;box-shadow:0 6px 16px #0004;white-space:nowrap}
.mapcur .leaflet-container{cursor:crosshair}
/* 상세 패널 */
#panel{display:none;position:absolute;top:0;right:0;bottom:0;width:430px;max-width:100%;background:#fff;border-left:1px solid #cbd5e1;z-index:1100;flex-direction:column;box-shadow:-6px 0 18px #0002}
#panel .hd{background:#0f172a;color:#fff;padding:10px 14px;display:flex;align-items:center;justify-content:space-between;flex-shrink:0}
#panel .bd{flex:1;overflow-y:auto;padding:14px}
label.fl{display:block;font-weight:700;color:#334155;margin:0 0 5px}
.in{width:100%;border:1px solid #cbd5e1;border-radius:8px;padding:9px 10px;font-weight:700;font-size:14px;outline:0}
.in:focus{border-color:#2563eb;box-shadow:0 0 0 3px #2563eb33}
.seg{display:grid;grid-template-columns:1fr 1fr;gap:8px}
.seg button{border:2px solid #cbd5e1;background:#fff;border-radius:10px;padding:12px 6px;font-weight:800;font-size:14px;color:#475569}
.seg button.a1{background:#2563eb;border-color:#2563eb;color:#fff}
.seg button.a2{background:#059669;border-color:#059669;color:#fff}
.sec{margin-bottom:16px}
.drop{border:2px dashed #cbd5e1;border-radius:12px;padding:10px;background:#f8fafc;text-align:center;color:#64748b}
.drop.over{border-color:#2563eb;background:#eff6ff}
.grid{display:grid;grid-template-columns:1fr;gap:10px;margin-top:10px}
.ph{position:relative;aspect-ratio:4/3;border-radius:8px;overflow:hidden;border:1px solid #cbd5e1;background:#e2e8f0}
.ph img{width:100%;height:100%;object-fit:cover;cursor:zoom-in;display:block}
.ph button{position:absolute;top:6px;right:6px;width:28px;height:28px;border-radius:50%;border:0;background:#000a;color:#fff;font-size:11px;line-height:1}
.ph span{position:absolute;left:0;right:0;bottom:0;background:#000a;color:#fff;font-size:11px;text-align:center;padding:3px}
.ft{padding:10px 14px;border-top:1px solid #e2e8f0;display:flex;gap:8px;justify-content:space-between;flex-shrink:0}
.btn.red{background:#fef2f2;color:#dc2626;border-color:#fecaca}
#lb{display:none;position:fixed;inset:0;background:#000d;z-index:99999;align-items:center;justify-content:center;padding:16px}
#lb img{max-width:100%;max-height:100%;border-radius:8px}
#toast{position:fixed;top:60px;right:12px;z-index:100000;display:flex;flex-direction:column;gap:6px;pointer-events:none}
#toast div{background:#0f172a;color:#fff;padding:8px 14px;border-radius:10px;font-weight:600;box-shadow:0 4px 12px #0005}
@media(max-width:640px){
 #panel{top:auto;width:100%;height:68%;border-left:0;border-top:2px solid #0f172a;border-radius:16px 16px 0 0;overflow:hidden}
 .badge{display:none}
}
</style>
</head>
<body>
<header>
  <div style="display:flex;align-items:center;gap:8px">
    <span class="logo">🚇</span><b>굴다리 현행화 조사 지도</b>
    <span class="badge">🛠️ 제작·관리: 김도훈 주무관</span>
  </div>
  <div class="chip">🗺️
    <select id="tileSel" onchange="setTile(this.value)">
      <option value="google_road">구글 도로지도</option>
      <option value="google_hybrid">구글 위성+도로</option>
      <option value="carto">Carto 도로지도</option>
      <option value="osm">OpenStreetMap</option>
    </select>
  </div>
</header>

<section class="tools">
  <button class="btn pri" id="btnAdd" onclick="toggleAdd()">📌 굴다리 핀 등록</button>
  <div class="chip">🏷️
    <select id="fDir" onchange="render()">
      <option value="">방향 전체</option><option value="1">단방향</option><option value="2">양방향</option><option value="0">미선택</option>
    </select>
  </div>
  <div class="chip">🔍 <input id="fQ" oninput="render()" placeholder="지번 검색..."></div>
  <button class="btn dk" id="btnDrag" onclick="toggleDrag()">🔒 핀 이동 잠금</button>
  <div class="mode" title="지도 핀 표시 방식">
    <button id="m_icon" onclick="setMode('icon')">📍 핀만</button>
    <button id="m_label" onclick="setMode('label')">🏷️ 핀+지번</button>
    <button id="m_photo" onclick="setMode('photo')">🖼️ 핀+지번+사진</button>
  </div>
  <button class="btn" onclick="exportJSON()">💾 백업</button>
  <button class="btn" onclick="document.getElementById('imp').click()">📂 복원</button>
  <input type="file" id="imp" accept=".json" hidden onchange="importJSON(event)">
  <div class="cnt">조사 <b id="cTot">0</b>개소 · 단방향 <b id="c1">0</b> · 양방향 <b id="c2">0</b> · 미선택 <b id="c0">0</b></div>
</section>

<main>
  <div id="mapView">
    <div id="map"></div>
    <div id="guide">📍 지도에서 굴다리 위치를 클릭하세요</div>
  </div>

  <div id="tableView">
    <div class="top">
      <b>📊 굴다리 조사 관리대장</b>
      <span style="color:#64748b">(행을 누르면 해당 📌 위치로 이동)</span>
      <button class="btn" style="margin-left:auto" onclick="exportCSV()">⬇️ 엑셀(CSV) 내려받기</button>
    </div>
    <div class="wrap"><table>
      <thead><tr><th style="width:56px">No</th><th>지번</th><th style="width:110px">방향</th><th style="width:80px">사진</th><th style="width:170px">좌표</th></tr></thead>
      <tbody id="tbody"></tbody>
    </table></div>
  </div>

  <aside id="panel">
    <div class="hd"><b>📌 굴다리 상세 내역</b><button class="btn dk" onclick="closePanel()">✕ 닫기</button></div>
    <div class="bd">
      <div class="sec"><label class="fl">지번</label>
        <input class="in" id="fJibun" placeholder="예: 봉명동 237-1" oninput="onField()"></div>
      <div class="sec"><label class="fl">통행 방향</label>
        <div class="seg"><button id="d1" onclick="setDir(1)">➡️ 단방향</button><button id="d2" onclick="setDir(2)">↔️ 양방향</button></div>
      </div>
      <div class="sec"><label class="fl">현장 사진 <span id="phCnt" style="color:#2563eb"></span></label>
        <div class="drop" id="drop">
          <div style="display:flex;gap:6px;justify-content:center">
            <button class="btn pri" onclick="document.getElementById('cam').click()">📷 촬영</button>
            <button class="btn" onclick="document.getElementById('gal').click()">🖼️ 앨범/파일</button>
          </div>
          <div style="margin-top:6px;font-size:11px">끌어놓기·붙여넣기(Ctrl+V)도 가능 · 올리면 자동 압축됩니다</div>
        </div>
        <input type="file" id="cam" accept="image/*" capture="environment" hidden onchange="addFiles(this.files);this.value=''">
        <input type="file" id="gal" accept="image/*" multiple hidden onchange="addFiles(this.files);this.value=''">
        <div class="grid" id="grid"></div>
      </div>
    </div>
    <div class="ft">
      <button class="btn red" onclick="delSpot()">🗑️ 삭제</button>
      <span class="st" id="saveSt"><i class="dot"></i>자동저장</span>
    </div>
  </aside>
</main>

<footer>
  <div>
    <button class="tab act" id="tabMap" onclick="sheet('map')">🗺️ 시트1: 굴다리 현행화 지도</button>
    <button class="tab" id="tabTbl" onclick="sheet('tbl')">📊 시트2: 조사 관리대장</button>
  </div>
  <div style="display:flex;gap:8px;align-items:center">
    <span class="st"><i class="dot"></i><span id="stTxt">저장소 준비 중</span></span>
  </div>
</footer>

<div id="lb" onclick="this.style.display='none'"><img id="lbImg"></div>
<div id="toast"></div>

<script>
const DEF=[36.3622,127.3561];
const TILES={
 google_road:{u:'https://mt1.google.com/vt/lyrs=m&hl=ko&gl=kr&x={x}&y={y}&z={z}',z:20},
 google_hybrid:{u:'https://mt1.google.com/vt/lyrs=y&hl=ko&gl=kr&x={x}&y={y}&z={z}',z:20},
 carto:{u:'https://{s}.basemaps.cartocdn.com/rastertiles/voyager/{z}/{x}/{y}{r}.png',z:19},
 osm:{u:'https://tile.openstreetmap.org/{z}/{x}/{y}.png',z:19}
};
const ORDER=['google_road','carto','osm'];
const COLOR={0:'#94a3b8',1:'#2563eb',2:'#059669'};
const DIRTXT={0:'미선택',1:'단방향',2:'양방향'};
const MAX_SIDE=1280, TARGET_KB=250;

let pinMode=(()=>{try{return localStorage.getItem('GUL_PINMODE')||'label'}catch(_){return 'label'}})();
let db=null, spots=[], selId=null, addMode=false, dragOn=false;
let map, layer, tile, tileErr=0, curTile='google_road', saveTimer=null;
const $=id=>document.getElementById(id);
const esc=s=>String(s||'').replace(/[&<>"']/g,c=>({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[c]));
function toast(m){const d=document.createElement('div');d.textContent=m;$('toast').appendChild(d);setTimeout(()=>d.remove(),2800)}

/* ===== 저장소 (IndexedDB: 사진이 많아도 용량 걱정 없음) ===== */
function openDB(){return new Promise(res=>{
  try{const r=indexedDB.open('GUL_DARI_SURVEY_V1',1);
    r.onupgradeneeded=()=>r.result.createObjectStore('spots',{keyPath:'id'});
    r.onsuccess=()=>{db=r.result;res(true)};r.onerror=()=>res(false);
  }catch(e){res(false)}})}
const store=m=>db.transaction('spots',m).objectStore('spots');
function dbAll(){return new Promise(res=>{const q=store('readonly').getAll();q.onsuccess=()=>res(q.result||[]);q.onerror=()=>res([])})}
function dbPut(s){if(!db)return;store('readwrite').put(s);flash()}
function dbDel(id){if(!db)return;store('readwrite').delete(id)}
function flash(){const e=$('saveSt');e.innerHTML='<i class="dot"></i>저장됨';setTimeout(()=>e.innerHTML='<i class="dot"></i>자동저장',1500);updUsage()}
async function updUsage(){
  try{const e=await navigator.storage.estimate();$('stTxt').textContent='사용 '+(e.usage/1048576).toFixed(1)+'MB · '+spots.length+'건 저장됨'}
  catch(_){$('stTxt').textContent=spots.length+'건 저장됨'}
}

/* ===== 지도 ===== */
function setTile(k,auto){
  if(!TILES[k])k='google_road';curTile=k;$('tileSel').value=k;tileErr=0;
  if(tile)map.removeLayer(tile);
  const c=TILES[k];
  tile=L.tileLayer(c.u,{maxZoom:c.z,subdomains:'abc',attribution:'© 지도 제공사'}).addTo(map);
  tile.on('tileerror',()=>{
    if(++tileErr===8){const n=ORDER[(ORDER.indexOf(k)+1)%ORDER.length];toast('⚠️ 지도 서버 차단 → '+TILES[n].u.split('/')[2]+' 로 우회합니다');setTile(n,true)}
  });
}
function initMap(){
  if(typeof L==='undefined'){$('map').innerHTML='<div style="padding:40px;font-weight:700">⚠️ 지도 라이브러리(Leaflet)를 불러오지 못했습니다. 네트워크/방화벽을 확인하세요.</div>';return false}
  map=L.map('map',{center:DEF,zoom:16,zoomControl:false,preferCanvas:true});
  L.control.zoom({position:'topright'}).addTo(map);
  layer=L.layerGroup().addTo(map);
  setTile('google_road');
  map.on('click',e=>{if(addMode)createSpot(e.latlng.lat,e.latlng.lng)});
  return true;
}
function pinHtml(s,sel){
  const n=s.photos.length;
  const name=esc(s.jibun)||'(지번 미입력)';
  let lab='';
  if(pinMode==='label')lab=`<div class="plab">${name}</div>`;
  else if(pinMode==='photo')lab=`<div class="plab">${n?`<img class="pthumb" src="${s.photos[0].data}">`:'<div class="pnoimg">사진 없음</div>'}${name}${n>1?` <span style="color:#2563eb">+${n-1}</span>`:''}</div>`;
  return `<div class="pinw ${sel?'sel':''}"><div class="pin" style="background:${COLOR[s.dir]}"><i>${n||''}</i></div>${lab}</div>`;
}
function filtered(){
  const d=$('fDir').value,q=$('fQ').value.trim();
  return spots.filter(s=>(d===''||String(s.dir)===d)&&(!q||(s.jibun||'').includes(q)));
}
function render(){
  const list=filtered();
  if(layer){layer.clearLayers();
    list.forEach(s=>{
      const m=L.marker([s.lat,s.lng],{icon:L.divIcon({className:'leaflet-custom-pin',html:pinHtml(s,s.id===selId),iconSize:null,iconAnchor:[14,34]}),draggable:dragOn&&!addMode});
      m.on('click',e=>{L.DomEvent.stopPropagation(e);openPanel(s.id)});
      m.on('dragend',()=>{const p=m.getLatLng();s.lat=p.lat;s.lng=p.lng;dbPut(s);render();renderTable()});
      layer.addLayer(m);
    });}
  $('cTot').textContent=spots.length;
  [0,1,2].forEach(k=>$('c'+k).textContent=spots.filter(s=>s.dir===k).length);
  renderTable();
}
function renderTable(){
  const list=filtered();
  $('tbody').innerHTML=list.length?list.map((s,i)=>`<tr ondblclick="goSpot('${s.id}')" onclick="goSpot('${s.id}')"><td>${i+1}</td><td class="l">${esc(s.jibun)||'<span style="color:#94a3b8">(미입력)</span>'}</td><td><span class="tag t${s.dir}">${DIRTXT[s.dir]}</span></td><td>${s.photos.length}장</td><td style="font-family:monospace;color:#64748b">${s.lat.toFixed(5)}, ${s.lng.toFixed(5)}</td></tr>`).join('')
   :'<tr><td colspan="5" style="padding:40px;color:#94a3b8">조사된 굴다리가 없습니다. 지도에서 📌 핀을 등록하세요.</td></tr>';
}
function sheet(k){
  $('mapView').style.display=k==='map'?'block':'none';
  $('tableView').style.display=k==='tbl'?'flex':'none';
  $('tabMap').classList.toggle('act',k==='map');$('tabTbl').classList.toggle('act',k==='tbl');
  if(k==='map'&&map)setTimeout(()=>map.invalidateSize(),50);
}
function goSpot(id){sheet('map');setTimeout(()=>{const s=spots.find(x=>x.id===id);if(s){map.setView([s.lat,s.lng],18);openPanel(id,true)}},80)}

/* ===== 핀 등록 / 이동 ===== */
function setMode(m){
  pinMode=m;try{localStorage.setItem('GUL_PINMODE',m)}catch(_){}
  ['icon','label','photo'].forEach(k=>$('m_'+k).classList.toggle('on',k===m));render();
}
function toggleAdd(){
  addMode=!addMode;
  $('btnAdd').classList.toggle('on',addMode);
  $('btnAdd').textContent=addMode?'✖ 등록 취소':'📌 굴다리 핀 등록';
  $('guide').style.display=addMode?'block':'none';
  $('mapView').classList.toggle('mapcur',addMode);
  if(addMode)closePanel();
  render();
}
function toggleDrag(){
  dragOn=!dragOn;const b=$('btnDrag');
  b.textContent=dragOn?'🔓 핀 이동 가능':'🔒 핀 이동 잠금';b.classList.toggle('pri',dragOn);b.classList.toggle('dk',!dragOn);
  render();
}
function createSpot(lat,lng){
  const s={id:'s'+Date.now().toString(36)+Math.random().toString(36).slice(2,5),lat,lng,jibun:'',dir:0,photos:[],created:Date.now()};
  spots.push(s);dbPut(s);toggleAdd();openPanel(s.id);
  setTimeout(()=>$('fJibun').focus(),100);
}

/* ===== 상세 패널 ===== */
function cur(){return spots.find(s=>s.id===selId)}
function openPanel(id,noPan){
  selId=id;const s=cur();if(!s)return;
  $('fJibun').value=s.jibun;paintDir();paintPhotos();
  $('panel').style.display='flex';render();
  if(!noPan&&map){
    const p=map.latLngToContainerPoint([s.lat,s.lng]),sz=map.getSize();
    if(innerWidth>640){const lim=sz.x-430-60;if(p.x>lim)map.panBy([p.x-lim+60,0])}
    else{const lim=sz.y*0.28;if(p.y>lim)map.panBy([0,p.y-lim])}
  }
}
function closePanel(){selId=null;$('panel').style.display='none';render()}
function onField(){
  const s=cur();if(!s)return;s.jibun=$('fJibun').value;
  clearTimeout(saveTimer);saveTimer=setTimeout(()=>{dbPut(s);render()},350);
}
function setDir(v){const s=cur();if(!s)return;s.dir=s.dir===v?0:v;paintDir();dbPut(s);render()}
function paintDir(){const s=cur();$('d1').className=s.dir===1?'a1':'';$('d2').className=s.dir===2?'a2':''}
function delSpot(){
  const s=cur();if(!s)return;
  if(!confirm('이 굴다리 조사 내역(사진 포함)을 삭제할까요?'))return;
  dbDel(s.id);spots=spots.filter(x=>x.id!==s.id);closePanel();updUsage();toast('🗑️ 삭제되었습니다');
}

/* ===== 사진 + 자동 압축 ===== */
function paintPhotos(){
  const s=cur();$('phCnt').textContent=s.photos.length?`(${s.photos.length}장)`:'';
  $('grid').innerHTML=s.photos.map((p,i)=>`<div class="ph"><img src="${p.data}" onclick="zoom(${i})"><button onclick="rmPhoto(${i})">✕</button><span>${p.kb}KB</span></div>`).join('');
}
function zoom(i){$('lbImg').src=cur().photos[i].data;$('lb').style.display='flex'}
function rmPhoto(i){const s=cur();s.photos.splice(i,1);dbPut(s);paintPhotos();render()}
function loadImg(file){return new Promise((res,rej)=>{
  const u=URL.createObjectURL(file),im=new Image();
  im.onload=()=>{URL.revokeObjectURL(u);res(im)};im.onerror=()=>{URL.revokeObjectURL(u);rej()};im.src=u})}
async function compress(file){
  const im=await loadImg(file);
  let scale=Math.min(1,MAX_SIDE/Math.max(im.naturalWidth,im.naturalHeight));
  let q=0.8,out='',kb=0;
  for(let t=0;t<6;t++){
    const c=document.createElement('canvas');
    c.width=Math.round(im.naturalWidth*scale);c.height=Math.round(im.naturalHeight*scale);
    c.getContext('2d').drawImage(im,0,0,c.width,c.height);
    q=0.8;
    do{out=c.toDataURL('image/jpeg',q);kb=Math.round((out.length-23)*0.75/1024);q-=0.1}while(kb>TARGET_KB&&q>0.45);
    if(kb<=TARGET_KB)break;scale*=0.82;
  }
  return {data:out,kb,orig:Math.round(file.size/1024)};
}
async function addFiles(files){
  const s=cur();if(!s)return;
  const arr=[...files].filter(f=>f.type.startsWith('image/'));
  if(!arr.length){toast('이미지 파일만 올릴 수 있습니다');return}
  toast('🗜️ 사진 압축 중...');let o=0,n=0;
  for(const f of arr){
    try{const r=await compress(f);s.photos.push({data:r.data,kb:r.kb});o+=r.orig;n+=r.kb}
    catch(e){toast('⚠️ '+f.name+' 읽기 실패')}
  }
  dbPut(s);paintPhotos();render();
  if(n)toast(`✅ ${arr.length}장 추가 · ${(o/1024).toFixed(1)}MB → ${(n/1024).toFixed(2)}MB (${Math.round((1-n/o)*100)}% 절감)`);
}
const dz=$('drop');
['dragenter','dragover'].forEach(e=>dz.addEventListener(e,ev=>{ev.preventDefault();dz.classList.add('over')}));
['dragleave','drop'].forEach(e=>dz.addEventListener(e,ev=>{ev.preventDefault();dz.classList.remove('over')}));
dz.addEventListener('drop',ev=>addFiles(ev.dataTransfer.files));
document.addEventListener('paste',ev=>{if(!selId)return;const f=[...(ev.clipboardData?.files||[])];if(f.length)addFiles(f)});

/* ===== 백업 / 복원 / CSV ===== */
function dl(name,blob){const a=document.createElement('a');a.href=URL.createObjectURL(blob);a.download=name;a.click();setTimeout(()=>URL.revokeObjectURL(a.href),2000)}
const stamp=()=>new Date().toISOString().slice(0,10);
function exportJSON(){dl(`굴다리조사_백업_${stamp()}.json`,new Blob([JSON.stringify({v:1,spots})],{type:'application/json'}));toast('💾 백업 파일을 내려받았습니다')}
function importJSON(e){
  const f=e.target.files[0];if(!f)return;const r=new FileReader();
  r.onload=()=>{try{
    const d=JSON.parse(r.result);let n=0;
    (d.spots||[]).forEach(s=>{if(!s.id||typeof s.lat!=='number')return;s.photos=s.photos||[];
      const i=spots.findIndex(x=>x.id===s.id);if(i>=0)spots[i]=s;else spots.push(s);dbPut(s);n++});
    render();toast(`📂 ${n}건 복원 완료`);
    if(spots.length&&map)map.setView([spots[0].lat,spots[0].lng],16);
  }catch(_){toast('⚠️ 올바른 백업 파일이 아닙니다')}e.target.value=''};
  r.readAsText(f);
}
function exportCSV(){
  const rows=[['No','지번','통행방향','사진수','위도','경도']];
  filtered().forEach((s,i)=>rows.push([i+1,s.jibun,DIRTXT[s.dir],s.photos.length,s.lat.toFixed(6),s.lng.toFixed(6)]));
  const csv='\ufeff'+rows.map(r=>r.map(v=>'"'+String(v).replace(/"/g,'""')+'"').join(',')).join('\r\n');
  dl(`굴다리조사_관리대장_${stamp()}.csv`,new Blob([csv],{type:'text/csv;charset=utf-8'}));
}

/* ===== 시작 ===== */
(async()=>{
  const ok=await openDB();
  if(!ok)toast('⚠️ 브라우저 저장소를 쓸 수 없습니다. 백업을 자주 해주세요.');
  else spots=(await dbAll()).map(s=>({photos:[],dir:0,jibun:'',...s}));
  const mo=initMap();
  setMode(pinMode);updUsage();
  if(mo&&spots.length)map.setView([spots[0].lat,spots[0].lng],16);
})();
</script>
</body>
</html>
