<!DOCTYPE html>
<html lang="zh-Hant">
<head>
  <meta charset="UTF-8">
  <title>WePlay 修仙輔助工具</title>
  <style>
    body {
      font-family: sans-serif;
      background: #fdf6e3;
      padding: 20px;
    }
    h1 {
      text-align: center;
    }
    .section {
      margin-bottom: 30px;
      padding: 15px;
      background: #fffbe6;
      border: 1px solid #ddd;
      border-radius: 10px;
    }
    button {
      padding: 10px;
      margin-top: 10px;
      font-size: 16px;
      cursor: pointer;
    }
    .result {
      margin-top: 10px;
      font-weight: bold;
      color: #1e5f5f;
    }
  </style>
</head>
<body>
  <h1>🧙 WePlay 修仙輔助工具</h1>

  <div class="section">
    <h2>🔮 法寶生成器</h2>
    <button onclick="generateArtifact()">生成法寶</button>
    <div class="result" id="artifactResult"></div>
  </div>

  <div class="section">
    <h2>💊 丹藥製作指南</h2>
    <button onclick="getPillGuide()">查看丹藥</button>
    <div class="result" id="pillResult"></div>
  </div>

  <div class="section">
    <h2>🏯 門派建議器</h2>
    <button onclick="suggestSect()">推薦門派</button>
    <div class="result" id="sectResult"></div>
  </div>

  <div class="section">
    <h2>🦄 靈獸夥伴推薦</h2>
    <button onclick="suggestPet()">召喚靈獸</button>
    <div class="result" id="petResult"></div>
  </div>

  <script>
    const artifacts = ["混元神劍", "九天雷珠", "紫炎火瓶", "玄冰天玉", "靈風扇"];
    const pills = ["養氣丹：增加靈力", "聚神丹：提高修練速度", "破障丹：突破瓶頸", "金骨丹：強化體魄"];
    const sects = ["天劍宗", "幽冥谷", "煉火門", "碧落宮", "萬妖山"];
    const pets = ["靈狐", "青龍", "白虎", "冰凰", "雷豹"];

    function getRandom(arr) {
      return arr[Math.floor(Math.random() * arr.length)];
    }

    function generateArtifact() {
      document.getElementById("artifactResult").textContent = getRandom(artifacts);
    }

    function getPillGuide() {
      document.getElementById("pillResult").textContent = getRandom(pills);
    }

    function suggestSect() {
      document.getElementById("sectResult").textContent = getRandom(sects);
    }

    function suggestPet() {
      document.getElementById("petResult").textContent = getRandom(pets);
    }
  </script>
</body>
</html>
