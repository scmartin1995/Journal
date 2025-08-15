<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1, user-scalable=no" />
  <title>Offline Audio Journal</title>
  <meta name="theme-color" content="#0a84ff" />
  <!-- Minimal icons as data URIs so this is truly single-file (replace with your own later for better quality) -->
  <link rel="icon" href="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAoAAAAKCAYAAACNMs+9AAAAHklEQVQoU2NkYGD4z0AEMHGqQAwjGAgGg0EwGgAAAJ5wC2aT3OQWAAAAAElFTkSuQmCC">
  <link rel="apple-touch-icon" href="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAMgAAADICAYAAACtWK6eAAAAGklEQVR4nO3BMQEAAADCoPdPbQ43oAAAAAAAAO4CwQAAAZ1A7+UAAAAASUVORK5CYII=">
  <style>
    :root{--bg:#0b0c10;--card:#12141a;--ink:#e8eef9;--muted:#94a3b8;--brand:#0a84ff;--accent:#1e293b;--danger:#ef4444;--ok:#10b981}
    *{box-sizing:border-box}
    html,body{margin:0;height:100%;background:var(--bg);color:var(--ink);font-family:system-ui,-apple-system,Segoe UI,Roboto,Helvetica,Arial,"Apple Color Emoji","Segoe UI Emoji";}
    button,input,select,textarea{font-family:inherit}
    a{color:var(--brand)}
    .app{max-width:720px;margin:0 auto;padding:16px 16px 96px}
    header{display:flex;align-items:center;justify-content:space-between;gap:12px;position:sticky;top:0;background:linear-gradient(180deg,var(--bg),rgba(11,12,16,.6) 70%,rgba(11,12,16,0));backdrop-filter:saturate(140%) blur(16px);padding:12px 4px;z-index:10}
    .title{font-weight:700;letter-spacing:.2px}
    .pill{padding:6px 10px;border-radius:999px;background:var(--accent);color:var(--ink);border:1px solid #1f2937}
    .toolbar{display:flex;gap:8px;align-items:center}
    .card{background:var(--card);border:1px solid #202532;box-shadow:0 10px 30px rgba(0,0,0,.25);border-radius:18px;padding:14px}
    .record-wrap{position:fixed;left:0;right:0;bottom:0;background:linear-gradient(180deg,rgba(11,12,16,0),var(--bg) 18%);padding:12px 16px 24px}
    .record{display:flex;gap:12px;align-items:center;justify-content:center}
    .recbtn{appearance:none;-webkit-appearance:none;border:none;background:var(--brand);color:white;width:92px;height:92px;border-radius:999px;box-shadow:0 10px 30px rgba(10,132,255,.35);font-weight:700;font-size:16px}
    .recbtn.rec{animation:pulse 1.2s infinite}
    @keyframes pulse{0%{box-shadow:0 0 0 0 rgba(10,132,255,.7)}70%{box-shadow:0 0 0 16px rgba(10,132,255,0)}100%{box-shadow:0 0 0 0 rgba(10,132,255,0)}}
    .timer{font-variant-numeric:tabular-nums;color:var(--muted)}
    .entry{display:grid;grid-template-columns:1fr;gap:8px}
    .row{display:flex;gap:8px;align-items:center}
    .grow{flex:1}
    .audio{width:100%}
    .chip{font-size:12px;color:var(--muted)}
    .list{display:flex;flex-direction:column;gap:12px;margin-top:12px}
    .searchbar{display:grid;grid-template-columns:1fr 1fr;gap:8px;margin:8px 0}
    .searchbar input, .pin input{width:100%;padding:10px 12px;border-radius:12px;border:1px solid #223047;background:#0f1320;color:var(--ink)}
    .muted{color:var(--muted)}
    .btn{padding:8px 12px;border:1px solid #253045;background:#0f1725;color:var(--ink);border-radius:12px}
    .btn.primary{background:var(--brand);border-color:transparent;color:#fff}
    .btn.danger{background:#2a1215;border-color:#3b1519;color:#fecaca}
    .pin-overlay{position:fixed;inset:0;background:radial-gradient(1200px 600px at 50% -10%,#0f172a,#0b0c10);display:grid;place-items:center;padding:28px;z-index:50}
    .pin{width:min(520px,100%);}
    .pin h1{margin:0 0 4px}
    .grid{display:grid;gap:8px}
    .pin .row{justify-content:space-between}
    textarea.transcript{width:100%;min-height:90px;padding:10px 12px;border-radius:12px;border:1px solid #223047;background:#0f1320;color:var(--ink);resize:vertical}
    .small{font-size:12px}
    .empty{padding:24px;text-align:center;color:var(--muted)}
  </style>
</head>
<body>
  <div id="pin-gate" class="pin-overlay" hidden>
    <div class="pin card">
      <h1>🔒 Audio Journal</h1>
      <p class="muted" id="pin-mode-help">Set a 4–8 digit PIN to secure your journal.</p>
      <div class="grid">
        <input id="pin-input" inputmode="numeric" autocomplete="one-time-code" maxlength="8" minlength="4" placeholder="Enter PIN" />
        <div class="row">
          <button id="pin-submit" class="btn primary">Continue</button>
          <button id="pin-reset" class="btn" title="Reset saved PIN">Reset PIN</button>
        </div>
        <p class="small muted" id="pin-msg"></p>
      </div>
    </div>
  </div>

  <div class="app">
    <header>
      <div class="title">🎙️ Offline Audio Journal</div>
      <div class="toolbar">
        <button id="export-btn" class="btn">Export ZIP</button>
        <button id="install-btn" class="btn" hidden>Install</button>
      </div>
    </header>

    <section class="card">
      <div class="record">
        <button id="record-btn" class="recbtn">Record</button>
        <div class="timer" id="timer">00:00</div>
      </div>
      <div class="searchbar">
        <input id="q" placeholder="Search transcript…" />
        <input id="date" type="date" />
      </div>
      <div class="row">
        <button id="clear-filters" class="btn">Clear filters</button>
      </div>
    </section>

    <section class="list" id="entries"></section>
    <div class="empty" id="empty-msg">No entries yet. Tap <b>Record</b> to begin.</div>
  </div>

  <!-- Service worker source (registered from this inline blob) -->
  <script id="sw-src" type="text/plain">
    const CACHE_NAME = 'audio-journal-v1';
    const ASSETS = [
      '/',
      location.href.split('#')[0],
    ];
    self.addEventListener('install', e=>{
      e.waitUntil(caches.open(CACHE_NAME).then(c=>c.addAll(ASSETS)).then(()=>self.skipWaiting()));
    });
    self.addEventListener('activate', e=>{
      e.waitUntil(caches.keys().then(keys=>Promise.all(keys.map(k=>k===CACHE_NAME?null:caches.delete(k)))));
      self.clients.claim();
    });
    self.addEventListener('fetch', e=>{
      const req = e.request;
      if(req.method!=='GET') return;
      e.respondWith(
        caches.match(req).then(r=> r || fetch(req).then(resp=>{
          const copy = resp.clone();
          caches.open(CACHE_NAME).then(c=>{ if(req.url.startsWith(self.location.origin)) c.put(req, copy); });
          return resp;
        }).catch(()=>caches.match('/')))
      );
    });
  </script>

  <script>
  // ======= Inject a web app manifest from this single file =======
  (function addManifest(){
    const icon192 = 'data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAMAAAADACAYAAABb0P0qAAAAGklEQVR4nO3BMQEAAADCoPdPbQ43oAAAAAAAAO4CwQAAAZ1A7+UAAAAASUVORK5CYII=';
    const icon512 = 'data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAQAAAAEACAYAAABccqhmAAAAGklEQVR4nO3BMQEAAADCoPdPbQ43oAAAAAAAAO4CwQAAAZ1A7+UAAAAASUVORK5CYII=';
    const manifest = {
      name: 'Offline Audio Journal',
      short_name: 'Journal',
      start_url: './index.html',
      display: 'standalone',
      background_color: '#0b0c10',
      theme_color: '#0a84ff',
      icons: [
        { src: icon192, sizes: '192x192', type: 'image/png' },
        { src: icon512, sizes: '512x512', type: 'image/png' }
      ]
    };
    const blob = new Blob([JSON.stringify(manifest)], {type:'application/manifest+json'});
    const url = URL.createObjectURL(blob);
    const link = document.createElement('link');
    link.rel = 'manifest'; link.href = url; document.head.appendChild(link);
    // clean up on unload
    window.addEventListener('unload', ()=>URL.revokeObjectURL(url));
  })();

  // =============== Utility: IndexedDB helper ===================
  const DB = (()=>{
    const name='audio_journal_db';
    const version=1;
    let db;
    function open(){
      if(db) return Promise.resolve(db);
      return new Promise((res,rej)=>{
        const req=indexedDB.open(name,version);
        req.onupgradeneeded = e=>{
          const d=e.target.result;
          if(!d.objectStoreNames.contains('entries')){
            const s=d.createObjectStore('entries',{keyPath:'id',autoIncrement:true});
            s.createIndex('by_time','timestamp');
          }
          if(!d.objectStoreNames.contains('settings')){
            d.createObjectStore('settings');
          }
        };
        req.onsuccess = ()=>{db=req.result;res(db)};
        req.onerror = ()=>rej(req.error);
      });
    }
    function tx(store,mode='readonly'){return open().then(d=>d.transaction(store,mode).objectStore(store));}
    return {
      async getSetting(k){const s=await tx('settings'); return new Promise((res,rej)=>{const r=s.get(k); r.onsuccess=()=>res(r.result); r.onerror=()=>rej(r.error);});},
      async setSetting(k,v){const s=await tx('settings','readwrite'); return new Promise((res,rej)=>{const r=s.put(v,k); r.onsuccess=()=>res(); r.onerror=()=>rej(r.error);});},
      async addEntry(e){const s=await tx('entries','readwrite'); return new Promise((res,rej)=>{const r=s.add(e); r.onsuccess=()=>res(r.result); r.onerror=()=>rej(r.error);});},
      async updateEntry(e){const s=await tx('entries','readwrite'); return new Promise((res,rej)=>{const r=s.put(e); r.onsuccess=()=>res(); r.onerror=()=>rej(r.error);});},
      async delEntry(id){const s=await tx('entries','readwrite'); return new Promise((res,rej)=>{const r=s.delete(id); r.onsuccess=()=>res(); r.onerror=()=>rej(r.error);});},
      async listEntries(){const s=await tx('entries'); return new Promise((res,rej)=>{const r=s.index('by_time').getAll(); r.onsuccess=()=>res(r.result.sort((a,b)=>b.timestamp-a.timestamp)); r.onerror=()=>rej(r.error);});},
    };
  })();

  // =============== Utility: Crypto (PIN hashing) ===================
  async function hashPIN(pin){
    const enc=new TextEncoder();
    const data=enc.encode(pin);
    const digest=await crypto.subtle.digest('SHA-256',data);
    return Array.from(new Uint8Array(digest)).map(b=>b.toString(16).padStart(2,'0')).join('');
  }

  // =============== WAV Recorder (16-bit PCM) =====================
  function createWavEncoder(sampleRate){
    let buffers=[]; let length=0;
    function write(input){ // input: Float32Array
      const pcm = new Int16Array(input.length);
      for(let i=0;i<input.length;i++){
        let s = Math.max(-1, Math.min(1, input[i]));
        pcm[i] = s<0 ? s*0x8000 : s*0x7FFF;
      }
      buffers.push(pcm);
      length += pcm.length;
    }
    function encodeWAV(){
      const headerSize=44;
      const dataSize=length*2; // 16-bit mono
      const total=headerSize+dataSize;
      const buf=new ArrayBuffer(total);
      const view=new DataView(buf);
      function setStr(o,str){for(let i=0;i<str.length;i++) view.setUint8(o+i,str.charCodeAt(i));}
      setStr(0,'RIFF');
      view.setUint32(4,36+dataSize,true);
      setStr(8,'WAVE');
      setStr(12,'fmt ');
      view.setUint32(16,16,true);
      view.setUint16(20,1,true);
      view.setUint16(22,1,true);
      view.setUint32(24,sampleRate,true);
      view.setUint32(28,sampleRate*2,true);
      view.setUint16(32,2,true);
      view.setUint16(34,16,true);
      setStr(36,'data');
      view.setUint32(40,dataSize,true);
      let off=44;
      for(const pcm of buffers){
        for(let i=0;i<pcm.length;i++,off+=2){ view.setInt16(off, pcm[i], true); }
      }
      return new Blob([view],{type:'audio/wav'});
    }
    return {write,encodeWAV};
  }

  // =============== Simple ZIP (store only) =======================
  function ZipWriter(){
    const files=[]; // {name, data(Uint8Array), crc, size, offset, header}
    let offset=0;
    function crc32(u8){ let c=~0>>>0; for(let i=0;i<u8.length;i++){ c ^= u8[i]; for(let k=0;k<8;k++) c = (c&1)?(0xEDB88320 ^ (c>>>1)):(c>>>1);} return (~c)>>>0; }
    async function add(name, blob){ const u8 = blob instanceof Uint8Array ? blob : new Uint8Array(await blob.arrayBuffer()); const size=u8.length; const crc=crc32(u8); const header = new Uint8Array(30 + name.length); const v = new DataView(header.buffer); v.setUint32(0,0x04034b50,true); v.setUint16(4,20,true); v.setUint16(6,0,true); v.setUint16(8,0,true); v.setUint16(10,0,true); v.setUint16(12,0,true); v.setUint32(14,crc,true); v.setUint32(18,size,true); v.setUint32(22,size,true); v.setUint16(26,name.length,true); v.setUint16(28,0,true); for(let i=0;i<name.length;i++) header[30+i]=name.charCodeAt(i); files.push({name,u8,crc,size,offset,header}); offset += header.length + size; }
    function build(){ const cdParts=[]; let cdSize=0; for(const f of files){ const cdh = new Uint8Array(46 + f.name.length); const v = new DataView(cdh.buffer); v.setUint32(0,0x02014b50,true); v.setUint16(4,20,true); v.setUint16(6,20,true); v.setUint16(8,0,true); v.setUint16(10,0,true); v.setUint16(12,0,true); v.setUint16(14,0,true); v.setUint32(16,f.crc,true); v.setUint32(20,f.size,true); v.setUint32(24,f.size,true); v.setUint16(28,f.name.length,true); v.setUint16(30,0,true); v.setUint16(32,0,true); v.setUint16(34,0,true); v.setUint16(36,0,true); v.setUint32(38,0,true); v.setUint32(42,f.offset,true); for(let i=0;i<f.name.length;i++) cdh[46+i]=f.name.charCodeAt(i); cdParts.push(cdh); cdSize += cdh.length; } const totalSize = files.reduce((n,f)=>n+f.header.length+f.u8.length,0); const out = new Uint8Array(totalSize + cdSize + 22); let p=0; for(const f of files){ out.set(f.header,p); p+=f.header.length; out.set(f.u8,p); p+=f.u8.length; } const cdStart=p; for(const c of cdParts){ out.set(c,p); p+=c.length; } const v=new DataView(out.buffer); v.setUint32(p,0x06054b50,true); v.setUint16(p+4,0,true); v.setUint16(p+6,0,true); v.setUint16(p+8,files.length,true); v.setUint16(p+10,files.length,true); v.setUint32(p+12,cdSize,true); v.setUint32(p+16,cdStart,true); v.setUint16(p+20,0,true); return new Blob([out],{type:'application/zip'}); }
    return {add,build};
  }

  // =============== Speech Recognition (Web Speech API) ============
  function createRecognizer(){
    const SR = window.SpeechRecognition || window.webkitSpeechRecognition;
    if(!SR) return null;
    const r=new SR();
    r.lang=navigator.language || 'en-US';
    r.interimResults=true; r.continuous=true;
    let finalText=''; let interim='';
    r.onresult = (e)=>{
      interim='';
      for(let i=e.resultIndex;i<e.results.length;i++){
        const res=e.results[i];
        if(res.isFinal) finalText += res[0].transcript + ' ';
        else interim += res[0].transcript + ' ';
      }
      transcriptLive.textContent = (finalText+interim).trim();
    };
    return {
      start(){try{r.start();}catch{}},
      stop(){try{r.stop();}catch{}},
      get text(){return (finalText).trim();}
    };
  }

  // =============== App State =====================================
  let recording=false; let startTs=0; let timerInt=null;
  let audioCtx, sourceNode, processor, mediaStream; let wav;
  let recognizer=null;
  const recordBtn = document.getElementById('record-btn');
  const timerEl = document.getElementById('timer');
  const listEl = document.getElementById('entries');
  const emptyMsg = document.getElementById('empty-msg');
  const qEl = document.getElementById('q');
  const dateEl = document.getElementById('date');
  const clearFiltersBtn = document.getElementById('clear-filters');
  const exportBtn = document.getElementById('export-btn');

  const transcriptLive = document.createElement('div');
  transcriptLive.className='chip';
  transcriptLive.style.marginTop='8px';
  document.querySelector('.card').appendChild(transcriptLive);

  function fmtTime(ms){ const s=Math.floor(ms/1000), m=Math.floor(s/60), r=s%60; return String(m).padStart(2,'0')+":"+String(r).padStart(2,'0'); }

  async function startRecording(){
    mediaStream = await navigator.mediaDevices.getUserMedia({audio:true});
    audioCtx = new (window.AudioContext||window.webkitAudioContext)({sampleRate:44100});
    sourceNode = audioCtx.createMediaStreamSource(mediaStream);
    processor = audioCtx.createScriptProcessor(4096,1,1);
    wav = createWavEncoder(audioCtx.sampleRate);
    processor.onaudioprocess = e=>{ const data=e.inputBuffer.getChannelData(0); wav.write(data); };
    sourceNode.connect(processor); processor.connect(audioCtx.destination);
    startTs=Date.now(); timerEl.textContent='00:00'; transcriptLive.textContent='';
    timerInt=setInterval(()=>{timerEl.textContent=fmtTime(Date.now()-startTs)},250);
    recording=true; recordBtn.textContent='Stop'; recordBtn.classList.add('rec');
    recognizer = createRecognizer(); if(recognizer) recognizer.start();
  }

  async function stopRecording(){
    processor && processor.disconnect(); sourceNode && sourceNode.disconnect(); audioCtx && audioCtx.close();
    mediaStream && mediaStream.getTracks().forEach(t=>t.stop());
    clearInterval(timerInt); recordBtn.textContent='Record'; recordBtn.classList.remove('rec'); recording=false;
    const duration = Date.now()-startTs; const blob = wav.encodeWAV();
    const transcript = recognizer? recognizer.text : '';
    if(recognizer) recognizer.stop();
    const entry = { timestamp:startTs, duration, transcript, editedTranscript: transcript, audioType:'audio/wav' };
    entry.audioBlob = blob;
    entry.id = await DB.addEntry(entry);
    renderList();
  }

  recordBtn.addEventListener('click', async()=>{ if(!recording) await startRecording(); else await stopRecording(); });
  clearFiltersBtn.addEventListener('click', ()=>{ qEl.value=''; dateEl.value=''; renderList(); });
  qEl.addEventListener('input', ()=>renderList());
  dateEl.addEventListener('change', ()=>renderList());

  async function renderList(){
    const items = await DB.listEntries();
    const q = qEl.value.trim().toLowerCase();
    const d = dateEl.value ? new Date(dateEl.value) : null;
    const y = d? d.getFullYear():null, m=d? d.getMonth():null, day=d? d.getDate():null;
    const filtered = items.filter(e=>{
      const text = (e.editedTranscript||e.transcript||'').toLowerCase();
      const okQ = q? text.includes(q):true;
      const okD = d? (new Date(e.timestamp)).toDateString() === new Date(y,m,day).toDateString() : true;
      return okQ && okD;
    });
    listEl.innerHTML='';
    emptyMsg.style.display = filtered.length===0 ? 'block' : 'none';
    for(const e of filtered){ listEl.appendChild(renderEntry(e)); }
  }

  function renderEntry(e){
    const wrap=document.createElement('div'); wrap.className='card entry'; wrap.dataset.id=e.id;
    const when = new Date(e.timestamp).toLocaleString();
    const head=document.createElement('div'); head.className='row';
    head.innerHTML = `<div class="grow"><div><b>${when}</b></div><div class="chip">${fmtTime(e.duration)}</div></div>`;
    const del = document.createElement('button'); del.className='btn danger'; del.textContent='Delete';
    del.onclick = async()=>{ if(confirm('Delete this entry?')){ await DB.delEntry(e.id); renderList(); } };
    head.appendChild(del);
    wrap.appendChild(head);

    const audio = document.createElement('audio'); audio.controls=true; audio.className='audio';
    audio.src = URL.createObjectURL(e.audioBlob);
    wrap.appendChild(audio);

    const ta=document.createElement('textarea'); ta.className='transcript'; ta.value = e.editedTranscript||e.transcript||''; ta.placeholder='Transcript (editable)…';
    ta.onchange = async()=>{ e.editedTranscript=ta.value; await DB.updateEntry(e); };
    wrap.appendChild(ta);

    return wrap;
  }

  // =============== Export ZIP =====================================
  exportBtn.addEventListener('click', async()=>{
    const items = await DB.listEntries();
    if(items.length===0){ alert('No entries to export yet.'); return; }
    const zip = ZipWriter();
    for(const e of items){
      const folder = `${e.id}_${new Date(e.timestamp).toISOString().replace(/[:]/g,'-')}`;
      await zip.add(`${folder}/audio.wav`, e.audioBlob);
      const meta = {id:e.id, timestamp:e.timestamp, duration:e.duration, transcript:e.transcript||'', editedTranscript:e.editedTranscript||'', audioType:e.audioType||'audio/wav'};
      await zip.add(`${folder}/meta.json`, new Blob([JSON.stringify(meta,null,2)],{type:'application/json'}));
    }
    const blob = zip.build();
    const a=document.createElement('a'); a.href=URL.createObjectURL(blob); a.download=`audio-journal-export-${new Date().toISOString().slice(0,10)}.zip`; a.click();
    URL.revokeObjectURL(a.href);
  });

  // =============== PIN Gate =======================================
  const pinGate = document.getElementById('pin-gate');
  const pinInput = document.getElementById('pin-input');
  const pinSubmit = document.getElementById('pin-submit');
  const pinReset = document.getElementById('pin-reset');
  const pinMsg = document.getElementById('pin-msg');
  const pinHelp = document.getElementById('pin-mode-help');

  async function showPinGate(mode){ // 'setup' or 'login'
    pinHelp.textContent = mode==='setup' ? 'Set a 4–8 digit PIN to secure your journal.' : 'Enter your PIN to unlock.';
    pinInput.value=''; pinMsg.textContent='';
    pinGate.hidden=false; pinInput.focus();
    pinSubmit.onclick = async()=>{
      const pin = pinInput.value.trim();
      if(pin.length<4 || pin.length>8){ pinMsg.textContent='PIN must be 4–8 digits.'; return; }
      const h = await hashPIN(pin);
      const saved = await DB.getSetting('pinHash');
      if(!saved){ await DB.setSetting('pinHash',h); pinGate.hidden=true; renderList(); }
      else if(saved===h){ pinGate.hidden=true; renderList(); }
      else { pinMsg.textContent='Incorrect PIN.'; }
    };
  }

  pinReset.onclick = async()=>{
    if(confirm('Reset saved PIN? You will need to enter a new one next time. (This does not delete entries)')){
      await DB.setSetting('pinHash', null);
      pinMsg.textContent='PIN reset. Enter a new PIN to set it.';
    }
  };

  // =============== Install (PWA prompt) ===========================
  let deferredPrompt=null; const installBtn=document.getElementById('install-btn');
  window.addEventListener('beforeinstallprompt', (e)=>{ e.preventDefault(); deferredPrompt=e; installBtn.hidden=false; });
  installBtn.addEventListener('click', async()=>{ if(!deferredPrompt) return; deferredPrompt.prompt(); const {outcome}=await deferredPrompt.userChoice; if(outcome==='accepted') installBtn.hidden=true; deferredPrompt=null; });

  // =============== Boot ===========================================
  (async function boot(){
    // Register service worker from inline source
    if('serviceWorker' in navigator){
      const src = document.getElementById('sw-src').textContent;
      const blob = new Blob([src],{type:'text/javascript'});
      const url = URL.createObjectURL(blob);
      try{ await navigator.serviceWorker.register(url,{scope:'./'}); }catch(e){ console.warn('SW register failed',e); }
      setTimeout(()=>URL.revokeObjectURL(url),5000);
    }
    const pinHash = await DB.getSetting('pinHash');
    if(!pinHash){ showPinGate('setup'); } else { showPinGate('login'); }
    renderList();
  })();

  </script>
</body>
</html>
