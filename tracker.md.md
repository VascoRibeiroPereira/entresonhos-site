---
layout: page
title: "Writting Tracker"
permalink: /tracker/
---


<!doctype html>
<html lang="pt">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Entre Sonhos — Writing Tracker</title>
  <style>
    :root{
      --bg:#0b0b0d;
      --panel:#111116;
      --panel2:#14141b;
      --text:#f2f2f3;
      --muted:#b8b8c2;
      --line:#2a2a36;
      --accent:#ff7a18;
      --good:#3ddc97;
      --bad:#ff5b5b;
      --warn:#ffcc66;
      --radius:16px;
    }
    *{box-sizing:border-box}
    body{
      margin:0;
      font-family: system-ui, -apple-system, Segoe UI, Roboto, Arial, sans-serif;
      background: radial-gradient(1000px 500px at 20% -10%, rgba(255,122,24,.18), transparent 60%),
                  radial-gradient(900px 500px at 90% 10%, rgba(255,122,24,.12), transparent 55%),
                  var(--bg);
      color:var(--text);
    }
    a{color:var(--accent); text-decoration:none}
    a:hover{text-decoration:underline}
    .wrap{max-width:1100px; margin:0 auto; padding:22px}
    header{
      display:flex; gap:14px; align-items:flex-start; justify-content:space-between;
      margin-bottom:18px;
    }
    h1{font-size:22px; margin:0}
    .sub{color:var(--muted); margin-top:6px; font-size:14px}
    .grid{
      display:grid;
      grid-template-columns: 360px 1fr;
      gap:16px;
    }
    @media (max-width: 900px){
      .grid{grid-template-columns:1fr}
    }
    .card{
      background: linear-gradient(180deg, rgba(255,255,255,.03), rgba(255,255,255,.015));
      border: 1px solid rgba(255,255,255,.06);
      border-radius: var(--radius);
      padding:16px;
      box-shadow: 0 10px 30px rgba(0,0,0,.35);
    }
    .card h2{font-size:16px; margin:0 0 10px 0}
    label{display:block; font-size:12px; color:var(--muted); margin:10px 0 6px}
    input, textarea{
      width:100%;
      background: var(--panel2);
      color: var(--text);
      border: 1px solid rgba(255,255,255,.08);
      border-radius: 12px;
      padding:10px 12px;
      outline:none;
    }
    textarea{min-height:88px; resize:vertical}
    input:focus, textarea:focus{border-color: rgba(255,122,24,.55); box-shadow:0 0 0 3px rgba(255,122,24,.12)}
    .row{display:flex; gap:10px}
    .row > *{flex:1}
    .btns{display:flex; gap:10px; flex-wrap:wrap; margin-top:12px}
    button{
      appearance:none; border:0;
      background: rgba(255,255,255,.06);
      color:var(--text);
      padding:10px 12px;
      border-radius: 12px;
      cursor:pointer;
      border:1px solid rgba(255,255,255,.08);
      font-weight:600;
    }
    button:hover{background: rgba(255,255,255,.09)}
    .primary{background: rgba(255,122,24,.20); border-color: rgba(255,122,24,.35)}
    .primary:hover{background: rgba(255,122,24,.28)}
    .danger{background: rgba(255,91,91,.16); border-color: rgba(255,91,91,.30)}
    .danger:hover{background: rgba(255,91,91,.22)}
    .hint{color:var(--muted); font-size:12px; margin-top:10px; line-height:1.4}
    .stats{
      display:grid; grid-template-columns: repeat(4, 1fr);
      gap:10px; margin-top:10px;
    }
    @media (max-width: 900px){
      .stats{grid-template-columns: repeat(2, 1fr)}
    }
    .stat{
      background: rgba(0,0,0,.18);
      border:1px solid rgba(255,255,255,.06);
      border-radius: 14px;
      padding:10px 12px;
    }
    .stat .k{font-size:11px; color:var(--muted)}
    .stat .v{font-size:18px; font-weight:800; margin-top:4px}
    .brand{
      display:flex; gap:10px; align-items:center; justify-content:space-between;
      margin-top:10px; padding-top:10px;
      border-top:1px solid rgba(255,255,255,.06);
      color:var(--muted); font-size:12px;
    }
    table{
      width:100%; border-collapse:collapse; margin-top:12px; font-size:13px;
      overflow:hidden; border-radius: 14px;
    }
    th, td{
      padding:10px 10px;
      border-bottom:1px solid rgba(255,255,255,.06);
      vertical-align:top;
    }
    th{color:var(--muted); font-weight:700; text-align:left; background: rgba(0,0,0,.20)}
    tr:hover td{background: rgba(255,255,255,.03)}
    .pill{
      display:inline-block; padding:2px 8px; border-radius:999px; font-size:11px; font-weight:800;
      border:1px solid rgba(255,255,255,.10);
    }
    .ok{color:var(--good); border-color: rgba(61,220,151,.35); background: rgba(61,220,151,.08)}
    .miss{color:var(--warn); border-color: rgba(255,204,102,.35); background: rgba(255,204,102,.07)}
    .bad{color:var(--bad); border-color: rgba(255,91,91,.35); background: rgba(255,91,91,.07)}
    canvas{
      width:100%;
      height:320px;
      background: rgba(0,0,0,.18);
      border:1px solid rgba(255,255,255,.06);
      border-radius: 16px;
    }
    .topline{display:flex; align-items:flex-end; justify-content:space-between; gap:10px; flex-wrap:wrap}
    .filemeta{color:var(--muted); font-size:12px}
    .small{font-size:12px; color:var(--muted)}
  </style>
</head>
<body>
  <div class="wrap">
    <header>
      <div>
        <h1>Entre Sonhos — Writing Tracker</h1>
        <div class="sub">Regista palavras por dia • objetivo flexível • gráfico + export/import JSON</div>
      </div>
      <div class="small">Marca: <strong>@blog_entre_sonhos</strong></div>
    </header>

    <div class="grid">
      <section class="card">
        <h2>Adicionar / editar entrada</h2>

        <label for="date">Data</label>
        <input id="date" type="date" />

        <div class="row">
          <div>
            <label for="words">Palavras escritas</label>
            <input id="words" type="number" min="0" step="1" placeholder="ex.: 850" />
          </div>
          <div>
            <label for="goal">Objetivo do dia</label>
            <input id="goal" type="number" min="0" step="1" placeholder="ex.: 1000" />
          </div>
        </div>

        <label for="note">Nota (opcional)</label>
        <textarea id="note" placeholder="Uma linha sobre como correu, o que mudas amanhã, etc."></textarea>

        <div class="btns">
          <button class="primary" id="saveBtn">Guardar entrada</button>
          <button id="clearBtn">Limpar</button>
          <button class="danger" id="deleteBtn">Apagar esta entrada</button>
        </div>

        <div class="btns" style="margin-top:10px">
          <button id="exportJsonBtn">Exportar JSON</button>
          <label style="margin:0; display:flex; align-items:center; gap:10px">
            <input id="importFile" type="file" accept="application/json" style="display:none" />
            <button id="importJsonBtn" type="button">Importar JSON</button>
          </label>
          <button id="exportPngBtn">Exportar gráfico (PNG)</button>
        </div>

        <div class="hint">
          Dica: usa <strong>Importar JSON</strong> para recuperar dados noutro dispositivo. O ficheiro é a “memória” da app.
        </div>

        <div class="stats">
          <div class="stat"><div class="k">Total</div><div class="v" id="totalOut">0</div></div>
          <div class="stat"><div class="k">Média / dia</div><div class="v" id="avgOut">0</div></div>
          <div class="stat"><div class="k">Dias registados</div><div class="v" id="daysOut">0</div></div>
          <div class="stat"><div class="k">% dias com objetivo</div><div class="v" id="goalPctOut">0%</div></div>
        </div>

        <div class="brand">
          <span>Entre Sonhos</span>
          <span class="filemeta">Ficheiro: <span id="fileNameOut">—</span></span>
        </div>
      </section>

      <section class="card">
        <div class="topline">
          <div>
            <h2 style="margin:0">Evolução</h2>
            <div class="small">Clique numa linha da tabela para carregar/editar essa entrada.</div>
          </div>
        </div>

        <div style="margin-top:12px">
          <canvas id="chart" width="1200" height="600"></canvas>
        </div>

        <div style="overflow:auto; margin-top:10px">
          <table>
            <thead>
              <tr>
                <th style="min-width:110px">Data</th>
                <th style="min-width:90px">Palavras</th>
                <th style="min-width:90px">Objetivo</th>
                <th style="min-width:110px">Estado</th>
                <th>Nota</th>
              </tr>
            </thead>
            <tbody id="tbody"></tbody>
          </table>
        </div>
      </section>
    </div>
  </div>

  <script>
  document.addEventListener("DOMContentLoaded", () => {
    // ---------- State ----------
    /** @type {Record<string, {words:number, goal:number|null, note:string}>} */
    let entries = {};
    let loadedFileName = "—";

    // ---------- Elements ----------
    const el = (id) => document.getElementById(id);

    const dateEl = el("date");
    const wordsEl = el("words");
    const goalEl  = el("goal");
    const noteEl  = el("note");

    const saveBtn   = el("saveBtn");
    const clearBtn  = el("clearBtn");
    const deleteBtn = el("deleteBtn");

    const exportJsonBtn = el("exportJsonBtn");
    const importJsonBtn = el("importJsonBtn");
    const importFile    = el("importFile");
    const exportPngBtn  = el("exportPngBtn");

    const totalOut   = el("totalOut");
    const avgOut     = el("avgOut");
    const daysOut    = el("daysOut");
    const goalPctOut = el("goalPctOut");
    const fileNameOut= el("fileNameOut");

    const tbody = el("tbody");
    const canvas = el("chart");
    const ctx = canvas.getContext("2d");

    // ---------- Helpers ----------
    const todayISO = () => {
      const d = new Date();
      const pad = (n) => String(n).padStart(2,"0");
      return `${d.getFullYear()}-${pad(d.getMonth()+1)}-${pad(d.getDate())}`;
    };

    const sortDates = (a,b) => a.localeCompare(b);
    const fmtNum = (n) => (Number.isFinite(n) ? n.toLocaleString("pt-PT") : "0");

    function safeInt(value){
      const n = Number(value);
      if (!Number.isFinite(n) || n < 0) return 0;
      return Math.floor(n);
    }

    function downloadBlob(blob, filename){
      const url = URL.createObjectURL(blob);
      const a = document.createElement("a");
      a.href = url;
      a.download = filename;
      document.body.appendChild(a);
      a.click();
      a.remove();
      URL.revokeObjectURL(url);
    }

    function currentFormKey(){
      return (dateEl.value || "").trim();
    }

    function clearForm(){
      dateEl.value = todayISO();
      wordsEl.value = "";
      goalEl.value = "";
      noteEl.value = "";
      loadedFileName = loadedFileName || "—";
      render();
    }

    function loadToForm(dateKey){
      const e = entries[dateKey];
      if (!e) return;
      dateEl.value = dateKey;
      wordsEl.value = String(e.words ?? 0);
      goalEl.value  = (e.goal === null || e.goal === undefined) ? "" : String(e.goal);
      noteEl.value  = e.note ?? "";
    }

    // ---------- Core ----------
    function saveEntry(){
      const k = currentFormKey();
      if (!k) { alert("Escolhe uma data."); return; }

      const words = safeInt(wordsEl.value);
      const goalRaw = goalEl.value.trim();
      const goal = goalRaw === "" ? null : safeInt(goalRaw);
      const note = (noteEl.value || "").trim();

      entries[k] = { words, goal, note };
      render();
    }

    function deleteEntry(){
      const k = currentFormKey();
      if (!k) return;
      if (!entries[k]) { alert("Não existe entrada para esta data."); return; }
      if (!confirm(`Apagar a entrada de ${k}?`)) return;
      delete entries[k];
      render();
    }

    function computeStats(){
      const keys = Object.keys(entries).sort(sortDates);
      const days = keys.length;
      let total = 0;
      let goalDays = 0;

      for (const k of keys){
        const e = entries[k];
        total += safeInt(e.words);
        if (e.goal !== null && e.goal !== undefined) goalDays++;
      }
      const avg = days ? Math.round(total / days) : 0;
      const goalPct = days ? Math.round((goalDays / days) * 100) : 0;

      totalOut.textContent = fmtNum(total);
      avgOut.textContent = fmtNum(avg);
      daysOut.textContent = fmtNum(days);
      goalPctOut.textContent = `${goalPct}%`;
      fileNameOut.textContent = loadedFileName || "—";

      return keys;
    }

    function statusPill(words, goal){
      if (goal === null || goal === undefined) return `<span class="pill miss">sem objetivo</span>`;
      if (words >= goal) return `<span class="pill ok">cumprido</span>`;
      if (goal === 0) return `<span class="pill ok">cumprido</span>`;
      const pct = Math.round((words / goal) * 100);
      return `<span class="pill bad">${pct}%</span>`;
    }

    function renderTable(keys){
      tbody.innerHTML = "";
      for (const k of keys){
        const e = entries[k];
        const words = safeInt(e.words);
        const goal = (e.goal === null || e.goal === undefined) ? null : safeInt(e.goal);
        const note = (e.note || "").trim();

        const tr = document.createElement("tr");
        tr.innerHTML = `
          <td>${k}</td>
          <td>${fmtNum(words)}</td>
          <td>${goal === null ? "—" : fmtNum(goal)}</td>
          <td>${statusPill(words, goal)}</td>
          <td>${note.replaceAll("<","&lt;").replaceAll(">","&gt;")}</td>
        `;
        tr.addEventListener("click", () => loadToForm(k));
        tbody.appendChild(tr);
      }
    }

    // Simple canvas line chart (no libs)
    function renderChart(keys){
      // clear
      ctx.clearRect(0,0,canvas.width,canvas.height);

      const W = canvas.width, H = canvas.height;
      const padL = 70, padR = 20, padT = 24, padB = 70;
      const plotW = W - padL - padR;
      const plotH = H - padT - padB;

      // background grid
      ctx.save();
      ctx.fillStyle = "rgba(0,0,0,0)";
      ctx.strokeStyle = "rgba(255,255,255,0.08)";
      ctx.lineWidth = 1;

      const gridY = 5;
      for (let i=0;i<=gridY;i++){
        const y = padT + (plotH * i / gridY);
        ctx.beginPath();
        ctx.moveTo(padL, y);
        ctx.lineTo(W-padR, y);
        ctx.stroke();
      }
      ctx.restore();

      // series
      const wordsSeries = keys.map(k => safeInt(entries[k].words));
      const goalSeries  = keys.map(k => {
        const g = entries[k].goal;
        return (g === null || g === undefined) ? null : safeInt(g);
      });

      const maxVal = Math.max(
        10,
        ...wordsSeries,
        ...goalSeries.filter(v => v !== null)
      );

      // axes
      ctx.save();
      ctx.strokeStyle = "rgba(255,255,255,0.18)";
      ctx.lineWidth = 2;
      ctx.beginPath();
      ctx.moveTo(padL, padT);
      ctx.lineTo(padL, H-padB);
      ctx.lineTo(W-padR, H-padB);
      ctx.stroke();
      ctx.restore();

      // y labels
      ctx.save();
      ctx.fillStyle = "rgba(255,255,255,0.70)";
      ctx.font = "18px system-ui, -apple-system, Segoe UI, Roboto, Arial";
      ctx.textAlign = "right";
      ctx.textBaseline = "middle";
      for (let i=0;i<=gridY;i++){
        const val = Math.round(maxVal * (1 - i/gridY));
        const y = padT + (plotH * i / gridY);
        ctx.fillText(val.toString(), padL-10, y);
      }
      ctx.restore();

      if (keys.length === 0){
        ctx.save();
        ctx.fillStyle = "rgba(255,255,255,0.55)";
        ctx.font = "26px system-ui, -apple-system, Segoe UI, Roboto, Arial";
        ctx.textAlign = "center";
        ctx.textBaseline = "middle";
        ctx.fillText("Sem dados — adiciona uma entrada para veres o gráfico.", W/2, H/2);
        ctx.restore();
        return;
      }

      const xAt = (i) => {
        if (keys.length === 1) return padL + plotW/2;
        return padL + (plotW * i / (keys.length - 1));
      };
      const yAt = (v) => {
        const t = v / maxVal;
        return padT + (plotH * (1 - t));
      };

      // words line (accent)
      ctx.save();
      ctx.strokeStyle = "rgba(255,122,24,0.95)";
      ctx.lineWidth = 4;
      ctx.lineJoin = "round";
      ctx.lineCap = "round";
      ctx.beginPath();
      keys.forEach((k,i)=>{
        const x = xAt(i);
        const y = yAt(wordsSeries[i]);
        if (i===0) ctx.moveTo(x,y); else ctx.lineTo(x,y);
      });
      ctx.stroke();
      ctx.restore();

      // goal line (white dashed-ish)
      // We'll draw segments only where goal exists
      ctx.save();
      ctx.strokeStyle = "rgba(255,255,255,0.60)";
      ctx.lineWidth = 3;
      // "fake dashed": small segments
      for (let i=0;i<keys.length-1;i++){
        const g1 = goalSeries[i], g2 = goalSeries[i+1];
        if (g1===null || g2===null) continue;
        const x1=xAt(i), y1=yAt(g1);
        const x2=xAt(i+1), y2=yAt(g2);

        const steps = 10;
        for (let s=0;s<steps;s++){
          if (s%2===1) continue; // skip every other segment
          const t1=s/steps, t2=(s+1)/steps;
          ctx.beginPath();
          ctx.moveTo(x1+(x2-x1)*t1, y1+(y2-y1)*t1);
          ctx.lineTo(x1+(x2-x1)*t2, y1+(y2-y1)*t2);
          ctx.stroke();
        }
      }
      ctx.restore();

      // points
      ctx.save();
      keys.forEach((k,i)=>{
        const x=xAt(i), y=yAt(wordsSeries[i]);
        ctx.fillStyle = "rgba(255,122,24,1)";
        ctx.beginPath(); ctx.arc(x,y,6,0,Math.PI*2); ctx.fill();
        ctx.fillStyle = "rgba(0,0,0,0.65)";
        ctx.beginPath(); ctx.arc(x,y,3,0,Math.PI*2); ctx.fill();
      });
      ctx.restore();

      // x labels (first/last)
      ctx.save();
      ctx.fillStyle = "rgba(255,255,255,0.70)";
      ctx.font = "18px system-ui, -apple-system, Segoe UI, Roboto, Arial";
      ctx.textAlign = "center";
      ctx.textBaseline = "top";
      const first = keys[0];
      const last  = keys[keys.length-1];
      ctx.fillText(first, xAt(0), H - padB + 18);
      if (keys.length>1) ctx.fillText(last, xAt(keys.length-1), H - padB + 18);

      // legend
      ctx.textAlign = "left";
      ctx.textBaseline = "alphabetic";
      ctx.fillStyle = "rgba(255,122,24,0.95)";
      ctx.fillText("Palavras", padL, padT - 6);
      ctx.fillStyle = "rgba(255,255,255,0.70)";
      ctx.fillText("Objetivo", padL + 120, padT - 6);
      ctx.restore();
    }

    function render(){
      const keys = computeStats();
      renderTable(keys);
      renderChart(keys);
    }

    // ---------- JSON import/export ----------
    function exportJSON(){
      const payload = {
        app: "Entre Sonhos — Writing Tracker",
        version: 1,
        exportedAt: new Date().toISOString(),
        entries
      };
      const blob = new Blob([JSON.stringify(payload, null, 2)], {type:"application/json"});
      const stamp = new Date().toISOString().slice(0,10);
      downloadBlob(blob, `writing-tracker_${stamp}.json`);
    }

    async function importJSON(file){
      const text = await file.text();
      let data;
      try { data = JSON.parse(text); }
      catch { alert("JSON inválido."); return; }

      if (!data || typeof data !== "object" || !data.entries || typeof data.entries !== "object"){
        alert("Formato inesperado. Esperava { entries: { 'YYYY-MM-DD': {words, goal, note} } }");
        return;
      }

      // normalize
      const cleaned = {};
      for (const [k,v] of Object.entries(data.entries)){
        if (!/^\d{4}-\d{2}-\d{2}$/.test(k)) continue;
        const words = safeInt(v?.words);
        const goal  = (v?.goal === null || v?.goal === undefined || v?.goal === "") ? null : safeInt(v.goal);
        const note  = (v?.note || "").toString();
        cleaned[k] = {words, goal, note};
      }

      entries = cleaned;
      loadedFileName = file.name || "importado.json";
      render();
      // carrega a última data para editar mais facilmente
      const keys = Object.keys(entries).sort(sortDates);
      if (keys.length) loadToForm(keys[keys.length-1]);
    }

    function exportPNG(){
      const a = document.createElement("a");
      a.download = `writing-tracker_chart_${new Date().toISOString().slice(0,10)}.png`;
      a.href = canvas.toDataURL("image/png");
      a.click();
    }

    // ---------- Wire up ----------
    // defaults
    dateEl.value = todayISO();

    saveBtn.addEventListe