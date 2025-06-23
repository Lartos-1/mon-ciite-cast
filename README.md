<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <title>Stormex Cast</title>
  <style>
    body {
      background: black;
      color: white;
      text-align: center;
      font-family: sans-serif;
    }
    .player-container {
      position: relative;
      display: inline-block;
      margin: 10px;
    }
    video {
      width: 300px;
      height: 200px;
      border: 2px solid white;
    }
    .overlay {
      position: absolute;
      top: 5px;
      left: 5px;
      background: rgba(0, 0, 0, 0.7);
      padding: 5px 10px;
      font-weight: bold;
      border-radius: 5px;
    }
    .controls {
      margin-top: 10px;
    }
    .share-button, .stop-button {
      background: white;
      color: black;
      border: none;
      padding: 5px 10px;
      cursor: pointer;
      margin: 5px;
      font-weight: bold;
      border-radius: 5px;
    }
  </style>
</head>
<body>
  <h1>🎥 Cast Stormex</h1>

  <div class="player-container">
    <div class="overlay">SOM FELA</div>
    <video id="fela" autoplay></video>
    <div class="controls">
      <button class="share-button" onclick="startShare('fela')">Partager ton écran</button>
      <button class="stop-button" onclick="stopShare('fela')">Arrêter</button>
    </div>
  </div>

  <div class="player-container">
    <div class="overlay">SOM NATOKY</div>
    <video id="natoky" autoplay></video>
    <div class="controls">
      <button class="share-button" onclick="startShare('natoky')">Partager ton écran</button>
      <button class="stop-button" onclick="stopShare('natoky')">Arrêter</button>
    </div>
  </div>

  <div class="player-container">
    <div class="overlay">SOM BEMA</div>
    <video id="bema" autoplay></video>
    <div class="controls">
      <button class="share-button" onclick="startShare('bema')">Partager ton écran</button>
      <button class="stop-button" onclick="stopShare('bema')">Arrêter</button>
    </div>
  </div>

  <div class="player-container">
    <div class="overlay">SOM W1XY</div>
    <video id="w1xy" autoplay></video>
    <div class="controls">
      <button class="share-button" onclick="startShare('w1xy')">Partager ton écran</button>
      <button class="stop-button" onclick="stopShare('w1xy')">Arrêter</button>
    </div>
  </div>

  <script>
    async function startShare(id) {
      try {
        const stream = await navigator.mediaDevices.getDisplayMedia({ video: true });
        document.getElementById(id).srcObject = stream;
      } catch (err) {
        alert("Erreur : " + err.message);
      }
    }

    function stopShare(id) {
      const video = document.getElementById(id);
      if (video.srcObject) {
        video.srcObject.getTracks().forEach(track => track.stop());
        video.srcObject = null;
      }
    }
  </script>
</body>
</html>
