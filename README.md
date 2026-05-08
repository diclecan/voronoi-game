# Voronoi Cells

This repository contains a Python implementation for computing Voronoi cells on graphs.

The project is based on the idea of Voronoi diagrams: each point or node is assigned to the closest center. In this implementation, the space is represented as a graph, and distance is measured by shortest paths along the graph edges.

## Project Context

This project was created in the context of a university programming project about Voronoi diagrams and the Voronoi game.

The original task discusses Voronoi diagrams, Delaunay triangulation, efficient computation, visualization, and testing. This repository contains a Python-based implementation focused on graph Voronoi cells.

## Features

- Computes Voronoi cells on graphs
- Supports weighted and unweighted graphs
- Supports directed and undirected graphs
- Supports multigraphs
- Handles unreachable nodes
- Includes unit tests for different graph types

## Repository Structure

```text
.
├── voronoi.py
├── tests/
│   └── test_voronoi.py
├── requirements.txt
├── pyproject.toml
├── .gitignore
└── README.md
```

## Requirements

This project requires Python 3.

Install the dependencies with:

```bash
pip install -r requirements.txt
```

Main dependencies:

```text
networkx
pytest
```

## Usage

Example:

```python
import networkx as nx
from voronoi import voronoi_cells

G = nx.path_graph(6)

center_nodes = {0, 3}

cells = voronoi_cells(G, center_nodes)

print(cells)
```

Example output:

```python
{
    0: {0, 1},
    3: {2, 3, 4, 5}
}
```

Each key represents a center node.  
Each value contains the graph nodes that are closest to that center.

## How It Works

The algorithm uses a multi-source shortest-path approach.

First, several center nodes are selected. Then the shortest path from the nearest center to every reachable node is computed. Each node is assigned to the center from which it can be reached with the smallest distance.

If some nodes are not reachable from any center node, they are stored under the key `"unreachable"`.

## Running Tests

To run the tests, use:

```bash
pytest
```

The tests cover:

- graphs with isolated nodes
- undirected unweighted graphs
- directed unweighted graphs
- weighted graphs
- multigraphs
- multidigraphs
- unreachable nodes

## Example Test Case

```python
import networkx as nx
from voronoi import voronoi_cells

G = nx.cycle_graph(6)

cells = voronoi_cells(G, {0, 3})

expected = {
    0: {0, 1, 5},
    3: {2, 3, 4}
}

assert cells == expected
```

## Possible Future Improvements

- Add a graphical visualization of the Voronoi cells
- Extend the project to geometric Voronoi diagrams in the plane
- Implement the full two-player Voronoi game
- Add an interactive user interface
- Compare the graph-based approach with a Delaunay-triangulation-based approach

## Author

Dicle Can

## License

This project is intended for educational use.
