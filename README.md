<!DOCTYPE html>
<html lang="zh-Hant">
<head>
  <meta charset="UTF-8">
  <title>WePlay 修仙系統</title>
  <style>
    body {
      font-family: "微軟正黑體", sans-serif;
      background: linear-gradient(#f0f8ff, #e0ffff);
      text-align: center;
      padding: 30px;
    }
    h1 {
      color: #8b0000;
    }
    button {
      padding: 10px 20px;
      margin: 10px;
      font-size: 18px;
    }
    #log {
      margin-top: 20px;
      white-space: pre-line;
      font-size: 16px;
      background: #fff;
      border: 1px solid #aaa;
      padding: 15px;
      width: 80%;
      margin-left: auto;
      margin-right: auto;
    }
  </style>
</head>
<body>

  <h1>✨ WePlay 修仙系統 ✨</h1>

  <p id="status">載入中...</p>

  <button onclick="cultivate()">🔮 修煉</button>
  <button onclick="usePill()">💊 使用丹藥</button>
  <button onclick="showStatus()">📜 查看狀態</button>

  <div id="log"></div>

  <script>
    // 初始資料
    const player = {
      name: "道友",
      sect: "蜀山",
      spiritualRoot: "火靈根",
      realmIndex: 0,
      exp: 0,
      realms: ["練氣", "築基", "結丹", "元嬰", "化神", "大乘", "飛升"],
      pills: 3,
      artifactBonus: 0.2,
      beastBonus: 0.1,
      sectBonus: 0.15
    };

    function cultivate() {
      const base = Math.floor(Math.random() * 30) + 20;
      const bonus = 1 + player.artifactBonus + player.beastBonus + player.sectBonus;
      const totalExp = Math.floor(base * bonus);
      player.exp += totalExp;

      let msg = `你修煉獲得了 ${totalExp} 修為（加成後）！`;

      if (player.exp >= 100) {
        player.exp = 0;
        if (player.realmIndex < player.realms.length - 1) {
          player.realmIndex++;
          msg += `\n🎉 恭喜突破到【${player.realms[player.realmIndex]}】！`;
        } else {
          msg += `\n🌟 你已達最高境界【${player.realms[player.realmIndex]}】！`;
        }
      }

      log(msg);
      updateStatus();
    }

    function usePill() {
      if (player.pills > 0) {
        player.exp += 40;
        player.pills--;
        log("💊 使用丹藥，修為增加 40！");
        updateStatus();
      } else {
        log("❌ 你沒有丹藥了！");
      }
    }

    function showStatus() {
      const status = 
        👤 名稱：${player.name}\n +
        🛕 門派：${player.sect}（修煉加成 +15%）\n +
        🌱 靈根：${player.spiritualRoot}\n +
        🔮 境界：${player.realms[player.realmIndex]}\n +
        📈 修為：${player.exp}/100\n +
        💎 法寶加成：+${Math.floor(player.artifactBonus * 100)}%\n +
        🐉 靈獸加成：+${Math.floor(player.beastBonus * 100)}%\n +
        `💊 丹藥數量：${player.pills}`;
      log(status);
    }

    function log(text) {
      document.getElementById("log").textContent = text;
    }

    function updateStatus() {
      document.getElementById("status").textContent =
        `【${player.name}｜${player.realms[player.realmIndex]}】 修為 ${player.exp}/100`;
    }

    // 初始狀態
    updateStatus();
  </script>

</body>
</html>
