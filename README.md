<!DOCTYPE html>
<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Nail Size Filter</title>
<style>
  body {
    margin: 0;
    overflow: hidden;
    background: #000;
  }
  #video {
    position: fixed;
    inset: 0;
    width: 100vw;
    height: 100vh;
    object-fit: cover;
  }
  #overlay {
    position: fixed;
    inset: 0;
    width: 100vw;
    height: 100vh;
    pointer-events: none;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  #chipImage {
    width: 55%;
    opacity: 0.9;
  }
  #chipSelector {
    position: fixed;
    bottom: 16px;
    left: 50%;
    transform: translateX(-50%);
    display: flex;
    gap: 12px;
    z-index: 10;
  }
  button {
    padding: 10px 14px;
    border-radius: 8px;
    border: none;
    background: white;
    font-size: 16px;
  }
</style>
</head>
<body>

<video id="video" autoplay playsinline></video>

<div id="overlay">
  <img id="chipImage" src="">
</div>

<div id="chipSelector">
  <button onclick="setChip('chipA.png')">A</button>
  <button onclick="setChip('chipB.png')">B</button>
  <button onclick="setChip('chipC.png')">C</button>
</div>

<script>
navigator.mediaDevices.getUserMedia({ video: { facingMode: "environment" } })
  .then(stream => {
    document.getElementById('video').srcObject = stream;
  })
  .catch(err => {
    alert("カメラを起動できません: " + err);
  });

function setChip(name) {
  document.getElementById("chipImage").src = name;
}
</script>

</body>
</html>
