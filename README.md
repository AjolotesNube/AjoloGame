# Ajolotes en la nube — Cómo ejecutar el juego localmente

Este repositorio contiene un pequeño juego HTML5 localizado en `index.html` y varios recursos (imágenes) usados por el juego.

## Archivos importantes
- `index.html` — archivo principal que carga y ejecuta el juego.
- Imágenes usadas por el juego (ya incluidas en el mismo directorio):
  - `depb.png` (player idle)
  - `depf.png` (player fall)
  - `depp.png`
  - `enep.png` (enemy)
  - `font.jpg` (fondo)
  - `plad1.jpg` (plataformas)
  - `poin.png` (checkpoint)
  - `walk1.png`, `walk2.png` (animaciones de caminar)

## Requisitos
- Navegador moderno (Chrome, Edge, Firefox, Safari).
- (Opcional, pero recomendado) Python 3 instalado para servir archivos estáticos fácilmente.
- Alternativa: Node.js + `http-server` o la extensión Live Server de VS Code.

---

## Opciones para ejecutar
A continuación hay varias formas para ejecutar el juego localmente. Puedes elegir la que prefieras.

### 1) (Recomendado) Usar Python (rápido y sin instalar dependencias)
Abre PowerShell en la carpeta del juego (o usa la terminal integrada de VS Code):

```powershell
cd 'C:\Users\VicenteGuzman\Downloads\AjoloGame'
# Si tienes 'python' disponible:
python -m http.server 8000
# O, si tu instalación usa 'py':
py -m http.server 8000
```

Esto levantará un servidor HTTP simple en el puerto 8000. Abre en tu navegador:

```
http://localhost:8000
```

Para detener el servidor, vuelve a la terminal donde lo ejecutaste y presiona Ctrl+C.

Si quieres iniciar el servidor desde PowerShell sin bloquear la terminal actual (ejecutarlo como proceso separado):

```powershell
Start-Process -FilePath python -ArgumentList '-m','http.server','8000' -WorkingDirectory 'C:\Users\VicenteGuzman\Downloads\AjoloGame'
```

Nota: si inicias con `Start-Process`, cierra el proceso desde el Administrador de tareas o usa `Get-Process`/`Stop-Process` si necesitas detenerlo por script.

---

### 2) Usar Node.js + http-server
Si tienes Node.js instalado:

```powershell
npm install -g http-server
cd 'C:\Users\VicenteGuzman\Downloads\AjoloGame'
http-server -p 8000
```

Después, abre `http://localhost:8000` en el navegador.

---

### 3) Usar VS Code Live Server
1. Abre la carpeta `AjoloGame` en VS Code.
2. Instala la extensión "Live Server" (Ritwick Dey).
3. Haz clic en "Go Live" (abajo a la derecha) o clic derecho en `index.html` -> "Open with Live Server".

Live Server abrirá una URL similar a `http://127.0.0.1:5500` y recargará automáticamente si editas archivos.

---

### 4) (No recomendado) Abrir `index.html` directamente
Puedes intentar abrir `index.html` con doble clic (ruta `file://...`). Esto puede funcionar localmente, pero algunos navegadores bloquean ciertas operaciones o pueden dar problemas con rutas relativas y seguridad (CORS). Por eso se recomienda usar un servidor HTTP simple.

---

## Verificar que el servidor responde
Desde PowerShell puedes verificar rápidamente la respuesta con:

```powershell
curl.exe -I http://localhost:8000/index.html
```

Debes ver un `HTTP/1.0 200 OK` y las cabeceras del archivo.

---

## Qué verás al abrir el juego
- Una pantalla de carga con la barra de progreso mientras el juego carga las imágenes.
- Controles en pantalla (botones izquierda/derecha y salto). En PC puedes usar clics del ratón sobre los botones. Actualmente no hay controles por teclado (si deseas, puedo añadirlos).

---

## Solución de problemas
- Si la barra de carga no avanza o faltan imágenes, verifica que los archivos listados arriba existan en el mismo directorio que `index.html`.
- Si `http://localhost:8000` no responde:
  - Asegúrate de haber ejecutado el comando de Python o `http-server` en la carpeta correcta.
  - Revisa que no haya otro proceso ocupando el puerto 8000 (puedes cambiar a otro puerto, por ejemplo 8080).
- Si el navegador muestra errores en consola (F12 → Consola), copia los mensajes y los puedo revisar.

---

## Mejoras sugeridas (opcional)
- Añadir soporte por teclado (flechas / A-D / espacio) para jugar en PC.
- Añadir un pequeño `README` en español (este archivo) — ya creado.
- Añadir un script `start` en `package.json` si se usa Node para simplificar el arranque.

---

Si quieres, puedo:
- Añadir soporte de teclado ahora mismo y crear un commit/archivo con los cambios.
- Generar un archivo `package.json` con un script `start` para `http-server`.
- Detener el servidor que arrancamos en esta sesión.

Indica qué prefieres y lo hago por ti.
