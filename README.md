<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Fiberhome Strategic Command Center</title>

<link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Mono:wght@400;600&family=IBM+Plex+Sans:wght@300;400;600;700&display=swap" rel="stylesheet">

<style>
/* ==========================================================================
   BASE & RESET
   ========================================================================== */
* { margin: 0; padding: 0; box-sizing: border-box; }
html { scroll-behavior: smooth; }
body { 
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif; 
    line-height: 1.6; 
    color: #333; 
    background: #f4f7f6; 
}

.main-container { max-width: 1200px; margin: 0 auto; padding: 10px; }

/* ==========================================================================
   HEADER & TABS
   ========================================================================== */
.global-header {
    background: #003366;
    color: white;
    padding: 15px 20px 0 20px;
    border-radius: 8px 8px 0 0;
    margin-bottom: 0;
    display: flex;
    flex-direction: column;
}

.header-top {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 15px;
}

.header-top h1 { font-size: 1.5rem; margin: 0; color: white; }
.header-top p { margin: 0; font-size: 0.9em; opacity: 0.8; }

@media (max-width: 768px) {
    .header-top { flex-direction: column; text-align: center; gap: 10px; }
}

/* Tab Buttons */
.tab-container {
    display: flex;
    gap: 5px;
    overflow-x: auto;
}
.tab-btn {
    background: rgba(255,255,255,0.1);
    color: white;
    border: none;
    padding: 12px 20px;
    border-radius: 8px 8px 0 0;
    cursor: pointer;
    font-weight: 600;
    font-size: 0.95em;
    transition: all 0.3s ease;
    white-space: nowrap;
}
.tab-btn:hover { background: rgba(255,255,255,0.2); }
.tab-btn.active {
    background: #f4f7f6;
    color: #003366;
}

/* Tab Content */
.tab-content {
    display: none;
    animation: fadeIn 0.4s;
    padding-top: 15px;
}
.tab-content.active { display: block; }

@keyframes fadeIn { from { opacity: 0; transform: translateY(5px); } to { opacity: 1; transform: translateY(0); } }

/* ==========================================================================
   ESTILOS GERAIS DE PAINÉIS
   ========================================================================== */
.kpi-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 10px; margin-bottom: 15px; }
@media(min-width: 768px) { .kpi-grid { grid-template-columns: repeat(4, 1fr); } }
.kpi-card { background: white; padding: 12px; border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.05); text-align: center; }
.kpi-title { font-size: 0.75rem; color: #777; font-weight: 600; text-transform: uppercase; }
.kpi-value { font-size: 1.4rem; font-weight: bold; color: #003366; }

.grid-main { display: grid; grid-template-columns: 1fr; gap: 15px; }
@media(min-width: 1024px) { .grid-main { grid-template-columns: 2fr 1fr; } }
.grid-single { display: grid; grid-template-columns: 1fr; gap: 15px; } 

.panel { background: white; padding: 15px; border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.05); overflow-x: auto; }

h2.section-title { border-bottom: 2px solid #eee; padding-bottom: 8px; color: #003366; font-size: 1.2rem; margin-top: 0; }
h3.sub-title { font-size: 1.05rem; margin-top: 20px; color: #333; }

.status-ok{color:#27ae60;font-weight:bold}
.status-warning{color:#f39c12;font-weight:bold}
.status-alert{color:#e74c3c;font-weight:bold}
.status-pending{color:#7f8c8d;font-weight:bold}

.priority-high{color:#e74c3c;font-weight:bold}
.priority-medium{color:#f39c12;font-weight:bold}
.priority-low{color:#27ae60;font-weight:bold}

.dash-table { width: 100%; border-collapse: collapse; font-size: 0.85em; }
.dash-table th, .dash-table td { padding: 8px 6px; border-bottom: 1px solid #eee; text-align: left; }
.dash-table th { background: #f8f9fa; color: #555; }
.dash-table tbody tr { transition: background-color 0.2s ease; cursor: pointer; }
.dash-table tbody tr:hover { background-color: #e6f0fa; }

/* ESTILOS DA MATRIZ DE COBERTURA (TAGS) */
.coverage-matrix { display: flex; flex-direction: column; gap: 8px; width: 100%; margin-top: 10px; }
.region-row { display: flex; align-items: center; justify-content: space-between; background: #fff; padding: 8px 10px; border-radius: 6px; border: 1px solid #e0e0e0; box-shadow: 0 1px 2px rgba(0,0,0,0.02); }
.region-name { font-size: 0.75em; font-weight: bold; color: #888; text-transform: uppercase; width: 85px; flex-shrink: 0; }
.uf-group { display: flex; gap: 5px; flex-wrap: wrap; justify-content: flex-end; flex: 1; }
.uf-badge { 
    background: #e9ecef; color: #adb5bd; font-size: 0.75em; padding: 4px 7px; 
    border-radius: 4px; font-weight: bold; transition: all 0.2s ease; 
    cursor: default; user-select: none;
}
.uf-badge.active { 
    background: #003366; color: #fff; transform: scale(1.1); 
    box-shadow: 0 2px 4px rgba(0,0,0,0.2); z-index: 2; position: relative;
}

.progress-bg { background: #e0e0e0; height: 6px; border-radius: 3px; margin: 4px 0; width: 100px; }
.progress-bar { background: #003366; height: 100%; border-radius: 3px; }
.progress-text { font-size: 0.75em; color: #777; }

.task-btn { background: #003366; color: white; border: none; padding: 4px 8px; border-radius: 4px; font-size: 0.7em; cursor: pointer; }
.task-btn:hover { background: #0056b3; }

.alert-box { background: #fff4f4; border-left: 5px solid #e74c3c; padding: 10px; border-radius: 6px; margin-bottom: 10px; font-size: 0.85em; }
.task-link { color: #e74c3c; text-decoration: none; font-weight: bold; border-bottom: 1px dashed #e74c3c; cursor: pointer; }

/* Tabela de Benchmark */
.benchmark-table { font-size: 0.9em; width: 100%; border-collapse: collapse; white-space: nowrap; margin-top: 15px; }
.benchmark-table th, .benchmark-table td { padding: 10px 12px; border-bottom: 1px solid #eee; text-align: left; }
.benchmark-table th { background: #f8f9fa; color: #003366; font-weight: bold; }
.benchmark-table tbody tr:hover { background-color: #f1f5f9; }

/* ==========================================================================
   ESTILOS DO CALCULATOR (Aba 3)
   ========================================================================== */
.calc-theme {
    --bg: #0d1117; --surface: #161b22; --border: #30363d; --accent: #00d4aa; --accent2: #0080ff;
    --text: #e6edf3; --text-muted: #8b949e; --warn: #f59e0b;
    background: var(--bg); color: var(--text); font-family: 'IBM Plex Sans', sans-serif;
    padding: 30px 20px; border-radius: 8px;
    background-image: radial-gradient(ellipse at 20% 10%, rgba(0,212,170,0.06) 0%, transparent 50%), radial-gradient(ellipse at 80% 80%, rgba(0,128,255,0.06) 0%, transparent 50%);
}
.calc-wrapper { max-width: 860px; margin: 0 auto; }
.calc-theme header { display: flex; justify-content: space-between; align-items: flex-start; margin-bottom: 32px; flex-wrap: wrap; gap: 12px; }
.calc-theme .title-block h1 { font-family: 'IBM Plex Mono', monospace; font-size: 1.5rem; color: var(--accent); margin-bottom: 0; }
.calc-theme .title-block p { color: var(--text-muted); font-size: 0.85rem; margin-top: 4px; }
.calc-theme .lang-toggle { display: flex; background: var(--surface); border: 1px solid var(--border); border-radius: 8px; overflow: hidden; }
.calc-theme .lang-btn { padding: 8px 18px; font-family: 'IBM Plex Mono', monospace; font-size: 0.8rem; font-weight: 600; cursor: pointer; border: none; background: transparent; color: var(--text-muted); transition: all 0.2s; letter-spacing: 1px; }
.calc-theme .lang-btn.active { background: var(--accent); color: #000; }
.calc-theme .card { background: var(--surface); border: 1px solid var(--border); border-radius: 12px; padding: 28px; margin-bottom: 20px; }
.calc-theme .card-title { font-family: 'IBM Plex Mono', monospace; font-size: 0.75rem; letter-spacing: 2px; color: var(--text-muted); text-transform: uppercase; margin-bottom: 20px; padding-bottom: 12px; border-bottom: 1px solid var(--border); }
.calc-theme .grid { display: grid; grid-template-columns: 1fr 1fr; gap: 18px; }
@media (max-width: 560px) { .calc-theme .grid { grid-template-columns: 1fr; } }
.calc-theme .field label { display: block; font-size: 0.78rem; font-weight: 600; color: var(--text-muted); margin-bottom: 7px; letter-spacing: 0.3px; }
.calc-theme .field input, .calc-theme .field select { width: 100%; padding: 11px 14px; background: var(--bg); border: 1px solid var(--border); border-radius: 8px; color: var(--text); font-family: 'IBM Plex Sans', sans-serif; font-size: 0.95rem; transition: border-color 0.2s; appearance: none; }
.calc-theme .field input:focus, .calc-theme .field select:focus { outline: none; border-color: var(--accent); box-shadow: 0 0 0 3px rgba(0,212,170,0.1); }
.calc-theme .field select { background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='12' viewBox='0 0 12 12'%3E%3Cpath fill='%238b949e' d='M6 8L1 3h10z'/%3E%3C/svg%3E"); background-repeat: no-repeat; background-position: right 12px center; padding-right: 36px; cursor: pointer; }
.calc-theme .badge-auto { display: inline-block; font-size: 0.6rem; font-family: 'IBM Plex Mono', monospace; padding: 2px 6px; border-radius: 4px; background: rgba(0,212,170,0.15); color: var(--accent); font-weight: 700; letter-spacing: 1px; margin-left: 6px; vertical-align: middle; }
.calc-theme .info-display { width: 100%; padding: 11px 14px; background: rgba(0,212,170,0.05); border: 1px solid rgba(0,212,170,0.2); border-radius: 8px; color: var(--accent); font-family: 'IBM Plex Mono', monospace; font-size: 0.95rem; font-weight: 600; }
.calc-theme .btn-calc { width: 100%; padding: 16px; background: linear-gradient(135deg, var(--accent), var(--accent2)); color: #000; border: none; border-radius: 10px; font-family: 'IBM Plex Mono', monospace; font-size: 1rem; font-weight: 700; letter-spacing: 1px; cursor: pointer; transition: all 0.2s; margin-top: 8px; }
.calc-theme .btn-calc:hover { opacity: 0.9; transform: translateY(-1px); box-shadow: 0 6px 20px rgba(0,212,170,0.25); }
.calc-theme .results { display: none; animation: fadeInCalc 0.4s ease; }
@keyframes fadeInCalc { from { opacity: 0; transform: translateY(8px); } to { opacity: 1; transform: translateY(0); } }
.calc-theme .result-row { display: flex; justify-content: space-between; align-items: center; padding: 12px 0; border-bottom: 1px solid var(--border); font-size: 0.95rem; }
.calc-theme .result-row:last-child { border-bottom: none; }
.calc-theme .result-label { color: var(--text-muted); }
.calc-theme .result-value { font-family: 'IBM Plex Mono', monospace; font-weight: 600; color: var(--text); }
.calc-theme .result-row.total { margin-top: 8px; padding: 16px 20px; background: linear-gradient(135deg, rgba(0,212,170,0.08), rgba(0,128,255,0.08)); border: 1px solid rgba(0,212,170,0.3); border-radius: 10px; }
.calc-theme .result-row.total .result-label { font-weight: 700; color: var(--text); font-size: 1rem; }
.calc-theme .result-row.total .result-value { font-size: 1.35rem; color: var(--accent); }
.calc-theme .difal-block { display: none; margin: 4px 0 8px 0; padding: 12px 16px; background: rgba(245,158,11,0.07); border: 1px solid rgba(245,158,11,0.25); border-radius: 8px; font-size: 0.83rem; color: var(--warn); }
.calc-theme .difal-block strong { display: block; margin-bottom: 3px; font-size: 0.85rem; }
.calc-theme .breakdown-bar { margin: 20px 0 0 0; border-radius: 6px; overflow: hidden; height: 10px; display: flex; gap: 2px; }
.calc-theme .bar-seg { height: 100%; transition: width 0.6s ease; border-radius: 3px; }
.calc-theme .legend { display: flex; flex-wrap: wrap; gap: 12px; margin: 14px 0 8px 0; }
.calc-theme .legend-item { display: flex; align-items: center; gap: 6px; font-size: 0.78rem; color: var(--text-muted); }
.calc-theme .legend-dot { width: 10px; height: 10px; border-radius: 2px; flex-shrink: 0; }
.calc-theme .info-note { font-size: 0.78rem; color: var(--text-muted); font-style: italic; margin-top: 14px; padding-top: 12px; border-top: 1px solid var(--border); }

/* ==========================================================================
   MODALS GERAIS E INTELIGÊNCIA DE CONTA
   ========================================================================== */
.modal { display: none; position: fixed; z-index: 9999; left: 0; top: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.5); }
.modal-content { background: white; margin: 10vh auto; padding: 25px; border-radius: 8px; width: 90%; max-width: 400px; position: relative; max-height: 80vh; overflow-y: auto;}
.modal-content.wide-modal { max-width: 650px; }
.close { position: absolute; right: 15px; top: 15px; cursor: pointer; font-size: 1.2em; font-weight: bold; color: #666; }
.modal-table { width: 100%; border-collapse: collapse; font-size: 0.85em; margin-bottom: 15px; }
.modal-table th, .modal-table td { padding: 8px; border-bottom: 1px solid #eee; text-align: left; }
.modal-table th { background: #f8f9fa; color: #333; font-weight: bold; }
</style>
</head>
<body>

<div class="main-container">

    <div class="global-header">
        <div class="header-top">
            <div>
                <h1>Fiberhome Strategic Command</h1>
                <p>Brazil Operation | March 2026</p>
            </div>
            <div style="text-align: right;">
                <strong style="font-size: 1.1em;">Denis Fernandes</strong><br>
                <span style="font-size: 0.8em; opacity: 0.8; background:#f39c12; padding:2px 6px; border-radius:4px; font-weight:bold;">Head of Channels</span>
            </div>
        </div>
        
        <div class="tab-container">
            <button class="tab-btn active" onclick="openTab(event, 'DashboardTab')">📊 Executive Dashboard</button>
            <button class="tab-btn" onclick="openTab(event, 'BenchmarkTab')">📈 Benchmark Prices</button>
            <button class="tab-btn" onclick="openTab(event, 'CalcTab')">🧮 Landed Cost</button>
        </div>
    </div>

    <div id="DashboardTab" class="tab-content active">
        
        <div class="kpi-grid">
            <div class="kpi-card"><div class="kpi-title">Pipeline Value</div><div class="kpi-value">$380K</div></div>
            <div class="kpi-card"><div class="kpi-title">Deals Approved</div><div class="kpi-value">1</div></div>
            <div class="kpi-card"><div class="kpi-title">In Progress</div><div class="kpi-value">4</div></div>
            <div class="kpi-card"><div class="kpi-title">Deals at Risk</div><div class="kpi-value">3</div></div>
        </div>

        <div class="grid-main">
            <div class="panel">
                <h2 class="section-title">Negotiation Summary</h2>
                
                <div style="overflow-x: auto; margin-top: 15px;">
                    <table class="dash-table">
                        <thead>
                            <tr>
                                <th>Partner</th>
                                <th>Status</th>
                                <th>Priority</th>
                                <th>Target ($3M/year)</th>
                                <th>Next Action</th>
                                <th>Tasks</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr onmouseenter="highlightMap('prexx')" onmouseleave="resetMap()">
                                <td>Prexx Group</td>
                                <td class="status-ok">Approved</td>
                                <td class="priority-low">Low</td>
                                <td><strong>$380K</strong><div class="progress-bg"><div class="progress-bar" style="width: 12.6%;"></div></div><span class="progress-text">of $3.0M</span></td>
                                <td>P.O. antecipated and Small distributor process</td>
                                <td><button class="task-btn" onclick="openModal('t1')" style="background-color: #f39c12;">View Data</button></td>
                            </tr>
                            <tr onmouseenter="highlightMap('chub')" onmouseleave="resetMap()">
                                <td>C-Hub (Toledo)</td>
                                <td class="status-warning">In Progress</td>
                                <td class="priority-high">High</td>
                                <td><strong>$0.00</strong><div class="progress-bg"><div class="progress-bar" style="width: 0%;"></div></div><span class="progress-text">of $3.0M</span></td>
                                <td>HQ verify financial report and give a table price suggestion</td>
                                <td><button class="task-btn" onclick="openModal('t2')" style="background-color: #f39c12;">View Data</button></td>
                            </tr>
                            <tr onmouseenter="highlightMap('route66')" onmouseleave="resetMap()">
                                <td>Route66</td>
                                <td class="status-warning">In Progress</td>
                                <td class="priority-high">High</td>
                                <td><strong>$0.00</strong><div class="progress-bg"><div class="progress-bar" style="width: 0%;"></div></div><span class="progress-text">of $3.0M</span></td>
                                <td>Presencial visit</td>
                                <td><button class="task-btn" onclick="openModal('t5')" style="background-color: #f39c12;">View Data</button></td>
                            </tr>
                            <tr onmouseenter="highlightMap('nextcable')" onmouseleave="resetMap()">
                                <td>Next Cable</td>
                                <td class="status-warning">In Progress</td>
                                <td class="priority-high">High</td>
                                <td><strong>$0.00</strong><div class="progress-bg"><div class="progress-bar" style="width: 0%;"></div></div><span class="progress-text">of $3.0M</span></td>
                                <td>Huawei Pricing (Rodrigo) & Fin. Report Analysis (Zachary)</td>
                                <td><button class="task-btn" onclick="openModal('t3')" style="background-color: #f39c12;">View Tasks</button></td>
                            </tr>
                            <tr onmouseenter="highlightMap('gw')" onmouseleave="resetMap()">
                                <td>GW</td>
                                <td class="status-warning">In Progress</td>
                                <td class="priority-high">High</td>
                                <td><strong>$0.00</strong><div class="progress-bg"><div class="progress-bar" style="width: 0%;"></div></div><span class="progress-text">of $3.0M</span></td>
                                <td>Portfolio/Docs Delivery & Fin. Report Alignment</td>
                                <td><button class="task-btn" onclick="openModal('t6')" style="background-color: #f39c12;">View Tasks</button></td>
                            </tr>
                            <tr onmouseenter="highlightMap('premium')" onmouseleave="resetMap()">
                                <td>Premium</td>
                                <td class="status-warning">In Progress</td>
                                <td class="priority-low">Low</td>
                                <td><strong>$0.00</strong><div class="progress-bg"><div class="progress-bar" style="width: 0%;"></div></div><span class="progress-text">of $3.0M</span></td>
                                <td>Evaluate operational capacity</td>
                                <td><button class="task-btn" onclick="openModal('t12')" style="background-color: #f39c12;">View Data</button></td>
                            </tr>
                            <tr onmouseenter="highlightMap('televit')" onmouseleave="resetMap()">
                                <td>Televit</td>
                                <td class="status-alert">Delayed</td>
                                <td class="priority-high">High</td>
                                <td><strong>$0.00</strong><div class="progress-bg"><div class="progress-bar" style="width: 0%;"></div></div><span class="progress-text">of $3.0M</span></td>
                                <td>Alliance Negotiations (CEO) & Target Pricing (CFO)</td>
                                <td><button class="task-btn" onclick="openModal('t4')" style="background-color: #e74c3c;">View Tasks</button></td>
                            </tr>
                            <tr onmouseenter="highlightMap('suprinordeste')" onmouseleave="resetMap()">
                                <td>Suprinordeste</td>
                                <td class="status-alert">Delayed</td>
                                <td class="priority-medium">Medium</td>
                                <td><strong>$0.00</strong><div class="progress-bg"><div class="progress-bar" style="width: 0%;"></div></div><span class="progress-text">of $3.0M</span></td>
                                <td>Receive financial reports</td>
                                <td><button class="task-btn" onclick="openModal('t7')">Open</button></td>
                            </tr>
                            <tr onmouseenter="highlightMap('oiw')" onmouseleave="resetMap()">
                                <td>OiW</td>
                                <td class="status-alert">Delayed</td>
                                <td class="priority-high">High</td>
                                <td><strong>$0.00</strong><div class="progress-bg"><div class="progress-bar" style="width: 0%;"></div></div><span class="progress-text">of $3.0M</span></td>
                                <td>Verify suggested prices and signature contract</td>
                                <td><button class="task-btn" onclick="openModal('t8')">Open</button></td>
                            </tr>
                            <tr onmouseenter="highlightMap('centry')" onmouseleave="resetMap()">
                                <td>Centry Group</td>
                                <td class="status-pending">On hold</td>
                                <td class="priority-medium">Medium</td>
                                <td><strong>$0.00</strong><div class="progress-bg"><div class="progress-bar" style="width: 0%;"></div></div><span class="progress-text">of $3.0M</span></td>
                                <td>Financial reports</td>
                                <td><button class="task-btn" onclick="openModal('t9')">Open</button></td>
                            </tr>
                            <tr onmouseenter="highlightMap('sheroline')" onmouseleave="resetMap()">
                                <td>Sheroline</td>
                                <td class="status-pending">On hold</td>
                                <td class="priority-low">Low</td>
                                <td><strong>$0.00</strong><div class="progress-bg"><div class="progress-bar" style="width: 0%;"></div></div><span class="progress-text">of $3.0M</span></td>
                                <td>Schedule meeting</td>
                                <td><button class="task-btn" onclick="openModal('t10')">Open</button></td>
                            </tr>
                            <tr onmouseenter="highlightMap('think')" onmouseleave="resetMap()">
                                <td>Think Technology</td>
                                <td class="status-pending">On hold</td>
                                <td class="priority-low">Low</td>
                                <td><strong>$0.00</strong><div class="progress-bg"><div class="progress-bar" style="width: 0%;"></div></div><span class="progress-text">of $3.0M</span></td>
                                <td>Broadband/ODN Feasibility & Portfolio Delivery</td>
                                <td><button class="task-btn" onclick="openModal('t11')" style="background-color: #f39c12;">View Tasks</button></td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>

            <div class="panel">
                <h2 class="section-title">Critical Alerts</h2>
                <div class="alert-box">
                    <strong>SDE Rio Risk</strong><br>
                    Possible migration to TP-Link. Shield via Prexx.
                </div>
                <div class="alert-box">
                    <strong><a class="task-link" onclick="openModal('alert-up2tech')">Up2Tech Compliance ⚠️</a></strong><br>
                    Possible tax irregularities impacting partnerships. (Click for details)
                </div>

                <h3 class="sub-title">Regional Presence</h3>
                <p style="font-size: 0.8em; color: #777; margin-bottom: 10px;">Hover over a partner in the Negotiation Summary to highlight their operating footprint.</p>
                
                <div class="coverage-matrix">
                    <div class="region-row">
                        <span class="region-name">North</span>
                        <div class="uf-group">
                            <span id="uf-AC" class="uf-badge">AC</span><span id="uf-AP" class="uf-badge">AP</span><span id="uf-AM" class="uf-badge">AM</span><span id="uf-PA" class="uf-badge">PA</span><span id="uf-RO" class="uf-badge">RO</span><span id="uf-RR" class="uf-badge">RR</span><span id="uf-TO" class="uf-badge">TO</span>
                        </div>
                    </div>
                    <div class="region-row">
                        <span class="region-name">Northeast</span>
                        <div class="uf-group">
                            <span id="uf-AL" class="uf-badge">AL</span><span id="uf-BA" class="uf-badge">BA</span><span id="uf-CE" class="uf-badge">CE</span><span id="uf-MA" class="uf-badge">MA</span><span id="uf-PB" class="uf-badge">PB</span><span id="uf-PE" class="uf-badge">PE</span><span id="uf-PI" class="uf-badge">PI</span><span id="uf-RN" class="uf-badge">RN</span><span id="uf-SE" class="uf-badge">SE</span>
                        </div>
                    </div>
                    <div class="region-row">
                        <span class="region-name">Midle-Contry</span>
                        <div class="uf-group">
                            <span id="uf-DF" class="uf-badge">DF</span><span id="uf-GO" class="uf-badge">GO</span><span id="uf-MT" class="uf-badge">MT</span><span id="uf-MS" class="uf-badge">MS</span>
                        </div>
                    </div>
                    <div class="region-row">
                        <span class="region-name">Southeast</span>
                        <div class="uf-group">
                            <span id="uf-ES" class="uf-badge">ES</span><span id="uf-MG" class="uf-badge">MG</span><span id="uf-RJ" class="uf-badge">RJ</span><span id="uf-SP" class="uf-badge">SP</span>
                        </div>
                    </div>
                    <div class="region-row">
                        <span class="region-name">South</span>
                        <div class="uf-group">
                            <span id="uf-PR" class="uf-badge">PR</span><span id="uf-RS" class="uf-badge">RS</span><span id="uf-SC" class="uf-badge">SC</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <div id="BenchmarkTab" class="tab-content">
        <div class="grid-single">
            <div class="panel">
                <h2 class="section-title" style="border-bottom:none; margin-bottom: 0;">Market Benchmarking (Prices)</h2>
                <p style="color: #666; margin-bottom: 20px;">Live comparison of equipment and material prices across key distributors in the Brazilian market.</p>
                
                <div style="overflow-x: auto;">
                    <table class="benchmark-table">
                        <thead>
                            <tr><th>Product</th><th>Price</th><th>Supplier</th><th>Market</th><th>Date</th></tr>
                        </thead>
                        <tbody>
                            <tr><td>Huawei ONTAX300</td><td>US$ 24.50</td><td>Next Cable</td><td>FOB</td><td>11/03/2026</td></tr>
                            <tr><td>Fiber (Raw)</td><td>US$ 250/kg</td><td>Next Cable</td><td>FOB</td><td>11/03/2026</td></tr>
                            <tr><td>Huawei ONTAX300</td><td>R$ 177,00</td><td>Prime 8</td><td>DDP</td><td>11/03/2026</td></tr>
                            <tr><td>Huawei ONTAX300</td><td>R$ 250,56</td><td>WDC</td><td>DDP_ISP</td><td>11/03/2026</td></tr>
                            <tr><td>Nokia ONTAX3000</td><td>R$ 242,82</td><td>WDC</td><td>DDP_ISP</td><td>11/03/2026</td></tr>
                            <tr><td>Huawei ONTAX300</td><td>R$ 241,90</td><td>OiW</td><td>DDP_ISP</td><td>11/03/2026</td></tr>
                            <tr><td>TP-Link ONTAX300</td><td>R$ 235,90</td><td>OiW</td><td>DDP_ISP</td><td>11/03/2026</td></tr>
                            <tr><td>Huawei ONTAX300</td><td>R$ 179,00</td><td>Up2Tech</td><td>DDP</td><td>11/03/2026</td></tr>
                        </tbody>
                    </table>
                </div>
            </div>
        </div>
    </div>

    <div id="CalcTab" class="tab-content">
        <div class="calc-theme">
            <div class="calc-wrapper">
                <header>
                    <div class="title-block">
                        <h1 data-pt="Landed Cost Calculator" data-en="Landed Cost Calculator">Landed Cost Calculator</h1>
                        <p data-pt="Simulador de importação — Fiberhome - by Denis Fernandes" data-en="Import simulator — Fiberhome - by Denis Fernandes">Simulador de importação — Fiberhome - by Denis Fernandes</p>
                    </div>
                    <div class="lang-toggle">
                        <button class="lang-btn active" onclick="setLang('pt')">PT</button>
                        <button class="lang-btn" onclick="setLang('en')">EN</button>
                    </div>
                </header>
                <div class="card">
                    <div class="card-title" data-pt="Parâmetros de Entrada" data-en="Input Parameters">Parâmetros de Entrada</div>
                    <div class="grid">
                        <div class="field">
                            <label data-pt="Produto" data-en="Product">Produto</label>
                            <select id="produto" onchange="onProdutoChange()"></select>
                        </div>
                        <div class="field">
                            <label>IPI<span class="badge-auto" data-pt="AUTO" data-en="AUTO">AUTO</span></label>
                            <div class="info-display" id="ipiDisplay">—</div>
                        </div>
                        <div class="field">
                            <label data-pt="Preço FOB (USD)" data-en="FOB Price (USD)">Preço FOB (USD)</label>
                            <input type="number" id="fob" placeholder="Ex: 25.00" step="0.01" min="0">
                        </div>
                        <div class="field">
                            <label data-pt="Câmbio (USD → BRL)" data-en="Exchange Rate (USD → BRL)">Câmbio (USD → BRL)</label>
                            <input type="number" id="cambio" value="5.75" step="0.01" min="0">
                        </div>
                        <div class="field">
                            <label data-pt="Frete + Seguro (USD)" data-en="Freight + Insurance (USD)">Frete + Seguro (USD)</label>
                            <input type="number" id="frete" value="2.00" step="0.10" min="0">
                        </div>
                        <div class="field">
                            <label data-pt="Estado Origem" data-en="Origin State">Estado Origem</label>
                            <select id="estadoOrigem" onchange="onEstadoChange()"></select>
                        </div>
                        <div class="field">
                            <label data-pt="Estado Destino" data-en="Destination State">Estado Destino</label>
                            <select id="estadoDestino" onchange="onEstadoChange()"></select>
                        </div>
                        <div class="field" style="grid-column: 1 / -1;">
                            <label>DIFAL B2B<span class="badge-auto" data-pt="AUTO" data-en="AUTO">AUTO</span></label>
                            <div class="difal-block" id="difalInfo">
                                <strong id="difalTitle">—</strong><span id="difalDesc">—</span>
                            </div>
                            <div class="info-display" id="difalDisplay">—</div>
                        </div>
                    </div>
                    <button class="btn-calc" onclick="calcular()" data-pt="▶ CALCULAR CUSTO FINAL" data-en="▶ CALCULATE FINAL COST">▶ CALCULAR CUSTO FINAL</button>
                </div>
                <div class="card results" id="resultado">
                    <div class="card-title" data-pt="Composição do Custo Final" data-en="Final Cost Breakdown">Composição do Custo Final</div>
                    <div class="breakdown-bar" id="breakdownBar"></div>
                    <div class="legend" id="breakdownLegend"></div>
                    <div class="result-row">
                        <span class="result-label" data-pt="Valor Aduaneiro — CIF (BRL)" data-en="Customs Value — CIF (BRL)">Valor Aduaneiro — CIF (BRL)</span>
                        <span class="result-value" id="resCif"></span>
                    </div>
                    <div class="result-row">
                        <span class="result-label" data-pt="Imposto de Importação (II)" data-en="Import Tax (II)">Imposto de Importação (II)</span>
                        <span class="result-value" id="resIi"></span>
                    </div>
                    <div class="result-row">
                        <span class="result-label" id="resIpiLabel" data-pt="IPI" data-en="IPI">IPI</span>
                        <span class="result-value" id="resIpi"></span>
                    </div>
                    <div class="result-row">
                        <span class="result-label" data-pt="PIS/COFINS Importação (~11,75%)" data-en="PIS/COFINS Import (~11.75%)">PIS/COFINS Importação (~11,75%)</span>
                        <span class="result-value" id="resPisCofins"></span>
                    </div>
                    <div class="result-row">
                        <span class="result-label" data-pt='ICMS (cálculo "por dentro")' data-en='ICMS ("gross-up" calculation)'>ICMS (cálculo "por dentro")</span>
                        <span class="result-value" id="resIcms"></span>
                    </div>
                    <div class="result-row" id="rowDifal" style="display:none;">
                        <span class="result-label" data-pt="DIFAL B2B" data-en="DIFAL B2B">DIFAL B2B</span>
                        <span class="result-value" id="resDifal"></span>
                    </div>
                    <div class="result-row">
                        <span class="result-label" data-pt="Taxas (AFRMM / Siscomex / Despacho)" data-en="Fees (AFRMM / Siscomex / Customs)">Taxas (AFRMM / Siscomex / Despacho)</span>
                        <span class="result-value" id="resTaxas"></span>
                    </div>
                    <div class="result-row total">
                        <span class="result-label" data-pt="CUSTO FINAL UNITÁRIO" data-en="UNIT LANDED COST">CUSTO FINAL UNITÁRIO</span>
                        <span class="result-value" id="resTotal"></span>
                    </div>
                    <p class="info-note" data-pt="* Cálculo simplificado para fins de estimativa comercial. DIFAL B2B conforme EC 87/2015, origem SP (ICMS 12%)." data-en="* Simplified calculation for commercial estimation. DIFAL B2B per EC 87/2015, origin SP (ICMS 12%).">
                        * Cálculo simplificado para fins de estimativa comercial. DIFAL B2B conforme EC 87/2015, origem SP (ICMS 12%).
                    </p>
                </div>
            </div>
        </div>
    </div>

</div>

<div id="t3" class="modal">
    <div class="modal-content wide-modal">
        <span class="close" onclick="closeModal('t3')">X</span>
        <h4>Next Cable - Pending Tasks</h4>
        <ul style="font-size: 0.85em; margin-bottom: 15px; line-height: 1.8;">
            <li><b style="color: #e74c3c;">[HIGH PRIORITY]</b> <b>Huawei Pricing Update:</b> Responsible: Rodrigo. <span style="background: #fff4f4; padding: 2px 4px; border-radius: 3px;">Due: TODAY</span>.</li>
            <li><b>Financial Report Analysis:</b> Zachary (FH) has already received and analyzed the report.</li>
            <li><b>Technical Alignment:</b> Technical meeting scheduled to finalize support process and registration details.</li>
        </ul>
        <h5 style="margin-top: 10px; margin-bottom: 5px;">Market Context</h5>
        <p style="font-size: 0.8em;">Current benchmarking: Huawei ONTAX300 at US$ 24.50 (FOB) and Raw Fiber at US$ 250/kg.</p>
    </div>
</div>

<div id="t4" class="modal">
    <div class="modal-content wide-modal">
        <span class="close" onclick="closeModal('t4')">X</span>
        <h4>Televit - Strategic Alliance Plan</h4>
        <ul style="font-size: 0.85em; margin-bottom: 15px; line-height: 1.8;">
            <li><b>Alliance Lead:</b> Tarcísio (CEO) will lead negotiations with Central Brasil and H2I to expedite the potential alliance and finalize with Fiberhome.</li>
            <li><b>Target Pricing & Volumes:</b> Tarciso Filho (CFO) to provide last year's sales volumes for GPON and ODN.</li>
            <li><b>Historical Mapping:</b> Denis (Fiberhome) will provide Intelbras historical sales data for the Northeast region.</li>
        </ul>
    </div>
</div>

<div id="t6" class="modal">
    <div class="modal-content wide-modal">
        <span class="close" onclick="closeModal('t6')">X</span>
        <h4>GW - Negotiation Checklist</h4>
        <ul style="font-size: 0.85em; margin-bottom: 15px; line-height: 1.8;">
            <li><b>Documentation:</b> FiberHome to send full portfolio and documentation for ODN/GPON pricing studies.</li>
            <li><b>Financial Credit:</b> Gilmar (GW) to forward financial report to define limits and installment conditions.</li>
            <li><b>Strategic Alignment:</b> Both parties must align on "Target Price" and the first batch quantity.</li>
        </ul>
    </div>
</div>

<div id="t11" class="modal">
    <div class="modal-content wide-modal">
        <span class="close" onclick="closeModal('t11')">X</span>
        <h4>Think Technology - Partnership Expansion</h4>
        <ul style="font-size: 0.85em; margin-bottom: 15px; line-height: 1.8;">
            <li><b>Product Portfolio:</b> FiberHome to send complete portfolio for Broadband and ODN (Washin Fujikura) lines.</li>
            <li><b>Feasibility Analysis:</b> FiberHome to provide "target pricing" ideas for feasibility assessment.</li>
            <li><b>Final Costing:</b> Kennedy and Valmir (Tink) will evaluate landed costs based on the upcoming pricing spreadsheet.</li>
        </ul>
    </div>
</div>

<div id="t1" class="modal">
    <div class="modal-content wide-modal">
        <span class="close" onclick="closeModal('t1')">X</span>
        <h4>Prexx Group - Strategic Alignment</h4>
        <p style="font-size: 0.85em;">Concerns regarding channel conflict and Q2 P.O. anticipation.</p>
    </div>
</div>

<div id="t2" class="modal">
    <div class="modal-content wide-modal">
        <span class="close" onclick="closeModal('t2')">X</span>
        <h4>C-Hub (Toledo) - Account Intelligence</h4>
        <p style="font-size: 0.85em;">40c container proposal sent. Waiting for start.</p>
    </div>
</div>

<div id="t5" class="modal">
    <div class="modal-content wide-modal">
        <span class="close" onclick="closeModal('t5')">X</span>
        <h4>Route 66 - Competitive Risk</h4>
        <p style="font-size: 0.85em;">TP-Link/Think competition identified. Up2Tech compliance risk.</p>
    </div>
</div>

<div id="t12" class="modal">
    <div class="modal-content wide-modal">
        <span class="close" onclick="closeModal('t12')">X</span>
        <h4>Premium - Account Intelligence</h4>
        <p style="font-size: 0.85em;">Operational capacity review. TP-Link risk.</p>
    </div>
</div>

<div id="t7" class="modal"><div class="modal-content"><span class="close" onclick="closeModal('t7')">X</span><h4>Suprinordeste Task</h4>Review updates.</div></div>
<div id="t8" class="modal"><div class="modal-content"><span class="close" onclick="closeModal('t8')">X</span><h4>OiW Task</h4>Region overlap with Prexx.</div></div>
<div id="t9" class="modal"><div class="modal-content"><span class="close" onclick="closeModal('t9')">X</span><h4>Centry Group Task</h4>Review updates.</div></div>
<div id="t10" class="modal"><div class="modal-content"><span class="close" onclick="closeModal('t10')">X</span><h4>Sheroline Task</h4>Review updates.</div></div>

<div id="alert-up2tech" class="modal">
    <div class="modal-content" style="border-top: 5px solid #e74c3c;">
        <span class="close" onclick="closeModal('alert-up2tech')">X</span>
        <h4 style="color: #e74c3c; margin-top: 0;">RED ALERT: Up2Tech</h4>
        <p style="font-size: 0.9em; line-height: 1.5;">Legal and reputational liability risks. Possible tax evasion issues.</p>
    </div>
</div>

<script>
// Logic remains unchanged as requested
const partnerRegions = {
    'prexx': ['SC', 'RS', 'SP', 'ES', 'AL'],
    'premium': ['PR'],
    'chub': ['AC','AM','RR','AP','RO','PA','TO'], 
    'nextcable': ['PR', 'MT', 'MG', 'SP', 'GO'],
    'route66': ['SP', 'ES', 'MG'],
    'gw': ['GO', 'DF', 'TO', 'MA', 'PA'],
    'televit': ['BA'],
    'suprinordeste': ['CE'],
    'oiw': ['RS', 'SC', 'SP', 'MG', 'MT', 'BA', 'CE'],
    'centry': ['PB', 'RN'],
    'sheroline': ['SP'],
    'think': ['MG']
};

function highlightMap(partnerId) {
    resetMap();
    const states = partnerRegions[partnerId];
    if (!states) return;
    states.forEach(uf => {
        const badge = document.getElementById('uf-' + uf);
        if (badge) badge.classList.add('active');
    });
}

function resetMap() {
    document.querySelectorAll('.uf-badge.active').forEach(b => b.classList.remove('active'));
}

function openTab(evt, tabName) {
    document.querySelectorAll(".tab-content").forEach(tc => { tc.style.display = "none"; tc.classList.remove("active"); });
    document.querySelectorAll(".tab-btn").forEach(tb => tb.className = tb.className.replace(" active", ""));
    document.getElementById(tabName).style.display = "block";
    setTimeout(() => { document.getElementById(tabName).classList.add("active"); }, 10);
    evt.currentTarget.className += " active";
}

function openModal(id){ document.getElementById(id).style.display="block"; }
function closeModal(id){ document.getElementById(id).style.display="none"; }

// Landed cost logic...
const PRODUTOS = [
    { value: 'ont',  label_pt: 'ONT (NCM 8517.62.55)', label_en: 'ONT (NCM 8517.62.55)', ii: 0.12, ipi: 0.10, ncm: '8517.62.55' },
    { value: 'olt',  label_pt: 'OLT (Ex-tarifário)',   label_en: 'OLT (Ex-tariff)',       ii: 0.00, ipi: 0.00, ncm: '8517.62.99' },
    { value: 'cabo', label_pt: 'Cabo Óptico',           label_en: 'Fiber Optic Cable',     ii: 0.18, ipi: 0.15, ncm: '8544.70.00' },
];

const ESTADOS = [
    { uf: 'AC',     nome_pt: 'Acre',                        nome_en: 'Acre',                        icms: 0.17  },
    { uf: 'AL',     nome_pt: 'Alagoas',                     nome_en: 'Alagoas',                     icms: 0.19  },
    { uf: 'AP',     nome_pt: 'Amapá',                       nome_en: 'Amapá',                       icms: 0.18  },
    { uf: 'AM',     nome_pt: 'Amazonas',                    nome_en: 'Amazonas',                    icms: 0.20  },
    { uf: 'BA',     nome_pt: 'Bahia',                       nome_en: 'Bahia',                       icms: 0.205 },
    { uf: 'CE',     nome_pt: 'Ceará',                       nome_en: 'Ceará',                       icms: 0.20  },
    { uf: 'DF',     nome_pt: 'Distrito Federal',            nome_en: 'Federal District',            icms: 0.18  },
    { uf: 'ES',     nome_pt: 'Espírito Santo',               nome_en: 'Espírito Santo',              icms: 0.17  },
    { uf: 'GO',     nome_pt: 'Goiás',                       nome_en: 'Goiás',                       icms: 0.17  },
    { uf: 'MA',     nome_pt: 'Maranhão',                    nome_en: 'Maranhão',                    icms: 0.22  },
    { uf: 'MT',     nome_pt: 'Mato Grosso',                 nome_en: 'Mato Grosso',                 icms: 0.17  },
    { uf: 'MS',     nome_pt: 'Mato Grosso do Sul',           nome_en: 'Mato Grosso do Sul',          icms: 0.17  },
    { uf: 'MG',     nome_pt: 'Minas Gerais',                 nome_en: 'Minas Gerais',                icms: 0.18  },
    { uf: 'PA',     nome_pt: 'Pará',                        nome_en: 'Pará',                        icms: 0.17  },
    { uf: 'PB',     nome_pt: 'Paraíba',                     nome_en: 'Paraíba',                     icms: 0.20  },
    { uf: 'PR',     nome_pt: 'Paraná',                       nome_en: 'Paraná',                      icms: 0.195 },
    { uf: 'PE',     nome_pt: 'Pernambuco',                  nome_en: 'Pernambuco',                  icms: 0.205 },
    { uf: 'PI',     nome_pt: 'Piauí',                       nome_en: 'Piauí',                       icms: 0.21  },
    { uf: 'RJ',     nome_pt: 'Rio de Janeiro',               nome_en: 'Rio de Janeiro',              icms: 0.20  },
    { uf: 'RN',     nome_pt: 'Rio Grande do Norte',          nome_en: 'Rio Grande do Norte',         icms: 0.18  },
    { uf: 'RS',     nome_pt: 'Rio Grande do Sul',            nome_en: 'Rio Grande do Sul',           icms: 0.18  },
    { uf: 'RO',     nome_pt: 'Rondônia',                    nome_en: 'Rondônia',                    icms: 0.175 },
    { uf: 'RR',     nome_pt: 'Roraima',                     nome_en: 'Roraima',                     icms: 0.17  },
    { uf: 'SC',     nome_pt: 'Santa Catarina',               nome_en: 'Santa Catarina',              icms: 0.17  },
    { uf: 'SC_TTD', nome_pt: 'Santa Catarina — Benef. TTD',  nome_en: 'Santa Catarina — TTD Benefit',icms: 0.12  },
    { uf: 'SP',     nome_pt: 'São Paulo',                   nome_en: 'São Paulo',                   icms: 0.18  },
    { uf: 'SE',     nome_pt: 'Sergipe',                     nome_en: 'Sergipe',                     icms: 0.19  },
    { uf: 'TO',     nome_pt: 'Tocantins',                   nome_en: 'Tocantins',                   icms: 0.18  },
];

const SUL_SUDESTE = new Set(['MG', 'RJ', 'SP', 'PR', 'SC', 'SC_TTD', 'RS']);
function getAliqInter(ufOrigem, ufDestino) { return SUL_SUDESTE.has(ufOrigem) && SUL_SUDESTE.has(ufDestino) ? 0.12 : 0.07; }

function calcDifalAliq(estadoOrigem, estadoDestino) {
    const ufOri = estadoOrigem.uf.replace('_TTD', '');
    const ufDst = estadoDestino.uf.replace('_TTD', '');
    if (ufOri === ufDst) return 0;
    const inter = getAliqInter(estadoOrigem.uf, estadoDestino.uf);
    return Math.max(0, estadoDestino.icms - inter);
}

const PISCOFINS_RATE = 0.1175; 
const TAXAS_FIXAS    = 15.00;  

let currentLang = 'pt';

function setLang(lang) {
    currentLang = lang;
    document.querySelectorAll('.lang-btn').forEach(b => b.classList.remove('active'));
    document.querySelector(`.lang-btn[onclick="setLang('${lang}')"]`).classList.add('active');
    document.querySelectorAll('[data-pt]').forEach(el => { el.textContent = el.getAttribute(`data-${lang}`); });
    buildProdutoSelect();
    buildEstadoSelects();
    onProdutoChange();
    onEstadoChange();
    document.getElementById('resultado').style.display = 'none';
}

function buildProdutoSelect() {
    const sel = document.getElementById('produto');
    const prev = sel.value;
    sel.innerHTML = '';
    PRODUTOS.forEach(p => {
        const opt = document.createElement('option');
        opt.value = p.value;
        const lbl = currentLang === 'pt' ? p.label_pt : p.label_en;
        opt.textContent = `${lbl} — II ${(p.ii*100).toFixed(0)}% | IPI ${(p.ipi*100).toFixed(0)}%`;
        sel.appendChild(opt);
    });
    if (prev) sel.value = prev;
}

function populateEstadoSelect(selId, defaultUf) {
    const sel = document.getElementById(selId);
    const prev = sel.value;
    sel.innerHTML = '';
    ESTADOS.forEach(e => {
        const opt = document.createElement('option');
        opt.value = e.uf;
        const nome = currentLang === 'pt' ? e.nome_pt : e.nome_en;
        opt.textContent = `${e.uf.replace('_TTD','')} — ${nome} (ICMS ${(e.icms*100).toFixed(1)}%)`;
        sel.appendChild(opt);
    });
    sel.value = prev || defaultUf;
}

function buildEstadoSelects() { populateEstadoSelect('estadoOrigem', 'SC'); populateEstadoSelect('estadoDestino', 'SP'); }
function getSelectedProduto() { return PRODUTOS.find(p => p.value === document.getElementById('produto').value); }
function getEstado(selId) { return ESTADOS.find(e => e.uf === document.getElementById(selId).value); }

function onProdutoChange() {
    const p = getSelectedProduto();
    if (p) document.getElementById('ipiDisplay').textContent = `${(p.ipi * 100).toFixed(0)}%  —  NCM ${p.ncm}`;
}

function onEstadoChange() {
    const origem = getEstado('estadoOrigem'); const destino = getEstado('estadoDestino');
    if (!origem || !destino) return;
    const difalAliq = calcDifalAliq(origem, destino);
    const mesmaUf = origem.uf.replace('_TTD','') === destino.uf.replace('_TTD','');
    if (mesmaUf) {
        document.getElementById('difalDisplay').textContent = currentLang === 'pt' ? '0%  — operação interna' : '0%  — internal operation';
        document.getElementById('difalInfo').style.display = 'none';
    } else {
        const inter = getAliqInter(origem.uf, destino.uf);
        document.getElementById('difalDisplay').textContent = `${(difalAliq*100).toFixed(1)}%`;
        document.getElementById('difalInfo').style.display = 'block';
    }
}

const fmt = v => 'R$ ' + v.toLocaleString('pt-BR', { minimumFractionDigits: 2, maximumFractionDigits: 2 });

function calcular() {
    const fob = parseFloat(document.getElementById('fob').value);
    const frete = parseFloat(document.getElementById('frete').value) || 0;
    const cambio = parseFloat(document.getElementById('cambio').value);
    const p = getSelectedProduto(); const d = getEstado('estadoDestino');
    const cif = (fob + frete) * cambio;
    const vIi = cif * p.ii;
    const vIpi = (cif + vIi) * p.ipi;
    const vPis = cif * PISCOFINS_RATE;
    const baseIcms = (cif + vIi + vIpi + vPis + TAXAS_FIXAS) / (1 - d.icms);
    const vIcms = baseIcms * d.icms;
    const total = cif + vIi + vIpi + vPis + vIcms + TAXAS_FIXAS;
    document.getElementById('resTotal').textContent = fmt(total);
    document.getElementById('resultado').style.display = 'block';
}

buildProdutoSelect(); buildEstadoSelects(); onProdutoChange(); onEstadoChange();
</script>

</body>
</html>
