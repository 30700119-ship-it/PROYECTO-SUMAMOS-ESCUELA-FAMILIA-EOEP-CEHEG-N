<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<meta name="theme-color" content="#48C5C7">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-title" content="Absentismo">
<title>Canal Absentismo · EOEP Cehegín</title>
<link rel="manifest" href="manifest.json">
<style>
  :root {
    --turquesa: #48C5C7;
    --turquesa-osc: #2A9A9C;
    --turquesa-cl: #E8F8F8;
    --verde: #4CAF50;
    --verde-bg: #E8F5E9;
    --amarillo: #FFA726;
    --amarillo-bg: #FFF3E0;
    --rojo: #E53935;
    --rojo-bg: #FFEBEE;
    --azul: #5C6BC0;
    --azul-bg: #E8EAF6;
    --texto: #2C3E50;
    --gris: #F5F7FA;
    --borde: #E0E6ED;
    --blanco: #FFFFFF;
    --sombra: 0 2px 8px rgba(0,0,0,0.06);
  }
  * { box-sizing: border-box; margin: 0; padding: 0; -webkit-tap-highlight-color: transparent; }
  html, body { height: 100%; }
  body {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Arial, sans-serif;
    background: var(--gris);
    color: var(--texto);
    line-height: 1.5;
    font-size: 16px;
    -webkit-font-smoothing: antialiased;
  }
  .app { max-width: 700px; margin: 0 auto; min-height: 100vh; background: var(--blanco); position: relative; padding-bottom: 80px; }

  /* HEADER */
  header {
    background: var(--blanco);
    padding: 14px 18px 12px;
    border-bottom: 3px solid var(--turquesa);
    position: sticky;
    top: 0;
    z-index: 100;
  }
  .header-content { display: flex; align-items: center; gap: 12px; }
  .logo-circle {
    width: 38px; height: 38px;
    border-radius: 50%;
    background: var(--turquesa);
    color: var(--blanco);
    display: flex; align-items: center; justify-content: center;
    font-weight: 800; font-size: 14px;
    flex-shrink: 0;
  }
  .header-title { flex: 1; }
  .header-title h1 { font-size: 14px; font-weight: 800; line-height: 1.2; }
  .header-title .subtitle { font-size: 11px; color: #7A8B99; font-weight: 500; margin-top: 1px; }
  .badge {
    background: var(--turquesa-cl);
    color: var(--turquesa-osc);
    padding: 4px 10px;
    border-radius: 12px;
    font-size: 10px;
    font-weight: 800;
    text-transform: uppercase;
    letter-spacing: 0.3px;
  }

  main { padding: 14px 18px; }
  .pantalla { display: none; }
  .pantalla.activa { display: block; animation: fadeIn 0.25s ease-out; }
  @keyframes fadeIn { from { opacity: 0; transform: translateY(6px); } to { opacity: 1; transform: translateY(0); } }

  /* CARDS */
  .card {
    background: var(--blanco);
    border: 1px solid var(--borde);
    border-radius: 14px;
    padding: 16px;
    margin-bottom: 14px;
    box-shadow: var(--sombra);
  }
  .card-title {
    font-size: 12px;
    font-weight: 800;
    text-transform: uppercase;
    color: var(--turquesa-osc);
    margin-bottom: 12px;
    letter-spacing: 0.6px;
  }

  /* WELCOME */
  .welcome-hero {
    background: linear-gradient(135deg, var(--turquesa) 0%, var(--turquesa-osc) 100%);
    color: var(--blanco);
    padding: 26px 20px;
    border-radius: 16px;
    margin-bottom: 16px;
    text-align: center;
  }
  .welcome-hero h2 { font-size: 20px; font-weight: 800; margin-bottom: 6px; }
  .welcome-hero p { font-size: 13px; opacity: 0.95; line-height: 1.5; }

  /* INTRO CARD (pantalla inicio) */
  .intro-card {
    background: var(--blanco);
    border: 1px solid var(--borde);
    border-left: 4px solid var(--turquesa);
    border-radius: 12px;
    padding: 18px 16px;
    margin-bottom: 18px;
    box-shadow: var(--sombra);
  }
  .intro-titulo {
    font-size: 14px;
    font-weight: 800;
    color: var(--turquesa-osc);
    margin-bottom: 10px;
    text-transform: uppercase;
    letter-spacing: 0.4px;
  }
  .intro-texto {
    font-size: 13px;
    line-height: 1.55;
    color: var(--texto);
    margin-bottom: 14px;
  }
  .intro-bloque {
    background: var(--turquesa-cl);
    border-radius: 10px;
    padding: 12px 14px;
    margin-bottom: 10px;
  }
  .intro-bloque-titulo {
    font-size: 13px;
    font-weight: 800;
    color: var(--turquesa-osc);
    margin-bottom: 4px;
  }
  .intro-bloque-texto {
    font-size: 12px;
    line-height: 1.5;
    color: var(--texto);
  }
  .intro-cierre {
    font-size: 12px;
    line-height: 1.5;
    color: #5A6B7A;
    margin-top: 12px;
    padding-top: 10px;
    border-top: 1px dashed var(--borde);
    font-style: italic;
  }
  .seleccion-titulo {
    font-size: 13px;
    font-weight: 800;
    color: var(--turquesa-osc);
    text-transform: uppercase;
    letter-spacing: 0.5px;
    margin-bottom: 10px;
    margin-left: 4px;
  }

  /* MODALIDAD CARDS */
  .modalidad-grid { display: grid; gap: 12px; }
  .modalidad {
    background: var(--blanco);
    border: 2px solid var(--borde);
    border-radius: 14px;
    padding: 18px;
    cursor: pointer;
    transition: all 0.18s;
    display: flex;
    align-items: center;
    gap: 14px;
    text-align: left;
    width: 100%;
    font-family: inherit;
  }
  .modalidad:active { transform: scale(0.98); }
  .modalidad.azul { border-color: #C5CAE9; }
  .modalidad.azul:hover, .modalidad.azul:focus { border-color: var(--azul); background: var(--azul-bg); }
  .modalidad.turquesa { border-color: #B8E5E6; }
  .modalidad.turquesa:hover, .modalidad.turquesa:focus { border-color: var(--turquesa); background: var(--turquesa-cl); }
  .modalidad.naranja { border-color: #FFCC80; }
  .modalidad.naranja:hover, .modalidad.naranja:focus { border-color: var(--amarillo); background: var(--amarillo-bg); }

  .mod-icon {
    width: 52px; height: 52px;
    border-radius: 14px;
    display: flex; align-items: center; justify-content: center;
    flex-shrink: 0;
  }
  .modalidad.turquesa .mod-icon { background: var(--turquesa-cl); color: var(--turquesa-osc); }
  .modalidad.azul .mod-icon { background: var(--azul-bg); color: var(--azul); }
  .modalidad.naranja .mod-icon { background: var(--amarillo-bg); color: var(--amarillo); }
  .mod-icon svg { width: 28px; height: 28px; }

  .mod-content { flex: 1; min-width: 0; }
  .mod-title { font-size: 15px; font-weight: 800; margin-bottom: 3px; }
  .mod-desc { font-size: 11px; color: #5A6B7A; line-height: 1.4; }
  .mod-arrow { color: #99A6B2; flex-shrink: 0; }

  /* CAMPOS */
  .field { margin-bottom: 14px; }
  .field label {
    display: flex;
    align-items: center;
    gap: 6px;
    font-size: 13px;
    font-weight: 700;
    color: var(--texto);
    margin-bottom: 6px;
  }
  .field label .required { color: var(--rojo); }
  .field label .optional { color: #99A6B2; font-weight: 500; font-size: 11px; }
  .field input, .field select, .field textarea {
    width: 100%;
    padding: 12px 14px;
    border: 1.5px solid var(--borde);
    border-radius: 10px;
    font-size: 16px;
    font-family: inherit;
    background: var(--blanco);
    color: var(--texto);
    transition: border-color 0.2s;
  }
  .field input:focus, .field select:focus, .field textarea:focus {
    outline: none;
    border-color: var(--turquesa);
  }
  .field input.error, .field select.error { border-color: var(--rojo); }
  .field-row { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
  .field-row-3 { display: grid; grid-template-columns: 1.2fr 0.8fr 1fr; gap: 8px; }
  .help-text {
    font-size: 11px;
    color: #7A8B99;
    margin-top: 4px;
    line-height: 1.4;
  }

  /* GLOSARIO TOOLTIP */
  .glosario-link {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    width: 16px; height: 16px;
    background: var(--turquesa);
    color: var(--blanco);
    border-radius: 50%;
    font-size: 11px;
    font-weight: 700;
    cursor: pointer;
    border: none;
    font-family: inherit;
    flex-shrink: 0;
  }

  /* TARJETAS GRANDES TRIMESTRE */
  .trim-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 10px; }
  .trim-card {
    background: var(--blanco);
    border: 2px solid var(--borde);
    border-radius: 14px;
    padding: 16px 8px;
    cursor: pointer;
    text-align: center;
    transition: all 0.2s;
    font-family: inherit;
  }
  .trim-card:active { transform: scale(0.97); }
  .trim-card.activa, .trim-card:hover { border-color: var(--turquesa); background: var(--turquesa-cl); }
  .trim-card.activa { box-shadow: 0 4px 14px rgba(72,197,199,0.25); }
  .trim-num {
    font-size: 28px;
    font-weight: 800;
    color: var(--turquesa-osc);
    line-height: 1;
    margin-bottom: 4px;
  }
  .trim-lbl { font-size: 10px; font-weight: 700; text-transform: uppercase; color: var(--texto); margin-bottom: 6px; }
  .trim-fechas { font-size: 10px; color: #7A8B99; margin-bottom: 4px; }
  .trim-indic { font-size: 9px; color: var(--turquesa-osc); font-weight: 700; }

  /* VISTA PREVIA EXPANDIBLE */
  .preview-grupo {
    background: var(--blanco);
    border: 1px solid var(--borde);
    border-radius: 10px;
    margin-bottom: 8px;
    overflow: hidden;
  }
  .preview-grupo-header {
    padding: 12px 14px;
    background: var(--turquesa-cl);
    cursor: pointer;
    display: flex;
    align-items: center;
    gap: 10px;
    user-select: none;
  }
  .preview-grupo-header .icono-grupo {
    width: 30px; height: 30px;
    border-radius: 8px;
    background: var(--turquesa);
    color: var(--blanco);
    display: flex; align-items: center; justify-content: center;
    flex-shrink: 0;
  }
  .preview-grupo-header .icono-grupo svg { width: 18px; height: 18px; }
  .preview-titulo { flex: 1; font-weight: 700; font-size: 13px; color: var(--turquesa-osc); }
  .preview-count { font-size: 11px; color: #5A6B7A; font-weight: 600; }
  .preview-flecha { color: var(--turquesa-osc); transition: transform 0.2s; }
  .preview-grupo.abierto .preview-flecha { transform: rotate(180deg); }
  .preview-items { display: none; padding: 10px 14px 12px; background: var(--blanco); }
  .preview-grupo.abierto .preview-items { display: block; }
  .preview-items li {
    list-style: none;
    padding: 6px 0;
    font-size: 12px;
    color: var(--texto);
    border-bottom: 1px solid var(--gris);
    line-height: 1.4;
  }
  .preview-items li:last-child { border-bottom: none; }
  .preview-items li:before { content: "• "; color: var(--turquesa); font-weight: 700; }

  /* PROGRESS BAR */
  .progress-card {
    background: var(--blanco);
    border: 1px solid var(--borde);
    border-radius: 12px;
    padding: 12px 14px;
    margin-bottom: 14px;
    position: sticky;
    top: 70px;
    z-index: 10;
    box-shadow: var(--sombra);
  }
  .progress-row { display: flex; justify-content: space-between; align-items: center; margin-bottom: 8px; }
  .progress-label { font-size: 12px; font-weight: 700; color: var(--texto); }
  .progress-counter { font-size: 12px; color: var(--turquesa-osc); font-weight: 700; }
  .progress-bar { height: 6px; background: var(--gris); border-radius: 4px; overflow: hidden; }
  .progress-fill { height: 100%; background: linear-gradient(90deg, var(--turquesa) 0%, var(--turquesa-osc) 100%); transition: width 0.3s; border-radius: 4px; }
  .progress-dims { display: grid; grid-template-columns: repeat(3, 1fr); gap: 6px; margin-top: 10px; }
  .progress-dim { text-align: center; font-size: 9px; color: #7A8B99; font-weight: 700; }
  .progress-dim-name { text-transform: uppercase; }
  .progress-dim-count { color: var(--turquesa-osc); margin-top: 2px; font-size: 11px; }

  /* INDICADORES */
  .indicador-grupo {
    background: var(--blanco);
    border: 1px solid var(--borde);
    border-radius: 12px;
    margin-bottom: 12px;
    overflow: hidden;
  }
  .indicador-grupo-header {
    background: var(--turquesa-cl);
    padding: 10px 14px;
    font-size: 12px;
    font-weight: 800;
    color: var(--turquesa-osc);
    border-bottom: 1px solid var(--borde);
    text-transform: uppercase;
    letter-spacing: 0.4px;
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .indicador-grupo-header svg { width: 16px; height: 16px; }
  .indicador { padding: 14px; border-bottom: 1px solid var(--borde); }
  .indicador:last-child { border-bottom: none; }
  .indicador.respondido { background: #FAFCFC; }
  .indicador-pregunta {
    font-size: 14px;
    color: var(--texto);
    margin-bottom: 12px;
    line-height: 1.45;
    font-weight: 500;
  }

  /* OPCIONES SI/EN PROCESO/NO */
  .opciones { display: grid; grid-template-columns: repeat(3, 1fr); gap: 6px; }
  .opcion {
    padding: 11px 4px;
    border: 1.5px solid var(--borde);
    border-radius: 10px;
    background: var(--blanco);
    font-size: 12px;
    font-weight: 700;
    cursor: pointer;
    text-transform: uppercase;
    color: #7A8B99;
    transition: all 0.15s;
    text-align: center;
    user-select: none;
    font-family: inherit;
    letter-spacing: 0.3px;
  }
  .opcion:active { transform: scale(0.96); }
  .opcion[data-value="si"].activo { background: var(--verde); color: var(--blanco); border-color: var(--verde); }
  .opcion[data-value="proceso"].activo { background: var(--amarillo); color: var(--blanco); border-color: var(--amarillo); }
  .opcion[data-value="no"].activo { background: var(--rojo); color: var(--blanco); border-color: var(--rojo); }

  /* BOTONES */
  .btn {
    width: 100%;
    padding: 14px 20px;
    border: none;
    border-radius: 12px;
    background: var(--turquesa);
    color: var(--blanco);
    font-size: 14px;
    font-weight: 800;
    cursor: pointer;
    font-family: inherit;
    text-transform: uppercase;
    letter-spacing: 0.5px;
    transition: all 0.2s;
  }
  .btn:active { transform: scale(0.98); background: var(--turquesa-osc); }
  .btn:disabled { background: var(--borde); color: #99A6B2; cursor: not-allowed; }
  .btn-secondary { background: var(--blanco); color: var(--turquesa-osc); border: 1.5px solid var(--turquesa); }
  .btn-danger { background: var(--rojo); }
  .btn-row { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; }
  .btn-block { margin-bottom: 10px; }

  /* RESULTADO */
  .resultado-card {
    text-align: center;
    padding: 32px 20px;
    border-radius: 16px;
    margin-bottom: 14px;
  }
  .resultado-card.verde { background: var(--verde-bg); border: 2px solid var(--verde); }
  .resultado-card.amarillo { background: var(--amarillo-bg); border: 2px solid var(--amarillo); }
  .resultado-card.rojo { background: var(--rojo-bg); border: 2px solid var(--rojo); }
  .resultado-icono { font-size: 56px; font-weight: 800; line-height: 1; margin-bottom: 10px; }
  .resultado-card.verde .resultado-icono { color: var(--verde); }
  .resultado-card.amarillo .resultado-icono { color: var(--amarillo); }
  .resultado-card.rojo .resultado-icono { color: var(--rojo); }
  .resultado-titulo { font-size: 22px; font-weight: 800; margin-bottom: 6px; }
  .resultado-subtitulo { font-size: 13px; color: var(--texto); }

  .resumen-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 8px; margin-bottom: 14px; }
  .resumen-item {
    text-align: center;
    padding: 14px 6px;
    border-radius: 12px;
    border: 1.5px solid var(--borde);
  }
  .resumen-item.verde { background: var(--verde-bg); border-color: var(--verde); }
  .resumen-item.amarillo { background: var(--amarillo-bg); border-color: var(--amarillo); }
  .resumen-item.rojo { background: var(--rojo-bg); border-color: var(--rojo); }
  .resumen-num { font-size: 30px; font-weight: 800; line-height: 1; }
  .resumen-item.verde .resumen-num { color: var(--verde); }
  .resumen-item.amarillo .resumen-num { color: var(--amarillo); }
  .resumen-item.rojo .resumen-num { color: var(--rojo); }
  .resumen-lbl { font-size: 10px; text-transform: uppercase; color: var(--texto); margin-top: 4px; font-weight: 700; }

  .accion-list { background: var(--blanco); border-radius: 12px; padding: 14px; text-align: left; margin-top: 14px; border: 1px solid var(--borde); }
  .accion-list h3 { font-size: 12px; text-transform: uppercase; color: var(--turquesa-osc); margin-bottom: 10px; letter-spacing: 0.4px; }
  .accion-list ol { padding-left: 20px; }
  .accion-list li { font-size: 13px; margin-bottom: 6px; line-height: 1.45; }

  /* HISTÓRICO */
  .historico-item {
    padding: 12px;
    border: 1px solid var(--borde);
    border-radius: 10px;
    margin-bottom: 8px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 10px;
    cursor: pointer;
    transition: background 0.15s;
  }
  .historico-item:hover { background: var(--gris); }
  .historico-info { flex: 1; min-width: 0; }
  .historico-alumno { font-size: 14px; font-weight: 700; }
  .historico-meta { font-size: 11px; color: #7A8B99; margin-top: 2px; }
  .alerta-pill {
    padding: 4px 10px;
    border-radius: 12px;
    font-size: 10px;
    font-weight: 800;
    text-transform: uppercase;
    flex-shrink: 0;
    letter-spacing: 0.3px;
  }
  .alerta-pill.verde { background: var(--verde); color: var(--blanco); }
  .alerta-pill.amarillo { background: var(--amarillo); color: var(--blanco); }
  .alerta-pill.rojo { background: var(--rojo); color: var(--blanco); }

  .empty-state { text-align: center; padding: 36px 16px; color: #7A8B99; }
  .empty-state svg { width: 56px; height: 56px; margin: 0 auto 10px; color: var(--turquesa); opacity: 0.5; }
  .empty-state p { font-size: 13px; }

  /* COMPARATIVA EVOLUCIÓN */
  .evolucion-card { background: var(--blanco); border: 1px solid var(--borde); border-radius: 12px; padding: 16px; margin-bottom: 12px; }
  .evolucion-titulo { font-size: 13px; font-weight: 700; color: var(--turquesa-osc); margin-bottom: 12px; }
  .evolucion-trims { display: grid; grid-template-columns: repeat(3, 1fr); gap: 10px; }
  .evolucion-trim {
    text-align: center;
    padding: 14px 6px;
    border-radius: 10px;
    border: 1.5px solid var(--borde);
    background: var(--gris);
  }
  .evolucion-trim.verde { background: var(--verde-bg); border-color: var(--verde); }
  .evolucion-trim.amarillo { background: var(--amarillo-bg); border-color: var(--amarillo); }
  .evolucion-trim.rojo { background: var(--rojo-bg); border-color: var(--rojo); }
  .evolucion-trim.empty { background: var(--gris); border-style: dashed; opacity: 0.6; }
  .evolucion-trim-num { font-size: 11px; font-weight: 700; color: #7A8B99; }
  .evolucion-trim-alerta { font-size: 12px; font-weight: 800; margin-top: 4px; text-transform: uppercase; }
  .evolucion-trim.verde .evolucion-trim-alerta { color: var(--verde); }
  .evolucion-trim.amarillo .evolucion-trim-alerta { color: var(--amarillo); }
  .evolucion-trim.rojo .evolucion-trim-alerta { color: var(--rojo); }
  .evolucion-trim-fecha { font-size: 9px; color: #7A8B99; margin-top: 4px; }
  .evolucion-tendencia {
    margin-top: 12px;
    padding: 10px 12px;
    border-radius: 10px;
    font-size: 12px;
    font-weight: 700;
    text-align: center;
  }
  .tendencia-mejora { background: var(--verde-bg); color: var(--verde); }
  .tendencia-estable { background: var(--azul-bg); color: var(--azul); }
  .tendencia-empeora { background: var(--rojo-bg); color: var(--rojo); }

  /* TAB NAV */
  .tab-nav {
    position: fixed;
    bottom: 0; left: 50%;
    transform: translateX(-50%);
    width: 100%; max-width: 700px;
    background: var(--blanco);
    border-top: 1px solid var(--borde);
    display: flex;
    z-index: 50;
  }
  .tab-btn {
    flex: 1;
    padding: 9px 4px;
    background: none;
    border: none;
    font-family: inherit;
    font-size: 9px;
    font-weight: 700;
    color: #99A6B2;
    cursor: pointer;
    text-transform: uppercase;
    text-align: center;
  }
  .tab-btn.active { color: var(--turquesa-osc); }
  .tab-icon { width: 22px; height: 22px; margin: 0 auto 2px; display: block; }

  /* FOOTER */
  footer {
    text-align: center;
    padding: 16px;
    font-size: 10px;
    color: #99A6B2;
    background: var(--blanco);
    border-top: 1px solid var(--borde);
    line-height: 1.6;
  }
  footer strong { color: var(--turquesa-osc); }

  /* TOAST */
  .toast {
    position: fixed;
    bottom: 90px;
    left: 50%;
    transform: translateX(-50%);
    background: var(--texto);
    color: var(--blanco);
    padding: 12px 22px;
    border-radius: 24px;
    font-size: 13px;
    font-weight: 600;
    z-index: 1000;
    opacity: 0;
    pointer-events: none;
    transition: opacity 0.3s, bottom 0.3s;
    max-width: 90%;
    text-align: center;
  }
  .toast.show { opacity: 1; bottom: 100px; }

  /* MODAL */
  .modal-overlay {
    position: fixed; inset: 0;
    background: rgba(0,0,0,0.55);
    display: none;
    align-items: center; justify-content: center;
    z-index: 200;
    padding: 16px;
  }
  .modal-overlay.show { display: flex; }
  .modal {
    background: var(--blanco);
    border-radius: 16px;
    max-width: 500px; width: 100%;
    max-height: 88vh;
    overflow-y: auto;
    padding: 22px;
  }
  .modal h2 { font-size: 17px; margin-bottom: 12px; color: var(--turquesa-osc); font-weight: 800; }
  .modal p { font-size: 13px; margin-bottom: 8px; line-height: 1.5; }
  .modal pre {
    background: var(--gris);
    padding: 12px;
    border-radius: 8px;
    font-size: 11px;
    overflow-x: auto;
    margin: 10px 0;
    white-space: pre-wrap;
    word-break: break-word;
    line-height: 1.4;
  }

  /* INFO BOX */
  .info-box {
    background: var(--turquesa-cl);
    border-left: 4px solid var(--turquesa);
    padding: 12px 14px;
    border-radius: 6px;
    font-size: 12px;
    color: var(--texto);
    margin-bottom: 14px;
    line-height: 1.5;
  }
  .info-box.amarillo { background: var(--amarillo-bg); border-left-color: var(--amarillo); }
  .info-box.azul { background: var(--azul-bg); border-left-color: var(--azul); }

  /* GLOSARIO */
  .glosario-item {
    padding: 12px 0;
    border-bottom: 1px solid var(--borde);
  }
  .glosario-item:last-child { border-bottom: none; }
  .glosario-termino { font-size: 13px; font-weight: 800; color: var(--turquesa-osc); margin-bottom: 4px; }
  .glosario-def { font-size: 12px; color: var(--texto); line-height: 1.5; }

  /* SUCCESS SCREEN */
  .success-screen { text-align: center; padding: 30px 16px; }
  .success-icon {
    width: 80px; height: 80px;
    margin: 0 auto 16px;
    background: var(--verde-bg);
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    color: var(--verde);
    animation: pulse 0.4s ease-out;
  }
  @keyframes pulse {
    0% { transform: scale(0.5); opacity: 0; }
    50% { transform: scale(1.1); }
    100% { transform: scale(1); opacity: 1; }
  }
  .success-icon svg { width: 50px; height: 50px; }
  /* FASE 2 · Estados durante el envío */
  .success-icon.enviando {
    background: rgba(72, 197, 199, 0.15);
    color: var(--turquesa, #48C5C7);
    animation: spinPulse 1.2s ease-in-out infinite;
  }
  .success-icon.enviando svg { display: none; }
  .success-icon.enviando::after {
    content: "";
    width: 36px; height: 36px;
    border: 4px solid rgba(72, 197, 199, 0.25);
    border-top-color: var(--turquesa, #48C5C7);
    border-radius: 50%;
    animation: spin 0.9s linear infinite;
  }
  .success-icon.error {
    background: #FDECEC;
    color: #C0392B;
    animation: shake 0.4s ease-out;
  }
  .success-icon.error svg { display: none; }
  .success-icon.error::after {
    content: "!";
    font-size: 42px; font-weight: 800; line-height: 1;
  }
  @keyframes spin { to { transform: rotate(360deg); } }
  @keyframes spinPulse { 0%,100% { transform: scale(1); } 50% { transform: scale(1.05); } }
  @keyframes shake {
    0%,100% { transform: translateX(0); }
    25% { transform: translateX(-6px); }
    75% { transform: translateX(6px); }
  }
  .success-title { font-size: 20px; font-weight: 800; color: var(--texto); margin-bottom: 6px; }
  .success-subtitle { font-size: 13px; color: #5A6B7A; margin-bottom: 4px; }

  /* Modalidad indicador en header */
  .modo-pill {
    display: inline-block;
    padding: 3px 10px;
    border-radius: 10px;
    font-size: 10px;
    font-weight: 800;
    text-transform: uppercase;
    margin-right: 6px;
    letter-spacing: 0.3px;
  }
  .modo-pill.trim { background: var(--turquesa-cl); color: var(--turquesa-osc); }
  .modo-pill.cons { background: var(--azul-bg); color: var(--azul); }
  .modo-pill.art { background: var(--amarillo-bg); color: var(--amarillo); }

  /* CONSULTA PREVENTIVA */
  .urgencia-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 6px; }
  .urgencia-card {
    padding: 12px 6px;
    border: 1.5px solid var(--borde);
    border-radius: 10px;
    background: var(--blanco);
    text-align: center;
    cursor: pointer;
    font-size: 11px;
    font-weight: 700;
    color: var(--texto);
    transition: all 0.15s;
    font-family: inherit;
  }
  .urgencia-card.activo[data-urg="1"] { background: var(--verde); color: var(--blanco); border-color: var(--verde); }
  .urgencia-card.activo[data-urg="2"] { background: var(--amarillo); color: var(--blanco); border-color: var(--amarillo); }
  .urgencia-card.activo[data-urg="3"] { background: var(--rojo); color: var(--blanco); border-color: var(--rojo); }
</style>
</head>
<body>
<div class="app">

  <header>
    <div class="header-content">
      <div class="logo-circle">A</div>
      <div class="header-title">
        <h1>Canal Absentismo</h1>
        <div class="subtitle">EOEP General Cehegín</div>
      </div>
      <div class="badge" id="headerBadge">v2.2</div>
    </div>
  </header>

  <main>

    <!-- ============ ONBOARDING (primera vez) ============ -->
    <section class="pantalla" id="pantallaOnboarding">
      <div class="welcome-hero">
        <h2>Bienvenido/a</h2>
        <p>Canal de seguimiento y prevención del absentismo escolar entre el equipo docente y el EOEP General Cehegín.</p>
      </div>
      <div class="card">
        <div class="card-title">Identificación inicial</div>
        <p style="font-size: 13px; line-height: 1.5; margin-bottom: 14px; color: #5A6B7A;">
          Solo necesitamos estos datos una vez. Quedarán guardados en tu dispositivo y se asociarán a todos los registros que envíes.
        </p>
        <div class="field">
          <label>Tu nombre y apellidos <span class="required">*</span></label>
          <input type="text" id="onb_nombre" placeholder="Ej. María García López">
        </div>
        <div class="field">
          <label>Tu correo electrónico <span class="required">*</span></label>
          <input type="email" id="onb_email" placeholder="tu.correo@ejemplo.com" autocomplete="email">
          <div class="help-text">Recibirás aquí confirmación de cada envío al EOEP.</div>
        </div>
        <div class="field">
          <label>Centro educativo en el que trabajas <span class="required">*</span></label>
          <input type="text" id="onb_centro" placeholder="Ej. CEIP Ntra. Sra. de las Maravillas" list="centrosList">
          <datalist id="centrosList">
            <option value="CEIP Ntra. Sra. de las Maravillas">
            <option value="CEIP Conde Campillo">
            <option value="CEIP Pedro Rodríguez">
            <option value="CEIP Antonio Robles">
            <option value="CRA Río Argos">
          </datalist>
          <div class="help-text">Empieza a escribir; aparecerán sugerencias.</div>
        </div>
      </div>
      <button class="btn" onclick="completarOnboarding()">Comenzar a usar la aplicación</button>
    </section>

    <!-- ============ INICIO: 3 MODALIDADES ============ -->
    <section class="pantalla" id="pantallaInicio">
      <div class="welcome-hero">
        <h2 id="saludo">Bienvenido/a</h2>
        <p>Canal de seguimiento y prevención del absentismo escolar.</p>
      </div>

      <div class="intro-card">
        <div class="intro-titulo">¿Para qué sirve este canal?</div>
        <p class="intro-texto">
          Esta aplicación es el canal directo entre el tutor o tutora y el EOEP General Cehegín para el <strong>seguimiento y la prevención del absentismo escolar</strong>. Te permite registrar comunicaciones desde el móvil, sin papel y de forma segura.
        </p>
        <div class="intro-bloque">
          <div class="intro-bloque-titulo">Seguimiento trimestral</div>
          <div class="intro-bloque-texto">
            Cumplimentación al cierre de cada trimestre con 39 indicadores. La app calcula automáticamente un nivel de alerta (verde, amarillo o rojo). Cuando la alerta es <strong>amarilla o roja, el caso llega directamente al EOEP</strong> para activar el protocolo correspondiente.
          </div>
        </div>
        <div class="intro-bloque">
          <div class="intro-bloque-titulo">Consulta preventiva</div>
          <div class="intro-bloque-texto">
            Si tienes una inquietud sobre un alumno o alumna y no quieres esperar al cierre del trimestre, puedes <strong>compartir la duda con el EOEP</strong> indicando el grado de urgencia.
          </div>
        </div>
        <p class="intro-cierre">
          Todo el seguimiento queda guardado en tu dispositivo. Puedes consultar el histórico de tus registros, ver la evolución de cada alumno o alumna entre trimestres, y reenviar cualquier registro en cualquier momento.
        </p>
      </div>

      <div class="seleccion-titulo">¿Qué quieres hacer hoy?</div>

      <div class="modalidad-grid">

        <button class="modalidad turquesa" onclick="abrirModalidad('trimestral')">
          <div class="mod-icon">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="3" y="4" width="18" height="18" rx="2"/><path d="M16 2v4M8 2v4M3 10h18"/></svg>
          </div>
          <div class="mod-content">
            <div class="mod-title">Seguimiento trimestral</div>
            <div class="mod-desc">Cumplimentación al cierre de trimestre · 39 indicadores · Cálculo automático de alerta</div>
          </div>
          <svg class="mod-arrow" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="9 18 15 12 9 6"/></svg>
        </button>

        <button class="modalidad azul" onclick="abrirModalidad('consulta')">
          <div class="mod-icon">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 15a2 2 0 0 1-2 2H7l-4 4V5a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2z"/></svg>
          </div>
          <div class="mod-content">
            <div class="mod-title">Consulta preventiva</div>
            <div class="mod-desc">Tengo dudas sobre un alumno/a y quiero que el EOEP lo sepa, sin esperar al trimestre</div>
          </div>
          <svg class="mod-arrow" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="9 18 15 12 9 6"/></svg>
        </button>

        <button class="modalidad naranja" onclick="abrirModalidad('art11')">
          <div class="mod-icon">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M10.29 3.86L1.82 18a2 2 0 0 0 1.71 3h16.94a2 2 0 0 0 1.71-3L13.71 3.86a2 2 0 0 0-3.42 0z"/><line x1="12" y1="9" x2="12" y2="13"/><line x1="12" y1="17" x2="12.01" y2="17"/></svg>
          </div>
          <div class="mod-content">
            <div class="mod-title">Notificación Art. 11 PRAE</div>
            <div class="mod-desc">Registro de ausencia del día · Notificación a la familia · Aviso al EOEP si se acumulan 3+ ausencias</div>
          </div>
          <svg class="mod-arrow" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="9 18 15 12 9 6"/></svg>
        </button>

      </div>

      <div id="resumenInicio" style="margin-top: 16px;"></div>
    </section>

    <!-- ============ TRIMESTRAL: PASO 1 - DATOS ALUMNO ============ -->
    <section class="pantalla" id="pantallaDatos">
      <div class="info-box">
        <span class="modo-pill trim">Trimestral</span>
        <strong>Paso 1 de 3:</strong> Datos del alumno/a y trimestre a evaluar.
      </div>
      <div class="card">
        <div class="card-title">Datos del alumno/a</div>
        <div class="field-row">
          <div class="field">
            <label>Iniciales <span class="required">*</span></label>
            <input type="text" id="alu_iniciales" placeholder="M.G.L." maxlength="10">
          </div>
          <div class="field">
            <label>Nº lista <span class="required">*</span></label>
            <input type="number" id="alu_numlista" placeholder="12" min="1" max="50">
          </div>
        </div>
        <div class="field-row">
          <div class="field">
            <label>Sexo <span class="optional">(opcional)</span></label>
            <select id="alu_sexo">
              <option value="">--</option>
              <option value="M">Niño</option>
              <option value="F">Niña</option>
              <option value="NB">No binario</option>
              <option value="NS">No declara</option>
            </select>
          </div>
          <div class="field">
            <label>Edad <span class="optional">(opcional)</span></label>
            <select id="alu_edad">
              <option value="">--</option>
              <option>3</option><option>4</option><option>5</option>
              <option>6</option><option>7</option><option>8</option>
              <option>9</option><option>10</option><option>11</option>
              <option>12</option>
            </select>
          </div>
        </div>
      </div>
      <div class="card">
        <div class="card-title">Curso y grupo</div>
        <div class="field-row">
          <div class="field">
            <label>Curso <span class="required">*</span></label>
            <select id="alu_curso">
              <option value="">--</option>
              <option>1º EI 3 años</option>
              <option>2º EI 4 años</option>
              <option>3º EI 5 años</option>
              <option>1º EP</option>
              <option>2º EP</option>
              <option>3º EP</option>
              <option>4º EP</option>
              <option>5º EP</option>
              <option>6º EP</option>
            </select>
          </div>
          <div class="field">
            <label>Grupo <span class="required">*</span></label>
            <input type="text" id="alu_grupo" placeholder="A / B / C">
          </div>
        </div>
      </div>
      <div class="card">
        <div class="card-title">Trimestre a evaluar <span style="text-transform:none;font-weight:600;color:#7A8B99;">· Toca el que corresponda</span></div>
        <div class="trim-grid">
          <button class="trim-card" data-trim="1" onclick="seleccionarTrim(1)">
            <div class="trim-num">1º</div>
            <div class="trim-lbl">Trimestre</div>
            <div class="trim-fechas">oct - dic</div>
            <div class="trim-indic">13 indicadores</div>
          </button>
          <button class="trim-card" data-trim="2" onclick="seleccionarTrim(2)">
            <div class="trim-num">2º</div>
            <div class="trim-lbl">Trimestre</div>
            <div class="trim-fechas">ene - mar</div>
            <div class="trim-indic">13 indicadores</div>
          </button>
          <button class="trim-card" data-trim="3" onclick="seleccionarTrim(3)">
            <div class="trim-num">3º</div>
            <div class="trim-lbl">Trimestre</div>
            <div class="trim-fechas">abr - jun</div>
            <div class="trim-indic">12 indicadores</div>
          </button>
        </div>
      </div>
      <div class="btn-row">
        <button class="btn btn-secondary" onclick="irA('pantallaInicio')">Cancelar</button>
        <button class="btn" onclick="continuarADatos()">Continuar →</button>
      </div>
    </section>

    <!-- ============ TRIMESTRAL: PASO 2 - VISTA PREVIA ============ -->
    <section class="pantalla" id="pantallaPreview">
      <div class="info-box">
        <span class="modo-pill trim">Trimestral</span>
        <strong>Paso 2 de 3:</strong> Echa un vistazo a las preguntas que vas a responder. Toca cada bloque para ver su contenido.
      </div>
      <div id="previewContenedor"></div>
      <div class="btn-row">
        <button class="btn btn-secondary" onclick="irA('pantallaDatos')">← Atrás</button>
        <button class="btn" onclick="empezarIndicadores()">Empezar →</button>
      </div>
    </section>

    <!-- ============ TRIMESTRAL: PASO 3 - INDICADORES ============ -->
    <section class="pantalla" id="pantallaIndicadores">
      <div class="progress-card">
        <div class="progress-row">
          <div class="progress-label">Tu progreso</div>
          <div class="progress-counter" id="progressCounter">0 de 0</div>
        </div>
        <div class="progress-bar"><div class="progress-fill" id="progressFill" style="width:0%"></div></div>
        <div class="progress-dims" id="progressDims"></div>
      </div>
      <div id="contenedorIndicadores"></div>
      <div class="card">
        <div class="card-title">Observaciones del tutor/a <span style="text-transform:none;font-weight:600;color:#7A8B99;">(opcional)</span></div>
        <div class="field">
          <textarea id="observaciones" rows="3" placeholder="Información complementaria que el EOEP deba conocer..."></textarea>
        </div>
      </div>
      <div class="btn-row">
        <button class="btn btn-secondary" onclick="irA('pantallaPreview')">← Atrás</button>
        <button class="btn" onclick="calcularYMostrar()">Calcular alerta →</button>
      </div>
    </section>

    <!-- ============ RESULTADO TRIMESTRAL ============ -->
    <section class="pantalla" id="pantallaResultado">
      <div id="resultadoContenido"></div>
      <div class="btn-row" style="margin-top: 14px;">
        <button class="btn btn-secondary" onclick="irA('pantallaIndicadores')">← Revisar</button>
        <button class="btn" onclick="enviarAlEOEP()">Guardar y enviar al EOEP</button>
      </div>
    </section>

    <!-- ============ MODALIDAD CONSULTA PREVENTIVA ============ -->
    <section class="pantalla" id="pantallaConsulta">
      <div class="info-box azul">
        <span class="modo-pill cons">Consulta</span>
        Comparte cualquier inquietud o duda sobre un alumno/a sin necesidad de cumplimentar el seguimiento completo.
      </div>
      <div class="card">
        <div class="card-title">Datos básicos</div>
        <div class="field-row">
          <div class="field">
            <label>Iniciales <span class="required">*</span></label>
            <input type="text" id="cons_iniciales" placeholder="M.G.L.">
          </div>
          <div class="field">
            <label>Nº lista</label>
            <input type="number" id="cons_numlista" placeholder="12">
          </div>
        </div>
        <div class="field-row">
          <div class="field">
            <label>Curso <span class="required">*</span></label>
            <select id="cons_curso">
              <option value="">--</option>
              <option>1º EI 3 años</option><option>2º EI 4 años</option><option>3º EI 5 años</option>
              <option>1º EP</option><option>2º EP</option><option>3º EP</option>
              <option>4º EP</option><option>5º EP</option><option>6º EP</option>
            </select>
          </div>
          <div class="field">
            <label>Grupo</label>
            <input type="text" id="cons_grupo" placeholder="A / B">
          </div>
        </div>
      </div>
      <div class="card">
        <div class="card-title">Tipo de consulta</div>
        <div class="field">
          <label>¿Sobre qué quieres consultar? <span class="required">*</span></label>
          <select id="cons_tipo">
            <option value="">Selecciona el tipo de duda</option>
            <option>Comportamiento que me preocupa</option>
            <option>Familia con dificultad de contacto</option>
            <option>Patrón de ausencias atípico</option>
            <option>Estado emocional del alumno/a</option>
            <option>Posible NEAE no detectada previamente</option>
            <option>Dificultad de aprendizaje</option>
            <option>Conflicto en el grupo de iguales</option>
            <option>Otra (especificar abajo)</option>
          </select>
        </div>
        <div class="field">
          <label>Descripción <span class="required">*</span></label>
          <textarea id="cons_descripcion" rows="4" placeholder="Describe brevemente la situación, el contexto y qué te preocupa..."></textarea>
        </div>
      </div>
      <div class="card">
        <div class="card-title">Nivel de urgencia <span class="required">*</span></div>
        <div class="urgencia-grid">
          <button class="urgencia-card" data-urg="1" onclick="marcarUrgencia(1)">
            <div style="font-size:18px;margin-bottom:4px;">📋</div>
            <div>Comentar en próxima visita</div>
          </button>
          <button class="urgencia-card" data-urg="2" onclick="marcarUrgencia(2)">
            <div style="font-size:18px;margin-bottom:4px;">⏱</div>
            <div>Necesito orientación esta semana</div>
          </button>
          <button class="urgencia-card" data-urg="3" onclick="marcarUrgencia(3)">
            <div style="font-size:18px;margin-bottom:4px;">⚠</div>
            <div>Es urgente</div>
          </button>
        </div>
      </div>
      <div class="btn-row">
        <button class="btn btn-secondary" onclick="irA('pantallaInicio')">Cancelar</button>
        <button class="btn" onclick="enviarConsulta()">Enviar consulta al EOEP</button>
      </div>
    </section>

    <!-- ============ MODALIDAD ART. 11 ============ -->
    <section class="pantalla" id="pantallaArt11">
      <div class="info-box amarillo">
        <span class="modo-pill art">Art. 11</span>
        Registro de ausencia del día y notificación a la familia (Art. 11 PRAE · Orden 24/11/2006). Si se acumulan 3 o más en 15 días del mismo alumno/a, se enviará automáticamente al EOEP.
      </div>
      <div class="card">
        <div class="card-title">Datos del alumno/a</div>
        <div class="field-row">
          <div class="field">
            <label>Iniciales <span class="required">*</span></label>
            <input type="text" id="art_iniciales" placeholder="M.G.L.">
          </div>
          <div class="field">
            <label>Nº lista <span class="required">*</span></label>
            <input type="number" id="art_numlista" placeholder="12">
          </div>
        </div>
        <div class="field-row">
          <div class="field">
            <label>Curso <span class="required">*</span></label>
            <select id="art_curso">
              <option value="">--</option>
              <option>1º EI 3 años</option><option>2º EI 4 años</option><option>3º EI 5 años</option>
              <option>1º EP</option><option>2º EP</option><option>3º EP</option>
              <option>4º EP</option><option>5º EP</option><option>6º EP</option>
            </select>
          </div>
          <div class="field">
            <label>Grupo <span class="required">*</span></label>
            <input type="text" id="art_grupo" placeholder="A / B">
          </div>
        </div>
      </div>
      <div class="card">
        <div class="card-title">Tipo de ausencia</div>
        <div class="field">
          <label>¿Cómo ha sido la ausencia hoy? <span class="required">*</span></label>
          <select id="art_tipo">
            <option value="">--</option>
            <option>Día completo</option>
            <option>Sesión de mañana</option>
            <option>Sesión de tarde</option>
            <option>Retraso significativo (más de 30 min)</option>
          </select>
        </div>
        <div class="field">
          <label>Fecha de la ausencia</label>
          <input type="date" id="art_fecha">
        </div>
      </div>
      <div class="card">
        <div class="card-title">Notificación a la familia</div>
        <div class="field">
          <label>¿Cómo has notificado a la familia? <span class="required">*</span></label>
          <select id="art_via">
            <option value="">--</option>
            <option>Llamada telefónica</option>
            <option>Mensaje (SMS / WhatsApp)</option>
            <option>Nota escrita</option>
            <option>Aún no ha sido posible contactar</option>
          </select>
        </div>
        <div class="field">
          <label>Respuesta de la familia</label>
          <select id="art_respuesta">
            <option value="">--</option>
            <option>La familia justifica adecuadamente</option>
            <option>La familia justifica genéricamente (sin documentación)</option>
            <option>La familia no responde</option>
            <option>Pendiente de confirmar</option>
          </select>
        </div>
        <div class="field">
          <label>Observaciones <span class="optional">(opcional)</span></label>
          <textarea id="art_obs" rows="2" placeholder="Cualquier dato adicional relevante..."></textarea>
        </div>
      </div>
      <div class="btn-row">
        <button class="btn btn-secondary" onclick="irA('pantallaInicio')">Cancelar</button>
        <button class="btn" onclick="enviarArt11()">Guardar registro Art. 11</button>
      </div>
    </section>

    <!-- ============ ÉXITO ============ -->
    <section class="pantalla" id="pantallaExito">
      <div class="success-screen">
        <div class="success-icon">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="3"><polyline points="20 6 9 17 4 12"/></svg>
        </div>
        <div class="success-title" id="exitoTitulo">Registro completado</div>
        <div class="success-subtitle" id="exitoSubtitulo">Se ha enviado correctamente al EOEP General Cehegín.</div>
        <div class="success-subtitle" style="margin-top: 6px;">Recibirás una confirmación en tu correo electrónico.</div>
      </div>
      <button class="btn btn-block" onclick="irA('pantallaInicio')">Volver al inicio</button>
      <button class="btn btn-secondary" onclick="irA('pantallaHistorico')">Ver mi histórico</button>
    </section>

    <!-- ============ HISTÓRICO ============ -->
    <section class="pantalla" id="pantallaHistorico">
      <div class="card">
        <div class="card-title">Mis registros enviados</div>
        <div id="listaHistorico"></div>
      </div>
      <div id="comparativaContainer"></div>
      <button class="btn btn-secondary btn-block" onclick="exportarTodo()">Exportar todos mis registros</button>
      <button class="btn btn-danger" onclick="confirmarLimpiar()" style="font-size:12px;">Borrar mis registros locales</button>
    </section>

    <!-- ============ DETALLE EVOLUCIÓN ALUMNO ============ -->
    <section class="pantalla" id="pantallaEvolucion">
      <div id="evolucionContenido"></div>
      <button class="btn btn-secondary btn-block" onclick="irA('pantallaHistorico')">← Volver</button>
    </section>

    <!-- ============ INFO + GLOSARIO ============ -->
    <section class="pantalla" id="pantallaInfo">
      <div class="card">
        <div class="card-title">Acerca de</div>
        <p style="font-size: 13px; line-height: 1.6;">
          Aplicación interna del <strong>EOEP General Cehegín</strong> para el seguimiento y la prevención del absentismo escolar en los centros adscritos del Noroeste de Murcia.
        </p>
        <p style="font-size: 13px; line-height: 1.6; margin-top: 10px;">
          Canal directo de comunicación entre el equipo docente y el EOEP. Sustituye la cumplimentación en papel por un registro digital con cálculo automático del nivel de alerta y aviso al equipo cuando procede.
        </p>
      </div>
      <div class="card">
        <div class="card-title">Niveles de alerta</div>
        <div style="display: flex; gap: 10px; margin-bottom: 10px; align-items: flex-start;">
          <span class="alerta-pill verde">Verde</span>
          <span style="font-size: 12px; line-height:1.4;">0-2 indicadores en NO. Seguimiento ordinario, no requiere intervención del PSC.</span>
        </div>
        <div style="display: flex; gap: 10px; margin-bottom: 10px; align-items: flex-start;">
          <span class="alerta-pill amarillo">Amarilla</span>
          <span style="font-size: 12px; line-height:1.4;">3-4 NO o 6 o más EN PROCESO. Comunicación al PSC del EOEP.</span>
        </div>
        <div style="display: flex; gap: 10px; align-items: flex-start;">
          <span class="alerta-pill rojo">Roja</span>
          <span style="font-size: 12px; line-height:1.4;">5 o más NO. Derivación urgente al EOEP.</span>
        </div>
      </div>
      <div class="card">
        <div class="card-title">Glosario PRAE</div>
        <div class="glosario-item">
          <div class="glosario-termino">PRAE</div>
          <div class="glosario-def">Plan Regional para la Prevención, Seguimiento y Control del Absentismo Escolar de la Región de Murcia (Orden 24 de noviembre de 2006).</div>
        </div>
        <div class="glosario-item">
          <div class="glosario-termino">Art. 11 PRAE</div>
          <div class="glosario-def">Obliga al centro a notificar a la familia el mismo día de la ausencia injustificada de un menor.</div>
        </div>
        <div class="glosario-item">
          <div class="glosario-termino">EOEP</div>
          <div class="glosario-def">Equipo de Orientación Educativa y Psicopedagógica. En Cehegín atiende los centros de Infantil y Primaria del Noroeste de Murcia.</div>
        </div>
        <div class="glosario-item">
          <div class="glosario-termino">PSC</div>
          <div class="glosario-def">Profesional de Servicios a la Comunidad (también llamado/a PTSC). Miembro del EOEP que coordina con familias y Servicios Sociales.</div>
        </div>
        <div class="glosario-item">
          <div class="glosario-termino">Alerta media (PRAE)</div>
          <div class="glosario-def">Situación en la que el alumno/a presenta entre el 10% y el 20% de faltas injustificadas mensuales. Activa protocolo de coordinación entre tutor/a, jefatura, PSC y familia.</div>
        </div>
        <div class="glosario-item">
          <div class="glosario-termino">Alerta alta (PRAE)</div>
          <div class="glosario-def">Más del 20% de faltas injustificadas mensuales. Activa protocolo multidisciplinar urgente y posible derivación a Servicios Sociales y Comisión Municipal de Absentismo.</div>
        </div>
        <div class="glosario-item">
          <div class="glosario-termino">NEAE</div>
          <div class="glosario-def">Necesidades Específicas de Apoyo Educativo. Alumnado que requiere atención específica por discapacidad, TDAH, dificultades específicas de aprendizaje, altas capacidades, etc.</div>
        </div>
        <div class="glosario-item">
          <div class="glosario-termino">Plumier / DELPHOS</div>
          <div class="glosario-def">Sistemas de gestión académica oficiales de la Consejería de Educación de Murcia donde se registran ausencias y otros datos del alumnado.</div>
        </div>
      </div>
      <div class="card">
        <div class="card-title">Marco normativo</div>
        <p style="font-size: 12px; line-height: 1.7;">
          · LOE-LOMLOE<br>
          · RD 95/2022 (Educación Infantil)<br>
          · RD 157/2022 (Educación Primaria)<br>
          · Decreto 196/2022 Murcia (Infantil)<br>
          · Decreto 359/2009 Murcia (atención a la diversidad)<br>
          · Orden 24 de noviembre de 2006 (PRAE Región de Murcia)
        </p>
      </div>
      <div class="card">
        <div class="card-title">Tu identificación</div>
        <p id="infoUsuario" style="font-size: 13px; line-height: 1.6;"></p>
        <button class="btn btn-secondary" style="margin-top:10px;font-size:12px;" onclick="resetearUsuario()">Cambiar identificación</button>
      </div>
    </section>

  </main>

  <nav class="tab-nav" id="tabNav">
    <button class="tab-btn active" data-tab="pantallaInicio" onclick="cambiarTab(this)">
      <svg class="tab-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M3 9l9-7 9 7v11a2 2 0 01-2 2H5a2 2 0 01-2-2z"/></svg>
      Inicio
    </button>
    <button class="tab-btn" data-tab="pantallaHistorico" onclick="cambiarTab(this)">
      <svg class="tab-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="3 13 9 13 12 4 15 20 18 11 21 11"/></svg>
      Histórico
    </button>
    <button class="tab-btn" data-tab="pantallaInfo" onclick="cambiarTab(this)">
      <svg class="tab-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="10"/><line x1="12" y1="16" x2="12" y2="12"/><line x1="12" y1="8" x2="12.01" y2="8"/></svg>
      Info
    </button>
  </nav>

</div>

<div class="toast" id="toast"></div>

<div class="modal-overlay" id="modal">
  <div class="modal">
    <h2 id="modalTitulo"></h2>
    <div id="modalContenido"></div>
    <div class="btn-row" style="margin-top: 16px;">
      <button class="btn btn-secondary" onclick="cerrarModal()">Cerrar</button>
      <button class="btn" id="btnModalAccion">Aceptar</button>
    </div>
  </div>
</div>

<footer>
  <strong>Canal Absentismo · EOEP General Cehegín</strong><br>
  Equipo de Orientación Educativa y Psicopedagógica del Noroeste de Murcia<br>
  Consejería de Educación · Región de Murcia · v2.2
</footer>

<script>
// =============== INDICADORES (POSITIVO) ===============
const INDICADORES = {
  "1": [
    { grupo: "Asistencia", icono: "asistencia", items: [
      { id: "1A1a", pregunta: "¿La asistencia del alumno/a se mantiene regular este trimestre (menos de 5 faltas injustificadas)?", accion: "Entrevista inmediata con la familia. Registrar en Plumier. Iniciar seguimiento semanal." },
      { id: "1A1b", pregunta: "¿El alumno/a asiste con normalidad los lunes y los viernes (sin patrón sistemático de ausencias)?", accion: "Explorar con la familia los motivos. Valorar fin de semana extendido." },
      { id: "1A1c", pregunta: "¿La puntualidad de entrada al aula es adecuada (menos de 3 retrasos por semana)?", accion: "Contactar con la familia. Acuerdos sobre el horario de entrada." },
      { id: "1A1d", pregunta: "¿Las ausencias se justifican adecuadamente y con documentación cuando procede?", accion: "Solicitar justificante médico. Si se reitera, valorar con el PSC." },
      { id: "1A1e", pregunta: "¿La situación de domicilio y núcleo de convivencia se mantiene estable este trimestre?", accion: "Actualizar datos. Verificar que la asistencia no se ve afectada." }
    ]},
    { grupo: "Familia", icono: "familia", items: [
      { id: "1A2a", pregunta: "¿La familia responde a los contactos del tutor/a (llamadas, mensajes, notas)?", accion: "Escalar al PSC. Probar diferentes vías de contacto." },
      { id: "1A2b", pregunta: "¿La familia asistió a la reunión trimestral de tutores?", accion: "Enviar resumen escrito. Fijar cita individual." },
      { id: "1A2c", pregunta: "¿La familia muestra acuerdo con las normas de asistencia del centro?", accion: "Entrevista con jefatura. Entregar reglamento y normativa PRAE." },
      { id: "1A2d", pregunta: "¿Se observa adecuada supervisión del menor en el hogar (material, alimentación, vestuario, higiene)?", accion: "Valorar con el PSC coordinación con Servicios Sociales." }
    ]},
    { grupo: "Estado emocional", icono: "emocional", items: [
      { id: "1A3a", pregunta: "¿El alumno/a ha completado el período de adaptación con normalidad y entra al aula sin resistencia?", accion: "Derivar a orientador/a del EOEP. Plan de adaptación individualizado." },
      { id: "1A3b", pregunta: "¿El comportamiento y estado de ánimo del alumno/a se mantienen estables?", accion: "Comunicar al orientador/a. Explorar factores externos." },
      { id: "1A3c", pregunta: "¿El alumno/a expresa una actitud positiva hacia el colegio?", accion: "Entrevista con el alumno/a. Analizar factores de exclusión o malestar." },
      { id: "1A3d", pregunta: "¿El alumno/a se integra adecuadamente con su grupo de iguales?", accion: "Activar acción tutorial. Informar al EOEP si persiste." }
    ]}
  ],
  "2": [
    { grupo: "Evolución asistencia", icono: "asistencia", items: [
      { id: "2B1a", pregunta: "¿Las faltas injustificadas se mantienen igual o han disminuido respecto al 1er trimestre?", accion: "Reunión: tutor/a + PSC + jefatura. Activar protocolo alerta media." },
      { id: "2B1b", pregunta: "¿No se han producido ausencias prolongadas (más de 5 días consecutivos) sin justificación?", accion: "Aplicar Art. 11 PRAE. Coordinar con PSC." },
      { id: "2B1c", pregunta: "¿El patrón de faltas ha mejorado tras las medidas aplicadas en el 1er trimestre?", accion: "Revisar y reforzar medidas. Valorar reunión multidisciplinar." },
      { id: "2B1d", pregunta: "¿No han aparecido ausencias nuevas no detectadas en el 1er trimestre?", accion: "Aplicar herramienta de detección temprana. Valorar nivel de riesgo." },
      { id: "2B1e", pregunta: "¿La familia se ajusta al calendario escolar (sin solicitar ausencias programadas de larga duración)?", accion: "Informar por escrito del impacto. Firmar acuerdo de mínimos." }
    ]},
    { grupo: "Acuerdos con familia", icono: "familia", items: [
      { id: "2B2a", pregunta: "¿La familia ha cumplido los acuerdos establecidos en el 1er trimestre?", accion: "Entrevista formal con jefatura. Nuevo compromiso por escrito." },
      { id: "2B2b", pregunta: "¿La situación familiar se mantiene estable (sin nuevas situaciones de riesgo)?", accion: "Valorar con el PSC actualizar coordinación con Servicios Sociales." },
      { id: "2B2c", pregunta: "¿La familia ha participado en alguna actividad formativa o informativa del centro?", accion: "Contacto personal y empático. Alternativa de encuentro." },
      { id: "2B2d", pregunta: "¿La familia muestra apertura y colaboración con las medidas propuestas?", accion: "Reunión: tutor/a + orientador/a + PSC. Adaptar el enfoque." }
    ]},
    { grupo: "Eficacia de medidas", icono: "evolucion", items: [
      { id: "2B3a", pregunta: "¿Las medidas preventivas aplicadas están produciendo mejora visible en la asistencia?", accion: "Reunión multidisciplinar urgente. Rediseñar el plan de actuación." },
      { id: "2B3b", pregunta: "¿El alumno/a mantiene el ritmo curricular del grupo (sin desfase relacionado con ausencias)?", accion: "Activar refuerzo educativo. Coordinar con el equipo del ciclo." },
      { id: "2B3c", pregunta: "¿La implicación familiar ha mejorado tras las actuaciones del 1er trimestre?", accion: "Intensificar coordinación con el PSC. Valorar derivación SS.SS." },
      { id: "2B3d", pregunta: "¿No se han detectado nuevos factores de riesgo social desde el 1er trimestre?", accion: "Actualizar diagnóstico de riesgo. Ampliar red de coordinación." }
    ]}
  ],
  "3": [
    { grupo: "Cierre patrón anual", icono: "asistencia", items: [
      { id: "3C1a", pregunta: "¿El porcentaje total de faltas injustificadas a final de curso se mantiene por debajo del 10% (umbral PRAE)?", accion: "Registrar en informe final. Trasladar al tutor/a siguiente como alerta prioritaria." },
      { id: "3C1b", pregunta: "¿El alumno/a presenta un patrón estable de asistencia a lo largo de los tres trimestres?", accion: "Abrir/actualizar expediente. Reunión de cierre con PSC, orientador/a y jefatura." },
      { id: "3C1c", pregunta: "¿La asistencia se mantiene regular en el último mes del curso (mayo-junio)?", accion: "Contacto inmediato con la familia. Registrar e informar." },
      { id: "3C1d", pregunta: "¿La continuidad del alumno/a en el centro está confirmada para el próximo curso?", accion: "Solicitar info del centro de destino. Trasladar historial de seguimiento." },
      { id: "3C1e", pregunta: "¿La asistencia del alumno/a se ha mantenido por encima del 90% del total de días lectivos del curso?", accion: "Calcular el porcentaje exacto de asistencia anual. Si está entre 80-90% (alerta media PRAE), incluir en informe final y trasladar al tutor/a siguiente. Si está por debajo del 80% (alerta alta PRAE), derivación urgente al EOEP y posible Comisión Municipal de Absentismo." }
    ]},
    { grupo: "Trabajo con familia", icono: "familia", items: [
      { id: "3C2a", pregunta: "¿La familia ha mostrado mejora en su implicación durante el curso?", accion: "Documentar proceso completo. Valorar derivación a Comisión Municipal de Absentismo." },
      { id: "3C2b", pregunta: "¿Se ha establecido algún acuerdo estable con la familia durante el curso?", accion: "Informe de cierre detallado. Trasladar a SS.SS. y EOEP." },
      { id: "3C2c", pregunta: "¿La asistencia ha aumentado de forma significativa gracias al trabajo con la familia?", accion: "Reforzar positivamente el cambio. Registrar como buena práctica." },
      { id: "3C2d", pregunta: "¿La familia ha participado en alguna actividad del centro a lo largo del curso?", accion: "Consolidar el vínculo. Proponer participación continuada." }
    ]},
    { grupo: "Traspaso curso siguiente", icono: "evolucion", items: [
      { id: "3C3a", pregunta: "¿Se ha elaborado informe de traspaso para el tutor/a del próximo curso?", accion: "Informe de traspaso al tutor/a siguiente con historial y medidas eficaces." },
      { id: "3C3b", pregunta: "¿No persisten factores de riesgo estructurales identificados para el próximo curso?", accion: "Incluir en el Plan de Prevención del Absentismo de la PGA siguiente." },
      { id: "3C3c", pregunta: "¿Las medidas preventivas aplicadas han demostrado ser eficaces?", accion: "Documentar como buena práctica en la memoria. Inclusión en plan del centro." },
      { id: "3C3d", pregunta: "¿Los casos detectados quedan resueltos o con plan de continuidad al cierre del curso?", accion: "Trasladar al EOEP para coordinación con IES de referencia." }
    ]}
  ]
};

const ICONOS_GRUPO = {
  asistencia: '<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="3" y="4" width="18" height="18" rx="2"/><path d="M16 2v4M8 2v4M3 10h18"/></svg>',
  familia: '<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M23 21v-2a4 4 0 0 0-3-3.87M16 3.13a4 4 0 0 1 0 7.75"/></svg>',
  emocional: '<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="10"/><path d="M8 14s1.5 2 4 2 4-2 4-2"/><line x1="9" y1="9" x2="9.01" y2="9"/><line x1="15" y1="9" x2="15.01" y2="9"/></svg>',
  evolucion: '<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="22 7 13.5 15.5 8.5 10.5 2 17"/><polyline points="16 7 22 7 22 13"/></svg>'
};

// =============== ESTADO ===============
const STORAGE_USUARIO = "sumamos_usuario_v1";
const STORAGE_REGISTROS = "sumamos_registros_v2";
const STORAGE_ART11 = "sumamos_art11_v1";
const EMAIL_EOEP = "eoepcehegin@gmail.com";
// FASE 2 · Endpoint Apps Script (motor de envío en eoepcehegin@gmail.com)
const APPS_SCRIPT_URL = "https://script.google.com/macros/s/AKfycbxRORz0qpeC7XsVOGzWZP2wasUs1EwMitDGKUOirzT0nUgIsNMrnKXx-x2ERARnIpKs/exec";
const ENVIO_TIMEOUT_MS = 15000;

let usuario = null;
let estado = {
  modo: "", // "trimestral" | "consulta" | "art11"
  trimestre: "",
  alumno: { iniciales: "", numlista: "", sexo: "", edad: "", curso: "", grupo: "" },
  respuestas: {},
  observaciones: "",
  fecha: "",
  alerta: "",
  consulta: { iniciales:"", numlista:"", curso:"", grupo:"", tipo:"", descripcion:"", urgencia:0 },
  art11: { iniciales:"", numlista:"", curso:"", grupo:"", tipo:"", fecha:"", via:"", respuesta:"", obs:"" }
};

// =============== INIT ===============
function init() {
  const u = localStorage.getItem(STORAGE_USUARIO);
  if (u) {
    usuario = JSON.parse(u);
    irA('pantallaInicio');
    actualizarSaludo();
    renderResumenInicio();
  } else {
    irA('pantallaOnboarding');
    document.getElementById('tabNav').style.display = 'none';
  }
}

function completarOnboarding() {
  const nombre = document.getElementById('onb_nombre').value.trim();
  const email = document.getElementById('onb_email').value.trim();
  const centro = document.getElementById('onb_centro').value.trim();
  if (!nombre || !email || !centro) { showToast("Completa todos los campos"); return; }
  if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email)) { showToast("Revisa el formato del email"); return; }
  usuario = { nombre, email, centro, alta: new Date().toISOString() };
  localStorage.setItem(STORAGE_USUARIO, JSON.stringify(usuario));
  document.getElementById('tabNav').style.display = 'flex';
  actualizarSaludo();
  irA('pantallaInicio');
  renderResumenInicio();
}

function actualizarSaludo() {
  document.getElementById('saludo').textContent = `Bienvenido/a`;
}

function resetearUsuario() {
  if (confirm("¿Quieres cambiar tu identificación? Tus registros guardados se mantendrán.")) {
    localStorage.removeItem(STORAGE_USUARIO);
    location.reload();
  }
}

// =============== NAVEGACIÓN ===============
function irA(id) {
  document.querySelectorAll('.pantalla').forEach(p => p.classList.remove('activa'));
  document.getElementById(id).classList.add('activa');
  window.scrollTo(0, 0);
  document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
  const tabBtn = document.querySelector(`.tab-btn[data-tab="${id}"]`);
  if (tabBtn) tabBtn.classList.add('active');
  if (id === 'pantallaHistorico') renderHistorico();
  if (id === 'pantallaInicio') { renderResumenInicio(); document.getElementById('headerBadge').textContent = 'v2.2'; }
  if (id === 'pantallaInfo') {
    if (usuario) {
      document.getElementById('infoUsuario').innerHTML = 
        `<strong>${usuario.nombre}</strong><br>${usuario.email}<br>${usuario.centro}`;
    }
  }
}

function cambiarTab(btn) {
  irA(btn.getAttribute('data-tab'));
}

// =============== ABRIR MODALIDAD ===============
function abrirModalidad(modo) {
  estado.modo = modo;
  if (modo === "trimestral") {
    estado.alumno = { iniciales:"", numlista:"", sexo:"", edad:"", curso:"", grupo:"" };
    estado.trimestre = "";
    estado.respuestas = {};
    estado.observaciones = "";
    document.querySelectorAll('.trim-card').forEach(c => c.classList.remove('activa'));
    ['alu_iniciales','alu_numlista','alu_sexo','alu_edad','alu_curso','alu_grupo'].forEach(id => {
      const e = document.getElementById(id);
      if (e) e.value = "";
    });
    irA('pantallaDatos');
    document.getElementById('headerBadge').textContent = 'TRIMESTRAL';
  } else if (modo === "consulta") {
    estado.consulta = { iniciales:"", numlista:"", curso:"", grupo:"", tipo:"", descripcion:"", urgencia:0 };
    ['cons_iniciales','cons_numlista','cons_curso','cons_grupo','cons_tipo','cons_descripcion'].forEach(id => {
      const e = document.getElementById(id);
      if (e) e.value = "";
    });
    document.querySelectorAll('.urgencia-card').forEach(c => c.classList.remove('activo'));
    irA('pantallaConsulta');
    document.getElementById('headerBadge').textContent = 'CONSULTA';
  } else if (modo === "art11") {
    estado.art11 = { iniciales:"", numlista:"", curso:"", grupo:"", tipo:"", fecha:"", via:"", respuesta:"", obs:"" };
    ['art_iniciales','art_numlista','art_curso','art_grupo','art_tipo','art_via','art_respuesta','art_obs'].forEach(id => {
      const e = document.getElementById(id);
      if (e) e.value = "";
    });
    document.getElementById('art_fecha').value = new Date().toISOString().slice(0,10);
    irA('pantallaArt11');
    document.getElementById('headerBadge').textContent = 'ART. 11';
  }
}

// =============== TRIMESTRAL ===============
function seleccionarTrim(num) {
  estado.trimestre = String(num);
  document.querySelectorAll('.trim-card').forEach(c => c.classList.remove('activa'));
  document.querySelector(`.trim-card[data-trim="${num}"]`).classList.add('activa');
}

function continuarADatos() {
  const a = estado.alumno;
  a.iniciales = document.getElementById('alu_iniciales').value.trim().toUpperCase();
  a.numlista = document.getElementById('alu_numlista').value.trim();
  a.sexo = document.getElementById('alu_sexo').value;
  a.edad = document.getElementById('alu_edad').value;
  a.curso = document.getElementById('alu_curso').value;
  a.grupo = document.getElementById('alu_grupo').value.trim().toUpperCase();
  if (!a.iniciales || !a.numlista || !a.curso || !a.grupo) { showToast("Completa los campos obligatorios"); return; }
  if (!estado.trimestre) { showToast("Selecciona el trimestre a evaluar"); return; }
  renderPreview();
  irA('pantallaPreview');
}

function renderPreview() {
  const cont = document.getElementById('previewContenedor');
  const grupos = INDICADORES[estado.trimestre];
  let html = `<div class="card"><div class="card-title">Vista previa del ${estado.trimestre}º trimestre</div>`;
  html += `<p style="font-size:12px;color:#5A6B7A;margin-bottom:14px;">Estos son los bloques de preguntas que vas a responder. Tócalos para ver el detalle.</p>`;
  grupos.forEach((g, idx) => {
    html += `
      <div class="preview-grupo" id="prev-${idx}">
        <div class="preview-grupo-header" onclick="togglePreview(${idx})">
          <div class="icono-grupo">${ICONOS_GRUPO[g.icono]}</div>
          <div class="preview-titulo">${g.grupo}</div>
          <div class="preview-count">${g.items.length} preguntas</div>
          <svg class="preview-flecha" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="6 9 12 15 18 9"/></svg>
        </div>
        <ul class="preview-items">
          ${g.items.map(i => `<li>${i.pregunta}</li>`).join('')}
        </ul>
      </div>`;
  });
  html += `</div>`;
  cont.innerHTML = html;
}

function togglePreview(idx) {
  document.getElementById(`prev-${idx}`).classList.toggle('abierto');
}

function empezarIndicadores() {
  renderIndicadores();
  irA('pantallaIndicadores');
}

function renderIndicadores() {
  const cont = document.getElementById('contenedorIndicadores');
  cont.innerHTML = '';
  const grupos = INDICADORES[estado.trimestre];
  grupos.forEach(g => {
    const div = document.createElement('div');
    div.className = 'indicador-grupo';
    let html = `<div class="indicador-grupo-header">${ICONOS_GRUPO[g.icono]} ${g.grupo}</div>`;
    g.items.forEach(item => {
      const val = estado.respuestas[item.id] || "";
      html += `
        <div class="indicador ${val?'respondido':''}" id="ind-${item.id}">
          <div class="indicador-pregunta">${item.pregunta}</div>
          <div class="opciones" data-id="${item.id}">
            <button class="opcion ${val==='si'?'activo':''}" data-value="si" onclick="marcar('${item.id}','si')">SÍ</button>
            <button class="opcion ${val==='proceso'?'activo':''}" data-value="proceso" onclick="marcar('${item.id}','proceso')">EN PROCESO</button>
            <button class="opcion ${val==='no'?'activo':''}" data-value="no" onclick="marcar('${item.id}','no')">NO</button>
          </div>
        </div>`;
    });
    div.innerHTML = html;
    cont.appendChild(div);
  });
  document.getElementById('observaciones').value = estado.observaciones || "";
  actualizarProgreso();
}

function marcar(id, valor) {
  estado.respuestas[id] = valor;
  const grupo = document.querySelector(`.opciones[data-id="${id}"]`);
  grupo.querySelectorAll('.opcion').forEach(b => b.classList.remove('activo'));
  grupo.querySelector(`[data-value="${valor}"]`).classList.add('activo');
  document.getElementById(`ind-${id}`).classList.add('respondido');
  actualizarProgreso();
}

function actualizarProgreso() {
  const grupos = INDICADORES[estado.trimestre];
  let total = 0, respondidos = 0;
  let porGrupo = grupos.map(g => {
    let r = 0;
    g.items.forEach(i => { total++; if (estado.respuestas[i.id]) { r++; respondidos++; } });
    return { nombre: g.grupo, respondidos: r, total: g.items.length };
  });
  document.getElementById('progressCounter').textContent = `${respondidos} de ${total}`;
  document.getElementById('progressFill').style.width = `${(respondidos/total)*100}%`;
  document.getElementById('progressDims').innerHTML = porGrupo.map(p => 
    `<div class="progress-dim"><div class="progress-dim-name">${p.nombre.split(' ')[0]}</div><div class="progress-dim-count">${p.respondidos}/${p.total}</div></div>`
  ).join('');
}

function calcularAlerta() {
  let si=0, proceso=0, no=0;
  const grupos = INDICADORES[estado.trimestre];
  let total = 0;
  grupos.forEach(g => g.items.forEach(i => {
    total++;
    const r = estado.respuestas[i.id];
    if (r==='si') si++; else if (r==='proceso') proceso++; else if (r==='no') no++;
  }));
  const sinResponder = total - (si+proceso+no);
  let nivel = "verde";
  if (no >= 5) nivel = "rojo";
  else if (no >= 3 || proceso >= 6) nivel = "amarillo";
  return { nivel, si, proceso, no, sinResponder, total };
}

function calcularYMostrar() {
  estado.observaciones = document.getElementById('observaciones').value.trim();
  const r = calcularAlerta();
  if (r.sinResponder > 0) {
    if (!confirm(`Quedan ${r.sinResponder} indicadores sin responder. ¿Continuar igualmente?`)) return;
  }
  estado.alerta = r.nivel;
  estado.fecha = new Date().toISOString();
  mostrarResultado(r);
  irA('pantallaResultado');
}

function mostrarResultado(r) {
  const cfg = {
    verde: { titulo: "ALERTA VERDE", subtitulo: "Seguimiento ordinario", icono: "✓",
      acciones: ["Registrar en tutoría y mantener contacto habitual con la familia.","No requiere intervención del PSC en este momento.","Próxima revisión: inicio del siguiente trimestre."]},
    amarillo: { titulo: "ALERTA AMARILLA", subtitulo: "Comunicación al PSC del EOEP", icono: "!",
      acciones: ["Comunicar al PSC del EOEP en los próximos días.","Reforzar la comunicación con la familia.","Activar o revisar las medidas preventivas individualizadas del centro.","Entrevista formal con la familia en los 15 días siguientes."]},
    rojo: { titulo: "ALERTA ROJA", subtitulo: "Derivación urgente al EOEP", icono: "!!",
      acciones: ["Derivación urgente al PSC del EOEP.","Reunión multidisciplinar (tutor/a + jefatura + PSC + orientador/a) en plazo de 1 semana.","Valorar coordinación inmediata con Servicios Sociales.","Si es 3er trimestre, elaborar informe de traspaso prioritario."]}
  };
  const c = cfg[r.nivel];
  const a = estado.alumno;
  document.getElementById('resultadoContenido').innerHTML = `
    <div class="resultado-card ${r.nivel}">
      <div class="resultado-icono">${c.icono}</div>
      <div class="resultado-titulo">${c.titulo}</div>
      <div class="resultado-subtitulo">${c.subtitulo}</div>
    </div>
    <div class="card">
      <div class="card-title">Recuento de respuestas</div>
      <div class="resumen-grid">
        <div class="resumen-item verde"><div class="resumen-num">${r.si}</div><div class="resumen-lbl">SÍ</div></div>
        <div class="resumen-item amarillo"><div class="resumen-num">${r.proceso}</div><div class="resumen-lbl">EN PROCESO</div></div>
        <div class="resumen-item rojo"><div class="resumen-num">${r.no}</div><div class="resumen-lbl">NO</div></div>
      </div>
      <p style="font-size:11px; color:#7A8B99; text-align:center;">${r.total - r.sinResponder} de ${r.total} indicadores valorados</p>
    </div>
    <div class="card">
      <div class="card-title">Datos del registro</div>
      <p style="font-size:13px; line-height:1.6;">
        <strong>Alumno/a:</strong> ${a.iniciales} (nº ${a.numlista})<br>
        <strong>Curso/Grupo:</strong> ${a.curso} ${a.grupo}<br>
        <strong>Centro:</strong> ${usuario.centro}<br>
        <strong>Tutor/a:</strong> ${usuario.nombre}<br>
        <strong>Trimestre:</strong> ${estado.trimestre}º
      </p>
    </div>
    <div class="accion-list">
      <h3>Acciones a realizar</h3>
      <ol>${c.acciones.map(a => `<li>${a}</li>`).join('')}</ol>
    </div>`;
}

// =============== CONSULTA PREVENTIVA ===============
function marcarUrgencia(n) {
  estado.consulta.urgencia = n;
  document.querySelectorAll('.urgencia-card').forEach(c => c.classList.remove('activo'));
  document.querySelector(`.urgencia-card[data-urg="${n}"]`).classList.add('activo');
}

function enviarConsulta() {
  const c = estado.consulta;
  c.iniciales = document.getElementById('cons_iniciales').value.trim().toUpperCase();
  c.numlista = document.getElementById('cons_numlista').value.trim();
  c.curso = document.getElementById('cons_curso').value;
  c.grupo = document.getElementById('cons_grupo').value.trim().toUpperCase();
  c.tipo = document.getElementById('cons_tipo').value;
  c.descripcion = document.getElementById('cons_descripcion').value.trim();
  if (!c.iniciales || !c.curso || !c.tipo || !c.descripcion || !c.urgencia) {
    showToast("Completa los campos obligatorios y la urgencia"); return;
  }
  const reg = {
    id: "reg_"+Date.now(), tipo:"consulta", fecha: new Date().toISOString(),
    usuario: usuario, datos: c
  };
  guardarRegistro(reg);
  enviarPorEmail(reg);
}

// =============== ART. 11 ===============
function enviarArt11() {
  const a = estado.art11;
  a.iniciales = document.getElementById('art_iniciales').value.trim().toUpperCase();
  a.numlista = document.getElementById('art_numlista').value.trim();
  a.curso = document.getElementById('art_curso').value;
  a.grupo = document.getElementById('art_grupo').value.trim().toUpperCase();
  a.tipo = document.getElementById('art_tipo').value;
  a.fecha = document.getElementById('art_fecha').value;
  a.via = document.getElementById('art_via').value;
  a.respuesta = document.getElementById('art_respuesta').value;
  a.obs = document.getElementById('art_obs').value.trim();
  if (!a.iniciales || !a.numlista || !a.curso || !a.grupo || !a.tipo || !a.via) {
    showToast("Completa los campos obligatorios"); return;
  }
  const reg = {
    id: "reg_"+Date.now(), tipo:"art11", fecha: new Date().toISOString(),
    usuario: usuario, datos: a
  };
  guardarRegistro(reg);
  // Comprobar acumulación
  const acumulados = comprobarAcumulacionArt11(a);
  if (acumulados >= 3) {
    enviarPorEmail(reg, true); // alerta acumulación
  } else {
    // Solo guarda local; si quiere puede enviar manualmente
    if (confirm(`Registro guardado localmente. Lleva ${acumulados} ausencia(s) de este alumno/a en los últimos 15 días.\n¿Quieres enviarlo igualmente al EOEP ahora?`)) {
      enviarPorEmail(reg, false);
    } else {
      irA('pantallaInicio');
      showToast("Registro Art. 11 guardado");
    }
  }
}

function comprobarAcumulacionArt11(a) {
  const registros = JSON.parse(localStorage.getItem(STORAGE_REGISTROS) || "[]");
  const ahora = Date.now();
  const dosSemanas = 15 * 24 * 60 * 60 * 1000;
  return registros.filter(r => 
    r.tipo === "art11" && 
    r.datos.iniciales === a.iniciales && 
    r.datos.numlista === a.numlista &&
    r.datos.curso === a.curso &&
    r.datos.grupo === a.grupo &&
    (ahora - new Date(r.fecha).getTime()) <= dosSemanas
  ).length;
}

// =============== TRIMESTRAL: ENVIAR ===============
function enviarAlEOEP() {
  const r = calcularAlerta();
  const reg = {
    id: "reg_"+Date.now(), tipo:"trimestral", fecha: new Date().toISOString(),
    usuario: usuario, alumno: estado.alumno, trimestre: estado.trimestre,
    respuestas: estado.respuestas, observaciones: estado.observaciones,
    alerta: r.nivel, recuento: r
  };
  guardarRegistro(reg);
  enviarPorEmail(reg);
}

// =============== GUARDAR Y ENVIAR ===============
function guardarRegistro(reg) {
  const lista = JSON.parse(localStorage.getItem(STORAGE_REGISTROS) || "[]");
  lista.push(reg);
  localStorage.setItem(STORAGE_REGISTROS, JSON.stringify(lista));
}

function enviarPorEmail(reg, alertaAcumulacion=false) {
  // FASE 2 · Envío vía POST al Apps Script (eoepcehegin@gmail.com como motor).
  // El registro YA está guardado en localStorage por guardarRegistro(reg) previamente,
  // así que aunque falle la red, el dato no se pierde.
  const { asunto, cuerpo } = construirEmail(reg, alertaAcumulacion);

  // Marcamos estado inicial del registro
  marcarEstadoEnvio(reg.id, { enviado: false, enviando: true, intentos: (reg.intentos||0)+1 });

  // Pantalla "Enviando..."
  document.getElementById('exitoTitulo').textContent = 'Enviando al EOEP...';
  document.getElementById('exitoSubtitulo').textContent = 'Conectando con el canal seguro. No cierres la app.';
  document.querySelector('#pantallaExito .success-icon').classList.add('enviando');
  irA('pantallaExito');

  // Construimos el payload aplanado al formato exacto que espera el backend
  const payload = aplanarPayload(reg, asunto, cuerpo, alertaAcumulacion);

  // Timeout manual con AbortController
  const ctrl = new AbortController();
  const t = setTimeout(() => ctrl.abort(), ENVIO_TIMEOUT_MS);

  // Truco anti-preflight: Content-Type text/plain evita el OPTIONS que Apps Script no maneja.
  // El Apps Script lee e.postData.contents igualmente.
  fetch(APPS_SCRIPT_URL, {
    method: 'POST',
    headers: { 'Content-Type': 'text/plain;charset=utf-8' },
    body: JSON.stringify(payload),
    signal: ctrl.signal,
    redirect: 'follow'
  })
    .then(r => r.json())
    .then(data => {
      clearTimeout(t);
      // Backend Canal Absentismo v1.0 responde {ok:true,...} en éxito y {ok:false,error:"..."} en fallo
      if (data && data.ok === true) {
        marcarEstadoEnvio(reg.id, { enviado: true, enviando: false, fechaEnvio: new Date().toISOString() });
        mostrarExitoEnvio(usuario.email);
      } else {
        const motivo = (data && data.error) || 'El servidor no confirmó la recepción.';
        marcarEstadoEnvio(reg.id, { enviado: false, enviando: false, error: motivo });
        mostrarErrorEnvio(motivo);
      }
    })
    .catch(err => {
      clearTimeout(t);
      const msg = (err && err.name === 'AbortError') ? 'Tiempo de espera agotado (15s).' : 'Sin conexión o error de red.';
      marcarEstadoEnvio(reg.id, { enviado: false, enviando: false, error: msg });
      mostrarErrorEnvio(msg);
    });
}

/**
 * ADAPTADOR · Convierte el objeto interno del HTML al contrato plano que espera
 * el backend Canal Absentismo Backend v1.0 (Apps Script en eoepcehegin@gmail.com).
 *
 * Backend espera campos planos según tipo:
 *  - tipo "trimestral": tutor, email, centro, trimestre, iniciales, numLista, sexo, edad,
 *                      totalSi, totalProceso, totalNo, alerta, indicadoresNo[], asunto, cuerpo
 *  - tipo "consulta":  tutor, email, centro, iniciales, numLista, tipoConsulta, urgencia,
 *                      descripcion, asunto, cuerpo
 *  - tipo "art11":     tutor, email, centro, iniciales, numLista, fechaAusencia, justificada,
 *                      familiaNotificada, viaNotificacion, acumulacion, alertaAcumulacion,
 *                      asunto, cuerpo
 */
function aplanarPayload(reg, asunto, cuerpo, alertaAcumulacion) {
  // Campos comunes a todos los tipos
  const base = {
    tipo: reg.tipo,
    tutor: (usuario && usuario.nombre) || "",
    email: (usuario && usuario.email) || "",
    centro: (usuario && usuario.centro) || "",
    asunto: asunto,
    cuerpo: cuerpo
  };

  if (reg.tipo === "trimestral") {
    const a = reg.alumno || {};
    const r = reg.recuento || {};
    // Lista de IDs de indicadores marcados "no" (a partir de las respuestas del registro)
    const indicadoresNo = [];
    if (reg.respuestas) {
      Object.keys(reg.respuestas).forEach(k => {
        if (reg.respuestas[k] === 'no') indicadoresNo.push(k);
      });
    }
    return Object.assign(base, {
      trimestre: reg.trimestre || "",
      iniciales: a.iniciales || "",
      numLista: a.numlista || "",
      sexo: a.sexo || "",
      edad: a.edad || "",
      totalSi: r.si || 0,
      totalProceso: r.proceso || 0,
      totalNo: r.no || 0,
      alerta: reg.alerta || "",
      indicadoresNo: indicadoresNo
    });
  }

  if (reg.tipo === "consulta") {
    const d = reg.datos || {};
    return Object.assign(base, {
      iniciales: d.iniciales || "",
      numLista: d.numlista || "",
      tipoConsulta: d.tipo || "",
      urgencia: d.urgencia || "",
      descripcion: d.descripcion || ""
    });
  }

  if (reg.tipo === "art11") {
    const d = reg.datos || {};
    // Recuento de acumulación en los últimos 15 días (mismo cálculo que comprobarAcumulacionArt11)
    const acumulacion = comprobarAcumulacionArt11(d);
    return Object.assign(base, {
      iniciales: d.iniciales || "",
      numLista: d.numlista || "",
      fechaAusencia: d.fecha || "",
      // En el HTML d.tipo es la DURACIÓN ("Día completo", "Sesión mañana"...)
      // En el HTML d.respuesta es la respuesta de la familia, que es donde se determina si hay justificación
      justificada: d.respuesta || "",
      familiaNotificada: d.via ? "SÍ" : "NO",
      viaNotificacion: d.via || "",
      duracionAusencia: d.tipo || "",        // campo extra para trazabilidad en el cuerpo del correo
      observaciones: d.obs || "",
      acumulacion: acumulacion,
      alertaAcumulacion: !!alertaAcumulacion
    });
  }

  // Fallback: tipo desconocido, mandamos lo que haya
  return Object.assign(base, { extra: reg });
}

function marcarEstadoEnvio(idRegistro, cambios) {
  const lista = JSON.parse(localStorage.getItem(STORAGE_REGISTROS) || "[]");
  const i = lista.findIndex(r => r.id === idRegistro);
  if (i >= 0) {
    Object.assign(lista[i], cambios);
    localStorage.setItem(STORAGE_REGISTROS, JSON.stringify(lista));
  }
}

function mostrarExitoEnvio(emailCC) {
  const icon = document.querySelector('#pantallaExito .success-icon');
  icon.classList.remove('enviando','error');
  document.getElementById('exitoTitulo').textContent = 'Enviado correctamente al EOEP';
  document.getElementById('exitoSubtitulo').textContent = `Confirmación enviada a tu correo (${emailCC}).`;
}

function mostrarErrorEnvio(motivo) {
  const icon = document.querySelector('#pantallaExito .success-icon');
  icon.classList.remove('enviando');
  icon.classList.add('error');
  document.getElementById('exitoTitulo').textContent = 'No se pudo enviar';
  document.getElementById('exitoSubtitulo').textContent = `${motivo} El registro queda guardado en tu dispositivo. Pulsa "Reenviar" en el histórico cuando vuelvas a tener conexión.`;
}

function construirEmail(reg, alertaAcumulacion=false) {
  let asunto, cuerpo;
  cuerpo = `NOTIFICACIÓN AUTOMÁTICA · CANAL ABSENTISMO\n`;
  cuerpo += `Tutor/a → EOEP General Cehegín\n`;
  cuerpo += `===============================================\n\n`;
  cuerpo += `Fecha y hora: ${new Date(reg.fecha).toLocaleString('es-ES')}\n`;
  cuerpo += `Tutor/a: ${usuario.nombre} (${usuario.email})\n`;
  cuerpo += `Centro: ${usuario.centro}\n\n`;

  if (reg.tipo === "trimestral") {
    asunto = `[${reg.alerta.toUpperCase()}] Seguimiento ${reg.trimestre}º Trim · ${reg.alumno.iniciales} nº${reg.alumno.numlista} · ${usuario.centro}`;
    cuerpo += `>>> RESUMEN EJECUTIVO <<<\n`;
    cuerpo += `Alumno/a ${reg.alumno.iniciales} (nº ${reg.alumno.numlista}) de ${reg.alumno.curso} ${reg.alumno.grupo} · ALERTA ${reg.alerta.toUpperCase()}\n`;
    const noProb = listaProblemas(reg, "no");
    const procProb = listaProblemas(reg, "proceso");
    if (noProb.length) cuerpo += `Áreas problemáticas: ${noProb.join(", ")}\n`;
    if (procProb.length) cuerpo += `Áreas en proceso: ${procProb.join(", ")}\n`;
    cuerpo += `\n--- DATOS DEL ALUMNO/A ---\n`;
    cuerpo += `Iniciales: ${reg.alumno.iniciales}\n`;
    cuerpo += `Nº lista: ${reg.alumno.numlista}\n`;
    if (reg.alumno.sexo) cuerpo += `Sexo: ${reg.alumno.sexo}\n`;
    if (reg.alumno.edad) cuerpo += `Edad: ${reg.alumno.edad} años\n`;
    cuerpo += `Curso: ${reg.alumno.curso} · Grupo: ${reg.alumno.grupo}\n`;
    cuerpo += `Trimestre evaluado: ${reg.trimestre}º\n\n`;
    cuerpo += `--- RECUENTO DE INDICADORES ---\n`;
    cuerpo += `SÍ (situación adecuada): ${reg.recuento.si}\n`;
    cuerpo += `EN PROCESO: ${reg.recuento.proceso}\n`;
    cuerpo += `NO (situación de alarma): ${reg.recuento.no}\n`;
    cuerpo += `Sin responder: ${reg.recuento.sinResponder}\n\n`;
    cuerpo += `--- INDICADORES MARCADOS COMO 'NO' (situación de alarma) ---\n`;
    INDICADORES[reg.trimestre].forEach(g => {
      g.items.forEach(item => {
        if (reg.respuestas[item.id] === 'no') cuerpo += `[NO] ${item.pregunta}\n   Acción sugerida: ${item.accion}\n`;
      });
    });
    cuerpo += `\n--- INDICADORES 'EN PROCESO' ---\n`;
    INDICADORES[reg.trimestre].forEach(g => {
      g.items.forEach(item => {
        if (reg.respuestas[item.id] === 'proceso') cuerpo += `[EN PROCESO] ${item.pregunta}\n`;
      });
    });
    if (reg.observaciones) cuerpo += `\n--- OBSERVACIONES DEL TUTOR/A ---\n${reg.observaciones}\n`;
  } 
  else if (reg.tipo === "consulta") {
    const urgLabel = ["", "Próxima visita", "Esta semana", "URGENTE"][reg.datos.urgencia];
    asunto = `[CONSULTA · ${urgLabel.toUpperCase()}] ${reg.datos.iniciales} nº${reg.datos.numlista} · ${usuario.centro}`;
    cuerpo += `>>> CONSULTA PREVENTIVA <<<\n`;
    cuerpo += `Nivel de urgencia: ${urgLabel}\n\n`;
    cuerpo += `--- DATOS DEL ALUMNO/A ---\n`;
    cuerpo += `Iniciales: ${reg.datos.iniciales}\n`;
    if (reg.datos.numlista) cuerpo += `Nº lista: ${reg.datos.numlista}\n`;
    cuerpo += `Curso: ${reg.datos.curso} · Grupo: ${reg.datos.grupo || '-'}\n\n`;
    cuerpo += `--- TIPO DE CONSULTA ---\n${reg.datos.tipo}\n\n`;
    cuerpo += `--- DESCRIPCIÓN ---\n${reg.datos.descripcion}\n`;
  } 
  else if (reg.tipo === "art11") {
    const acc = comprobarAcumulacionArt11(reg.datos);
    const tag = alertaAcumulacion ? "ART.11 · ACUMULACIÓN" : "ART.11";
    asunto = `[${tag}] ${reg.datos.iniciales} nº${reg.datos.numlista} · ${reg.datos.curso} ${reg.datos.grupo} · ${usuario.centro}`;
    if (alertaAcumulacion) {
      cuerpo += `>>> ALERTA POR ACUMULACIÓN DE AUSENCIAS <<<\n`;
      cuerpo += `Este alumno/a ha acumulado ${acc} notificaciones Art.11 en los últimos 15 días.\n\n`;
    } else {
      cuerpo += `>>> NOTIFICACIÓN ART. 11 PRAE <<<\n\n`;
    }
    cuerpo += `--- DATOS DEL ALUMNO/A ---\n`;
    cuerpo += `Iniciales: ${reg.datos.iniciales}\n`;
    cuerpo += `Nº lista: ${reg.datos.numlista}\n`;
    cuerpo += `Curso: ${reg.datos.curso} · Grupo: ${reg.datos.grupo}\n\n`;
    cuerpo += `--- AUSENCIA ---\n`;
    cuerpo += `Tipo: ${reg.datos.tipo}\n`;
    cuerpo += `Fecha: ${reg.datos.fecha}\n\n`;
    cuerpo += `--- NOTIFICACIÓN A LA FAMILIA ---\n`;
    cuerpo += `Vía: ${reg.datos.via}\n`;
    if (reg.datos.respuesta) cuerpo += `Respuesta familia: ${reg.datos.respuesta}\n`;
    if (reg.datos.obs) cuerpo += `\nObservaciones: ${reg.datos.obs}\n`;
  }

  cuerpo += `\n===============================================\n`;
  cuerpo += `Enviado desde la app Canal Absentismo · Tutores\n`;
  cuerpo += `EOEP General Cehegín\n`;
  cuerpo += `Consejería de Educación · Región de Murcia`;
  return { asunto, cuerpo };
}

function listaProblemas(reg, tipoResp) {
  const grupos = INDICADORES[reg.trimestre];
  const grupoMap = new Map();
  grupos.forEach(g => g.items.forEach(i => grupoMap.set(i.id, g.grupo)));
  const probGrupos = new Set();
  Object.entries(reg.respuestas).forEach(([id, v]) => {
    if (v === tipoResp) probGrupos.add(grupoMap.get(id));
  });
  return Array.from(probGrupos);
}

// =============== HISTÓRICO Y EVOLUCIÓN ===============
function renderHistorico() {
  const lista = document.getElementById('listaHistorico');
  const registros = JSON.parse(localStorage.getItem(STORAGE_REGISTROS) || "[]");
  if (registros.length === 0) {
    lista.innerHTML = `<div class="empty-state">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/><polyline points="14 2 14 8 20 8"/></svg>
      <p>Aún no has guardado ningún registro.</p></div>`;
    document.getElementById('comparativaContainer').innerHTML = '';
    return;
  }
  registros.sort((a,b) => new Date(b.fecha) - new Date(a.fecha));
  lista.innerHTML = registros.map(r => {
    let alumnoTxt, metaTxt, pill;
    if (r.tipo === "trimestral") {
      alumnoTxt = `${r.alumno.iniciales} (nº ${r.alumno.numlista}) · ${r.alumno.curso}`;
      metaTxt = `Trimestral · ${r.trimestre}º Trim · ${new Date(r.fecha).toLocaleDateString('es-ES')}`;
      pill = `<span class="alerta-pill ${r.alerta}">${r.alerta}</span>`;
    } else if (r.tipo === "consulta") {
      alumnoTxt = `${r.datos.iniciales} (nº ${r.datos.numlista || '-'}) · ${r.datos.curso}`;
      metaTxt = `Consulta · ${r.datos.tipo.substring(0,30)}... · ${new Date(r.fecha).toLocaleDateString('es-ES')}`;
      pill = `<span class="alerta-pill" style="background:var(--azul);color:white;">CONSULTA</span>`;
    } else {
      alumnoTxt = `${r.datos.iniciales} (nº ${r.datos.numlista}) · ${r.datos.curso}`;
      metaTxt = `Art. 11 · ${r.datos.tipo} · ${r.datos.fecha}`;
      pill = `<span class="alerta-pill" style="background:var(--amarillo);color:white;">ART.11</span>`;
    }
    return `<div class="historico-item" onclick="verDetalle('${r.id}')">
      <div class="historico-info">
        <div class="historico-alumno">${alumnoTxt}</div>
        <div class="historico-meta">${metaTxt}</div>
      </div>${pill}</div>`;
  }).join('');

  renderComparativasPorAlumno(registros);
}

function renderComparativasPorAlumno(registros) {
  const trimestrales = registros.filter(r => r.tipo === "trimestral");
  if (trimestrales.length === 0) { document.getElementById('comparativaContainer').innerHTML = ''; return; }
  const porAlumno = {};
  trimestrales.forEach(r => {
    const k = `${r.alumno.iniciales}-${r.alumno.numlista}-${r.alumno.curso}-${r.alumno.grupo}`;
    if (!porAlumno[k]) porAlumno[k] = { alumno: r.alumno, trims: {} };
    porAlumno[k].trims[r.trimestre] = r;
  });
  const conMultiples = Object.values(porAlumno).filter(a => Object.keys(a.trims).length >= 2);
  if (conMultiples.length === 0) { document.getElementById('comparativaContainer').innerHTML = ''; return; }
  let html = `<div class="card"><div class="card-title">Evolución por alumno/a</div>`;
  html += `<p style="font-size:11px;color:#7A8B99;margin-bottom:12px;">Comparativa entre trimestres del mismo alumno/a.</p>`;
  conMultiples.forEach(a => {
    const trims = a.trims;
    let tendencia = "estable", textoTend = "Situación estable";
    const niveles = [trims["1"]?.alerta, trims["2"]?.alerta, trims["3"]?.alerta].filter(Boolean);
    const valores = { verde:1, amarillo:2, rojo:3 };
    if (niveles.length >= 2) {
      const primero = valores[niveles[0]];
      const ultimo = valores[niveles[niveles.length-1]];
      if (ultimo < primero) { tendencia="mejora"; textoTend="↑ Tendencia de mejora"; }
      else if (ultimo > primero) { tendencia="empeora"; textoTend="↓ Tendencia de empeoramiento"; }
    }
    html += `<div class="evolucion-card">
      <div class="evolucion-titulo">${a.alumno.iniciales} (nº ${a.alumno.numlista}) · ${a.alumno.curso} ${a.alumno.grupo}</div>
      <div class="evolucion-trims">`;
    ["1","2","3"].forEach(t => {
      if (trims[t]) {
        html += `<div class="evolucion-trim ${trims[t].alerta}">
          <div class="evolucion-trim-num">${t}º Trim</div>
          <div class="evolucion-trim-alerta">${trims[t].alerta}</div>
          <div class="evolucion-trim-fecha">${new Date(trims[t].fecha).toLocaleDateString('es-ES')}</div>
        </div>`;
      } else {
        html += `<div class="evolucion-trim empty"><div class="evolucion-trim-num">${t}º Trim</div><div class="evolucion-trim-alerta" style="color:#99A6B2;">- - -</div></div>`;
      }
    });
    html += `</div><div class="evolucion-tendencia tendencia-${tendencia}">${textoTend}</div></div>`;
  });
  html += `</div>`;
  document.getElementById('comparativaContainer').innerHTML = html;
}

function verDetalle(id) {
  const registros = JSON.parse(localStorage.getItem(STORAGE_REGISTROS) || "[]");
  const r = registros.find(x => x.id === id);
  if (!r) return;
  let html = `<h2 style="font-size:18px;margin-bottom:14px;">Detalle del registro</h2>`;
  if (r.tipo === "trimestral") {
    html += `<p><strong>Tipo:</strong> Seguimiento trimestral</p>`;
    html += `<p><strong>Fecha:</strong> ${new Date(r.fecha).toLocaleString('es-ES')}</p>`;
    html += `<p><strong>Alumno:</strong> ${r.alumno.iniciales} (nº ${r.alumno.numlista})</p>`;
    html += `<p><strong>Curso:</strong> ${r.alumno.curso} ${r.alumno.grupo}</p>`;
    html += `<p><strong>Trimestre:</strong> ${r.trimestre}º</p>`;
    html += `<p><strong>Alerta:</strong> <span class="alerta-pill ${r.alerta}">${r.alerta.toUpperCase()}</span></p>`;
    html += `<p style="margin-top:10px;"><strong>SÍ:</strong> ${r.recuento.si} · <strong>EN PROCESO:</strong> ${r.recuento.proceso} · <strong>NO:</strong> ${r.recuento.no}</p>`;
    if (r.observaciones) html += `<p style="margin-top:10px;"><strong>Observaciones:</strong> ${r.observaciones}</p>`;
  } else if (r.tipo === "consulta") {
    html += `<p><strong>Tipo:</strong> Consulta preventiva</p>`;
    html += `<p><strong>Fecha:</strong> ${new Date(r.fecha).toLocaleString('es-ES')}</p>`;
    html += `<p><strong>Alumno:</strong> ${r.datos.iniciales} (nº ${r.datos.numlista || '-'})</p>`;
    html += `<p><strong>Curso:</strong> ${r.datos.curso} ${r.datos.grupo || ''}</p>`;
    html += `<p><strong>Tipo de consulta:</strong> ${r.datos.tipo}</p>`;
    html += `<p style="margin-top:10px;"><strong>Descripción:</strong></p><p>${r.datos.descripcion}</p>`;
  } else if (r.tipo === "art11") {
    html += `<p><strong>Tipo:</strong> Notificación Art. 11</p>`;
    html += `<p><strong>Fecha de la ausencia:</strong> ${r.datos.fecha}</p>`;
    html += `<p><strong>Alumno:</strong> ${r.datos.iniciales} (nº ${r.datos.numlista})</p>`;
    html += `<p><strong>Curso:</strong> ${r.datos.curso} ${r.datos.grupo}</p>`;
    html += `<p><strong>Tipo de ausencia:</strong> ${r.datos.tipo}</p>`;
    html += `<p><strong>Vía de notificación:</strong> ${r.datos.via}</p>`;
    if (r.datos.respuesta) html += `<p><strong>Respuesta familia:</strong> ${r.datos.respuesta}</p>`;
    if (r.datos.obs) html += `<p style="margin-top:10px;"><strong>Observaciones:</strong> ${r.datos.obs}</p>`;
  }
  document.getElementById('modalTitulo').textContent = "Detalle del registro";
  document.getElementById('modalContenido').innerHTML = html;
  document.getElementById('btnModalAccion').textContent = "Reenviar al EOEP";
  document.getElementById('btnModalAccion').onclick = () => { cerrarModal(); enviarPorEmail(r); };
  document.getElementById('modal').classList.add('show');
}

// =============== RESUMEN EN INICIO ===============
function renderResumenInicio() {
  if (!usuario) return;
  const cont = document.getElementById('resumenInicio');
  const registros = JSON.parse(localStorage.getItem(STORAGE_REGISTROS) || "[]");
  if (registros.length === 0) {
    cont.innerHTML = "";
    return;
  }
  const ultimos = registros.slice().sort((a,b) => new Date(b.fecha) - new Date(a.fecha)).slice(0,3);
  let html = `<div class="card"><div class="card-title">Tus últimos registros</div>`;
  ultimos.forEach(r => {
    let alumnoTxt, pill;
    if (r.tipo === "trimestral") {
      alumnoTxt = `${r.alumno.iniciales} · ${r.trimestre}º Trim`;
      pill = `<span class="alerta-pill ${r.alerta}">${r.alerta}</span>`;
    } else if (r.tipo === "consulta") {
      alumnoTxt = `${r.datos.iniciales} · Consulta`;
      pill = `<span class="alerta-pill" style="background:var(--azul);color:white;">CONSULTA</span>`;
    } else {
      alumnoTxt = `${r.datos.iniciales} · Art.11`;
      pill = `<span class="alerta-pill" style="background:var(--amarillo);color:white;">ART.11</span>`;
    }
    html += `<div class="historico-item" onclick="irA('pantallaHistorico')">
      <div class="historico-info">
        <div class="historico-alumno">${alumnoTxt}</div>
        <div class="historico-meta">${new Date(r.fecha).toLocaleDateString('es-ES')}</div>
      </div>${pill}</div>`;
  });
  if (registros.length > 3) html += `<p style="font-size:11px;text-align:center;color:#7A8B99;margin-top:8px;">+${registros.length-3} más en pestaña Histórico</p>`;
  html += `</div>`;
  cont.innerHTML = html;
}

// =============== UTILIDADES ===============
function exportarTodo() {
  const reg = JSON.parse(localStorage.getItem(STORAGE_REGISTROS) || "[]");
  if (reg.length === 0) { showToast("No hay registros para exportar"); return; }
  const blob = new Blob([JSON.stringify({ usuario, registros: reg, exportado: new Date().toISOString() }, null, 2)], { type: "application/json" });
  const url = URL.createObjectURL(blob);
  const a = document.createElement('a');
  a.href = url;
  a.download = `absentismo_${usuario.nombre.replace(/\s+/g,'_')}_${new Date().toISOString().slice(0,10)}.json`;
  a.click();
  URL.revokeObjectURL(url);
  showToast("Archivo exportado");
}

function confirmarLimpiar() {
  if (confirm("¿Eliminar todos tus registros locales? Esta acción no se puede deshacer.")) {
    localStorage.removeItem(STORAGE_REGISTROS);
    showToast("Registros eliminados");
    renderHistorico();
    renderResumenInicio();
  }
}

function cerrarModal() { document.getElementById('modal').classList.remove('show'); }

function showToast(msg) {
  const t = document.getElementById('toast');
  t.textContent = msg;
  t.classList.add('show');
  setTimeout(() => t.classList.remove('show'), 2400);
}

// =============== ARRANQUE ===============
init();
</script>
</body>
</html>
