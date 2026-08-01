# Sudoku

A fully client-side Sudoku game built as a single HTML file — no frameworks, no build tools, no dependencies. Open it in any modern browser and play.

![License](https://img.shields.io/badge/license-MIT-blue.svg)

## Features

- **4 difficulty levels** — Easy, Medium, Hard and Expert, tuned by the number of given clues (38, 32, 27 and 22 respectively).
- **Unique-solution puzzles** — every puzzle is generated on the fly and verified to have exactly one solution.
- **Classic gameplay tools**:
  - Undo, erase, and pencil-mark (notes) mode.
  - Hints that reveal the correct value of a cell.
  - Mistake tracking — 3 mistakes and the game is over (the solution is revealed).
  - "Check solution" and "reveal solution" options in the menu.
- **Live statistics** — a running timer, mistakes counter and hints counter.
- **Best-time records** — your fastest solve is saved per difficulty in `localStorage`.
- **In-progress save** — your current game is saved automatically and restored when you come back.
- **Keyboard support** — `1–9` to enter digits, arrow keys to move, `N` to toggle notes, `Ctrl+Z` to undo, `Backspace`/`Delete` to erase.
- **Mobile friendly** — responsive layout and a touch-friendly number pad.
- **Dark theme** with a clean, modern UI and clear 3×3 box borders.

## How the puzzles are created

The game generates a Sudoku entirely in your browser, no server required:

1. **Fill the grid** — a complete, valid Sudoku board is generated using a backtracking solver that fills empty cells with shuffled candidate digits.
2. **Dig holes** — starting from the solved board, cells are removed one by one in random order, down to the target clue count for the selected difficulty.
3. **Verify uniqueness** — before a cell is removed, a solver counts the solutions of the resulting grid; a cell is only removed if the puzzle still has exactly one solution. If removing it would create multiple solutions, the digit is put back.

This guarantees every puzzle you play is valid and has a single, well-defined solution.

## Getting started

There is nothing to install or build — just open the file:

```bash
git clone git@github.com:davinux/sudoku.git
cd sudoku
# open index.html in your browser
```

Or serve it locally with any static file server:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

You can also play it directly on [GitHub Pages](https://davinux.github.io/sudoku/) if enabled for the repository.

## How to play

1. Pick a difficulty (Easy / Medium / Hard / Expert).
2. Select any cell, then tap a number on the pad (or press a key) to fill it in.
3. Turn on **Notes** to leave pencil marks for candidates instead of entering a final value.
4. Use **Undo**, **Erase** and **Hint** whenever you get stuck.
5. Complete the grid without making 3 mistakes to win. Beats on each level are saved as your personal best.

## Project structure

```
sudoku/
├── index.html   # the entire game (markup, styles and logic)
└── LICENSE      # MIT License
```

## Technologies

- Plain **HTML5 + CSS3 + JavaScript (ES5+)** — no frameworks, libraries, or external resources.
- **CSS Grid** for the board, number pad and responsive layout.
- **Canvas-free rendering** — the 9×9 board is built and updated with the DOM.
- **localStorage** for best times and in-progress games.

## How it was created

This project started as a single `index.html` file with a working Sudoku solver. The puzzle generator (fill the grid, then dig holes while guaranteeing a unique solution) came next, followed by the interactive board, game state (mistakes, hints, notes, undo), the timer and win conditions. Finally, persistence via `localStorage` was added so a game can be resumed later and personal bests are kept per difficulty.

The whole thing deliberately stays dependency-free and build-less: open the file and it just works, on desktop and mobile alike.

## License

Released under the [MIT License](./LICENSE). Copyright (c) 2026 Davinux.
