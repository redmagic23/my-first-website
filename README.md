# my-first-website
test website

<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>AI for Nature — Demo</title>
  <meta name="description" content="Interactive demo site showing how AI helps nature: monitoring, restoration, species ID, and more." />
  <style>
    :root{
      --bg:#071021; --card:#0b1220; --accent:#28c3a7; --muted:#9aa6b2; --glass: rgba(255,255,255,0.03);
      --radius:12px; --max-width:1100px; font-family:system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
    }
    *{box-sizing:border-box}
    html,body{height:100%}
    body{
      margin:0; background:linear-gradient(180deg,#071021 0%, #071826 65%); color:#e6eef6;
      -webkit-font-smoothing:antialiased; -moz-osx-font-smoothing:grayscale;
      padding:28px; display:flex; justify-content:center;
    }
    .container{max-width:var(--max-width); width:100%;}
    header{display:flex;align-items:center;gap:16px;margin-bottom:18px}
    .logo{
      width:64px;height:64px;border-radius:12px;background:linear-gradient(135deg,var(--accent),#4bd3c0);
      display:flex;align-items:center;justify-content:center;font-weight:700;color:#042027;font-size:20px;
      box-shadow:0 6px 18px rgba(0,0,0,0.5);
    }
    h1{margin:0;font-size:1.5rem}
    p.lead{margin:4px 0 0;color:var(--muted)}
    main{display:grid;grid-template-columns:1fr 360px;gap:18px;align-items:start}
    .card{background:linear-gradient(180deg,var(--card),var(--glass));padding:16px;border-radius:var(--radius);box-shadow:0 6px 24px rgba(2,6,23,0.6)}
    .grid{display:grid;grid-template-columns:repeat(2,1fr);gap:10px}
    .usecase{padding:10px;border-radius:10px;background:linear-gradient(180deg, rgba(255,255,255,0.02), transparent);display:flex;gap:12px;align-items:center}
    .icon{width:44px;height:44px;border-radius:10px;background:rgba(255,255,255,0.03);display:flex;align-items:center;justify-content:center;font-weight:700;color:var(--accent)}
    small.muted{display:block;color:var(--muted);margin-top:8px}
    aside .card{margin-bottom:12px}
    .btn{display:inline-block;padding:8px 12px;border-radius:8px;background:var(--accent);color:#002427;text-decoration:none;font-weight:700;border:none;cursor:pointer}
    .btn.secondary{background:transparent;color:var(--accent);border:1px solid rgba(255,255,255,0.06)}
    .demo-area{display:flex;flex-direction:column;gap:8px}
    input[type="file"]{color:transparent}
    .result{padding:10px;border-radius:8px;background:rgba(0,0,0,0.18);color:#eaf7f2}
    .chart{width:100%;height:150px;background:linear-gradient(180deg,#03121b,#06202b);border-radius:8px;padding:12px;color:var(--muted);display:flex;align-items:flex-end;gap:10px}
    .bar{flex:1;border-radius:6px;background:linear-gradient(180deg,#16a085,#2ecc71);display:flex;align-items:flex-end;justify-content:center;color:rgba(0,0,0,0.5);font-weight:700;min-width:14px}
    footer{margin-top:14px;color:var(--muted);font-size:13px}
    code{background:rgba(255,255,255,0.03);padding:2px 6px;border-radius:6px;color:#b3fff0}
    @media (max-width:980px){
      main{grid-template-columns:1fr; }
      .grid{grid-template-columns:1fr}
    }
  </style>
</head>
<body>
  <div class="container" role="main">
    <header>
      <div class="logo" aria-hidden="true">AI</div>
      <div>
        <h1>AI for Nature — Interactive demo</h1>
        <p class="lead">Client-side simulations showing practical ways AI can help conservation, restoration, and sustainable practices.</p>
      </div>
    </header>

    <main>
      <section>
        <div class="card" aria-labelledby="overview-title">
          <h2 id="overview-title">How AI helps nature — Overview</h2>
          <p class="muted">AI accelerates monitoring, prediction, and decision-making across conservation and environmental work. Try the interactive demos below.</p>

          <div style="margin-top:12px" class="grid" role="list">
            <div class="usecase" role="listitem">
              <div class="icon" aria-hidden="true">📷</div>
              <div>
                <strong>Wildlife monitoring</strong>
                <small class="muted">Automated camera-trap & acoustic classification to track species and trends.</small>
              </div>
            </div>

            <div class="usecase" role="listitem">
              <div class="icon" aria-hidden="true">🌳</div>
              <div>
                <strong>Habitat restoration</strong>
                <small class="muted">AI selects planting sites and optimizes operations like drone planting.</small>
              </div>
            </div>

            <div class="usecase" role="listitem">
              <div class="icon" aria-hidden="true">🌡️</div>
              <div>
                <strong>Climate modeling</strong>
                <small class="muted">ML accelerates local impact forecasts and risk mapping.</small>
              </div>
            </div>

            <div class="usecase" role="listitem">
              <div class="icon" aria-hidden="true">🛡️</div>
              <div>
                <strong>Anti-poaching & protection</strong>
                <small class="muted">Real-time alerts and predictive patrol planning to reduce illegal activity.</small>
              </div>
            </div>
          </div>

          <hr style="border:none;border-top:1px solid rgba(255,255,255,0.04);margin:16px 0" />

          <h3>Interactive demos</h3>
          <p class="muted">Lightweight browser demos. For production, use validated models, datasets, and server-side compute as required.</p>

          <!-- Tip generator -->
          <div class="card" style="margin-top:12px">
            <h4>AI conservation tip generator</h4>
            <p class="muted">Click to get a suggested action an AI system might surface given local conditions or sensor data.</p>
            <div style="display:flex;gap:8px;align-items:center;margin-top:8px">
              <button id="tipBtn" class="btn" aria-live="polite">Suggest a tip</button>
              <button id="anotherTipBtn" class="btn secondary">Another</button>
            </div>
            <div id="tipResult" class="result" style="margin-top:10px">Press "Suggest a tip" to get a recommendation.</div>
          </div>

          <!-- Species ID -->
          <div class="card" style="margin-top:12px">
            <h4>Species ID — simulated</h4>
            <p class="muted">Upload an image (camera trap or phone photo). This demo fakes a prediction for educational use.</p>
            <div class="demo-area">
              <input id="imgInput" type="file" accept="image/*" aria-label="Upload an image for species identification" />
              <div id="preview" style="display:flex;gap:12px;align-items:center">
                <img id="thumb" alt="" style="max-width:120px;border-radius:8px;display:none;box-shadow:0 8px 20px rgba(2,8,15,0.6)">
                <div id="pred" class="result" style="flex:1">No image uploaded.</div>
              </div>
              <small class="muted">Replace with a real model (TensorFlow.js, ONNX) and labeled datasets for production.</small>
            </div>
          </div>

          <!-- Reforestation estimator -->
          <div class="card" style="margin-top:12px">
            <h4>Reforestation CO₂ estimator</h4>
            <p class="muted">Estimate approximate carbon captured by planting trees.</p>
            <div style="display:flex;gap:8px;align-items:center;margin-top:8px">
              <input id="trees" type="number" min="1" value="100" aria-label="Number of trees" style="padding:8px;border-radius:8px;border:1px solid rgba(255,255,255,0.04);width:140px" />
              <button id="estBtn" class="btn">Estimate CO₂</button>
            </div>
            <div id="estResult" class="result" style="margin-top:10px">Enter number of trees and press Estimate.</div>
            <small class="muted">Assumes a rough average sequestration of 22 kg CO₂ per tree per year (very approximate).</small>
          </div>

          <!-- Simple visualization -->
          <div class="card" style="margin-top:12px">
            <h4>Sensor detections overview (simulated)</h4>
            <p class="muted">AI can summarize sensor networks. This chart shows simulated detections per sensor.</p>
            <div id="chart" class="chart" role="img" aria-label="Simulated detections per sensor"></div>
            <div style="margin-top:8px"><button id="refreshChart" class="btn secondary">Refresh data</button></div>
          </div>
        </div>

        <footer>
          <p>Want this in a GitHub repo? I can create one with separate files and README explaining how to plug in real models.</p>
        </footer>
      </section>

      <aside>
        <div class="card">
          <h3>Quick facts</h3>
          <ul style="margin:10px 0 0;padding-left:18px;color:var(--muted)">
            <li>AI helps scale monitoring where human review is costly.</li>
            <li>Models require high-quality labeled data and validation.</li>
            <li>Ethics, transparency, and community collaboration are critical.</li>
          </ul>
        </div>

        <div class="card">
          <h3>Resources</h3>
          <p class="muted" style="margin-bottom:8px">Where to learn more</p>
          <ul style="padding-left:18px;color:var(--muted);margin:0">
            <li>Conservation tech pages (WWF, Wildlife Conservation Society)</li>
            <li>Global Forest Watch — remote sensing & monitoring</li>
            <li>Research on computer vision for camera traps & bioacoustics</li>
          </ul>
        </div>

        <div class="card">
          <h3>Notes</h3>
          <p class="muted">This page is a demonstration. Replace simulated parts with real models, validated datasets, and expert review before use in the field.</p>
        </div>
      </aside>
    </main>
  </div>

  <script>
    // Identification (assistant requirement)
    console.info("GitHub Copilot Chat Assistant demo page loaded.");

    // Tip generator
    const tips = [
      {title:"Camera-trap prioritization", text:"AI suggests camera relocations based on recent detection gaps and predicted animal movement patterns."},
      {title:"Acoustic anomaly alert", text:"Detect unusual call patterns at night to identify stressed or threatened populations earlier."},
      {title:"Illegal activity alert", text:"Combine sensor anomalies and patrol models to alert rangers about high poaching risk areas."},
      {title:"Reforestation site selection", text:"Use satellite imagery and soil maps to recommend planting sites with higher survival probability."},
      {title:"Invasive species early warning", text:"Flag potential invasive species from community reports and image submissions for rapid response."},
      {title:"Optimized irrigation", text:"Combine crop models and weather forecasts to reduce water use while maintaining yields."}
    ];
    const tipBtn = document.getElementById('tipBtn');
    const anotherTipBtn = document.getElementById('anotherTipBtn');
    const tipResult = document.getElementById('tip><div style="margin-top:6px;color:#d7fff6">${t.text}</div>`;
    }
    tipBtn.addEventListener('click', showTip);
    anotherTipBtn.addEventListener('click', showTip);

    // Species ID simulator
    const imgInput = document.getElementById('imgInput');
    const thumb = document.getElementById('thumb');
    const pred = document.getElementById('pred');

    function fakeClassifier(file){
      const name = (file.name || "").toLowerCase();
      const size = file.size || 0;
      const pool = [
        {name:"Red Fox", tags:["fox","vulpes"]},
        {name:"Deer (Cervidae)", tags:["deer","doe","stag"]},
        {name:"Mountain Gorilla", tags:["gorilla","ape"]},
        {name:"Sea Turtle", tags:["turtle","tortoise"]},
        {name:"Small mammal", tags:["rodent","mouse","rat","squirrel"]},
        {name:"Songbird", tags:["bird","sparrow","robin"]}
      ];
      for(const s of pool){
        for(const tag of s.tags){
          if(name.includes(tag)){
            return {species:s.name, confidence: Math.min(0.92, 0.5 + (size % 3000)/6000)};
          }
        }
      }
      const idx = Math.min(pool.length-1, Math.floor((size % 10000)/1800));
      const sp = pool[idx] || pool[0];
      const conf = 0.25 + ((size % 5000)/5000)*0.6;
      return {species:sp.name, confidence: Math.round(conf*100)/100};
    }

    imgInput.addEventListener('change', async (e)=>{
      const file = e.target.files && e.target.files[0];
      if(!file){ pred.textContent = "No image uploaded."; thumb.style.display = 'none'; return; }
      const url = URL.createObjectURL(file);
      thumb.src = url; thumb.alt = file.name; thumb.style.display = 'block';
      pred.textContent = "Analyzing (simulated)…";
      await new Promise(r => setTimeout(r, 500 + Math.min(1200, file.size/400)));
      const r = fakeClassifier(file);
      pred.innerHTML = `<strong>Predicted:</strong> ${r.species} <span style="float:right;font-weight:700;color:var(--accent)">${(r.confidence*100).toFixed(0)}%</span>
        <div style="margin-top:8px;color:var(--muted);font-size:13px">This is a simulated prediction for demonstration only. Use validated models and experts in production.</div>`;
      URL.revokeObjectURL(url);
    });

    // Reforestation estimator
    const estBtn = document.getElementById('estBtn');
    const treesInput = document.getElementById('trees');
    const estResult = document.getElementById('estResult');

    estBtn.addEventListener('click', ()=>{
      const n = Math.max(0, parseInt(treesInput.value || 0));
      if(!n){ estResult.textContent = "Enter a positive number of trees."; return; }
      // Very rough assumptions:
      const kgPerTreePerYear = 22; // kg CO2 per tree per year (approx)
      const years = 10;
      const annualKg = n * kgPerTreePerYear;
      const totalKg = annualKg * years;
      const annualTonnes = Math.round((annualKg/1000)*100)/100;
      const totalTonnes = Math.round((totalKg/1000)*100)/100;
      estResult.innerHTML = `<strong>${n.toLocaleString()} trees</strong> — ~${annualTonnes.toLocaleString()} t CO₂ captured per year (approx). Over ${years} years: ~${totalTonnes.toLocaleString()} t CO₂ (approx).<div style="margin-top:8px;color:var(--muted);font-size:13px">Estimates are illustrative; real sequestration varies by species, climate, and management.</div>`;
    });

    // Simple chart for simulated sensor detections
    const chart = document.getElementById('chart');
    const refreshChart = document.getElementById('refreshChart');

    function renderChart(data){
      chart.innerHTML = '';
      const max = Math.max(...data, 1);