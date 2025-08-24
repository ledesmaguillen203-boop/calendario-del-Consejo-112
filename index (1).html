<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Calendario Escolar · Centro de Estudiantes</title>
<style>
  :root {
    --bg: #0b1020;
    --card: #0f162d;
    --text: #e8eefc;
    --muted: #a6b3d9;
    --accent: #7aa2ff;
    --accent-2: #18dba9;
    --border: rgba(255,255,255,.08);
    --shadow: 0 6px 24px rgba(0,0,0,.35);
  }
  body{margin:0;font-family:system-ui;-apple-system,Segoe UI,Roboto,Ubuntu,'Helvetica Neue',Arial,'Noto Sans',sans-serif;background:var(--bg);color:var(--text);}
  .wrap{max-width:980px;margin:0 auto;padding:18px;}
  header{position:sticky;top:0;background:linear-gradient(180deg,rgba(11,16,32,.98),rgba(11,16,32,.85));border-bottom:1px solid var(--border);}
  h1{font-size:clamp(22px,3.5vw,32px);}
  .grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(260px,1fr));gap:14px;}
  .card{background:var(--card);border:1px solid var(--border);border-radius:16px;padding:14px 14px 16px;box-shadow:var(--shadow);}
  .pill{display:inline-block;padding:4px 8px;border-radius:999px;border:1px solid var(--border);font-size:12px;margin-right:8px;}
  .pill.acto{background:rgba(122,162,255,.12);}
  .pill.examen{background:rgba(255,107,107,.14);}
  .pill.feriado{background:rgba(24,219,169,.12);}
  .pill.reunion{background:rgba(255,209,102,.12);}
  .pill.taller{background:rgba(170,132,255,.12);}
  .fab{position:fixed;right:18px;bottom:18px;display:flex;flex-direction:column;gap:10px;}
  .fab button{background:var(--accent);color:#0c1225;border:none;padding:12px 14px;border-radius:14px;box-shadow:var(--shadow);font-weight:700;cursor:pointer;}
  /* Modal */
  .modal-bg{display:none;position:fixed;top:0;left:0;width:100%;height:100%;background:rgba(0,0,0,.7);align-items:center;justify-content:center;z-index:1000;}
  .modal{background:var(--card);padding:20px;border-radius:16px;max-width:400px;width:90%;display:flex;flex-direction:column;gap:12px;}
  .modal input,.modal select, .modal textarea{padding:10px;border-radius:12px;border:1px solid var(--border);background:var(--bg);color:var(--text);}
  .modal-buttons{display:flex;gap:10px;justify-content:flex-end;}
</style>
</head>
<body>

<header class="wrap">
  <h1>📅 Calendario Escolar · Centro de Estudiantes</h1>
</header>

<main class="wrap">
  <section>
    <h2>Próximas fechas</h2>
    <div class="grid" id="upcomingGrid"></div>
  </section>
  <section>
    <h2>Todas las fechas</h2>
    <div class="grid" id="allGrid"></div>
  </section>
</main>

<div class="fab">
  <button id="addBtn">➕ Agregar Evento</button>
</div>

<!-- Modal para agregar/editar -->
<div class="modal-bg" id="modalBg">
  <div class="modal">
    <h3 id="modalTitle">Agregar Evento</h3>
    <input type="text" id="eventTitle" placeholder="Título">
    <input type="date" id="eventDate">
    <select id="eventType">
      <option value="acto">Acto</option>
      <option value="examen">Examen</option>
      <option value="feriado">Feriado</option>
      <option value="reunion">Reunión</option>
      <option value="taller">Taller</option>
    </select>
    <textarea id="eventNote" placeholder="Nota (opcional)"></textarea>
    <div class="modal-buttons">
      <button id="saveBtn">Guardar</button>
      <button id="cancelBtn">Cancelar</button>
    </div>
  </div>
</div>

<script>
let EVENTS = JSON.parse(localStorage.getItem('events') || `[
  {"title":"Inicio de clases","date":"2025-03-10","type":"acto","note":"Bienvenida y presentación del Centro"},
  {"title":"Acto Día de la Bandera","date":"2025-06-20","type":"acto","note":"Promesa a la bandera · Primario"},
  {"title":"Semana de Evaluaciones – Matemática","date":"2025-07-07","type":"examen","note":"Turno mañana y tarde"},
  {"title":"Feriado Nacional – Independencia","date":"2025-07-09","type":"feriado","note":"Sin actividad escolar"}
]`);

const $ = s => document.querySelector(s);
const escapeHtml = s => String(s).replace(/[&<>"']/g, m => ({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;','\'':'&#39;'}[m]));
const fmt = d => new Date(d).toLocaleDateString('es-AR',{ weekday:'short', day:'2-digit', month:'short', year:'numeric' });
const empty = msg => `<div class="card" style="grid-column:1 / -1;text-align:center">${msg}</div>`;

function cardEvent(e,i){
  const typeLabel = ({acto:'Acto',examen:'Examen',feriado:'Feriado',reunion:'Reunión',taller:'Taller'})[e.type]||'Evento';
  return `<article class="card">
    <div class="pill ${e.type}">${typeLabel}</div>
    <h3>${escapeHtml(e.title)}</h3>
    <div class="muted date">${fmt(e.date)}</div>
    ${e.note?`<p class="muted" style="margin:.4rem 0 0">${escapeHtml(e.note)}</p>`:''}
    <div style="margin-top:8px; display:flex; gap:8px;">
      <button class="pill acto" onclick="openModal('edit', ${i})">✏️ Editar</button>
      <button class="pill feriado" onclick="deleteEvent(${i})">🗑️ Borrar</button>
    </div>
  </article>`;
}

function render(){
  EVENTS.sort((a,b)=>new Date(a.date)-new Date(b.date));
  localStorage.setItem('events',JSON.stringify(EVENTS));
  const today = new Date(); today.setHours(0,0,0,0);
  $('#upcomingGrid').innerHTML = EVENTS.filter(e => new Date(e.date) >= today).slice(0,8).map(cardEvent).join('') || empty('Sin próximas fechas.');
  $('#allGrid').innerHTML = EVENTS.map(cardEvent).join('') || empty('Sin eventos.');
}

// Borrar evento
function deleteEvent(i){
  if(confirm('¿Seguro que querés borrar este evento?')){ EVENTS.splice(i,1); render(); }
}

// Modal
let currentIndex = null;
function openModal(mode,i=null){
  $('#modalTitle').textContent = mode==='edit'?'Editar Evento':'Agregar Evento';
  $('#modalBg').style.display='flex';
  currentIndex = i;
  if(mode==='edit' && i!==null){
    const e = EVENTS[i];
    $('#eventTitle').value = e.title;
    $('#eventDate').value = e.date;
    $('#eventType').value = e.type;
    $('#eventNote').value = e.note;
  } else {
    $('#eventTitle').value=''; $('#eventDate').value=''; $('#eventType').value='acto'; $('#eventNote').value='';
  }
}

$('#cancelBtn').onclick = ()=> $('#modalBg').style.display='none';

$('#saveBtn').onclick = ()=>{
  const title = $('#eventTitle').value.trim();
  const date = $('#eventDate').value;
  const type = $('#eventType').value;
  const note = $('#eventNote').value.trim();
  if(!title || !/^\d{4}-\d{2}-\d{2}$/.test(date)){ alert('Título y fecha válida obligatorios'); return; }
  const obj = {title,date,type,note};
  if(currentIndex!==null){ EVENTS[currentIndex]=obj; } else { EVENTS.push(obj); }
  currentIndex=null; $('#modalBg').style.display='none'; render();
}

// Botón agregar
$('#addBtn').onclick = ()=> openModal('add');

// Inicial render
render();
</script>
</body>
</html>
