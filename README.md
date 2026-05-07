* {
  box-sizing: border-box;
}

html {
  scroll-behavior: smooth;
}

html,
body {
  min-height: 100%;
}

body {
  margin: 0;
  background:
    radial-gradient(circle at 18% 8%, rgba(47, 155, 179, 0.22), transparent 28%),
    linear-gradient(145deg, #c8e6f1 0%, #f0e4cf 58%, #d9e8eb 100%);
  color: #123044;
  font-family:
    Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI",
    sans-serif;
}

.site {
  width: min(100%, 1180px);
  min-height: 100vh;
  margin: 0 auto;
  padding: 18px;
  display: grid;
  gap: 18px;
}

.site-header {
  min-height: 78px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 16px;
  border-bottom: 3px solid #2f9bb3;
}

.eyebrow {
  margin: 0 0 2px;
  color: #176477;
  font-size: 0.78rem;
  font-weight: 900;
  letter-spacing: 0;
  text-transform: uppercase;
}

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

  ], "#234c5f");
  for (let i = 0; i < 5; i += 1) {
    drawGlass(552 + i * 50, baseY - 604, 34, 56, i, true);
  }

  ctx.fillStyle = "#163f56";
  ctx.font = "800 28px Arial";
  ctx.fillText("PHOENIX", 228, baseY - 718);
  ctx.fillText("CODING ACADEMY", 228, baseY - 686);
  ctx.strokeStyle = ACCENT;
  ctx.lineWidth = 6;
  ctx.beginPath();
  ctx.moveTo(198, baseY - 730);
  ctx.lineTo(176, baseY - 704);
  ctx.lineTo(198, baseY - 678);
  ctx.stroke();

  drawEntrance(baseY, time);
  drawAddressSign(baseY);
  drawPalmShadows(baseY, time);
  ctx.fillStyle = "rgba(18,48,68,0.08)";
  ctx.fillRect(88, baseY + 392, 718, 18);
}

function drawPoly(points, color) {
  ctx.fillStyle = color;
  ctx.beginPath();
  ctx.moveTo(points[0][0], points[0][1]);
  for (let i = 1; i < points.length; i += 1) ctx.lineTo(points[i][0], points[i][1]);
  ctx.closePath();
  ctx.fill();
}

function drawWindowGrid(startX, startY, cols, rows, time) {
  for (let row = 0; row < rows; row += 1) {
    for (let col = 0; col < cols; col += 1) {
      const x = startX + col * 64 + (row % 2) * 3;
      const y = startY + row * 66;
      const lit = Math.sin(time / 520 + row * 1.7 + col * 1.2) > 0.18;
      drawGlass(x, y, 34, 40, row + col, lit);
    }
  }
}

function drawEntrance(baseY, time) {
  drawPoly([
    [560, baseY - 340],
    [702, baseY - 340],
    [724, baseY - 306],
    [694, baseY + 8],
    [570, baseY + 8],
    [544, baseY - 306],
  ], ACCENT);
  ctx.fillStyle = "#123044";
  ctx.fillRect(590, baseY - 280, 78, 288);
  ctx.fillStyle = "rgba(124,206,230,0.65)";
  ctx.fillRect(600, baseY - 260, 24, 254);
  ctx.fillRect(634, baseY - 260, 24, 254);
  ctx.fillStyle = `rgba(255,212,59,${0.2 + Math.sin(time / 300) * 0.06})`;
  ctx.fillRect(604, baseY - 226, 50, 84);
  ctx.strokeStyle = "rgba(255,255,255,0.42)";
  ctx.lineWidth = 3;
  ctx.beginPath();
  ctx.moveTo(604, baseY - 254);
  ctx.lineTo(652, baseY - 18);
  ctx.stroke();
}

function drawAddressSign(baseY) {
  drawPoly([
    [616, baseY - 492],
    [794, baseY - 492],
    [786, baseY - 446],
    [608, baseY - 446],
  ], "#123044");
  ctx.fillStyle = "#ffffff";
  ctx.font = "800 20px Arial";
  ctx.fillText("4359", 678, baseY - 462);
}

function drawPalmShadows(baseY, time) {
  ctx.save();
  ctx.strokeStyle = "rgba(18,48,68,0.1)";
  ctx.lineWidth = 4;
  for (let i = 0; i < 4; i += 1) {
    const x = 140 + i * 168;
    ctx.beginPath();
    ctx.moveTo(x, baseY + 438);
    ctx.quadraticCurveTo(x + Math.sin(time / 700 + i) * 28, baseY + 270, x + 20, baseY + 132);
    ctx.stroke();
    for (let j = 0; j < 5; j += 1) {
      ctx.beginPath();
      ctx.moveTo(x + 20, baseY + 132);
      ctx.lineTo(x + 20 + Math.cos(j * 1.2) * 48, baseY + 132 + Math.sin(j * 1.2) * 22);
      ctx.stroke();
    }
  }
  ctx.restore();
}

function drawGlass(x, y, w, h, seed, lit = true) {
  const pulse = Math.sin(performance.now() / 380 + seed) * 0.12;
  const glow = lit ? 0.28 + pulse : 0.08;
  ctx.fillStyle = `rgba(135, 213, 235, ${0.62 + glow})`;
  ctx.fillRect(x, y, w, h);
  ctx.fillStyle = `rgba(255, 212, 59, ${glow})`;
  ctx.fillRect(x + 4, y + 5, w - 8, h - 10);
  ctx.strokeStyle = "rgba(18,48,68,0.26)";
  ctx.lineWidth = 2;
  ctx.strokeRect(x, y, w, h);
  ctx.strokeStyle = "rgba(255,255,255,0.45)";
  ctx.beginPath();
  ctx.moveTo(x + 6, y + 7);
  ctx.lineTo(x + w - 5, y + h - 10);
  ctx.stroke();
}

function drawVents() {
  const time = performance.now();
  for (const vent of vents) {
    ctx.fillStyle = "#123044";
    ctx.fillRect(vent.x - 32, vent.y, 64, 12);
    ctx.fillStyle = "#d9e9ed";
    for (let i = 0; i < 4; i += 1) {
      const y = vent.y - 10 - i * 17 - ((time / 36 + i * 7) % 17);
      ctx.globalAlpha = 0.24 - i * 0.04;
      ctx.beginPath();
      ctx.ellipse(vent.x + Math.sin(time / 260 + i) * 18, y, 30 + i * 8, 8, 0, 0, Math.PI * 2);
      ctx.fill();
    }
    ctx.globalAlpha = 1;
  }
}

function drawPlatforms() {
  const time = performance.now();
  for (const platform of platforms) {
    const isRoof = platform.type === "roof";
    const isGround = platform.type === "ground";
    const top = isGround ? "#243c45" : isRoof ? "#123044" : ACCENT;
    const bottom = isGround ? "#142932" : isRoof ? "#0d2634" : ACCENT_DARK;

    drawPoly([
      [platform.x, platform.y],
      [platform.x + platform.w, platform.y],
      [platform.x + platform.w - 12, platform.y + platform.h + 14],
      [platform.x + 12, platform.y + platform.h + 14],
    ], bottom);
    ctx.fillStyle = top;
    roundRect(platform.x, platform.y - 2, platform.w, platform.h + 4, 5);
    ctx.fill();
    ctx.fillStyle = "rgba(255,255,255,0.36)";
    roundRect(platform.x + 8, platform.y + 2, platform.w - 16, 4, 2);
    ctx.fill();

    if (!isGround) {
      ctx.strokeStyle = "rgba(18,48,68,0.32)";
      ctx.lineWidth = 3;
      ctx.beginPath();
      ctx.moveTo(platform.x + 18, platform.y - 14);
      ctx.lineTo(platform.x + platform.w - 18, platform.y - 14);
      ctx.stroke();
      for (let x = platform.x + 28; x < platform.x + platform.w - 18; x += 46) {
        ctx.beginPath();
        ctx.moveTo(x, platform.y - 14);
        ctx.lineTo(x, platform.y - 2);
        ctx.stroke();
      }
    }

    if (!isGround) {
      ctx.fillStyle = `rgba(255, 212, 59, ${0.22 + Math.sin(time / 240 + platform.x) * 0.08})`;
      for (let x = platform.x + 14; x < platform.x + platform.w - 12; x += 42) {
        ctx.fillRect(x, platform.y + platform.h - 5, 18, 3);
      }
    }
  }
}

function roundRect(x, y, w, h, r) {
  ctx.beginPath();
  ctx.moveTo(x + r, y);
  ctx.lineTo(x + w - r, y);
  ctx.quadraticCurveTo(x + w, y, x + w, y + r);
  ctx.lineTo(x + w, y + h - r);
  ctx.quadraticCurveTo(x + w, y + h, x + w - r, y + h);
  ctx.lineTo(x + r, y + h);
  ctx.quadraticCurveTo(x, y + h, x, y + h - r);
  ctx.lineTo(x, y + r);
  ctx.quadraticCurveTo(x, y, x + r, y);
  ctx.closePath();
}

function drawBadges() {
  const time = performance.now();
  for (const badge of state.badges) {
    if (badge.collected) continue;
    const pulse = Math.sin(time / 150 + badge.x) * 3;
    const spin = time / 360 + badge.x;
    ctx.fillStyle = "rgba(18,48,68,0.22)";
    ctx.beginPath();
    ctx.ellipse(badge.x, badge.y + 24, 18, 5, 0, 0, Math.PI * 2);
    ctx.fill();

    ctx.save();
    ctx.translate(badge.x, badge.y + pulse);
    ctx.rotate(Math.sin(spin) * 0.18);

    ctx.shadowColor = "rgba(255,212,59,0.72)";
    ctx.shadowBlur = 18;
    ctx.fillStyle = GOLD;
    ctx.beginPath();
    for (let i = 0; i < 8; i += 1) {
      const r = i % 2 ? badge.r * 0.78 : badge.r * 1.18;
      const a = (Math.PI * 2 * i) / 8 - Math.PI / 2;
      ctx.lineTo(Math.cos(a) * r, Math.sin(a) * r);
    }
    ctx.closePath();
    ctx.fill();
    ctx.shadowBlur = 0;

    ctx.strokeStyle = "#123044";
    ctx.lineWidth = 3;
    ctx.stroke();
    ctx.fillStyle = "#123044";
    ctx.font = "800 11px Arial";
    ctx.textAlign = "center";
    ctx.textBaseline = "middle";
    ctx.fillText(badge.label, 0, 1);
    ctx.restore();
  }
  ctx.textAlign = "left";
  ctx.textBaseline = "alphabetic";
}

function drawParticles() {
  for (const wave of state.shockwaves) {
    ctx.strokeStyle = `rgba(255,255,255,${wave.life / 20})`;
    ctx.lineWidth = 3;
    ctx.beginPath();
    ctx.ellipse(wave.x, wave.y, wave.r, wave.r * 0.28, 0, 0, Math.PI * 2);
    ctx.stroke();
  }

  for (const particle of state.particles) {
    ctx.fillStyle = particle.color;
    ctx.globalAlpha = Math.max(0, Math.min(1, particle.life / 28));
    ctx.beginPath();
    ctx.arc(particle.x, particle.y, particle.size, 0, Math.PI * 2);
    ctx.fill();
