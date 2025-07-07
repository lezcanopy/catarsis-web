## 🧩 Lienzo CE | Publicación de sitio Quartz en GitLab Pages (How To)

### Objetivo:

Desplegar un sitio web estático basado en Quartz (Hugo) a través de GitLab Pages, con integración automática mediante CI/CD cada vez que se hace `push`.

---

### 🔧 PRERREQUISITOS

1. Tener una cuenta en GitLab verificada.
    
2. Tener Git instalado y configurado localmente.
    
3. Tener una carpeta local con la estructura básica de Quartz funcionando (con `config.toml`, carpetas `assets/`, `content/`, etc.).
    
4. Haber inicializado un repositorio Git dentro de esa carpeta (`git init`).
    
5. Tener Git vinculado al repositorio remoto en GitLab (`git remote add origin <URL>`).
    

---

### 🗂 ESTRUCTURA MÍNIMA ESPERADA DE LA CARPETA

```
quartz/
├── .git/
├── .gitlab-ci.yml
├── config.toml
├── content/
├── assets/
└── README.md
```

---

### ⚙️ CONFIGURAR `.gitlab-ci.yml`

Crear el archivo `.gitlab-ci.yml` (sin espacios delante del nombre) con el siguiente contenido exacto:

```yaml
image: klakegg/hugo:0.111.3-ext-alpine

pages:
  script:
    - hugo --minify
  artifacts:
    paths:
      - public
  only:
    - main
```

Este archivo configura el pipeline para construir el sitio usando Hugo y publicar el contenido generado en la carpeta `public`.

---

### 🧪 COMANDOS PARA SUBIR Y DESENCADENAR PIPELINE

Desde la terminal:

```bash
git add .
git commit -m "Primer push de Quartz con config para GitLab Pages"
git push origin main
```

---

### 📍 NOTAS CLAVE

- El archivo `config.toml` debe estar presente en la raíz.
    
- No se debe incluir comandos erróneos como `sh` ni referencias vacías.
    
- GitLab Pages se activa automáticamente con este pipeline si no hay errores.
    
- Asegurate de tener la verificación de cuenta hecha (puede requerir tarjeta para desbloquear Pipelines, aunque no se cobre).
    
- Los errores como `"unknown command 'sh' for 'hugo'"` indican un `script` mal escrito o un problema previo que fue corregido en este lienzo.
    

---

### 🧱 CONTINUAR DESDE AQUÍ

Con este lienzo podés abrir un nuevo hilo y continuar en limpio, desde el commit inicial o desde la configuración actual.  
Todo lo que se publique en el branch `main` se desplegará automáticamente si el pipeline corre correctamente.