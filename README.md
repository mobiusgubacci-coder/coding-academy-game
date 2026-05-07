# coding-academy-game
<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta
      name="description"
      content="Play Phoenix Coding Academy Climb, a 2D graduation platformer about reaching the school rooftop."
    />
    <title>Phoenix Coding Academy Climb</title>
    <link rel="stylesheet" href="styles.css?v=18" />
  </head>
  <body>
    <main class="site">
      <header class="site-header">
        <div>
          <p class="eyebrow">Phoenix Coding Academy</p>
          <h1>Graduation Climb</h1>
        </div>
        <a class="play-link" href="#game">Play</a>
      </header>

      <section id="game" class="game-shell" aria-label="Phoenix Coding Academy Climb game">
        <section class="hud" aria-label="Game status">
          <div>
            <span class="label">Height</span>
            <strong id="heightReadout">0%</strong>
          </div>
          <div>
            <span class="label">Badges</span>
            <strong id="badgeReadout">0 / 6</strong>
          </div>
          <div>
            <span class="label">Status</span>
            <strong id="statusReadout">Loading</strong>
          </div>
          <button id="restartButton" type="button">Restart</button>
        </section>

        <canvas
          id="gameCanvas"
          width="960"
          height="640"
          tabindex="0"
          aria-label="Phoenix Coding Academy platformer"
        ></canvas>

        <section class="touch-controls" aria-label="Game controls">
          <button id="leftButton" type="button" aria-label="Move left">Left</button>
          <button id="jumpButton" type="button" aria-label="Jump">Jump</button>
          <button id="rightButton" type="button" aria-label="Move right">Right</button>
        </section>

        <section class="controls" aria-label="Controls">
          <span>A / D or arrows to move</span>
          <span>Space, W, or up to jump</span>
          <span>Reach the CONGRATS!! flag</span>
        </section>
      </section>

      <section class="site-info" aria-label="Game details">
        <article>
          <h2>Goal</h2>
          <p>Climb the school, collect code badges, and reach the rooftop graduation flag.</p>
        </article>
        <article>
          <h2>Controls</h2>
          <p>Use the keyboard or the on-screen buttons. Click the game once if keyboard controls do not respond.</p>
        </article>
        <article>
          <h2>Website Files</h2>
          <p>This folder is ready to publish as a static website with HTML, CSS, and JavaScript.</p>
        </article>
      </section>
    </main>

    <script src="game.js?v=18"></script>
  </body>
</html>

h1,
h2,
p {
  margin: 0;
}

h1 {
  color: #123044;
  font-size: clamp(2rem, 5vw, 4.5rem);
  line-height: 0.95;
}

h2 {
  color: #123044;
  font-size: 1rem;
}

.play-link,
button {
  min-width: 96px;
  min-height: 40px;
  border: 0;
  border-radius: 6px;
  background: linear-gradient(180deg, #4dc0d4, #2f9bb3);
  color: white;
  cursor: pointer;
  font: inherit;
  font-weight: 800;
  text-decoration: none;
  display: inline-grid;
  place-items: center;
  box-shadow: 0 8px 18px rgba(18, 48, 68, 0.16);
}

.play-link:hover,
.play-link:focus-visible,
button:hover,
button:focus-visible {
  background: #176477;
  outline: 3px solid rgba(47, 155, 179, 0.25);
}

.game-shell {
  min-height: calc(100vh - 128px);
  display: grid;
  grid-template-rows: auto minmax(440px, 1fr) auto auto;
  gap: 12px;
}

.hud,
.controls {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 12px;
  color: #123044;
}

.hud {
  min-height: 58px;
  padding: 0 2px 10px;
  text-shadow: 0 1px 0 rgba(255, 255, 255, 0.55);
}

.hud div {
  display: grid;
  gap: 2px;
}

.label {
  color: #446374;
  font-size: 0.78rem;
  font-weight: 700;
  text-transform: uppercase;
}

strong {
  font-size: 1.25rem;
}

canvas {
  width: 100%;
  height: 100%;
  min-height: 440px;
  border: 3px solid #123044;
  border-radius: 8px;
  background: #b9d9e8;
  display: block;
  image-rendering: auto;
  box-shadow: 0 20px 52px rgba(18, 48, 68, 0.24);
}

.touch-controls {
  display: grid;
  grid-template-columns: 1fr 1.2fr 1fr;
  gap: 10px;
}

.touch-controls button {
  min-height: 48px;
  touch-action: none;
}

.controls {
  min-height: 44px;
  color: #385565;
  font-size: 0.92rem;
  flex-wrap: wrap;
}

.site-info {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 14px;
  padding: 6px 0 20px;
}

.site-info article {
  border-top: 2px solid rgba(18, 48, 68, 0.18);
  padding-top: 12px;
  color: #385565;
  display: grid;
  gap: 6px;
}

@media (max-width: 760px) {
  .site {
    padding: 10px;
  }

  .site-header,
  .hud,
  .controls {
    align-items: flex-start;
  }

  .site-header {
    display: grid;
  }

  .hud,
  .controls,
  .site-info {
    display: grid;
  }

  .site-info {
    grid-template-columns: 1fr;
  }
}
  ctx.fillRect(3, 32 - run * 4, 15 + Math.max(0, -stride) * 4, 5);

  ctx.restore();
}

function drawReadableShirtText(facing) {
  ctx.save();
  if (facing < 0) ctx.scale(-1, 1);
  ctx.fillStyle = "#123044";
  ctx.font = "900 10px Arial";
  ctx.fillText("PCA", facing < 0 ? -9 : -6, 13);
  ctx.restore();
}

function drawGraduationCap(run) {
  drawPoly([
    [-18, -39],
    [0, -47],
    [18, -39],
    [0, -32],
  ], "#071b27");
  ctx.fillStyle = "#123044";
  roundRect(-10, -38, 20, 8, 2);
  ctx.fill();
  ctx.fillStyle = GOLD;
  ctx.beginPath();
  ctx.arc(0, -39, 2.5, 0, Math.PI * 2);
  ctx.fill();
  ctx.strokeStyle = GOLD;
  ctx.lineWidth = 2;
  ctx.beginPath();
  ctx.moveTo(0, -39);
  ctx.quadraticCurveTo(12, -31 + run * 1.5, 15, -22);
  ctx.stroke();
  ctx.fillStyle = GOLD;
  ctx.beginPath();
  ctx.moveTo(15, -22);
  ctx.lineTo(11, -14);
  ctx.lineTo(19, -14);
  ctx.closePath();
  ctx.fill();
}

function drawFinish() {
  const time = performance.now();
  const poleX = 610;
  const poleTop = 142;
  const poleBottom = 228;

  ctx.save();
  ctx.globalAlpha = 0.18 + Math.sin(time / 260) * 0.05;
  ctx.fillStyle = GOLD;
  ctx.beginPath();
  ctx.ellipse(FINISH_ZONE.x + FINISH_ZONE.w / 2, FINISH_ZONE.y + FINISH_ZONE.h - 14, 92, 14, 0, 0, Math.PI * 2);
  ctx.fill();
  ctx.restore();

  ctx.fillStyle = "#123044";
  ctx.fillRect(poleX, poleTop, 8, poleBottom - poleTop);
  ctx.fillStyle = ACCENT;
  ctx.beginPath();
  ctx.moveTo(poleX + 8, 150);
  ctx.quadraticCurveTo(684, 136 + Math.sin(time / 190) * 6, 786, 150);
  ctx.lineTo(786, 194);
  ctx.quadraticCurveTo(684, 180 + Math.cos(time / 210) * 6, poleX + 8, 194);
  ctx.closePath();
  ctx.fill();
  ctx.fillStyle = "#ffffff";
  ctx.font = "900 17px Arial";
  ctx.fillText("CONGRATS!!", 646, 178);
}

function drawOverlay() {
  if (!state.won) return;

  const elapsed = performance.now() - state.winStartedAt;
  const panelIn = Math.min(1, elapsed / 700);
  const ease = 1 - Math.pow(1 - panelIn, 3);

  ctx.fillStyle = "rgba(18,48,68,0.58)";
  ctx.fillRect(0, 0, WIDTH, HEIGHT);

  drawWinCapCelebration(elapsed);

  const panelW = 560;
  const panelH = 236;
  const panelX = WIDTH / 2 - panelW / 2;
  const panelY = HEIGHT / 2 - panelH / 2 + 30 - (1 - ease) * 34;
  const collected = state.badges.filter((badge) => badge.collected).length;
  const total = state.badges.length;
  ctx.save();
  ctx.globalAlpha = ease;
  ctx.shadowColor = "rgba(0,0,0,0.28)";
  ctx.shadowBlur = 28;
  ctx.shadowOffsetY = 14;
  ctx.fillStyle = "#f8fcfd";
  roundRect(panelX, panelY, panelW, panelH, 16);
  ctx.fill();
  ctx.shadowBlur = 0;
  ctx.shadowOffsetY = 0;

  ctx.fillStyle = "#123044";
  roundRect(panelX + 22, panelY + 22, panelW - 44, 8, 4);
  ctx.fill();
  ctx.fillStyle = ACCENT;
  roundRect(panelX + 22, panelY + 22, (panelW - 44) * ease, 8, 4);
  ctx.fill();

  ctx.textAlign = "center";
  ctx.fillStyle = "#123044";
  ctx.font = "900 44px Arial";
  ctx.fillText("Graduated the Climb!", WIDTH / 2, panelY + 82);
  ctx.fillStyle = "#176477";
  ctx.font = "800 23px Arial";
  ctx.fillText("Happy Graduation", WIDTH / 2, panelY + 124);
  ctx.fillStyle = "#385565";
  ctx.font = "700 18px Arial";
  ctx.fillText(`Code badges: ${collected} / ${total}. Press Restart to climb again.`, WIDTH / 2, panelY + 166);

  ctx.fillStyle = ACCENT;
  roundRect(WIDTH / 2 - 78, panelY + 188, 156, 30, 15);
  ctx.fill();
  ctx.fillStyle = "#ffffff";
  ctx.font = "900 15px Arial";
  ctx.fillText("PCA CLASS UP", WIDTH / 2, panelY + 209);
  ctx.textAlign = "left";
  ctx.restore();
}

function drawWinCapCelebration(elapsed) {
  const t = Math.min(1, elapsed / 1500);
  const spin = elapsed / 115;
  const arcY = Math.sin(t * Math.PI) * 260;
  const capX = WIDTH / 2 + Math.sin(elapsed / 250) * 70;
  const capY = HEIGHT / 2 + 40 - arcY + t * 42;

  for (let i = 0; i < 22; i += 1) {
    const drop = (elapsed * (0.08 + i * 0.002) + i * 37) % 420;
    const x = 120 + ((i * 71) % 720) + Math.sin(elapsed / 300 + i) * 12;
    const y = 68 + drop;
    ctx.fillStyle = i % 3 === 0 ? GOLD : i % 3 === 1 ? ACCENT : "#ffffff";
    ctx.save();
    ctx.translate(x, y);
    ctx.rotate(elapsed / 240 + i);
    ctx.fillRect(-4, -4, 8, 8);
    ctx.restore();
  }

  ctx.save();
  ctx.translate(capX, capY);
  ctx.rotate(spin);
  ctx.scale(2.2, 2.2);
  drawPoly([
    [-18, -5],
    [0, -14],
    [18, -5],
    [0, 4],
  ], "#071b27");
  ctx.fillStyle = "#123044";
  roundRect(-10, -4, 20, 8, 2);
  ctx.fill();
  ctx.fillStyle = GOLD;
  ctx.beginPath();
  ctx.arc(0, -5, 2.5, 0, Math.PI * 2);
  ctx.fill();
  ctx.strokeStyle = GOLD;
  ctx.lineWidth = 2;
  ctx.beginPath();
  ctx.moveTo(0, -5);
  ctx.quadraticCurveTo(13, 0 + Math.sin(elapsed / 110) * 2, 17, 12);
  ctx.stroke();
  ctx.fillStyle = GOLD;
  ctx.beginPath();
  ctx.moveTo(17, 12);
  ctx.lineTo(13, 21);
  ctx.lineTo(21, 21);
  ctx.closePath();
  ctx.fill();
  ctx.restore();
}

function loop() {
  update();
  draw();
  requestAnimationFrame(loop);
}

window.addEventListener("error", (event) => {
  setStatus("Error");
  ctx.setTransform(1, 0, 0, 1, 0, 0);
  ctx.fillStyle = "#ffffff";
  ctx.fillRect(0, 0, WIDTH, HEIGHT);
  ctx.fillStyle = "#123044";
  ctx.font = "700 26px Arial";
  ctx.fillText("Game error", 32, 58);
  ctx.font = "18px Arial";
  ctx.fillText(event.message || "Refresh the page and try again.", 32, 94);
});

try {
  loop();
} catch (error) {
  setStatus("Error");
  ctx.fillStyle = "#ffffff";
  ctx.fillRect(0, 0, WIDTH, HEIGHT);
  ctx.fillStyle = "#123044";
  ctx.font = "700 26px Arial";
  ctx.fillText("Game error", 32, 58);
  ctx.font = "18px Arial";
  ctx.fillText(error.message || "Refresh the page and try again.", 32, 94);
}
Filter files
Filter files…
