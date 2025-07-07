<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Catarsis - Publicación Editorial</title>
  <style>
    :root {
      --border-color: #e0e0e0;
      --accent-color: #2c3e50;
      --error-color: #e74c3c;
    }
    
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }
    
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      line-height: 1.6;
      color: #333;
      max-width: 800px;
      margin: 0 auto;
      padding: 1rem;
    }
    
    .logo-container {
      text-align: center;
      margin: 2rem 0;
    }
    
    .logo-container img {
      max-width: 200px;
      height: auto;
    }
    
    .epigraph {
      text-align: center;
      font-style: italic;
      margin: 2rem 0;
      padding: 1.5rem;
      border-left: 3px solid var(--accent-color);
      background-color: #f9f9f9;
    }
    
    .epigraph strong {
      color: var(--accent-color);
    }
    
    .access-container {
      text-align: center;
      padding: 2rem;
      border: 1px dashed var(--border-color);
      border-radius: 8px;
      margin: 3rem auto;
      max-width: 600px;
    }
    
    .access-input {
      padding: 0.8rem;
      width: 100%;
      max-width: 400px;
      margin: 1rem 0;
      border: 1px solid var(--border-color);
      border-radius: 4px;
      font-size: 1rem;
    }
    
    .access-btn {
      background-color: var(--accent-color);
      color: white;
      border: none;
      padding: 0.8rem 1.5rem;
      border-radius: 4px;
      cursor: pointer;
      font-size: 1rem;
      transition: background-color 0.3s;
    }
    
    .access-btn:hover {
      background-color: #1a2530;
    }
    
    .error-msg {
      color: var(--error-color);
      margin-top: 1rem;
      min-height: 1.5rem;
    }
    
    .content {
      display: none;
      margin-top: 3rem;
    }
    
    .section {
      margin-bottom: 2.5rem;
    }
    
    .section-title {
      color: var(--accent-color);
      margin-bottom: 1rem;
      padding-bottom: 0.5rem;
      border-bottom: 1px solid var(--border-color);
    }
    
    .article-list {
      list-style-type: none;
    }
    
    .article-list li {
      margin-bottom: 0.8rem;
      padding-left: 1rem;
      border-left: 2px solid var(--border-color);
    }
    
    @media (max-width: 768px) {
      .access-container {
        padding: 1.5rem;
        margin: 1.5rem auto;
      }
      
      .access-input {
        width: 100%;
      }
    }
  </style>
</head>
<body>
  <!-- Logo -->
  <div class="logo-container">
    <img src="../quartz/assets/images/catarsis-logo.png" alt="Logo Catarsis">
  </div>

  <!-- Acápite -->
  <blockquote class="epigraph">
    “Se puede emplear el término <strong>‘catarsis’</strong> para indicar el paso del momento meramente económico al momento ético-político ...<br>
    Esto significa también el paso de lo objetivo a lo subjetivo y de la necesidad a la libertad...<br>
    <strong>La fijación del momento catártico se convierte así en el punto de partida para toda la filosofía de la praxis</strong>.”
    <br><br>— Antonio Gramsci
  </blockquote>

  <!-- Contenedor de acceso -->
  <div id="access-container" class="access-container">
    <h3>🧠 Confirmá que no sos un robot</h3>
    <p>Ingresá la clave compartida por quien te invitó:</p>
    <input type="password" id="clave-input" class="access-input" placeholder="Escribí la clave...">
    <br><br>
    <button id="confirm-btn" class="access-btn">✓ Confirmar</button>
    <p id="error-msg" class="error-msg"></p>
  </div>

  <!-- Contenido protegido -->
  <div id="content" class="content">
    <div class="section">
      <h2 class="section-title">🗞️ Publicación de junio 2025</h2>
      
      <h3>📍 ¿Qué es hoy el desarrollo?</h3>
      <p><strong>¿Qué implica hoy hablar de desarrollo sin caer en el vacío tecnocrático o en el cinismo multilateral?</strong><br>
      Una exploración crítica del concepto bajo crisis y el problema de la legitimidad del progreso.</p>
      
      <!-- Espacio para contenido del artículo -->
      <div id="article-content">
        <!-- PEGA AQUÍ EL CONTENIDO COMPLETO DE TU ARTÍCULO -->
      </div>
    </div>

    <div class="section">
      <h2 class="section-title">📚 Archivo por año</h2>
      <h3>2025</h3>
      <ul class="article-list">
        <li>Mayo: <em>Tiempos sin estrategia</em></li>
        <li>Abril: <em>El antagonismo difuso</em></li>
        <li>Marzo: <em>La producción simbólica en crisis</em></li>
        <li>Febrero: <em>La guerra y el silencio</em></li>
        <li>Enero: <em>Inicios de ciclo</em></li>
      </ul>
    </div>
  </div>

  <script>
    // 🔑 CAMBIA ESTAS CLAVES (mínimo 1)
    const clavesValidas = ["abril", "claveSecreta"];
    const claveStorage = "catarsis-acceso";
    const MAX_ATTEMPTS = 5;
    let attempts = 0;
    
    const accessContainer = document.getElementById('access-container');
    const content = document.getElementById('content');
    const claveInput = document.getElementById('clave-input');
    const errorMsg = document.getElementById('error-msg');
    const confirmBtn = document.getElementById('confirm-btn');
    
    // Verificar si ya tiene acceso
    function checkAccess() {
      const hasAccess = localStorage.getItem(claveStorage) === "true";
      if (hasAccess) {
        accessContainer.style.display = 'none';
        content.style.display = 'block';
      }
      return hasAccess;
    }
    
    // Verificar clave ingresada
    function verificarClave() {
      attempts++;
      
      if (attempts >= MAX_ATTEMPTS) {
        errorMsg.textContent = "Demasiados intentos. Recargá la página para intentar nuevamente.";
        confirmBtn.disabled = true;
        return;
      }
      
      const entrada = claveInput.value.trim().toLowerCase();
      
      if (clavesValidas.includes(entrada)) {
        localStorage.setItem(claveStorage, "true");
        accessContainer.style.display = 'none';
        content.style.display = 'block';
      } else {
        errorMsg.textContent = "Clave incorrecta. Revisá con quien te compartió el acceso.";
        claveInput.value = '';
        claveInput.focus();
      }
    }
    
    // Event Listeners
    confirmBtn.addEventListener('click', verificarClave);
    
    claveInput.addEventListener('keypress', (e) => {
      if (e.key === 'Enter') {
        verificarClave();
      }
    });
    
    // Al cargar la página
    document.addEventListener('DOMContentLoaded', () => {
      checkAccess();
      claveInput.focus();
    });
  </script>
</body>
</html>
