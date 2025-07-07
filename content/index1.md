<!-- Logo -->
<p align="center">
  <img src="../assets/images/catarsis-logo.png" alt="Logo Catarsis" width="200">
</p>

<!-- Acápite -->
<blockquote style="text-align:center; font-style:italic;">
  “Se puede emplear el término <strong>‘catarsis’</strong> para indicar el paso del momento meramente económico al momento ético-político ...<br>
  Esto significa también el paso de lo objetivo a lo subjetivo y de la necesidad a la libertad...<br>
  <strong>La fijación del momento catártico se convierte así en el punto de partida para toda la filosofía de la praxis</strong>.”
  <br><br>— Antonio Gramsci
</blockquote>

<style>
  @media (max-width: 768px) {
    #clave-container {
      padding: 1em !important;
      margin: 1em auto !important;
    }
    #clave-input {
      width: 90% !important;
    }
  }
</style>

<div id="clave-container" style="text-align:center; padding:2em; border:1px dashed #aaa; margin: 2em auto; max-width: 600px;">
  <h3>🧠 Confirmá que no sos un robot</h3>
  <p>Ingresá la clave compartida por quien te invitó:</p>
  <input type="text" id="clave-input" placeholder="Escribí la clave..." style="padding:0.5em; width:60%;">
  <br><br>
  <button onclick="verificarClave()" style="padding:0.5em 1em;">✓ Confirmar</button>
  <p id="error-msg" style="color:red;"></p>
</div>

<div id="contenido-catarsis" style="display:none;">

## 🗞️ Publicación de junio 2025

### 📍 ¿Qué es hoy el desarrollo?  
**¿Qué implica hoy hablar de desarrollo sin caer en el vacío tecnocrático o en el cinismo multilateral?**  
Una exploración crítica del concepto bajo crisis y el problema de la legitimidad del progreso.

<!-- PEGA AQUÍ EL CONTENIDO COMPLETO DE TU ARTÍCULO -->

## 📚 Archivo por año
### 2025
- Mayo: *Tiempos sin estrategia*
- Abril: *El antagonismo difuso*
- Marzo: *La producción simbólica en crisis*
- Febrero: *La guerra y el silencio*
- Enero: *Inicios de ciclo*

</div>

<script>
  // 🔑 CAMBIA ESTAS CLAVES (mínimo 1)
  const clavesValidas = ["abril", "claveSecreta"];
  const claveStorage = "catarsis-acceso";

  function verificarClave() {
    const entrada = document.getElementById("clave-input").value.trim().toLowerCase();
    if (clavesValidas.includes(entrada)) {
      localStorage.setItem(claveStorage, "true");
      mostrarContenido();
    } else {
      document.getElementById("error-msg").innerText = "Clave incorrecta. Revisá con quien te compartió el acceso.";
    }
  }

  function mostrarContenido() {
    document.getElementById("clave-container").style.display = "none";
    document.getElementById("contenido-catarsis").style.display = "block";
  }

  document.addEventListener('DOMContentLoaded', function() {
    if (localStorage.getItem(claveStorage) === "true") {
      mostrarContenido();
    }
  });
</script>
<!-- COPIAR HASTA AQUÍ -->