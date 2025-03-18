### ✅ **¿Qué es WebSockets?**

**WebSockets** es un protocolo de comunicación en tiempo real que permite una **conexión bidireccional** (de ida y vuelta) entre un cliente (por ejemplo, un navegador) y un servidor.

A diferencia de las **APIs REST** (donde el cliente debe hacer una petición al servidor para recibir una respuesta), con **WebSockets** el servidor puede enviar datos al cliente **en cualquier momento** sin esperar una solicitud.

---

### 📊 **Diferencias entre HTTP y WebSockets**

| Característica   | HTTP (REST)                               | WebSockets                                             |
| ---------------- | ----------------------------------------- | ------------------------------------------------------ |
| **Comunicación** | Unidireccional (cliente → servidor)       | Bidireccional (cliente ↔ servidor)                     |
| **Conexión**     | Nueva conexión por cada petición          | Conexión persistente (única conexión abierta)          |
| **Velocidad**    | Más lenta (requiere múltiples peticiones) | Más rápida (envío continuo de datos)                   |
| **Uso común**    | CRUD (Crear, Leer, Actualizar, Borrar)    | Chats, notificaciones en tiempo real, juegos en línea. |
| **Protocolo**    | HTTP/HTTPS                                | ws:// o wss:// (WebSocket seguro).                     |

---

### 📚 **¿Cómo funciona WebSockets?**

1. **Handshake (Apretón de manos):**

   - El cliente inicia una petición HTTP especial al servidor.
   - Si el servidor acepta, se actualiza la conexión a **WebSocket**.

2. **Comunicación Persistente:**

   - Ambos pueden enviar y recibir mensajes **sin cerrar la conexión**.

3. **Cierre de Conexión:**
   - La conexión permanece abierta hasta que el cliente o servidor la cierra.

---

### 🛠️ **Pasos para Practicar WebSockets con Node.js**

A continuación te muestro cómo crear una API básica de chat en tiempo real con **Node.js** y **Socket.io**.

---

### 📌 **1. Configurar el proyecto**

Asegúrate de tener **Node.js** instalado.  
En la terminal:

```bash
mkdir websocket-demo && cd websocket-demo
npm init -y
npm install express socket.io
```

---

### 📄 **2. Crear el servidor WebSocket**

En el archivo **server.js**:

```js
const express = require('express');
const http = require('http');
const { Server } = require('socket.io');

const app = express();
const server = http.createServer(app);
const io = new Server(server);

// Servir el cliente (HTML)
app.get('/', (req, res) => {
  res.sendFile(__dirname + '/index.html');
});

// Detectar conexiones WebSocket
io.on('connection', (socket) => {
  console.log('🔗 Usuario conectado');

  // Recibir mensaje del cliente
  socket.on('mensaje', (msg) => {
    console.log('Mensaje recibido:', msg);
    // Reenviar mensaje a todos los clientes
    io.emit('mensaje', msg);
  });

  // Detectar desconexión
  socket.on('disconnect', () => {
    console.log('❌ Usuario desconectado');
  });
});

// Escuchar en el puerto 3000
server.listen(3000, () => {
  console.log('✅ Servidor WebSocket en http://localhost:3000');
});
```

---

### 📄 **3. Crear el cliente WebSocket**

En el archivo **index.html**:

```html
<!DOCTYPE html>
<html lang="es">
  <head>
    <title>Chat en Tiempo Real</title>
  </head>
  <body>
    <h1>🗨️ Chat en Tiempo Real</h1>
    <input id="mensaje" placeholder="Escribe un mensaje..." />
    <button onclick="enviar()">Enviar</button>
    <ul id="chat"></ul>

    <script src="/socket.io/socket.io.js"></script>
    <script>
      const socket = io();

      // Enviar mensaje al servidor
      function enviar() {
        const mensaje = document.getElementById('mensaje').value;
        socket.emit('mensaje', mensaje);
      }

      // Escuchar mensajes y mostrarlos
      socket.on('mensaje', (msg) => {
        const chat = document.getElementById('chat');
        const item = document.createElement('li');
        item.textContent = msg;
        chat.appendChild(item);
      });
    </script>
  </body>
</html>
```

---

### ▶️ **4. Ejecutar el proyecto**

1. Inicia el servidor:

```bash
node server.js
```

2. Abre **http://localhost:3000** en dos pestañas del navegador y ¡prueba el chat en tiempo real!

---

### 📊 **5. Retos para Avanzar**

1. **Autenticación**: Solo permitir que usuarios autenticados accedan al chat.
2. **Notificaciones**: Mostrar alertas si alguien se conecta o desconecta.
3. **Privacidad**: Implementar chats privados entre dos usuarios.
4. **Optimización**: Usar Redis para manejar múltiples servidores WebSocket.
