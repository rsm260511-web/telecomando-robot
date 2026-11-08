
<!DOCTYPE html>
<html lang="it">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Telecomando Robot</title>
  <script src="https://unpkg.com/mqtt/dist/mqtt.min.js"></script>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #101827;
      color: white;
      text-align: center;
      padding: 20px;
    }
    .panel {
      max-width: 420px;
      margin: auto;
      background: #1e293b;
      padding: 22px;
      border-radius: 18px;
    }
    input {
      box-sizing: border-box;
      width: 100%;
      padding: 12px;
      margin: 6px 0;
      border-radius: 8px;
      border: 0;
    }
    button {
      padding: 20px;
      margin: 7px;
      border: 0;
      border-radius: 12px;
      font-size: 20px;
      font-weight: bold;
      min-width: 90px;
      cursor: pointer;
      touch-action: none;
    }
    .move { background: #2563eb; color: white; }
    .stop { background: #dc2626; color: white; width: 90%; }
    .connect { background: #16a34a; color: white; width: 90%; }
    #status { color: #fbbf24; }
  </style>
</head>
<body>
  <div class="panel">
    <h1>🤖 Robot Controller</h1>
    <p id="status">Non connesso</p>

    <h3>Connessione MQTT</h3>
    <input id="host" placeholder="Indirizzo broker MQTT">
    <input id="port" value="8884" placeholder="Porta WebSocket">
    <input id="username" placeholder="Nome utente MQTT">
    <input id="password" type="password" placeholder="Password MQTT">
    <button class="connect" onclick="connectMQTT()">CONNETTI</button>

    <h3>Velocità: <span id="speedValue">30</span>%</h3>
    <input id="speed" type="range" min="10" max="100" value="30"
      oninput="speedValue.textContent=this.value">

    <h3>Movimento</h3>
    <div><button class="move" data-command="FWD">⬆️</button></div>
    <div>
      <button class="move" data-command="LEFT">⬅️</button>
      <button class="stop" onclick="sendStop()">STOP</button>
      <button class="move" data-command="RIGHT">➡️</button>
    </div>
    <div><button class="move" data-command="REV">⬇️</button></div>
  </div>

<script>
  let client = null;
  const topic = "robot/robot01/cmd";
  let interval = null;

  function connectMQTT() {
    const host = document.getElementById("host").value.trim();
    const port = document.getElementById("port").value.trim();
    const username = document.getElementById("username").value;
    const password = document.getElementById("password").value;

    if (!host || !username || !password) {
      alert("Inserisci i dati del broker MQTT.");
      return;
    }

    document.getElementById("status").textContent = "Connessione...";

    client = mqtt.connect(`wss://${host}:${port}/mqtt`, {
      username,
      password,
      clientId: "robot_controller_" + Math.random().toString(16).slice(2),
      clean: true,
      reconnectPeriod: 3000,
      connectTimeout: 10000
    });

    client.on("connect", () => {
      document.getElementById("status").textContent = "Connesso ✅";
    });

    client.on("error", (err) => {
      document.getElementById("status").textContent = "Errore di connessione";
      console.error(err);
    });

    client.on("close", () => {
      document.getElementById("status").textContent = "Disconnesso";
    });
  }

  function sendCommand(command) {
    if (!client || !client.connected) return;
    const speed = document.getElementById("speed").value;
    client.publish(topic, `${command},${speed}`);
  }

  function sendStop() {
    clearInterval(interval);
    interval = null;
    if (client && client.connected) {
      client.publish(topic, "STOP");
    }
  }

  document.querySelectorAll("[data-command]").forEach(button => {
    button.addEventListener("pointerdown", event => {
      event.preventDefault();
      if (!client || !client.connected) return;
      clearInterval(interval);
      sendCommand(button.dataset.command);
      interval = setInterval(() => {
        sendCommand(button.dataset.command);
      }, 200);
    });

    button.addEventListener("pointerup", sendStop);
    button.addEventListener("pointerleave", sendStop);
    button.addEventListener("pointercancel", sendStop);
  });

  window.addEventListener("blur", sendStop);
  document.addEventListener("visibilitychange", () => {
    if (document.hidden) sendStop();
  });
</script>
</body>
</html>
