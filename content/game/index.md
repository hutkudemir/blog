---
title: "Central Bank Game"
draft: false
---

<!-- ── Full-screen toggle styles ───────────────────────────────────── -->
<style>
.game-wrapper {
  position: relative;             /* so the button can be positioned */
  width: 100%;
  max-width: 100%;
  height: 85vh;                   /* normal embedded height          */
}
.game-iframe {
  width: 100%;
  height: 100%;
  border: none;
}
/* the little square button */
.fs-btn {
  position: absolute;
  top: 8px;
  right: 8px;
  width: 36px;
  height: 36px;
  cursor: pointer;
  border: 2px solid #ffffffaa;
  border-radius: 4px;
  background: #00000055;
  backdrop-filter: blur(2px);
}
.fs-btn::after {                  /* draw the ⬜ icon with CSS        */
  content: "";
  display: block;
  width: 60%;
  height: 60%;
  margin: 20% auto;
  border: 2px solid #fff;
}
.fs-btn:hover {
  background: #00000088;
}
</style>

<!-- ── HTML: wrapper, iframe, button ───────────────────────────────── -->
<div class="game-wrapper" id="gameBox">
  <iframe
    id="gameFrame"
    class="game-iframe"
    src="https://hutkudemir.github.io/central-bank-game/"
    loading="lazy">
  </iframe>
  <div class="fs-btn" id="fsBtn" title="Tam ekran"></div>
</div>

<!-- ── JavaScript: toggle Fullscreen API ───────────────────────────── -->
<script>
(function () {
  const btn   = document.getElementById('fsBtn');
  const wrap  = document.getElementById('gameBox');

  btn.addEventListener('click', async () => {
    if (!document.fullscreenElement) {
      try {
        /* requestFullscreen works on the wrapper;
           the iframe expands with it */
        await wrap.requestFullscreen({ navigationUI: 'hide' });
        wrap.style.height = '100vh';   // fill screen
      } catch (err) {
        console.error(err);
      }
    } else {
      /* exit */
      await document.exitFullscreen();
      wrap.style.height = '85vh';      // restore embedded height
    }
  });

  /* When user presses Esc, restore height */
  document.addEventListener('fullscreenchange', () => {
    if (!document.fullscreenElement) {
      wrap.style.height = '85vh';
    }
  });
})();
</script>
