# 🎮 Tetris 🚀

This project is a classic implementation of the popular game Tetris, written in C++ using the SDL2 library. Tetris is a puzzle game where players manipulate falling blocks called "tetrominos" to create complete lines on the game board. When a line is completed, it clears from the board, and the player earns points. The game ends when the stack of tetrominos reaches the top of the game board.

The main objective of this project is to provide a fun and interactive way to play the timeless game of Tetris, while also serving as a practical example of using the SDL2 library for game development in C++.

<img src="./assets/screenshots/game.png" width="400px">

<div align="center">

## 🎮 [Try it online! 🌐](https://calebe94.github.io/tetris/#play)

<a href="#play" id="play-button" onclick="document.getElementById('play-overlay').style.display='flex'; return false;" style="display:inline-block;padding:16px 32px;background:#e94560;color:#fff;text-decoration:none;border-radius:8px;font-weight:bold;font-size:1.2em;box-shadow:0 4px 12px rgba(233,69,96,0.4);">🎮 JOGAR TETRIS AGORA 🎮</a>

<div id="play-overlay" style="display:none;position:fixed;top:0;left:0;width:100%;height:100%;background:rgba(0,0,0,0.95);z-index:9999;align-items:center;justify-content:center;flex-direction:column;padding:20px;box-sizing:border-box;">
  <div style="width:100%;max-width:600px;display:flex;justify-content:space-between;align-items:center;margin-bottom:12px;">
    <h2 style="color:#fff;margin:0;">🎮 Tetris</h2>
    <button onclick="document.getElementById('play-overlay').style.display='none'" style="background:#e94560;color:#fff;border:none;padding:8px 16px;border-radius:4px;cursor:pointer;font-size:1em;">✕ Fechar</button>
  </div>
  <iframe src="https://cdn.jsdelivr.net/gh/calebe94/tetris@gh-pages/wasm/index.html" style="width:100%;max-width:600px;height:80vh;max-height:800px;border:1px solid #333;border-radius:8px;background:#000;" allow="autoplay" allowfullscreen></iframe>
  <p style="color:#888;font-size:0.85em;margin-top:12px;">Controles: ← → mover | ↑ / Space rotacionar | ↓ descer | P pausar</p>
</div>

</div>

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
