# A* Pathfinding Visualizer

An interactive grid-based visualizer for the A* search algorithm, built with
plain HTML, CSS, and JavaScript — no frameworks, no build step.

**[→ Live Demo](https://tanushreenegi-dev.github.io/astar-pathfinding-visualizer/)**

<!-- Add a screenshot or GIF here once it's live. A short screen recording of
     the search running on "Slow" speed works great — drag it into this repo
     as demo.gif and reference it below:
![Demo](demo.gif)
-->

## What it does

- Click and drag to draw walls on the grid
- Drag the green (start) and red (end) squares anywhere
- Hit **Run A\*** to watch the algorithm search in real time
- Live counters show the size of the open set (frontier) and closed set
  (visited nodes) as the search progresses
- **Random maze** generates a random wall layout to test against
- Three speed settings, including a slow "study mode" for watching the
  search expand node by node

## How A* works

A* finds the shortest path between two points by repeatedly expanding the
node in its **open set** (the frontier of nodes it hasn't explored yet) with
the lowest score:

```
f(n) = g(n) + h(n)
```

- **g(n)** — the actual cost to reach node `n` from the start
- **h(n)** — a heuristic *estimate* of the remaining cost from `n` to the goal
- **f(n)** — the algorithm's best guess at the total cost of a path through `n`

This implementation uses **Manhattan distance** (`|dr| + |dc|`) as the
heuristic, since movement is restricted to up/down/left/right on a grid.

Unlike breadth-first search, which expands outward in all directions equally,
A* uses the heuristic to bias its search toward the goal — which is why the
blue "open set" cells in the visualizer tend to stretch toward the red end
square instead of flooding the whole grid.

Once the end node is reached, the path is reconstructed by walking backward
through each node's parent pointer, all the way to the start.

## Why I built this

I implemented A* as part of my AI & ML coursework, but writing the algorithm
on paper or in a script doesn't really show *why* it explores the way it
does. Visualizing the open and closed sets as they grow made the
cost-so-far vs. heuristic tradeoff click in a way the math alone didn't —
and it's a much better way to show that understanding to someone else, too.

## Running it locally

No installation needed — it's a single HTML file.

```bash
git clone https://github.com/tanushreenegi-dev/astar-pathfinding-visualizer.git
cd astar-pathfinding-visualizer
open index.html   # or just double-click the file
```

## Possible extensions

- Add Dijkstra's algorithm or plain BFS as a side-by-side comparison
- Add diagonal movement with an adjusted heuristic
- Add a Minimax visualizer for a simple game tree (the natural companion
  to this project from the same coursework)

## License

MIT
