# 🧭 Pathfinding Visualizer

An interactive browser-based tool to **visualize how pathfinding algorithms explore a grid** — step by step, in real time. Draw walls, place your start and end nodes, pick an algorithm, and watch it work.

🔗 **Live Demo:** [https://practical-benz-8a0ad1.netlify.app](https://practical-benz-8a0ad1.netlify.app)

![Pathfinding Visualizer Screenshot](https://user-images.githubusercontent.com/60571252/82052701-b52e4700-96d9-11ea-8387-e84816091b62.png)

---

## ✨ Features

- **Multiple algorithms** — Dijkstra's, A\*, BFS, and DFS
- **Heuristic selection** — Choose the heuristic used by informed search algorithms (A\*)
- **Interactive grid** — Click and drag to draw walls (obstacles)
- **Random maze** — Generate a random obstacle layout with one click
- **Smooth animations** — Watch the traversal unfold cell by cell, followed by the shortest path highlight
- **Reset & repeat** — Clear the grid and try a different setup instantly

---

## 🧠 Algorithms

| Algorithm | Type | Guarantees Shortest Path |
|---|---|---|
| **Dijkstra's** | Uninformed |  Yes |
| **A\*** | Informed (heuristic) |  Yes |
| **BFS** (Breadth-First Search) | Uninformed |  Yes |
| **DFS** (Depth-First Search) | Uninformed |  No |

> Informed algorithms use a heuristic (e.g. Manhattan distance) to prioritize which nodes to explore, making them faster in practice. DFS is included for comparison — it finds *a* path, not necessarily the *shortest* one.

---

## 🚀 Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) (v14 or above)
- npm (comes with Node.js)

### Installation

```bash
# Clone the repository
git clone https://github.com/Harsh-trains/PathfindingVisualizer.git

# Navigate into the project
cd PathfindingVisualizer

# Install dependencies
npm install

# Start the development server
npm start
```

Open [http://localhost:3000](http://localhost:3000) in your browser. The page reloads automatically on edits.

### Build for Production

```bash
npm run build
```

---

## 🕹️ How to Use

1. **Select an algorithm** from the dropdown in the navbar
2. **Select a heuristic** (relevant for A\*)
3. **Draw walls** — click and drag on any cell to add obstacles
4. *(Optional)* Click **Random Grid** to generate a random maze
5. Click **Visualize** to run the algorithm
6. Watch the **traversal animation**, then see the **shortest path** highlighted
7. Click **Reset** and repeat with a different setup

---

## 🗂️ Project Structure

```
PathfindingVisualizer/
├── public/
│   └── index.html
├── src/
│   ├── App.js
│   ├── PathfindingVisualizer/
│   │   ├── PathfindingVisualizer.jsx   # Main orchestrator component
│   │   ├── PathfindingVisualizer.css
│   │   └── Node/
│   │       ├── Node.jsx                # Individual grid cell
│   │       └── Node.css
│   └── algorithms/
│       ├── dijkstra.js
│       ├── astar.js
│       ├── bfs.js
│       └── dfs.js
├── package.json
└── README.md
```

---

## 🏗️ Architecture Overview

The app is built with **React** (Create React App). The core design separates algorithm logic from rendering:

- **`PathfindingVisualizer`** — The stateful orchestrator. Holds the grid (a 2D array of node objects), handles mouse events for wall-drawing, calls the selected algorithm, and drives the animation via staggered `setTimeout` calls.
- **`Node`** — A presentational component for each cell. Receives props (`isWall`, `isVisited`, `isShortestPath`, etc.) and applies the corresponding CSS class.
- **`/algorithms`** — Pure functions that take the grid + start/finish nodes and return `visitedNodesInOrder[]`. They have no side effects and are completely independent of the UI.

Animation is handled by **direct DOM class mutation** (rather than React state updates) to avoid re-rendering hundreds of cells on every frame — a deliberate performance trade-off.

---

## 🛠️ Tech Stack

- **ReactJS** — UI and component logic
- **HTML / CSS** — Layout and animation styling
- **JavaScript (ES6+)** — Algorithm implementations

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

## 🙏 Acknowledgements

Inspired by the pathfinding visualizer tutorial by [Clément Mihailescu](https://github.com/clementmihailescu/Pathfinding-Visualizer).
