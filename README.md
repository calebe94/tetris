# 🎮 Tetris 🚀

This project is a classic implementation of the popular game Tetris, written in C++ using the SDL2 library. Tetris is a puzzle game where players manipulate falling blocks called "tetrominos" to create complete lines on the game board. When a line is completed, it clears from the board, and the player earns points. The game ends when the stack of tetrominos reaches the top of the game board.

The main objective of this project is to provide a fun and interactive way to play the timeless game of Tetris, while also serving as a practical example of using the SDL2 library for game development in C++.

<img src="./assets/screenshots/game.png" width="400px">

<div align="center">

## 🎮 [Try it online! 🌐](https://calebe94.github.io/tetris/#play)

<a href="#play" id="play-button" style="display:inline-block;padding:16px 32px;background:#e94560;color:#fff;text-decoration:none;border-radius:8px;font-weight:bold;font-size:1.2em;box-shadow:0 4px 12px rgba(233,69,96,0.4);">🎮 JOGAR TETRIS AGORA 🎮</a>

<div id="play-overlay" role="dialog" aria-label="Tetris game">
  <div class="play-header">
    <h2>🎮 Tetris</h2>
    <button type="button" data-close>✕ Fechar</button>
  </div>
  <iframe id="game-frame" title="Tetris" allow="autoplay" referrerpolicy="no-referrer"></iframe>
  <p class="play-hint">Controles: ← → mover | ↑ / Space rotacionar | ↓ descer | P pausar</p>
  <p id="play-status"></p>
</div>

</div>

<style>
  #play-overlay {
    display: none;
    position: fixed;
    inset: 0;
    background: rgba(0, 0, 0, 0.95);
    z-index: 9999;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    padding: 20px;
    box-sizing: border-box;
  }
  #play-overlay.is-open { display: flex; }
  #play-overlay .play-header {
    width: 100%;
    max-width: 600px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 12px;
    color: #fff;
  }
  #play-overlay .play-header h2 { margin: 0; }
  #play-overlay .play-header button {
    background: #e94560;
    color: #fff;
    border: none;
    padding: 8px 16px;
    border-radius: 4px;
    cursor: pointer;
    font-size: 1em;
  }
  #play-overlay iframe {
    width: 100%;
    max-width: 600px;
    height: 80vh;
    max-height: 800px;
    border: 1px solid #333;
    border-radius: 8px;
    background: #000;
  }
  #play-overlay .play-hint { color: #888; font-size: 0.85em; margin-top: 12px; }
  #play-status { color: #888; font-size: 0.75em; margin-top: 4px; }
</style>

<script>
(function () {
  var REPO = 'calebe94/tetris';
  var API = 'https://api.github.com/repos/' + REPO + '/releases/latest';
  var CACHE = 'tetris-release-sha';
  var STATUS = document.getElementById('play-status');
  var FRAME = document.getElementById('game-frame');
  var OPEN = document.getElementById('play-overlay');
  var BTN = document.getElementById('play-button');

  function closeGame() {
    OPEN.classList.remove('is-open');
    FRAME.removeAttribute('src');
  }

  OPEN.addEventListener('click', function (e) {
    if (e.target === OPEN || e.target.matches('[data-close]')) closeGame();
  });
  document.addEventListener('keydown', function (e) {
    if (e.key === 'Escape') closeGame();
  });

  function getRelease() {
    try {
      var cached = JSON.parse(sessionStorage.getItem(CACHE) || 'null');
      if (cached && Date.now() - cached.at < 10 * 60 * 1000) return Promise.resolve(cached.data);
    } catch (_) {}
    return fetch(API, { headers: { 'Accept': 'application/vnd.github+json' } })
      .then(function (r) {
        if (!r.ok) throw new Error('Release API ' + r.status);
        return r.json();
      })
      .then(function (j) {
        sessionStorage.setItem(CACHE, JSON.stringify({ data: j, at: Date.now() }));
        return j;
      });
  }

  function openGame(ev) {
    if (ev) ev.preventDefault();
    OPEN.classList.add('is-open');
    STATUS.textContent = 'Resolving latest release…';
    getRelease()
      .then(function (release) {
        // Use commit SHA for jsDelivr (immutable, sync-immediate)
        var sha = release.target_commitish;
        var tag = release.tag_name;
        var url = 'https://cdn.jsdelivr.net/gh/' + REPO + '@' + sha + '/wasm/index.html';
        FRAME.src = url;
        STATUS.textContent = 'Playing release ' + tag + ' (' + sha.substring(0, 7) + ')';
      })
      .catch(function (err) {
        STATUS.textContent = 'Could not resolve latest release: ' + err.message + ' — falling back to main.';
        FRAME.src = 'https://cdn.jsdelivr.net/gh/' + REPO + '@main/wasm/index.html';
      });
  }

  BTN.addEventListener('click', openGame);
})();
</script>

## Features

- Classic Tetris gameplay mechanics.
- Intuitive controls for moving, rotating, and dropping tetrominos.
- Scoring system: earn points by clearing lines and completing levels.
- Display of the next tetromino that will appear.
- Simple and clean user interface.

## Requirements

- C++ compiler
- SDL2 library
- SDL2_ttf library (for rendering text)
- SDL2_mixer library (for sound effects)

## How to Play

1. **Compile the Game:**

```sh
make all
```

2. **Run the Game:**

```sh
./bin/tetris
```

3. **Controls:**
    - **Left Arrow:** Move tetromino left
    - **Right Arrow:** Move tetromino right
    - **Down Arrow:** Soft drop tetromino
    - **Up Arrow or Space:** Rotate tetromino
    - **P:** Pause the game
    - **Esc:** Quit the game

4. **Gameplay:**
    - Tetrominos will fall from the top of the screen. Move and rotate them to fit into the empty spaces.
    - Complete lines by filling all cells in a row. Cleared lines will give you points and prevent the stack from reaching the top.
    - The game speeds up as you clear more lines and progress to higher levels.

## Developer

| <img src="https://github.com/Calebe94.png" width="200px">        |
|:----------------------------------------------------------------:|
| [Edimar Calebe Castanho (Calebe94)](https://github.com/Calebe94) |

# License

This project is licensed under the [GNU General Public License v3.0 or later](https://www.gnu.org/licenses/gpl-3.0.en.html).
