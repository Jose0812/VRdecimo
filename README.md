# VRdecimo
```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Evaluación Rápida: Operaciones Combinadas (Sobre 10)</title>
  <style>
    /* =====================================================================
       ESTILOS AUTOCONTENIDOS (SIN DEPENDENCIAS EXTERNAS)
    ====================================================================== */
    *, *::before, *::after {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    :root {
      --bg-page: #f1f5f9;
      --bg-card: #ffffff;
      --bg-subtle: #f8fafc;
      --bg-dark: #0f172a;
      --text-main: #0f172a;
      --text-muted: #64748b;
      --border-color: #cbd5e1;
      --border-light: #e2e8f0;
      --primary: #4f46e5;
      --primary-hover: #4338ca;
      --primary-soft: #eef2ff;
      --success: #059669;
      --success-hover: #047857;
      --success-soft: #ecfdf5;
      --success-border: #34d399;
      --danger: #e11d48;
      --danger-soft: #fff1f2;
      --danger-border: #fda4af;
      --warning: #d97706;
    }

    body {
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
      background-color: var(--bg-page);
      color: var(--text-main);
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      line-height: 1.45;
      -webkit-font-smoothing: antialiased;
    }

    .hidden {
      display: none !important;
    }

    /* =====================================================================
       CABECERA COMPACTA Y CONTROLES PÍLDORA
    ====================================================================== */
    .top-header {
      background-color: var(--bg-card);
      border-bottom: 1px solid var(--border-light);
      position: sticky;
      top: 0;
      z-index: 30;
      box-shadow: 0 2px 6px rgba(15, 23, 42, 0.05);
    }

    .header-container {
      max-width: 1120px;
      margin: 0 auto;
      padding: 0.7rem 1rem;
      display: flex;
      flex-direction: column;
      gap: 0.65rem;
    }

    .header-row-top {
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      justify-content: space-between;
      gap: 0.75rem;
    }

    .brand-title {
      display: flex;
      align-items: center;
      gap: 0.55rem;
      font-weight: 800;
      font-size: 1.05rem;
      color: var(--text-main);
    }

    .brand-badge {
      background-color: var(--primary);
      color: #ffffff;
      font-size: 0.72rem;
      font-weight: 800;
      padding: 0.22rem 0.55rem;
      border-radius: 0.5rem;
      letter-spacing: 0.03em;
    }

    .student-inputs-group {
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      gap: 0.5rem;
      flex: 1;
      justify-content: flex-end;
    }

    .name-input-wrap {
      position: relative;
      flex: 1 1 220px;
      max-width: 300px;
    }

    .course-input-wrap {
      flex: 0 1 145px;
      min-width: 120px;
    }

    .control-input {
      width: 100%;
      padding: 0.5rem 0.8rem;
      border-radius: 0.75rem;
      border: 1.5px solid var(--border-color);
      background-color: var(--bg-subtle);
      color: var(--text-main);
      font-size: 0.875rem;
      font-weight: 600;
      font-family: inherit;
      transition: border-color 0.15s, background-color 0.15s, box-shadow 0.15s;
    }

    .control-input:focus {
      outline: none;
      border-color: var(--primary);
      background-color: #ffffff;
      box-shadow: 0 0 0 3px rgba(79, 70, 229, 0.15);
    }

    .btn-clear-name {
      position: absolute;
      right: 0.55rem;
      top: 50%;
      transform: translateY(-50%);
      background: transparent;
      border: none;
      color: var(--text-muted);
      font-weight: 800;
      font-size: 0.85rem;
      cursor: pointer;
      padding: 0.2rem;
    }

    /* Barra de configuración rápida con píldoras */
    .header-row-pills {
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      justify-content: space-between;
      gap: 0.65rem;
      padding-top: 0.55rem;
      border-top: 1px solid var(--border-light);
    }

    .pill-section {
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      gap: 0.4rem;
    }

    .pill-label {
      font-size: 0.74rem;
      font-weight: 800;
      text-transform: uppercase;
      letter-spacing: 0.04em;
      color: var(--text-muted);
      margin-right: 0.2rem;
    }

    .pill-group {
      display: inline-flex;
      flex-wrap: wrap;
      gap: 0.35rem;
      background-color: var(--bg-subtle);
      padding: 0.22rem;
      border-radius: 999px;
      border: 1px solid var(--border-light);
    }

    .pill-btn {
      border: none;
      background: transparent;
      color: #475569;
      font-family: inherit;
      font-size: 0.78rem;
      font-weight: 700;
      padding: 0.35rem 0.85rem;
      border-radius: 999px;
      cursor: pointer;
      transition: all 0.15s ease;
    }

    .pill-btn:hover {
      color: var(--text-main);
      background-color: #e2e8f0;
    }

    .pill-btn.active {
      background-color: var(--primary);
      color: #ffffff;
      box-shadow: 0 2px 5px rgba(79, 70, 229, 0.28);
    }

    .pill-btn.timer-pill.active {
      background-color: var(--bg-dark);
      color: #ffffff;
      box-shadow: 0 2px 5px rgba(15, 23, 42, 0.25);
    }

    .btn-icon {
      display: inline-flex;
      align-items: center;
      gap: 0.35rem;
      padding: 0.42rem 0.75rem;
      border-radius: 999px;
      border: 1.5px solid var(--border-color);
      background-color: #ffffff;
      color: var(--text-main);
      font-family: inherit;
      font-size: 0.78rem;
      font-weight: 700;
      cursor: pointer;
      transition: background-color 0.15s;
    }

    .btn-icon:hover {
      background-color: #e2e8f0;
    }

    /* =====================================================================
       CONTENEDOR PRINCIPAL Y TARJETA DE EVALUACIÓN
    ====================================================================== */
    .main-container {
      max-width: 1120px;
      width: 100%;
      margin: 0 auto;
      padding: 1.15rem 1rem 2.5rem;
      display: flex;
      flex-direction: column;
      gap: 1.35rem;
      flex-grow: 1;
    }

    .card {
      background-color: var(--bg-card);
      border-radius: 1.25rem;
      border: 1px solid var(--border-light);
      box-shadow: 0 4px 14px rgba(15, 23, 42, 0.04);
      overflow: hidden;
    }

    /* Barra oscura del turno activo */
    .turn-header {
      background-color: var(--bg-dark);
      color: #ffffff;
      padding: 0.8rem 1.25rem;
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      justify-content: space-between;
      gap: 0.75rem;
    }

    .turn-info-left {
      display: flex;
      align-items: center;
      flex-wrap: wrap;
      gap: 0.55rem;
    }

    .turn-badge {
      background-color: var(--primary);
      color: #ffffff;
      font-size: 0.74rem;
      font-weight: 800;
      text-transform: uppercase;
      letter-spacing: 0.04em;
      padding: 0.22rem 0.6rem;
      border-radius: 0.5rem;
    }

    .active-student-name {
      font-weight: 800;
      font-size: 0.98rem;
      color: #f8fafc;
    }

    .level-pill {
      background-color: #1e293b;
      border: 1px solid #334155;
      color: #cbd5e1;
      font-size: 0.74rem;
      font-weight: 700;
      padding: 0.2rem 0.55rem;
      border-radius: 0.45rem;
    }

    .turn-info-right {
      display: flex;
      align-items: center;
      flex-wrap: wrap;
      gap: 0.85rem;
      font-size: 0.8rem;
      color: #cbd5e1;
    }

    .timer-badge {
      display: inline-flex;
      align-items: center;
      gap: 0.4rem;
      padding: 0.24rem 0.72rem;
      border-radius: 0.5rem;
      background-color: #1e293b;
      border: 1px solid #475569;
      color: #34d399;
      font-family: ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, monospace;
      font-weight: 800;
      font-size: 0.95rem;
    }

    .timer-badge.timer-danger {
      background-color: var(--danger);
      border-color: #fda4af;
      color: #ffffff;
      animation: pulseAlert 0.85s infinite;
    }

    @keyframes pulseAlert {
      0%, 100% { opacity: 1; transform: scale(1); }
      50% { opacity: 0.72; transform: scale(1.03); }
    }

    .kbd-hint {
      background-color: #1e293b;
      border: 1px solid #475569;
      border-radius: 0.35rem;
      padding: 0.1rem 0.4rem;
      font-family: monospace;
      color: #f1f5f9;
    }

    /* Tarjeta destacada de resultado inmediato */
    .result-banner {
      background-color: var(--bg-subtle);
      border-bottom: 1px solid var(--border-light);
      padding: 1.15rem 1.25rem;
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      justify-content: space-between;
      gap: 1rem;
    }

    .result-left {
      display: flex;
      align-items: center;
      flex-wrap: wrap;
      gap: 0.9rem;
    }

    .score-cards-pair {
      display: flex;
      gap: 0.65rem;
      flex-wrap: wrap;
    }

    .score-box {
      padding: 0.65rem 1.1rem;
      border-radius: 0.95rem;
      background-color: var(--success);
      color: #ffffff;
      text-align: center;
      min-width: 122px;
      box-shadow: 0 2px 6px rgba(5, 150, 105, 0.22);
    }

    .score-box.score-secondary {
      background-color: var(--bg-dark);
      box-shadow: 0 2px 6px rgba(15, 23, 42, 0.18);
    }

    .score-box.score-indigo { background-color: var(--primary); }
    .score-box.score-amber { background-color: var(--warning); }
    .score-box.score-rose { background-color: var(--danger); }

    .score-box-label {
      display: block;
      font-size: 0.66rem;
      font-weight: 800;
      text-transform: uppercase;
      letter-spacing: 0.05em;
      opacity: 0.92;
    }

    .score-box-value {
      font-size: 1.85rem;
      font-weight: 900;
      line-height: 1.1;
    }

    .score-box-sub {
      font-size: 0.82rem;
      font-weight: 700;
      opacity: 0.9;
    }

    .qual-badge {
      display: inline-block;
      padding: 0.2rem 0.65rem;
      border-radius: 999px;
      font-size: 0.74rem;
      font-weight: 800;
      background-color: #d1fae5;
      color: #065f46;
    }

    .qual-badge.qual-indigo { background-color: #e0e7ff; color: #3730a3; }
    .qual-badge.qual-amber { background-color: #fef3c7; color: #92400e; }
    .qual-badge.qual-rose { background-color: #ffe4e6; color: #9f1239; }

    /* Cuadrícula de 10 ejercicios en 2 columnas */
    .exam-form {
      padding: 1.25rem;
    }

    .questions-grid {
      display: grid;
      grid-template-columns: repeat(2, minmax(0, 1fr));
      gap: 1.15rem;
    }

    @media (max-width: 820px) {
      .questions-grid {
        grid-template-columns: 1fr;
        gap: 0.75rem;
      }
    }

    .questions-col {
      display: flex;
      flex-direction: column;
      gap: 0.7rem;
    }

    .q-row {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 0.65rem;
      padding: 0.72rem 0.95rem;
      border-radius: 0.95rem;
      background-color: var(--bg-subtle);
      border: 2px solid var(--border-light);
      transition: border-color 0.15s, background-color 0.15s;
    }

    .q-row:focus-within {
      border-color: var(--primary);
      background-color: var(--primary-soft);
    }

    .q-row.q-correct {
      background-color: var(--success-soft);
      border-color: var(--success-border);
    }

    .q-row.q-wrong {
      background-color: var(--danger-soft);
      border-color: var(--danger-border);
    }

    .q-left {
      display: flex;
      align-items: center;
      gap: 0.65rem;
      min-width: 0;
    }

    .q-num {
      width: 1.75rem;
      height: 1.75rem;
      border-radius: 0.5rem;
      background-color: #ffffff;
      border: 1.5px solid var(--border-color);
      color: #475569;
      font-weight: 800;
      font-size: 0.78rem;
      display: inline-flex;
      align-items: center;
      justify-content: center;
      flex-shrink: 0;
    }

    .q-label {
      font-size: 1.18rem;
      font-weight: 800;
      color: var(--text-main);
      letter-spacing: -0.01em;
      cursor: pointer;
      user-select: none;
      font-variant-numeric: tabular-nums;
    }

    .q-label sup {
      font-size: 0.76rem;
      font-weight: 900;
      line-height: 0;
      vertical-align: super;
      margin-left: 1px;
    }

    .q-equals {
      color: var(--text-muted);
      font-weight: 700;
      margin-left: 0.25rem;
    }

    .q-right {
      display: flex;
      align-items: center;
      gap: 0.5rem;
      flex-shrink: 0;
    }

    .q-input {
      width: 5.75rem;
      padding: 0.45rem 0.5rem;
      text-align: center;
      font-size: 1.25rem;
      font-weight: 900;
      font-family: inherit;
      border-radius: 0.75rem;
      border: 2px solid var(--border-color);
      background-color: #ffffff;
      color: var(--primary);
      transition: border-color 0.15s, box-shadow 0.15s;
    }

    .q-input:focus {
      outline: none;
      border-color: var(--primary);
      box-shadow: 0 0 0 3px rgba(79, 70, 229, 0.2);
    }

    .q-input.input-correct {
      border-color: var(--success);
      color: var(--success);
    }

    .q-input.input-wrong {
      border-color: var(--danger);
      color: var(--danger);
      text-decoration: line-through;
    }

    .q-feedback {
      font-size: 0.76rem;
      font-weight: 800;
      padding: 0.28rem 0.52rem;
      border-radius: 0.5rem;
      white-space: nowrap;
    }

    .fb-correct {
      background-color: #d1fae5;
      color: #065f46;
    }

    .fb-wrong {
      background-color: #ffe4e6;
      color: #9f1239;
    }

    /* Pie del formulario */
    .form-footer {
      margin-top: 1.15rem;
      padding-top: 1rem;
      border-top: 1px solid var(--border-light);
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      justify-content: space-between;
      gap: 0.85rem;
    }

    .footer-note {
      font-size: 0.8rem;
      color: var(--text-muted);
    }

    .btn {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 0.5rem;
      padding: 0.78rem 1.45rem;
      border-radius: 0.9rem;
      border: none;
      font-family: inherit;
      font-weight: 800;
      font-size: 0.95rem;
      cursor: pointer;
      transition: background-color 0.15s, transform 0.08s;
    }

    .btn:active {
      transform: scale(0.99);
    }

    .btn-success {
      background-color: var(--success);
      color: #ffffff;
      box-shadow: 0 4px 10px rgba(5, 150, 105, 0.25);
    }

    .btn-success:hover {
      background-color: var(--success-hover);
    }

    .btn-primary {
      background-color: var(--primary);
      color: #ffffff;
      box-shadow: 0 4px 10px rgba(79, 70, 229, 0.25);
    }

    .btn-primary:hover {
      background-color: var(--primary-hover);
    }

    .btn-sm {
      padding: 0.45rem 0.85rem;
      border-radius: 0.65rem;
      font-size: 0.8rem;
      font-weight: 700;
    }

    .btn-outline-indigo {
      background-color: var(--primary-soft);
      color: var(--primary);
      border: 1px solid #c7d2fe;
    }

    .btn-outline-indigo:hover {
      background-color: #e0e7ff;
    }

    .btn-outline-slate {
      background-color: var(--bg-subtle);
      color: var(--text-main);
      border: 1px solid var(--border-color);
    }

    .btn-outline-slate:hover {
      background-color: #e2e8f0;
    }

    .btn-outline-danger {
      background-color: #ffffff;
      color: var(--danger);
      border: 1px solid var(--border-light);
    }

    .btn-outline-danger:hover {
      background-color: var(--danger-soft);
      border-color: var(--danger-border);
    }

    /* =====================================================================
       HISTORIAL ACUMULATIVO DE LA SESIÓN
    ====================================================================== */
    .history-header {
      padding: 0.95rem 1.25rem;
      background-color: var(--bg-subtle);
      border-bottom: 1px solid var(--border-light);
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      justify-content: space-between;
      gap: 0.75rem;
    }

    .history-title-row {
      display: flex;
      align-items: center;
      flex-wrap: wrap;
      gap: 0.5rem;
    }

    .history-title {
      font-size: 1.02rem;
      font-weight: 800;
    }

    .count-pill {
      background-color: #e2e8f0;
      color: #1e293b;
      font-size: 0.74rem;
      font-weight: 800;
      padding: 0.2rem 0.6rem;
      border-radius: 999px;
    }

    .history-actions {
      display: flex;
      flex-wrap: wrap;
      gap: 0.45rem;
    }

    .confirm-bar {
      background-color: var(--danger-soft);
      border-bottom: 1px solid var(--danger-border);
      padding: 0.75rem 1.25rem;
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      justify-content: space-between;
      gap: 0.6rem;
      font-size: 0.85rem;
      font-weight: 600;
      color: #881337;
    }

    .table-wrap {
      width: 100%;
      overflow-x: auto;
    }

    table {
      width: 100%;
      border-collapse: collapse;
      text-align: left;
    }

    th {
      background-color: var(--bg-subtle);
      border-bottom: 1px solid var(--border-light);
      padding: 0.72rem 0.9rem;
      font-size: 0.71rem;
      font-weight: 800;
      text-transform: uppercase;
      letter-spacing: 0.04em;
      color: var(--text-muted);
      white-space: nowrap;
    }

    td {
      padding: 0.72rem 0.9rem;
      border-bottom: 1px solid #f1f5f9;
      font-size: 0.86rem;
    }

    .text-center { text-align: center; }
    .text-right { text-align: right; }

    .grade-chip {
      display: inline-block;
      padding: 0.2rem 0.65rem;
      border-radius: 0.5rem;
      font-weight: 900;
      font-size: 0.88rem;
    }

    .chip-green { background-color: #d1fae5; color: #065f46; }
    .chip-indigo { background-color: #e0e7ff; color: #3730a3; }
    .chip-amber { background-color: #fef3c7; color: #92400e; }
    .chip-rose { background-color: #ffe4e6; color: #9f1239; }

    /* Toast flotante */
    .toast {
      position: fixed;
      bottom: 1.25rem;
      right: 1.25rem;
      z-index: 50;
      background-color: var(--bg-dark);
      color: #ffffff;
      padding: 0.75rem 1.1rem;
      border-radius: 0.9rem;
      box-shadow: 0 10px 25px rgba(15, 23, 42, 0.25);
      display: flex;
      align-items: center;
      gap: 0.6rem;
      font-size: 0.85rem;
      font-weight: 600;
    }

    @media print {
      .no-print { display: none !important; }
      body { background-color: #ffffff; }
      .card { box-shadow: none; border: 1px solid #cbd5e1; }
    }
  </style>
</head>
<body>

  <!-- Notificación flotante interna -->
  <div id="toast-message" class="toast hidden no-print" role="status" aria-live="polite">
    <span style="color:#34d399; font-weight:900;">✓</span>
    <span id="toast-text"></span>
  </div>

  <!-- =====================================================================
       CABECERA COMPACTA Y BARRA DE CONFIGURACIÓN RÁPIDA
  ====================================================================== -->
  <header class="top-header no-print">
    <div class="header-container">
      <!-- Fila 1: Título y datos del estudiante -->
      <div class="header-row-top">
        <div class="brand-title">
          <span class="brand-badge">10 ÍTEMS / 20 PTS</span>
          <span>Evaluación Rápida: Operaciones Combinadas</span>
        </div>

        <div class="student-inputs-group">
          <div class="name-input-wrap">
            <input type="text" id="student-name-input" class="control-input" autocomplete="off"
              placeholder="Nombre y apellido (Estudiante #1)" aria-label="Nombre y apellido del estudiante">
            <button type="button" id="btn-clear-name" class="btn-clear-name hidden" title="Limpiar nombre">✕</button>
          </div>
          <div class="course-input-wrap">
            <input type="text" id="student-course-input" class="control-input" autocomplete="off"
              placeholder="Curso / Paralelo" aria-label="Curso o paralelo opcional">
          </div>
        </div>
      </div>

      <!-- Fila 2: Píldoras de Nivel, Tiempo y Botón Nuevos Ejercicios -->
      <div class="header-row-pills">
        <div class="pill-section">
          <span class="pill-label">Nivel:</span>
          <div class="pill-group" role="group" aria-label="Nivel de dificultad">
            <button type="button" class="pill-btn level-pill-btn active" data-level="easy">
              Nivel Fácil
            </button>
            <button type="button" class="pill-btn level-pill-btn" data-level="medium">
              Nivel Medio
            </button>
            <button type="button" class="pill-btn level-pill-btn" data-level="hard">
              Nivel Difícil
            </button>
          </div>
        </div>

        <div class="pill-section">
          <span class="pill-label">Tiempo:</span>
          <div class="pill-group" role="group" aria-label="Selector de tiempo">
            <button type="button" class="pill-btn timer-pill active" data-seconds="0">
              Sin tiempo
            </button>
            <button type="button" class="pill-btn timer-pill" data-seconds="120">
              2 min (02:00)
            </button>
            <button type="button" class="pill-btn timer-pill" data-seconds="240">
              4 min (04:00)
            </button>
          </div>

          <button type="button" id="btn-shuffle-questions" class="btn-icon" title="Generar 10 nuevos ejercicios">
            <svg width="16" height="16" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2.2" d="M4 4v5h.582m15.356 2A8.001 8.001 0 004.582 9m0 0H9m11 11v-5h-.581m0 0a8.003 8.003 0 01-15.357-2m15.357 2H15"/>
            </svg>
            <span>Nuevos</span>
          </button>
        </div>
      </div>
    </div>
  </header>

  <!-- =====================================================================
       CONTENIDO PRINCIPAL
  ====================================================================== -->
  <main class="main-container">

    <!-- TARJETA PRINCIPAL DE LOS 10 EJERCICIOS -->
    <section class="card">
      <!-- Encabezado oscuro de turno -->
      <div class="turn-header">
        <div class="turn-info-left">
          <span id="turn-badge" class="turn-badge">Turno #1</span>
          <span id="active-student-label" class="active-student-name">Estudiante #1</span>
          <span id="active-level-badge" class="level-pill">Nivel Fácil (2 pasos)</span>
        </div>

        <div class="turn-info-right">
          <div id="timer-display-badge" class="timer-badge hidden">
            <span>⏱</span>
            <span id="timer-countdown-text">02:00</span>
          </div>
          <span>Respondidas: <strong id="answered-counter" style="color:#ffffff;">0 / 10</strong></span>
          <span>Tecla <kbd class="kbd-hint">Enter</kbd> avanza y califica</span>
        </div>
      </div>

      <!-- Tarjeta destacada de resultado inmediato (visible al calificar) -->
      <div id="result-summary-panel" class="result-banner hidden">
        <div class="result-left">
          <div class="score-cards-pair">
            <div id="score-box-10" class="score-box">
              <span class="score-box-label">Nota Final</span>
              <div>
                <span id="final-grade-10" class="score-box-value">10,00</span>
                <span class="score-box-sub">/ 10</span>
              </div>
            </div>

            <div class="score-box score-secondary">
              <span class="score-box-label">Puntaje</span>
              <div>
                <span id="final-points-20" class="score-box-value">20</span>
                <span class="score-box-sub">/ 20</span>
              </div>
            </div>
          </div>

          <div>
            <div style="display:flex; align-items:center; gap:0.5rem; flex-wrap:wrap;">
              <h2 id="result-student-title" style="font-size:1.12rem; font-weight:800;">Estudiante #1</h2>
              <span id="result-qualitative-tag" class="qual-badge">Domina (DAR)</span>
              <span id="time-expired-tag" class="qual-badge qual-rose hidden">⏱ Tiempo agotado</span>
            </div>
            <p id="result-points-detail" style="font-weight:700; color:#334155; margin-top:0.2rem;">
              10 de 10 aciertos — Tiempo usado: Sin límite
            </p>
            <p style="font-size:0.78rem; color:#64748b; margin-top:0.15rem;">
              Calificación registrada abajo. Presiona <strong>Enter</strong> o el botón para continuar.
            </p>
          </div>
        </div>

        <button type="button" id="btn-next-student-top" class="btn btn-primary no-print">
          <span>Siguiente estudiante →</span>
        </button>
      </div>

      <!-- Formulario de 10 ejercicios en 2 columnas -->
      <form id="quick-exam-form" class="exam-form" novalidate>
        <div class="questions-grid">
          <div id="col-left-questions" class="questions-col"></div>
          <div id="col-right-questions" class="questions-col"></div>
        </div>

        <div class="form-footer no-print">
          <p class="footer-note">
            Jerarquía de operaciones: Paréntesis → Potencias/Raíces → × y ÷ → + y −. Cada acierto = <strong>2 pts</strong> (1,00 sobre 10).
          </p>

          <div style="display:flex; gap:0.65rem; flex-wrap:wrap;">
            <button type="submit" id="btn-grade-now" class="btn btn-success">
              <span>✓ Calificar (Enter)</span>
            </button>

            <button type="button" id="btn-next-student-bottom" class="btn btn-primary hidden">
              <span>Siguiente estudiante →</span>
            </button>
          </div>
        </div>
      </form>
    </section>

    <!-- =====================================================================
         TABLA INFERIOR ACUMULATIVA DE CALIFICACIONES DE LA SESIÓN
    ====================================================================== -->
    <section class="card">
      <div class="history-header">
        <div>
          <div class="history-title-row">
            <h2 class="history-title">Registro de calificaciones de la sesión</h2>
            <span id="session-count-badge" class="count-pill">0 evaluados</span>
          </div>
          <p style="font-size:0.8rem; color:#64748b; margin-top:0.15rem;">
            Promedio del grupo: <strong id="session-avg-10" style="color:#0f172a;">0,00 / 10</strong>
          </p>
        </div>

        <div class="history-actions no-print">
          <button type="button" id="btn-copy-results" class="btn btn-sm btn-outline-indigo">
            Copiar tabla
          </button>
          <button type="button" id="btn-download-csv" class="btn btn-sm btn-outline-slate">
            Descargar CSV
          </button>
          <button type="button" id="btn-clear-history" class="btn btn-sm btn-outline-danger">
            Limpiar lista
          </button>
        </div>
      </div>

      <!-- Confirmación inline sin confirm() -->
      <div id="clear-confirm-bar" class="confirm-bar hidden no-print">
        <span>¿Deseas borrar todas las calificaciones registradas en esta sesión?</span>
        <div style="display:flex; gap:0.4rem;">
          <button type="button" id="btn-cancel-clear" class="btn btn-sm btn-outline-slate">Cancelar</button>
          <button type="button" id="btn-confirm-clear" class="btn btn-sm" style="background:#e11d48; color:#fff;">Sí, borrar</button>
        </div>
      </div>

      <div class="table-wrap">
        <table>
          <thead>
            <tr>
              <th class="text-center" style="width:55px;">N°</th>
              <th>Estudiante</th>
              <th class="text-center">Nivel</th>
              <th class="text-center">Tiempo usado</th>
              <th class="text-center">Aciertos/10</th>
              <th class="text-center">Puntaje/20</th>
              <th class="text-right">Nota/10</th>
            </tr>
          </thead>
          <tbody id="session-history-body">
            <tr>
              <td colspan="7" class="text-center" style="padding:2rem 1rem; color:#94a3b8;">
                Aún no hay estudiantes calificados. Completa las 10 operaciones y presiona <strong>Calificar</strong>.
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </section>

  </main>

  <!-- =====================================================================
       LÓGICA DE GENERACIÓN DE OPERACIONES COMBINADAS Y FLUJO RÁPIDO
  ====================================================================== -->
  <script>
    (function () {
      'use strict';

      const state = {
        studentCounter: 1,
        level: 'easy', // 'easy' | 'medium' | 'hard'
        timerSecondsConfig: 0, // 0 | 120 | 240
        timeRemaining: 0,
        timerInterval: null,
        timerRunning: false,
        turnStartTimestamp: null,
        questions: [],
        isGraded: false,
        history: []
      };

      // Referencias DOM
      const studentNameInput = document.getElementById('student-name-input');
      const studentCourseInput = document.getElementById('student-course-input');
      const btnClearName = document.getElementById('btn-clear-name');
      const activeStudentLabel = document.getElementById('active-student-label');
      const activeLevelBadge = document.getElementById('active-level-badge');
      const turnBadge = document.getElementById('turn-badge');
      const answeredCounter = document.getElementById('answered-counter');

      const timerDisplayBadge = document.getElementById('timer-display-badge');
      const timerCountdownText = document.getElementById('timer-countdown-text');
      const timeExpiredTag = document.getElementById('time-expired-tag');

      const colLeft = document.getElementById('col-left-questions');
      const colRight = document.getElementById('col-right-questions');
      const quickExamForm = document.getElementById('quick-exam-form');
      const resultSummaryPanel = document.getElementById('result-summary-panel');
      const btnGradeNow = document.getElementById('btn-grade-now');
      const btnNextTop = document.getElementById('btn-next-student-top');
      const btnNextBottom = document.getElementById('btn-next-student-bottom');

      const sessionHistoryBody = document.getElementById('session-history-body');
      const sessionCountBadge = document.getElementById('session-count-badge');
      const sessionAvg10 = document.getElementById('session-avg-10');
      const clearConfirmBar = document.getElementById('clear-confirm-bar');

      let toastTimeout = null;

      function showToast(msg) {
        const toastEl = document.getElementById('toast-message');
        const toastText = document.getElementById('toast-text');
        if (!toastEl || !toastText) return;
        toastText.textContent = msg;
        toastEl.classList.remove('hidden');
        if (toastTimeout) clearTimeout(toastTimeout);
        toastTimeout = setTimeout(() => {
          toastEl.classList.add('hidden');
        }, 2800);
      }

      function formatGrade10(num) {
        return num.toFixed(2).replace('.', ',');
      }

      function escapeHtml(text) {
        return String(text)
          .replace(/&/g, '&amp;')
          .replace(/</g, '&lt;')
          .replace(/>/g, '&gt;')
          .replace(/"/g, '&quot;')
          .replace(/'/g, '&#039;');
      }

      function randInt(min, max) {
        return Math.floor(Math.random() * (max - min + 1)) + min;
      }

      function getCurrentStudentDisplay() {
        const typedName = studentNameInput.value.trim();
        const typedCourse = studentCourseInput.value.trim();
        const baseName = typedName !== '' ? typedName : `Estudiante #${state.studentCounter}`;
        return typedCourse !== '' ? `${baseName} (${typedCourse})` : baseName;
      }

      function getLevelShortLabel(level) {
        if (level === 'medium') return 'Nivel Medio';
        if (level === 'hard') return 'Nivel Difícil';
        return 'Nivel Fácil';
      }

      function getLevelDetailedLabel(level) {
        if (level === 'medium') return 'Nivel Medio (Paréntesis y 3 pasos)';
        if (level === 'hard') return 'Nivel Difícil (Potencias, raíces y enteros)';
        return 'Nivel Fácil (2 pasos básicos)';
      }

      function syncHeaderLabels() {
        activeStudentLabel.textContent = getCurrentStudentDisplay();
        turnBadge.textContent = `Turno #${state.studentCounter}`;
        studentNameInput.placeholder = `Nombre y apellido (Estudiante #${state.studentCounter})`;
        activeLevelBadge.textContent = getLevelDetailedLabel(state.level);

        if (studentNameInput.value.trim() !== '') {
          btnClearName.classList.remove('hidden');
        } else {
          btnClearName.classList.add('hidden');
        }
      }

      // =====================================================================
      // CONTROL DE TEMPORIZADOR Y REGISTRO DE TIEMPO USADO
      // =====================================================================
      function formatSecondsMMSS(totalSeconds) {
        const safe = Math.max(0, Math.floor(totalSeconds));
        const mins = Math.floor(safe / 60);
        const secs = safe % 60;
        return `${String(mins).padStart(2, '0')}:${String(secs).padStart(2, '0')}`;
      }

      function stopTimer() {
        if (state.timerInterval) {
          clearInterval(state.timerInterval);
          state.timerInterval = null;
        }
        state.timerRunning = false;
      }

      function updateTimerBadgeStyle() {
        if (state.timeRemaining <= 20) {
          timerDisplayBadge.classList.add('timer-danger');
        } else {
          timerDisplayBadge.classList.remove('timer-danger');
        }
      }

      function resetTimerDisplay() {
        stopTimer();
        state.turnStartTimestamp = null;
        state.timeRemaining = state.timerSecondsConfig;
        if (state.timerSecondsConfig <= 0) {
          timerDisplayBadge.classList.add('hidden');
          return;
        }
        timerDisplayBadge.classList.remove('hidden');
        timerCountdownText.textContent = formatSecondsMMSS(state.timeRemaining);
        updateTimerBadgeStyle();
      }

      function startTimerIfNeeded() {
        if (state.isGraded) return;
        if (!state.turnStartTimestamp) {
          state.turnStartTimestamp = Date.now();
        }
        if (state.timerSecondsConfig <= 0 || state.timerRunning) return;
        if (state.timeRemaining <= 0) state.timeRemaining = state.timerSecondsConfig;

        state.timerRunning = true;
        updateTimerBadgeStyle();

        state.timerInterval = setInterval(() => {
          if (state.isGraded) {
            stopTimer();
            return;
          }
          state.timeRemaining--;
          timerCountdownText.textContent = formatSecondsMMSS(state.timeRemaining);
          updateTimerBadgeStyle();

          if (state.timeRemaining <= 0) {
            stopTimer();
            showToast('¡Tiempo agotado! Evaluación calificada automáticamente');
            gradeCurrentEvaluation(true);
          }
        }, 1000);
      }

      function computeTimeUsedLabel(byTimeout) {
        if (byTimeout && state.timerSecondsConfig > 0) {
          return formatSecondsMMSS(state.timerSecondsConfig);
        }
        if (state.timerSecondsConfig > 0) {
          const used = Math.max(1, state.timerSecondsConfig - state.timeRemaining);
          return formatSecondsMMSS(used);
        }
        if (state.turnStartTimestamp) {
          const elapsedSec = Math.max(1, Math.round((Date.now() - state.turnStartTimestamp) / 1000));
          return formatSecondsMMSS(elapsedSec);
        }
        return 'Sin tiempo';
      }

      // =====================================================================
      // GENERADORES DE OPERACIONES COMBINADAS POR NIVEL (SIN REPETICIONES)
      // =====================================================================
      function createEasyOperation() {
        const pattern = randInt(1, 6);
        let html = '';
        let key = '';
        let answer = 0;

        if (pattern === 1) {
          // a + b × c
          const a = randInt(2, 15);
          const b = randInt(2, 8);
          const c = randInt(2, 7);
          answer = a + (b * c);
          html = `${a} + ${b} × ${c}`;
          key = `${a}+${b}*${c}`;
        } else if (pattern === 2) {
          // a × b + c
          const a = randInt(2, 8);
          const b = randInt(2, 7);
          const c = randInt(2, 15);
          answer = (a * b) + c;
          html = `${a} × ${b} + ${c}`;
          key = `${a}*${b}+${c}`;
        } else if (pattern === 3) {
          // a − b × c (resultado >= 0)
          const b = randInt(2, 6);
          const c = randInt(2, 6);
          const prod = b * c;
          const a = prod + randInt(1, 14);
          answer = a - prod;
          html = `${a} − ${b} × ${c}`;
          key = `${a}-${b}*${c}`;
        } else if (pattern === 4) {
          // a × b − c (resultado >= 0)
          const a = randInt(3, 8);
          const b = randInt(3, 7);
          const prod = a * b;
          const c = randInt(1, prod - 1);
          answer = prod - c;
          html = `${a} × ${b} − ${c}`;
          key = `${a}*${b}-${c}`;
        } else if (pattern === 5) {
          // (d × q) ÷ d + c
          const d = randInt(2, 8);
          const q = randInt(2, 9);
          const dividend = d * q;
          const c = randInt(2, 14);
          answer = q + c;
          html = `${dividend} ÷ ${d} + ${c}`;
          key = `${dividend}/${d}+${c}`;
        } else {
          // a − (d × q) ÷ d (resultado >= 0)
          const d = randInt(2, 7);
          const q = randInt(2, 8);
          const dividend = d * q;
          const a = q + randInt(2, 15);
          answer = a - q;
          html = `${a} − ${dividend} ÷ ${d}`;
          key = `${a}-${dividend}/${d}`;
        }

        return { html, key, answer };
      }

      function createMediumOperation() {
        const pattern = randInt(1, 6);
        let html = '';
        let key = '';
        let answer = 0;

        if (pattern === 1) {
          // (a + b) × c − d
          const a = randInt(2, 9);
          const b = randInt(2, 8);
          const c = randInt(2, 5);
          const d = randInt(2, 15);
          answer = (a + b) * c - d;
          html = `(${a} + ${b}) × ${c} − ${d}`;
          key = `(${a}+${b})*${c}-${d}`;
        } else if (pattern === 2) {
          // dividend ÷ (a − b) + c
          const divisor = randInt(2, 7);
          const b = randInt(2, 6);
          const a = b + divisor;
          const q = randInt(2, 9);
          const dividend = divisor * q;
          const c = randInt(2, 12);
          answer = q + c;
          html = `${dividend} ÷ (${a} − ${b}) + ${c}`;
          key = `${dividend}/(${a}-${b})+${c}`;
        } else if (pattern === 3) {
          // a × b − dividend ÷ d
          const a = randInt(3, 8);
          const b = randInt(2, 7);
          const d = randInt(2, 6);
          const q = randInt(2, 8);
          const dividend = d * q;
          answer = (a * b) - q;
          html = `${a} × ${b} − ${dividend} ÷ ${d}`;
          key = `${a}*${b}-${dividend}/${d}`;
        } else if (pattern === 4) {
          // a + b × (c − d) (puede dar entero negativo sencillo)
          const a = randInt(3, 12);
          const b = randInt(2, 6);
          const c = randInt(2, 9);
          let d = randInt(2, 9);
          if (c === d) d += 1;
          answer = a + b * (c - d);
          html = `${a} + ${b} × (${c} − ${d})`;
          key = `${a}+${b}*(${c}-${d})`;
        } else if (pattern === 5) {
          // (a − b) × c + d
          const a = randInt(2, 9);
          let b = randInt(2, 10);
          if (a === b) b += 1;
          const c = randInt(2, 6);
          const d = randInt(2, 14);
          answer = (a - b) * c + d;
          html = `(${a} − ${b}) × ${c} + ${d}`;
          key = `(${a}-${b})*${c}+${d}`;
        } else {
          // (a × b + c) ÷ d
          const d = randInt(2, 6);
          const q = randInt(3, 9);
          const totalInside = d * q;
          const a = randInt(2, 6);
          const b = randInt(2, Math.max(2, Math.floor((totalInside - 2) / a)));
          const c = totalInside - (a * b);
          if (c >= 1) {
            answer = q;
            html = `(${a} × ${b} + ${c}) ÷ ${d}`;
            key = `(${a}*${b}+${c})/${d}`;
          } else {
            return createMediumOperation();
          }
        }

        return { html, key, answer };
      }

      function createHardOperation() {
        const pattern = randInt(1, 6);
        let html = '';
        let key = '';
        let answer = 0;

        if (pattern === 1) {
          // b² + m × (x − y)
          const b = randInt(2, 6);
          const m = randInt(2, 5);
          const x = randInt(2, 7);
          const y = x + randInt(1, 5); // x - y negativo
          answer = (b * b) + m * (x - y);
          html = `${b}<sup>2</sup> + ${m} × (${x} − ${y})`;
          key = `${b}^2+${m}*(${x}-${y})`;
        } else if (pattern === 2) {
          // √sq × m − (x − y)
          const root = randInt(3, 9);
          const sq = root * root;
          const m = randInt(2, 5);
          const x = randInt(4, 12);
          const y = randInt(1, 9);
          answer = (root * m) - (x - y);
          html = `√${sq} × ${m} − (${x} − ${y})`;
          key = `sqrt(${sq})*${m}-(${x}-${y})`;
        } else if (pattern === 3) {
          // (a + b) × c − p³ + dividend ÷ d
          const a = randInt(2, 6);
          const b = randInt(1, 5);
          const c = randInt(2, 4);
          const p = randInt(2, 3);
          const d = randInt(2, 5);
          const q = randInt(2, 6);
          const dividend = d * q;
          answer = ((a + b) * c) - Math.pow(p, 3) + q;
          html = `(${a} + ${b}) × ${c} − ${p}<sup>3</sup> + ${dividend} ÷ ${d}`;
          key = `(${a}+${b})*${c}-${p}^3+${dividend}/${d}`;
        } else if (pattern === 4) {
          // [a − (b × c)] + √sq
          const a = randInt(3, 10);
          const b = randInt(2, 5);
          const c = randInt(2, 4);
          const root = randInt(3, 8);
          const sq = root * root;
          answer = (a - (b * c)) + root;
          html = `[${a} − (${b} × ${c})] + √${sq}`;
          key = `[${a}-(${b}*${c})]+sqrt(${sq})`;
        } else if (pattern === 5) {
          // b² × c − (x + y) ÷ d
          const b = randInt(2, 5);
          const c = randInt(2, 4);
          const d = randInt(2, 5);
          const q = randInt(2, 6);
          const sumXY = d * q;
          const x = randInt(2, sumXY - 2);
          const y = sumXY - x;
          answer = (b * b * c) - q;
          html = `${b}<sup>2</sup> × ${c} − (${x} + ${y}) ÷ ${d}`;
          key = `${b}^2*${c}-(${x}+${y})/${d}`;
        } else {
          // p³ − m × (x − y) − √sq
          const p = randInt(2, 4);
          const m = randInt(2, 4);
          const x = randInt(5, 11);
          const y = randInt(1, 8);
          const root = randInt(2, 7);
          const sq = root * root;
          answer = Math.pow(p, 3) - m * (x - y) - root;
          html = `${p}<sup>3</sup> − ${m} × (${x} − ${y}) − √${sq}`;
          key = `${p}^3-${m}*(${x}-${y})-sqrt(${sq})`;
        }

        return { html, key, answer };
      }

      function generate10Questions() {
        const uniqueMap = new Map();
        let guard = 0;

        while (uniqueMap.size < 10 && guard < 500) {
          guard++;
          let op;
          if (state.level === 'medium') {
            op = createMediumOperation();
          } else if (state.level === 'hard') {
            op = createHardOperation();
          } else {
            op = createEasyOperation();
          }

          if (!uniqueMap.has(op.key)) {
            uniqueMap.set(op.key, op);
          }
        }

        state.questions = Array.from(uniqueMap.values()).map((item, idx) => ({
          number: idx + 1,
          html: item.html,
          answer: item.answer
        }));

        state.isGraded = false;
        timeExpiredTag.classList.add('hidden');
      }

      // =====================================================================
      // RENDERIZADO DE LAS 10 FILAS EN 2 COLUMNAS (1-5 IZQ, 6-10 DER)
      // =====================================================================
      function renderQuestionsGrid() {
        colLeft.innerHTML = '';
        colRight.innerHTML = '';

        state.questions.forEach((q, idx) => {
          const row = document.createElement('div');
          row.id = `q-card-${q.number}`;
          row.className = 'q-row';

          row.innerHTML = `
            <div class="q-left">
              <span class="q-num">${q.number}.</span>
              <label for="ans-${q.number}" class="q-label">
                ${q.html} <span class="q-equals">=</span>
              </label>
            </div>
            <div class="q-right">
              <input type="text" inputmode="numeric" pattern="-?[0-9]*" id="ans-${q.number}" data-idx="${idx}"
                autocomplete="off" placeholder="?" class="q-input">
              <span id="feedback-${q.number}" class="q-feedback hidden"></span>
            </div>
          `;

          if (q.number <= 5) {
            colLeft.appendChild(row);
          } else {
            colRight.appendChild(row);
          }
        });

        bindInputsBehavior();
        updateAnsweredCount();
      }

      function sanitizeSignedIntegerInput(inputEl) {
        let val = inputEl.value.replace(/[^0-9-]/g, '');
        if (val.indexOf('-') > 0) {
          val = val.replace(/-/g, '');
        }
        if ((val.match(/-/g) || []).length > 1) {
          val = '-' + val.replace(/-/g, '');
        }
        if (inputEl.value !== val) {
          inputEl.value = val;
        }
      }

      function bindInputsBehavior() {
        const inputs = Array.from(document.querySelectorAll('.q-input'));

        inputs.forEach((input, idx) => {
          input.addEventListener('input', () => {
            sanitizeSignedIntegerInput(input);
            startTimerIfNeeded();
            updateAnsweredCount();
          });

          input.addEventListener('keydown', (e) => {
            if (e.key === 'Enter') {
              e.preventDefault();
              if (state.isGraded) {
                startNextStudentTurn();
                return;
              }
              const next = inputs[idx + 1];
              if (next) {
                next.focus();
                next.select();
              } else {
                // En la casilla 10, Enter califica automáticamente
                gradeCurrentEvaluation(false);
              }
            }
          });
        });
      }

      function updateAnsweredCount() {
        const inputs = Array.from(document.querySelectorAll('.q-input'));
        const filled = inputs.filter(inp => {
          const v = inp.value.trim();
          return v !== '' && v !== '-';
        }).length;
        answeredCounter.textContent = `${filled} / 10`;
      }

      // =====================================================================
      // CALIFICACIÓN AUTOMÁTICA (10 ÍTEMS × 2 PTS = 20 PTS → NOTA SOBRE 10)
      // =====================================================================
      function gradeCurrentEvaluation(byTimeout = false) {
        if (state.isGraded) return;
        const timeUsedStr = computeTimeUsedLabel(byTimeout);
        state.isGraded = true;
        stopTimer();

        if (byTimeout) {
          timeExpiredTag.classList.remove('hidden');
        } else {
          timeExpiredTag.classList.add('hidden');
        }

        let correctCount = 0;

        state.questions.forEach((q) => {
          const card = document.getElementById(`q-card-${q.number}`);
          const input = document.getElementById(`ans-${q.number}`);
          const feedback = document.getElementById(`feedback-${q.number}`);

          const rawValue = input.value.trim();
          const isValidNumber = /^-?\d+$/.test(rawValue);
          const numericValue = isValidNumber ? parseInt(rawValue, 10) : NaN;
          const isCorrect = isValidNumber && numericValue === q.answer;

          input.readOnly = true;
          feedback.classList.remove('hidden');

          if (isCorrect) {
            correctCount++;
            card.classList.add('q-correct');
            input.classList.add('input-correct');
            feedback.className = 'q-feedback fb-correct';
            feedback.textContent = '✓ +2 pts';
          } else {
            card.classList.add('q-wrong');
            input.classList.add('input-wrong');
            feedback.className = 'q-feedback fb-wrong';
            feedback.textContent = `✗ Era ${q.answer}`;
          }
        });

        const points20 = correctCount * 2;
        const grade10 = correctCount * 1.0;
        const studentName = getCurrentStudentDisplay();

        document.getElementById('final-grade-10').textContent = formatGrade10(grade10);
        document.getElementById('final-points-20').textContent = String(points20);
        document.getElementById('result-student-title').textContent = studentName;
        document.getElementById('result-points-detail').textContent =
          `${correctCount} de 10 aciertos — Tiempo usado: ${timeUsedStr}`;

        const scoreBox10 = document.getElementById('score-box-10');
        const qualTag = document.getElementById('result-qualitative-tag');

        scoreBox10.className = 'score-box';
        qualTag.className = 'qual-badge';

        if (grade10 >= 9) {
          qualTag.textContent = 'Domina (DAR)';
        } else if (grade10 >= 7) {
          scoreBox10.classList.add('score-indigo');
          qualTag.classList.add('qual-indigo');
          qualTag.textContent = 'Alcanza (AAR)';
        } else if (grade10 >= 5) {
          scoreBox10.classList.add('score-amber');
          qualTag.classList.add('qual-amber');
          qualTag.textContent = 'Próximo (PAAR)';
        } else {
          scoreBox10.classList.add('score-rose');
          qualTag.classList.add('qual-rose');
          qualTag.textContent = 'Refuerzo (NAAR)';
        }

        resultSummaryPanel.classList.remove('hidden');
        btnGradeNow.classList.add('hidden');
        btnNextBottom.classList.remove('hidden');

        state.history.push({
          order: state.history.length + 1,
          name: studentName,
          levelLabel: getLevelShortLabel(state.level),
          timeUsed: timeUsedStr,
          correct: correctCount,
          points20,
          grade10
        });

        renderSessionHistory();

        setTimeout(() => {
          btnNextTop.focus();
        }, 50);
      }

      // =====================================================================
      // SIGUIENTE ESTUDIANTE Y REGISTRO DE SESIÓN
      // =====================================================================
      function startNextStudentTurn() {
        state.studentCounter++;
        studentNameInput.value = '';
        syncHeaderLabels();

        resultSummaryPanel.classList.add('hidden');
        btnNextBottom.classList.add('hidden');
        btnGradeNow.classList.remove('hidden');

        generate10Questions();
        renderQuestionsGrid();
        resetTimerDisplay();

        if (state.timerSecondsConfig > 0) {
          startTimerIfNeeded();
        }

        const firstInput = document.getElementById('ans-1');
        if (firstInput) firstInput.focus();
      }

      function renderSessionHistory() {
        const total = state.history.length;
        sessionCountBadge.textContent = `${total} ${total === 1 ? 'evaluado' : 'evaluados'}`;

        if (total === 0) {
          sessionAvg10.textContent = '0,00 / 10';
          sessionHistoryBody.innerHTML = `
            <tr>
              <td colspan="7" class="text-center" style="padding:2rem 1rem; color:#94a3b8;">
                Aún no hay estudiantes calificados. Completa las 10 operaciones y presiona <strong>Calificar</strong>.
              </td>
            </tr>
          `;
          return;
        }

        const sum10 = state.history.reduce((acc, item) => acc + item.grade10, 0);
        sessionAvg10.textContent = `${formatGrade10(sum10 / total)} / 10`;

        sessionHistoryBody.innerHTML = state.history
          .slice()
          .reverse()
          .map((item) => {
            let chipClass = 'chip-rose';
            if (item.grade10 >= 9) chipClass = 'chip-green';
            else if (item.grade10 >= 7) chipClass = 'chip-indigo';
            else if (item.grade10 >= 5) chipClass = 'chip-amber';

            return `
              <tr>
                <td class="text-center" style="font-weight:700; color:#64748b;">${item.order}</td>
                <td style="font-weight:700;">${escapeHtml(item.name)}</td>
                <td class="text-center" style="color:#475569; font-weight:600;">${escapeHtml(item.levelLabel)}</td>
                <td class="text-center" style="font-family:monospace; font-weight:700; color:#334155;">${escapeHtml(item.timeUsed)}</td>
                <td class="text-center" style="font-weight:700;">${item.correct} / 10</td>
                <td class="text-center" style="font-weight:700;">${item.points20} / 20</td>
                <td class="text-right">
                  <span class="grade-chip ${chipClass}">${formatGrade10(item.grade10)}</span>
                </td>
              </tr>
            `;
          })
          .join('');
      }

      // =====================================================================
      // EVENTOS DE INTERFAZ Y PÍLDORAS
      // =====================================================================
      studentNameInput.addEventListener('input', syncHeaderLabels);
      studentCourseInput.addEventListener('input', syncHeaderLabels);

      studentNameInput.addEventListener('keydown', (e) => {
        if (e.key === 'Enter') {
          e.preventDefault();
          startTimerIfNeeded();
          const firstInput = document.getElementById('ans-1');
          if (firstInput) firstInput.focus();
        }
      });

      studentCourseInput.addEventListener('keydown', (e) => {
        if (e.key === 'Enter') {
          e.preventDefault();
          startTimerIfNeeded();
          const firstInput = document.getElementById('ans-1');
          if (firstInput) firstInput.focus();
        }
      });

      btnClearName.addEventListener('click', () => {
        studentNameInput.value = '';
        syncHeaderLabels();
        studentNameInput.focus();
      });

      // Píldoras de nivel
      const levelPillButtons = Array.from(document.querySelectorAll('.level-pill-btn'));
      levelPillButtons.forEach((btn) => {
        btn.addEventListener('click', () => {
          const selectedLevel = btn.getAttribute('data-level');
          if (!selectedLevel) return;
          state.level = selectedLevel;

          levelPillButtons.forEach(b => b.classList.remove('active'));
          btn.classList.add('active');
          syncHeaderLabels();

          if (!state.isGraded) {
            generate10Questions();
            renderQuestionsGrid();
            resetTimerDisplay();
            const firstInput = document.getElementById('ans-1');
            if (firstInput) firstInput.focus();
          }
        });
      });

      // Píldoras de tiempo
      const timerPillButtons = Array.from(document.querySelectorAll('.timer-pill'));
      timerPillButtons.forEach((btn) => {
        btn.addEventListener('click', () => {
          const seconds = Number(btn.getAttribute('data-seconds')) || 0;
          state.timerSecondsConfig = seconds;

          timerPillButtons.forEach(b => b.classList.remove('active'));
          btn.classList.add('active');

          if (!state.isGraded) {
            resetTimerDisplay();
            const firstInput = document.getElementById('ans-1');
            if (firstInput) firstInput.focus();
          }
        });
      });

      document.getElementById('btn-shuffle-questions').addEventListener('click', () => {
        if (state.isGraded) {
          startNextStudentTurn();
          return;
        }
        generate10Questions();
        renderQuestionsGrid();
        resetTimerDisplay();
        const firstInput = document.getElementById('ans-1');
        if (firstInput) firstInput.focus();
        showToast('10 nuevas operaciones combinadas generadas');
      });

      quickExamForm.addEventListener('submit', (e) => {
        e.preventDefault();
        gradeCurrentEvaluation(false);
      });

      btnNextTop.addEventListener('click', startNextStudentTurn);
      btnNextBottom.addEventListener('click', startNextStudentTurn);

      document.getElementById('btn-copy-results').addEventListener('click', () => {
        if (state.history.length === 0) {
          showToast('No hay notas registradas para copiar');
          return;
        }
        const header = 'N°\tEstudiante\tNivel\tTiempo usado\tAciertos/10\tPuntaje/20\tNota/10';
        const rows = state.history.map(r =>
          `${r.order}\t${r.name}\t${r.levelLabel}\t${r.timeUsed}\t${r.correct}/10\t${r.points20}/20\t${formatGrade10(r.grade10)}`
        );
        const fullText = [header, ...rows].join('\n');

        const tempArea = document.createElement('textarea');
        tempArea.value = fullText;
        tempArea.style.position = 'fixed';
        tempArea.style.opacity = '0';
        document.body.appendChild(tempArea);
        tempArea.select();
        try {
          document.execCommand('copy');
          showToast('Tabla copiada para pegar en Excel o WhatsApp');
        } catch (err) {
          showToast('No se pudo copiar automáticamente');
        }
        document.body.removeChild(tempArea);
      });

      document.getElementById('btn-download-csv').addEventListener('click', () => {
        if (state.history.length === 0) {
          showToast('No hay notas registradas para descargar');
          return;
        }
        const bom = '\uFEFF';
        const csvHeader = 'N°,Estudiante,Nivel,Tiempo usado,Aciertos/10,Puntaje/20,Nota/10\n';
        const csvRows = state.history.map(r =>
          `${r.order},"${r.name.replace(/"/g, '""')}","${r.levelLabel}","${r.timeUsed}",${r.correct},${r.points20},"${formatGrade10(r.grade10)}"`
        ).join('\n');

        const blob = new Blob([bom + csvHeader + csvRows], { type: 'text/csv;charset=utf-8;' });
        const url = URL.createObjectURL(blob);
        const link = document.createElement('a');
        const dateTag = new Date().toISOString().slice(0, 10);
        link.href = url;
        link.download = `calificaciones_operaciones_combinadas_${dateTag}.csv`;
        document.body.appendChild(link);
        link.click();
        document.body.removeChild(link);
        URL.revokeObjectURL(url);
        showToast('Archivo CSV descargado');
      });

      document.getElementById('btn-clear-history').addEventListener('click', () => {
        if (state.history.length === 0) {
          showToast('La lista ya está vacía');
          return;
        }
        clearConfirmBar.classList.remove('hidden');
      });

      document.getElementById('btn-cancel-clear').addEventListener('click', () => {
        clearConfirmBar.classList.add('hidden');
      });

      document.getElementById('btn-confirm-clear').addEventListener('click', () => {
        state.history = [];
        state.studentCounter = 1;
        clearConfirmBar.classList.add('hidden');
        renderSessionHistory();
        syncHeaderLabels();
        showToast('Lista de calificaciones reiniciada');
      });

      // =====================================================================
      // INICIALIZACIÓN INMEDIATA
      // =====================================================================
      function initApp() {
        syncHeaderLabels();
        if (state.questions.length === 0) {
          generate10Questions();
          renderQuestionsGrid();
          resetTimerDisplay();
        }
        const firstInput = document.getElementById('ans-1');
        if (firstInput) firstInput.focus();
      }

      initApp();
      window.addEventListener('DOMContentLoaded', initApp);
    })();
  </script>
</body>
</html>
```
