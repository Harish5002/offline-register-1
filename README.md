

<html lang="en">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Mahendra College Symposium — AI&DS Registration</title>
<style>
:root{--bg:#071022;--card:#0b1220;--accent:#06b6d4;--muted:#9fb0c5;--glass:rgba(255,255,255,0.03)}
*{box-sizing:border-box;font-family:Inter,system-ui,Segoe UI,Roboto,Arial}
body{margin:0;background:linear-gradient(180deg,#031021,#071024);color:#e6eef6;padding:24px}
.container{max-width:1100px;margin:0 auto}
.header{display:flex;gap:14px;align-items:center}
.logo{width:56px;height:56px;border-radius:10px;background:linear-gradient(90deg,#052f3b,#063b46);display:flex;align-items:center;justify-content:center;font-weight:700}
h1{margin:0;font-size:20px}
.subtitle{color:var(--muted);font-size:13px}
.grid{display:grid;grid-template-columns:1fr 380px;gap:18px;margin-top:18px}
.card{background:var(--card);padding:14px;border-radius:12px;box-shadow:0 8px 24px rgba(2,6,23,0.6)}
label{display:block;font-size:13px;margin-top:8px;color:#dbeafe}
input[type=text], input[type=email], input[type=tel], select, textarea{width:100%;padding:8px;border-radius:8px;border:1px solid rgba(255,255,255,0.03);background:transparent;color:inherit}
.small{font-size:12px;color:var(--muted)}
.events-list{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-top:8px}
.event-box{background:rgba(255,255,255,0.02);padding:10px;border-radius:10px;display:flex;gap:10px;align-items:center}
.btn{background:var(--accent);border:none;padding:8px 12px;border-radius:8px;color:#042026;cursor:pointer;font-weight:600}
.btn-ghost{background:transparent;border:1px solid rgba(255,255,255,0.05);color:var(--muted);padding:8px 10px;border-radius:8px;cursor:pointer}
.member-row{display:flex;gap:8px;align-items:center;margin-top:8px;flex-wrap:wrap}
.member-row input{flex:1;min-width:120px}
.actions{display:flex;gap:8px;margin-top:12px;flex-wrap:wrap}
.table{width:100%;border-collapse:collapse;margin-top:8px}
.table th,.table td{padding:8px;border-bottom:1px solid rgba(255,255,255,0.03);font-size:13px;text-align:left}
.tag{padding:6px 8px;border-radius:999px;background:rgba(255,255,255,0.03);font-size:12px}
.small-muted{font-size:12px;color:var(--muted)}
.mailto-list{max-height:220px;overflow:auto;margin-top:8px;padding:8px;background:rgba(0,0,0,0.14);border-radius:8px}
.config input{width:70px}
.footer{margin-top:14px;color:var(--muted);font-size:13px}
</style>
</head>
<body>
<div class="container">
  <div class="header">
    <div class="logo">MC</div>
    <div>
      <h1>Mahendra College Symposium — AI&DS Registration Portal</h1>
      <div class="subtitle">Technical & Non-technical events + Workshop. Save to CSV (Excel), create email confirmations.</div>
    </div>
  </div>

  <div class="grid">
    <main>
      <div class="card">
        <h3 style="margin-top:0">Register Team / Participant</h3>
        <div class="small-muted">Fill participant details and the event(s) they are joining. You can add multiple members to a team.</div>

        <label>Team / Group Name (optional)</label>
        <input id="teamName" type="text" placeholder="Example: Team Alpha">

        <label>Main Contact Name</label>
        <input id="contactName" type="text" placeholder="Full name (main contact)">

        <div style="display:flex;gap:8px;margin-top:8px">
          <div style="flex:1">
            <label>Contact Email</label>
            <input id="contactEmail" type="email" placeholder="email@example.com">
          </div>
          <div style="width:160px">
            <label>Contact Phone</label>
            <input id="contactPhone" type="tel" placeholder="9876543210">
          </div>
        </div>

        <div style="display:flex;gap:8px;margin-top:8px">
          <div style="flex:1">
            <label>College</label>
            <input id="contactCollege" type="text" placeholder="Mahendra College of Engineering">
          </div>
          <div style="width:180px">
            <label>Department</label>
            <input id="contactDept" type="text" placeholder="AI&DS">
          </div>
          <div style="width:120px">
            <label>Year</label>
            <input id="contactYear" type="text" placeholder="III Year">
          </div>
        </div>

        <label style="margin-top:12px">Choose Event(s)</label>
        <div class="events-list" id="eventsList"></div>
        <div class="small-muted" style="margin-top:8px">Event team sizes configurable in right panel. Selected events must satisfy team size when registering.</div>

        <div style="margin-top:10px;display:flex;align-items:center;justify-content:space-between">
          <label style="margin:0">Members</label>
          <button id="addMemberBtn" class="btn-ghost">+ Add member</button>
        </div>
        <div id="membersContainer" style="margin-top:8px"></div>

        <div class="actions">
          <button id="registerBtn" class="btn">Register</button>
          <button id="clearFormBtn" class="btn-ghost">Clear</button>
          <button id="downloadCsvBtn" class="btn-ghost">Download CSV (all)</button>
        </div>

        <div id="messageBox" style="margin-top:10px"></div>
      </div>

      <div class="card" style="margin-top:12px">
        <h3 style="margin-top:0">Registrations</h3>
        <div class="small-muted">Saved in browser storage. You can export per-event, view or generate confirmation emails.</div>

        <div style="margin-top:8px">
          <label>Filter by event</label>
          <select id="filterEvent"><option value="">-- All events --</option></select>
        </div>

        <div style="margin-top:8px;overflow:auto;max-height:260px">
          <table class="table" id="regsTable"><thead><tr><th>Team</th><th>Contact</th><th>Events</th><th>Members</th><th></th></tr></thead><tbody></tbody></table>
        </div>

        <div class="actions" style="margin-top:8px">
          <button id="exportFiltered" class="btn">Export filtered CSV</button>
          <button id="sendEmailsForFiltered" class="btn">Prepare confirmation emails</button>
          <button id="clearAll" class="btn-ghost">Clear all registrations</button>
        </div>

        <div id="mailtoBox" style="margin-top:10px"></div>
      </div>
    </main>

    <aside>
      <div class="card">
        <h3 style="margin-top:0">Event Configuration (Admin)</h3>
        <div class="small-muted">Set min/max members per event. Defaults are prefilled.</div>
        <div class="config" id="configArea" style="margin-top:8px"></div>
        <div style="margin-top:10px"><button id="saveConfig" class="btn">Save Config</button></div>
      </div>

      <div class="card" style="margin-top:12px">
        <h3 style="margin-top:0">How to use</h3>
        <ol class="small-muted">
          <li>Fill contact & member details (college/department/year for each).</li>
          <li>Choose events and click Register. The portal validates team size rules.</li>
          <li>Use Export to download CSV for Excel. Use Prepare confirmation emails to open drafts in email client.</li>
          <li>To send automatic emails & centrally save Excel on server, add a Node.js backend — instructions below.</li>
        </ol>
      </div>

      <div class="card" style="margin-top:12px">
        <h3 style="margin-top:0">Notes</h3>
        <p class="small-muted">This single-file is client-side. Browser cannot send email automatically — it can create email drafts. For automatic sending install the server (Node.js) provided in instructions below.</p>
      </div>
    </aside>
  </div>

  <div class="footer">Built for <strong>Mahendra College of Engineering — AI&DS</strong>. CSV is Excel-compatible.</div>
</div>

<script>
/* ------------- EVENTS & DEFAULT RULES ------------- */
const defaultEvents = [
  {id:'TALKTREK', title:'TALKTREK', min:1, max:3},
  {id:'PATCHUP', title:'PATCHUP', min:2, max:4},
  {id:'QBIT', title:'QBIT', min:1, max:3},
  {id:'HOTZONEX', title:'HOTZONEX', min:1, max:2},
  {id:'CINEBLAST', title:'CINEBLAST', min:3, max:6},
  {id:'WORKSHOP', title:'Bringing Drawings to Life with AI (Workshop)', min:1, max:1}
];

function loadConfig(){
  const raw = localStorage.getItem('mc_events_config');
  if(!raw) return JSON.parse(JSON.stringify(defaultEvents));
  try{ return JSON.parse(raw); }catch(e){ return JSON.parse(JSON.stringify(defaultEvents)); }
}
let events = loadConfig();

/* ------------- UI RENDER ------------- */
const eventsList = document.getElementById('eventsList');
const filterEvent = document.getElementById('filterEvent');
const configArea = document.getElementById('configArea');

function renderEventsUI(){
  eventsList.innerHTML=''; filterEvent.innerHTML='<option value="">-- All events --</option>';
  events.forEach(ev=>{
    const box = document.createElement('label'); box.className='event-box';
    box.innerHTML = `<input type='checkbox' data-id='${ev.id}' class='evchk' /> <div style='flex:1'><strong style='font-size:14px'>${ev.title}</strong><div class='small-muted' style='font-size:12px'>Team size: ${ev.min} to ${ev.max}</div></div>`;
    eventsList.appendChild(box);
    const opt = document.createElement('option'); opt.value = ev.id; opt.textContent = ev.title; filterEvent.appendChild(opt);
  });
}
function renderConfig(){
  configArea.innerHTML='';
  events.forEach((ev,idx)=>{
    const div = document.createElement('div'); div.style.marginBottom='10px';
    div.innerHTML = `<div style='font-weight:600'>${ev.title}</div>
      <div class='small-muted' style='margin-bottom:6px'>Min / Max members</div>
      <div style='display:flex;gap:6px;align-items:center'>
        <input data-idx='${idx}' class='cfg-min' value='${ev.min}' />
        <input data-idx='${idx}' class='cfg-max' value='${ev.max}' />
        <div class='small-muted' style='margin-left:8px'>(event)</div>
      </div>`;
    configArea.appendChild(div);
  });
}
renderEventsUI(); renderConfig();

/* ------------- MEMBERS UI ------------- */
const membersContainer = document.getElementById('membersContainer');
function addMemberRow(data){
  const id = 'm_'+Date.now()+Math.floor(Math.random()*999);
  const div = document.createElement('div'); div.className='member-row'; div.dataset.id=id;
  div.innerHTML = `
    <input placeholder='Member full name' class='m-name' />
    <input placeholder='email@example.com' class='m-email' />
    <input placeholder='phone' class='m-phone' style='width:120px' />
    <input placeholder='college' class='m-college' style='width:180px' />
    <input placeholder='department' class='m-dept' style='width:140px' />
    <input placeholder='year' class='m-year' style='width:90px' />
    <button class='btn-ghost remove' style='padding:6px'>Remove</button>
  `;
  if(data){
    div.querySelector('.m-name').value = data.name||'';
    div.querySelector('.m-email').value = data.email||'';
    div.querySelector('.m-phone').value = data.phone||'';
    div.querySelector('.m-college').value = data.college||'';
    div.querySelector('.m-dept').value = data.dept||'';
    div.querySelector('.m-year').value = data.year||'';
  }
  membersContainer.appendChild(div);
  div.querySelector('.remove').addEventListener('click', ()=>div.remove());
}
addMemberRow();
document.getElementById('addMemberBtn').addEventListener('click', (e)=>{ e.preventDefault(); addMemberRow(); });

/* ------------- REGISTRATIONS storage ------------- */
function loadRegs(){ try{ return JSON.parse(localStorage.getItem('mc_regs')||'[]'); }catch(e){return[];} }
function saveRegs(arr){ localStorage.setItem('mc_regs', JSON.stringify(arr)); }
let registrations = loadRegs();

function renderRegsTable(filter=''){
  const tbody = document.querySelector('#regsTable tbody'); tbody.innerHTML='';
  registrations.filter(r=>!filter || r.events.includes(filter)).forEach((r,idx)=>{
    const tr = document.createElement('tr');
    const evs = r.events.map(eid=>events.find(e=>e.id===eid)?.title||eid).join(', ');
    tr.innerHTML = `<td>${r.teamName||'-'}</td>
      <td>${r.contactName}<br/><span class='small-muted'>${r.contactEmail}</span></td>
      <td>${evs}</td>
      <td>${r.members.length}</td>
      <td><button data-idx='${idx}' class='btn-ghost view'>View</button> <button data-idx='${idx}' class='btn-ghost delete'>Delete</button></td>`;
    tbody.appendChild(tr);
  });
  document.querySelectorAll('.view').forEach(b=>{ b.addEventListener('click', ()=>{ openRegistrationModal(registrations[b.dataset.idx]); }); });
  document.querySelectorAll('.delete').forEach(b=>{ b.addEventListener('click', ()=>{ if(confirm('Delete this registration?')){ registrations.splice(b.dataset.idx,1); saveRegs(registrations); renderRegsTable(filterEvent.value); showMessage('Deleted',''); } }); });
}
renderRegsTable();

/* ------------- UTILS ------------- */
function showMessage(msg, type=''){ const box=document.getElementById('messageBox'); box.innerHTML=`<div class='tag'>${msg}</div>`; setTimeout(()=>box.innerHTML='',3500); }

function escapeCsv(v){ if(v==null) return ''; return '"'+String(v).replace(/"/g,'""')+'"'; }
function registrationsToCSV(rows){
  const cols=['TeamName','ContactName','ContactEmail','ContactPhone','ContactCollege','ContactDept','ContactYear','Events','MemberCount','Members'];
  const lines=[cols.join(',')];
  rows.forEach(r=>{
    const evs=r.events.join(';');
    const mems=r.members.map(m=>`${m.name} <${m.email}> (${m.phone}) [${m.college} - ${m.dept} - ${m.year}]`).join(' | ');
    const line=[escapeCsv(r.teamName||''),escapeCsv(r.contactName),escapeCsv(r.contactEmail),escapeCsv(r.contactPhone),escapeCsv(r.contactCollege),escapeCsv(r.contactDept),escapeCsv(r.contactYear),escapeCsv(evs),r.members.length,escapeCsv(mems)];
    lines.push(line.join(','));
  });
  return lines.join('\n');
}
function downloadText(filename,text){ const blob=new Blob([text],{type:'text/csv;charset=utf-8;'}); const url=URL.createObjectURL(blob); const a=document.createElement('a'); a.href=url; a.download=filename; document.body.appendChild(a); a.click(); a.remove(); URL.revokeObjectURL(url); }

/* ------------- REGISTER button logic ------------- */
document.getElementById('registerBtn').addEventListener('click', async ()=>{
  const teamName=document.getElementById('teamName').value.trim();
  const contactName=document.getElementById('contactName').value.trim();
  const contactEmail=document.getElementById('contactEmail').value.trim();
  const contactPhone=document.getElementById('contactPhone').value.trim();
  const contactCollege=document.getElementById('contactCollege').value.trim();
  const contactDept=document.getElementById('contactDept').value.trim();
  const contactYear=document.getElementById('contactYear').value.trim();
  const checked=Array.from(document.querySelectorAll('.evchk:checked')).map(i=>i.dataset.id);
  if(!contactName||!contactEmail) return alert('Please fill contact name and email');
  if(checked.length===0) return alert('Please choose at least one event');
  const memberElems=Array.from(document.querySelectorAll('.member-row'));
  const members=memberElems.map(m=>({
    name:m.querySelector('.m-name').value.trim(),
    email:m.querySelector('.m-email').value.trim(),
    phone:m.querySelector('.m-phone').value.trim(),
    college:m.querySelector('.m-college').value.trim(),
    dept:m.querySelector('.m-dept').value.trim(),
    year:m.querySelector('.m-year').value.trim()
  })).filter(x=>x.name);
  if(members.length===0) return alert('Please add at least one member with a name');

  // validate team sizes for each chosen event
  for(const eid of checked){
    const ev=events.find(e=>e.id===eid);
    if(!ev) continue;
    if(members.length < ev.min || members.length > ev.max){
      return alert(`Event "${ev.title}" requires ${ev.min} to ${ev.max} members. Current members: ${members.length}`);
    }
  }

  const reg={teamName,contactName,contactEmail,contactPhone,contactCollege,contactDept,contactYear,events:checked,members,createdAt:new Date().toISOString()};
  registrations.push(reg); saveRegs(registrations); renderRegsTable(filterEvent.value); showMessage('Registered successfully','success');
  // auto-generate mailto if no backend (client side)
  prepareSingleMailto(reg);
  // Optional: send to backend server for automatic email & central Excel (uncomment and set URL if you have server)
  // try{ await fetch('http://localhost:3000/register',{method:'POST',headers:{'Content-Type':'application/json'},body:JSON.stringify(reg)}); }catch(e){ console.warn('Backend not available',e); }
  clearForm(false);
});

/* ------------- other UI actions ------------- */
document.getElementById('clearFormBtn').addEventListener('click',()=>clearForm(true));
function clearForm(full=true){
  document.getElementById('teamName').value=''; document.getElementById('contactName').value='';
  document.getElementById('contactEmail').value=''; document.getElementById('contactPhone').value='';
  document.getElementById('contactCollege').value=''; document.getElementById('contactDept').value=''; document.getElementById('contactYear').value='';
  document.querySelectorAll('.evchk').forEach(c=>c.checked=false);
  membersContainer.innerHTML=''; addMemberRow();
  if(full) showMessage('Form cleared');
}

document.getElementById('downloadCsvBtn').addEventListener('click',()=>{
  if(registrations.length===0) return alert('No registrations to download');
  downloadText('registrations_all.csv', registrationsToCSV(registrations));
});
document.getElementById('exportFiltered').addEventListener('click', ()=>{
  const f=filterEvent.value; const rows=f? registrations.filter(r=>r.events.includes(f)) : registrations;
  if(rows.length===0) return alert('No registrations for this filter');
  downloadText((f||'registrations_all')+'.csv', registrationsToCSV(rows));
});

document.getElementById('filterEvent').addEventListener('change', ()=>renderRegsTable(filterEvent.value));

document.getElementById('clearAll').addEventListener('click', ()=>{ if(confirm('Clear all registrations from this browser?')){ registrations=[]; saveRegs(registrations); renderRegsTable(); showMessage('All cleared',''); } });

document.getElementById('saveConfig').addEventListener('click', ()=>{
  const mins=document.querySelectorAll('.cfg-min'), maxs=document.querySelectorAll('.cfg-max');
  mins.forEach(mi=>{ events[mi.dataset.idx].min = Math.max(1, parseInt(mi.value)||1); });
  maxs.forEach(ma=>{ events[ma.dataset.idx].max = Math.max(1, parseInt(ma.value)||1); });
  localStorage.setItem('mc_events_config', JSON.stringify(events));
  renderEventsUI(); renderConfig(); showMessage('Configuration saved');
});

/* ------------- mailto generation ------------- */
function prepareMailtoList(filter=''){
  const rows = filter? registrations.filter(r=>r.events.includes(filter)) : registrations;
  const box=document.getElementById('mailtoBox'); box.innerHTML='';
  if(rows.length===0){ box.innerHTML='<div class="small-muted">No registrations for this filter</div>'; return; }
  const wrapper=document.createElement('div'); wrapper.innerHTML=`<div class='small-muted'>Click Compose to open an email draft per registration (automatic sending requires backend SMTP).</div>`;
  const list=document.createElement('div'); list.className='mailto-list';
  rows.forEach((r,idx)=>{
    const evs = r.events.map(eid=>events.find(e=>e.id===eid)?.title||eid).join(', ');
    const subject = encodeURIComponent(`Mahendra College Symposium — Registration confirmation`);
    const body = encodeURIComponent(`Hello ${r.contactName},\n\nThank you for registering for Mahendra College Symposium 2025.\n\nTeam: ${r.teamName||'--'}\nCollege: ${r.contactCollege}\nDepartment: ${r.contactDept}\nYear: ${r.contactYear}\nEvents: ${evs}\n\nMembers:\n${r.members.map(m=>`- ${m.name} (${m.college}, ${m.dept}, ${m.year}) <${m.email}>`).join('\n')}\n\nRegards,\nDepartment of AI&DS\nMahendra College of Engineering`);
    const to = encodeURIComponent(r.contactEmail||'');
    const mailto = `mailto:${to}?subject=${subject}&body=${body}`;
    const item=document.createElement('div'); item.style.display='flex'; item.style.justifyContent='space-between'; item.style.alignItems='center'; item.style.gap='8px'; item.style.padding='6px 0';
    item.innerHTML = `<div><strong>${r.contactName}</strong> <span class='small-muted'>(${r.contactEmail})</span><div class='small-muted'>${evs} — ${r.members.length} members</div></div><div style='display:flex;gap:8px'><a class='btn-ghost' href='${mailto}' target='_blank'>Compose</a><button class='btn' data-idx='${idx}'>Download CSV</button></div>`;
    list.appendChild(item);
  });
  wrapper.appendChild(list); box.appendChild(wrapper);
}
document.getElementById('sendEmailsForFiltered').addEventListener('click', ()=>prepareMailtoList(filterEvent.value));
document.getElementById('mailtoBox').addEventListener('click',(e)=>{ if(e.target.matches('button')){ const idx=e.target.dataset.idx; const rows = filterEvent.value? registrations.filter(r=>r.events.includes(filterEvent.value)) : registrations; const r=rows[idx]; if(r) downloadText((r.teamName||'reg')+'.csv', registrationsToCSV([r])); }});

/* ------------- helper for single registration mailto after register ------------- */
function prepareSingleMailto(reg){
  const evs = reg.events.map(eid=>events.find(e=>e.id===eid)?.title||eid).join(', ');
  const subject = encodeURIComponent(`Mahendra College Symposium — Registration confirmation`);
  const body = encodeURIComponent(`Hello ${reg.contactName},\n\nThank you for registering for Mahendra College Symposium 2025.\n\nTeam: ${reg.teamName||'--'}\nCollege: ${reg.contactCollege}\nDepartment: ${reg.contactDept}\nYear: ${reg.contactYear}\nEvents: ${evs}\n\nMembers:\n${reg.members.map(m=>`- ${m.name} (${m.college}, ${m.dept}, ${m.year}) <${m.email}>`).join('\n')}\n\nRegards,\nDepartment of AI&DS\nMahendra College of Engineering`);
  // open draft automatically (uncomment if you want auto open)
  // window.open(`mailto:${encodeURIComponent(reg.contactEmail)}?subject=${subject}&body=${body}`);
}

/* ------------- modal / view ------------- */
function openRegistrationModal(reg){
  alert(`Team: ${reg.teamName||'-'}\nContact: ${reg.contactName} (${reg.contactEmail})\nCollege: ${reg.contactCollege}\nDepartment: ${reg.contactDept}\nYear: ${reg.contactYear}\nEvents: ${reg.events.map(e=>events.find(x=>x.id===e)?.title||e).join(', ')}\n\nMembers:\n${reg.members.map(m=>`- ${m.name} | ${m.email} | ${m.college} | ${m.dept} | ${m.year}`).join('\n')}`);
}

/* ------------- initial render ------------- */
renderRegsTable();
document.getElementById('mailtoBox').innerHTML = '<div class="small-muted">No email drafts prepared yet.</div>';

/* ------------- persist config change from other tabs ------------- */
window.addEventListener('storage', ()=>{ events = loadConfig(); renderEventsUI(); renderConfig(); });

</script>
</body>
</html>
