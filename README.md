# IV-start
Nursing Student IV Start
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>IV Start & LDA Record — Student Submission</title>
  <style>
    :root{
      --bg:#0f172a; --panel:#0b1220; --text:#e5e7eb; --muted:#94a3b8; --border:#1f2937; --brand:#60a5fa; --ok:#34d399;
    }
    html,body{height:100%}
    body{margin:0; font:16px/1.5 system-ui,-apple-system,Segoe UI,Roboto,Helvetica,Arial; background:radial-gradient(1200px 800px at 10% -10%, rgba(96,165,250,.12), transparent 60%), radial-gradient(900px 600px at 110% -20%, rgba(52,211,153,.10), transparent 50%), var(--bg); color:var(--text)}
    .container{max-width:1024px; margin:36px auto; padding:0 16px}
    .card{background:linear-gradient(180deg, rgba(255,255,255,.02), rgba(255,255,255,.01)); border:1px solid var(--border); border-radius:18px; padding:22px; box-shadow:0 10px 30px rgba(0,0,0,.25)}
    h1{margin:0 0 6px; font-size:clamp(22px,3.6vw,32px)}
    p.lead{margin:0; color:var(--muted)}
    fieldset{border:1px dashed var(--border); border-radius:14px; padding:14px; margin-top:16px}
    legend{padding:0 8px; color:var(--brand); font-weight:700}
    label{display:block; font-weight:600; margin:10px 0 6px}
    input[type="text"], input[type="date"], input[type="time"], input[type="number"], textarea, select{width:100%; padding:12px 14px; border-radius:12px; border:1px solid var(--border); background:var(--panel); color:var(--text); outline:none}
    input:focus, textarea:focus, select:focus{border-color:var(--brand); box-shadow:0 0 0 3px rgba(96,165,250,.18)}
    textarea{min-height:100px; resize:vertical}
    .grid{display:grid; gap:16px}
    @media(min-width:860px){ .grid.two{grid-template-columns:1fr 1fr} .grid.three{grid-template-columns:repeat(3,1fr)} }
    .checks{display:grid; grid-template-columns:repeat(auto-fit,minmax(220px,1fr)); gap:8px 14px}
    .checks label{display:flex; align-items:center; gap:10px; margin:0; font-weight:500}
    .row{display:flex; flex-wrap:wrap; gap:10px}
    .chip{display:inline-block; padding:6px 10px; border:1px solid var(--border); border-radius:999px; background:#0a1020; font-size:13px; cursor:pointer}
    .actions{display:flex; flex-wrap:wrap; gap:10px; padding-top:10px}
    .actions button{appearance:none; border:none; cursor:pointer; padding:12px 16px; border-radius:12px; font-weight:700; color:#0b1220; background:var(--brand); box-shadow:0 8px 18px rgba(96,165,250,.25)}
    .actions button.secondary{background:#1f2937; color:var(--text); box-shadow:none; border:1px solid var(--border)}
    .actions button.success{background:var(--ok); box-shadow:0 8px 18px rgba(52,211,153,.22)}
    .actions .right{margin-left:auto}
    .status{margin-top:10px; font-size:14px; color:var(--muted)}
    @media print{ body{background:#fff; color:#000} .actions,.hide-print{display:none !important} .card{box-shadow:none; border-color:#000} }
  </style>
</head>
<body>
  <div class="container">
    <header class="card" style="margin-bottom:16px">
      <h1>IV Start & LDA Record — Student Submission</h1>
      <p class="lead">For 2nd‑semester IV Start and primary fluids documentation. Autosaves locally; export JSON or print to PDF for BlackBoard/LMS upload.</p>
    </header>

    <form id="iv-form" class="card" novalidate>
      <!-- Identification -->
      <fieldset>
        <legend>Identification</legend>
        <div class="grid two">
          <div>
            <label for="studentName">Student Name <span id="nameReq" class="hide-print" style="color:#fca5a5" hidden>required</span></label>
            <input id="studentName" name="studentName" type="text" autocomplete="name" placeholder="First Last" required />
          </div>
          <div>
            <label for="date">Date of Documentation</label>
            <input id="date" name="date" type="date" />
          </div>
          <div>
            <label for="course">Course / Cohort</label>
            <input id="course" name="course" type="text" placeholder="e.g., NSG 213 — Fall 2025" />
          </div>
          <div>
            <label for="instructor">Instructor</label>
            <input id="instructor" name="instructor" type="text" />
          </div>
        </div>
      </fieldset>

      <!-- LDA Selection -->
      <fieldset>
        <legend>Lines, Drains & Airways (LDA)</legend>
        <p class="hide-print" style="margin:0 0 8px; color:var(--muted)">Select the device you started/managed.</p>
        <div class="checks">
          <label><input type="radio" name="lda" value="Peripheral IV" required /> Peripheral IV (PIV)</label>
          <label><input type="radio" name="lda" value="PICC" /> Peripherally Inserted Central Catheter (PICC)</label>
          <label><input type="radio" name="lda" value="CVC" /> Central Venous Catheter (CVC)</label>
        </div>

        <div class="grid two">
          <div>
            <label for="insertDate">Insertion Date</label>
            <input id="insertDate" name="insertDate" type="date" />
          </div>
          <div>
            <label for="insertTime">Insertion Time</label>
            <input id="insertTime" name="insertTime" type="time" />
          </div>
        </div>

        <!-- Site & Laterality (for PIV default; still useful for central access site notes) -->
        <div class="grid three">
          <div>
            <label for="anteriorPosterior">Site Orientation</label>
            <select id="anteriorPosterior" name="anteriorPosterior">
              <option value="">—</option>
              <option>Anterior</option>
              <option>Posterior</option>
            </select>
          </div>
          <div>
            <label for="laterality">Laterality</label>
            <select id="laterality" name="laterality">
              <option value="">—</option>
              <option>Left</option>
              <option>Right</option>
            </select>
          </div>
          <div>
            <label for="site">Site</label>
            <select id="site" name="site">
              <option value="">—</option>
              <option>Dorsal hand</option>
              <option>Forearm</option>
              <option>Antecubital</option>
              <option>Upper arm</option>
              <option>Other</option>
            </select>
          </div>
        </div>

        <!-- Gauge (PIV only) + Attempts -->
        <div class="grid three" id="pivOnly">
          <div>
            <label for="gauge">IV Gauge (PIV)</label>
            <select id="gauge" name="gauge">
              <option value="">—</option>
              <option>18</option>
              <option>20</option>
              <option>22</option>
              <option>24</option>
            </select>
          </div>
          <div>
            <label for="attempts">Number of Attempts</label>
            <input id="attempts" name="attempts" type="number" min="0" step="1" />
          </div>
          <div>
            <label for="otherNotes">Other Notes</label>
            <input id="otherNotes" name="otherNotes" type="text" placeholder="e.g., ultrasound‑guided, difficult stick" />
          </div>
        </div>

        <!-- Central line specifics (shown when PICC/CVC selected) -->
        <div class="grid two" id="centralOnly" hidden>
          <div>
            <label for="centralType">Central Line Type</label>
            <select id="centralType" name="centralType">
              <option value="">—</option>
              <option>Single lumen</option>
              <option>Double lumen</option>
              <option>Triple lumen</option>
              <option>Implanted port</option>
            </select>
          </div>
          <div>
            <label for="centralSite">Central Site/Vein</label>
            <input id="centralSite" name="centralSite" type="text" placeholder="e.g., R basilic (PICC), R IJ (CVC), subclavian" />
          </div>
        </div>
      </fieldset>

      <!-- Dressing -->
      <fieldset>
        <legend>Dressing</legend>
        <div class="grid two">
          <div>
            <label for="dressingApplied">Dressing Applied?</label>
            <select id="dressingApplied" name="dressingApplied">
              <option value="">—</option>
              <option>Yes</option>
              <option>No</option>
            </select>
          </div>
          <div>
            <label for="dressingStatus">Dressing Status</label>
            <select id="dressingStatus" name="dressingStatus">
              <option value="">—</option>
              <option>CDI (Clean, Dry, Intact)</option>
              <option>Bleeding</option>
              <option>Loose/Soiled</option>
              <option>Other</option>
            </select>
          </div>
        </div>
      </fieldset>

      <!-- Fluids / Med Admin -->
      <fieldset>
        <legend>Fluids / Medication Administration</legend>
        <div class="grid two">
          <div>
            <label for="solution">Solution</label>
            <select id="solution" name="solution">
              <option value="">—</option>
              <option>Normal Saline 0.9%</option>
              <option>Lactated Ringers</option>
              <option>D5W</option>
              <option>Other</option>
            </select>
          </div>
          <div>
            <label for="route">Route</label>
            <select id="route" name="route">
              <option value="">—</option>
              <option>Intravenous (IV)</option>
              <option>IV Push (IVP)</option>
              <option>Intermittent (IVPB)</option>
            </select>
          </div>
        </div>
        <div class="grid two">
          <div>
            <label for="rate">Infusion Rate (mL/hr)</label>
            <input id="rate" name="rate" type="number" min="0" step="1" />
          </div>
          <div>
            <label for="startTime">Infusion Start Time</label>
            <input id="startTime" name="startTime" type="time" />
          </div>
        </div>
      </fieldset>

      <!-- Assessment Checks -->
      <fieldset>
        <legend>Assessment / Complications</legend>
        <div class="checks">
          <label><input type="checkbox" name="checks" value="Flushed without resistance"/> Flushed without resistance</label>
          <label><input type="checkbox" name="checks" value="Blood return present"/> Blood return present</label>
          <label><input type="checkbox" name="checks" value="Infiltration suspected"/> Infiltration suspected</label>
          <label><input type="checkbox" name="checks" value="Phlebitis signs"/> Phlebitis signs</label>
          <label><input type="checkbox" name="checks" value="Site pain/tenderness"/> Site pain/tenderness</label>
          <label><input type="checkbox" name="checks" value="Securement device in place"/> Securement device in place</label>
        </div>
        <label for="remarks">Remarks / Narrative</label>
        <textarea id="remarks" name="remarks" placeholder="Summarize your procedure, patient tolerance, and any teaching provided."></textarea>
      </fieldset>

      <!-- Acknowledgment -->
      <fieldset>
        <legend>Sign‑off</legend>
        <div class="grid two">
          <div>
            <label for="signature">Student Signature (type name)</label>
            <input id="signature" name="signature" type="text" />
          </div>
          <div>
            <label for="signedDate">Date Signed</label>
            <input id="signedDate" name="signedDate" type="date" />
          </div>
        </div>
      </fieldset>

      <!-- Actions -->
      <div class="actions">
        <button type="button" id="saveDraft">Save Draft</button>
        <button type="button" id="exportJson" class="secondary">Export JSON</button>
        <button type="button" id="printPage" class="secondary">Print / Save PDF</button>
        <button type="reset" id="clearForm" class="secondary">Clear</button>
        <span class="right"></span>
        <button type="submit" class="success">Submit</button>
      </div>
      <div id="status" class="status" role="status" aria-live="polite"></div>
      <div class="hide-print" style="font-size:13px; color:var(--muted)">To post this to your server/LMS, set <code>action</code> and <code>method</code> on <code>&lt;form id="iv-form"&gt;</code> and remove the JS <em>preventDefault</em> in the submit handler.</div>
    </form>
  </div>

  <script>
    (function(){
      const form = document.getElementById('iv-form');
      const statusEl = document.getElementById('status');
      const nameReq = document.getElementById('nameReq');

      // Default dates to today
      const today = new Date(); const pad = (n)=> String(n).padStart(2,'0');
      const iso = `${today.getFullYear()}-${pad(today.getMonth()+1)}-${pad(today.getDate())}`;
      ['date','signedDate','insertDate'].forEach(id=>{ const el=document.getElementById(id); if(el && !el.value) el.value=iso; });

      // Show/hide sections based on LDA selection
      const ldaRadios = Array.from(document.querySelectorAll('input[name="lda"]'));
      const pivOnly = document.getElementById('pivOnly');
      const centralOnly = document.getElementById('centralOnly');
      function updateVisibility(){
        const sel = (ldaRadios.find(r=>r.checked)||{}).value || '';
        const isPIV = sel === 'Peripheral IV';
        pivOnly.hidden = !isPIV;
        centralOnly.hidden = isPIV || sel === '';
      }
      ldaRadios.forEach(r=> r.addEventListener('change', updateVisibility));
      updateVisibility();

      // Local storage helpers
      const STORAGE_KEY = 'iv_start_lda_form_v1';
      function serialize(){
        const out={}; const fd=new FormData(form);
        for (const [k,v] of fd.entries()){
          if(out[k]){ if(!Array.isArray(out[k])) out[k]=[out[k]]; out[k].push(v);} else out[k]=v;
        }
        out._ts = Date.now();
        return out;
      }
      function restore(data){
        if(!data) return;
        for (const [k,v] of Object.entries(data)){
          if(k.startsWith('_')) continue;
          const el = form.elements[k]; if(!el) continue;
          if (el instanceof RadioNodeList){ el.value = v; }
          else if (Array.isArray(v)){
            v.forEach(val=>{ const box=form.querySelector(`[name="${k}"][value="${val}"]`); if(box) box.checked=true; });
          } else { el.value = v; }
        }
        updateVisibility();
      }
      function saveDraft(){ localStorage.setItem(STORAGE_KEY, JSON.stringify(serialize())); status('Draft saved.'); }
      function loadDraft(){ try{ const raw=localStorage.getItem(STORAGE_KEY); if(!raw) return; const data=JSON.parse(raw); restore(data); if(data._ts){ status(`Draft loaded (saved ${new Date(data._ts).toLocaleString()}).`);} }catch(e){}
      }
      function clearDraft(){ localStorage.removeItem(STORAGE_KEY); status('Local draft cleared.'); }
      function status(msg){ statusEl.textContent = msg; }

      document.getElementById('saveDraft').addEventListener('click', saveDraft);
      document.getElementById('exportJson').addEventListener('click', ()=>{
        const blob = new Blob([JSON.stringify(serialize(),null,2)], {type:'application/json'});
        const a = document.createElement('a');
        a.href = URL.createObjectURL(blob);
        const nm = (form.studentName?.value||'student').replace(/\s+/g,'-');
        a.download = `iv-start-lda_${nm}_${form.date?.value||iso}.json`;
        document.body.appendChild(a); a.click(); a.remove();
        status('JSON exported.');
      });
      document.getElementById('printPage').addEventListener('click', ()=> window.print());
      document.getElementById('clearForm').addEventListener('click', ()=>{ setTimeout(()=> status('Form cleared.'),0); clearDraft(); });

      // Submit (client-side). Change to real POST by adding form action/method and removing preventDefault
      form.addEventListener('submit', (e)=>{
        e.preventDefault();
        const ok = form.studentName.value.trim().length>1 && !!form.lda.value;
        nameReq.hidden = form.studentName.value.trim().length>1;
        if(!ok){ status('Please enter your name and select an LDA.'); return; }
        saveDraft();
        alert('Submission validated and saved locally on this device. Use Export JSON or Print/PDF to upload.');
        status('Submission validated.');
      });

      loadDraft();
    })();
  </script>
</body>
</html>
