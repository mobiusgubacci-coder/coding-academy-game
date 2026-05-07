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
