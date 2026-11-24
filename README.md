# Mexico City Metro | Graph Theory and Dijkstra's Algorithm

### Public Transportation Network Modeling, Graph Analysis, and Shortest-Path Optimization with Python

![Mexico City Metro Network](https://mapamexicodf360.com.mx/carte/image/es/mapa-metro-mexico.png)

*Figure: Mexico City Metro network map. Image source: [Mapa México DF 360](https://mapamexicodf360.com.mx/). External reference image.*

**Project Type:** Applied Graph Theory and Transportation Network Analysis  
**Field:** Computer Science | Discrete Mathematics | Graph Theory | Urban Mobility  
**Programming Language:** Python  
**Environment:** Google Colab | Jupyter Notebook  
**Author:** Data Engineer Luis Barahona

---

## 1. Project Overview

This project explores the computational modeling of the Mexico City Metro transportation network using Python and graph theory.

The main objective is to represent Metro stations as vertices and their connections as weighted edges, allowing the network to be studied through mathematical and computational methods.

The notebook includes exercises involving:

- Graph construction.
- Metro station connectivity.
- Weighted transportation networks.
- Vertex degree analysis.
- Eulerian path and circuit conditions.
- Directed and undirected graphs.
- Numerical graph representations.
- Dijkstra's shortest-path algorithm.
- Route visualization.

Through these experiments, the project demonstrates how discrete mathematics and graph algorithms can be applied to transportation network analysis.

The notebook represents an educational computational model rather than an official transportation routing service.

---

## 2. Project Objectives

The main objectives are to:

1. Represent the 12 Mexico City Metro lines using graph structures.
2. Model Metro stations as nodes and connections as edges.
3. Associate numerical weights with station connections.
4. Visualize transportation networks using NetworkX.
5. Calculate vertex degrees.
6. Explore Eulerian path and circuit conditions.
7. Construct experimental graphs with 195 numbered vertices.
8. Implement Dijkstra's algorithm for shortest-path calculations.
9. Allow users to select an origin and destination station.
10. Display the resulting route and calculated distance.
11. Explore the practical applications of graph theory in urban transportation systems.

---

## 3. Graph Theory Fundamentals

Graph theory studies mathematical structures formed by vertices and edges.

In transportation networks, graphs can represent relationships between stations, routes, intersections, and transportation infrastructure.

### 3.1 Vertices

Vertices represent individual stations.

Examples include:

- Pantitlán
- Hidalgo
- Tacubaya
- Bellas Artes
- Pino Suárez
- La Raza

### 3.2 Edges

Edges represent connections between stations.

For example:

```python
("Observatorio", "Tacubaya", 1262)
```

This tuple represents:

- Origin station: Observatorio
- Destination station: Tacubaya
- Edge weight: 1,262

In the weighted-distance sections of the notebook, these values are expressed in meters.

### 3.3 Undirected Graphs

The Metro network is primarily represented using:

```python
metro_cdmx = nx.Graph()
```

An undirected graph represents connections without imposing a specific direction of travel.

### 3.4 Directed Graphs

The notebook also explores directed graphs using:

```python
E = nx.DiGraph()
```

Directed graphs distinguish connections according to their direction.

These experimental directed graphs are used to illustrate graph traversal concepts rather than actual Metro operating directions.

### 3.5 Weighted Graphs

A weighted graph assigns numerical values to its edges.

The notebook uses weights representing station-to-station distances in the main routing experiments.

These weights allow algorithms to compare alternative paths according to their accumulated distance.

---

## 4. Modeling the Mexico City Metro

The notebook defines twelve Metro lines:

| Line | Graph Representation |
|:---|:---|
| Line 1 | Red |
| Line 2 | Blue |
| Line 3 | Olive |
| Line 4 | Light green |
| Line 5 | Yellow |
| Line 6 | Red |
| Line 7 | Orange |
| Line 8 | Green |
| Line 9 | Brown |
| Line A | Purple |
| Line B | Green |
| Line 12 | Gold |

These colors are used to distinguish lines in the graphical representation.

### Graph Construction

NetworkX is used to build the graph:

```python
import networkx as nx
import matplotlib.pyplot as plt

metro_cdmx = nx.Graph()
```

The graph is populated with station connections:

```python
for station1, station2, weight in connections:
    metro_cdmx.add_edge(
        station1,
        station2,
        weight=weight
    )
```

The resulting structure allows stations and weighted connections to be analyzed computationally.

### Network Visualization

The notebook uses NetworkX and Matplotlib to display stations and connections.

A force-directed layout is generated using:

```python
pos = nx.spring_layout(metro_cdmx)
```

This layout provides an abstract visualization of connectivity.

It should not be interpreted as a geographically accurate Metro map.

---

## 5. Experimental Network Structure

One of the saved executions reports:

| Metric | Value |
|:---|---:|
| Stations (vertices) | 163 |
| Connections (edges) | 182 |

These values correspond to one constructed graph in the notebook.

Other sections use different graph configurations, including numbered graphs and reduced station subsets.

Consequently, these metrics should not be interpreted as an official inventory of the Mexico City Metro network.

---

## 6. Vertex Degree Analysis

The degree of a vertex represents the number of edges incident to that vertex.

In a transportation graph, the degree indicates how many modeled connections a station has.

The notebook calculates vertex degrees using:

```python
node_degrees = dict(metro_cdmx.degree())
```

It also identifies vertices with odd degree:

```python
odd_degree_nodes = [
    node
    for node, degree in metro_cdmx.degree()
    if degree % 2 != 0
]
```

### Practical Interpretation

Vertex-degree analysis can help identify:

- Terminal stations.
- Stations with multiple connections.
- Network branching structures.
- Mathematical conditions relevant to graph traversal.

The number of connections in the model does not necessarily represent the number of physical passenger transfer options.

---

## 7. Eulerian Paths and Circuits

The notebook introduces Eulerian graph theory.

An Eulerian path traverses every edge exactly once.

An Eulerian circuit traverses every edge exactly once and returns to its starting vertex.

### Eulerian Conditions

For a connected undirected graph:

| Odd-Degree Vertices | Mathematical Result |
|:---|:---|
| 0 | Eulerian circuit exists |
| 2 | Eulerian path exists |
| More than 2 | No Eulerian path exists |

These conditions assume that all vertices with nonzero degree belong to a single connected component.

### Application to the Metro Model

The notebook evaluates station degrees and identifies whether the modeled graph satisfies Eulerian conditions.

The analysis discusses how adding connections could alter vertex degrees and make Eulerian traversals possible.

However, the notebook does not implement a verified minimum-cost network augmentation algorithm.

### Graph Traversal vs. Passenger Routing

Eulerian paths and Dijkstra's algorithm solve different problems.

**Eulerian path:**

Attempts to traverse every edge exactly once.

**Dijkstra's algorithm:**

Identifies a minimum-weight path between a selected origin and destination.

Both methods are relevant to graph theory, but they serve different computational objectives.

---

## 8. Experimental Graphs with 195 Vertices

The notebook includes numerical graph representations consisting of 195 vertices.

The vertices are labeled:

```text
1, 2, 3, ..., 195
```

These experiments explore:

- Sequential connections.
- Additional graph edges.
- Directed connections.
- Undirected connections.
- Vertex degrees.
- Edge enumeration.
- Graph visualization.

### Saved Numerical Results

The notebook includes an experimental graph containing 212 edges.

It also constructs a separate sequence of 194 edges connecting consecutive numbered vertices.

These exercises illustrate graph structures and traversal concepts.

The numbered graphs are not established as exact reproductions of the physical Metro network.

---

## 9. Dijkstra's Shortest-Path Algorithm

Dijkstra's algorithm identifies shortest paths in graphs with nonnegative edge weights.

The algorithm maintains the shortest currently known distance from an origin to each reachable vertex.

### Main Procedure

1. Select the origin station.
2. Assign the origin a distance of zero.
3. Assign infinity to the remaining stations.
4. Select the unvisited station with the smallest tentative distance.
5. Update the distances of its neighboring stations.
6. Mark the selected station as visited.
7. Repeat until the required distances are determined.
8. Reconstruct the shortest path using predecessor information.

### Mathematical Principle

For a current vertex u and adjacent vertex v:

```text
Alternative Distance =
Distance(u) + Weight(u, v)
```

If the alternative distance is smaller than the existing distance to v, the algorithm updates the value.

### Python Implementation

The notebook implements the algorithm using dictionaries containing:

- Tentative distances.
- Visited vertices.
- Predecessor vertices.

Its central distance update follows this structure:

```python
new_distance = (
    distances[current_node]
    + metro_cdmx[current_node][neighbor]["weight"]
)

if new_distance < distances[neighbor]:
    distances[neighbor] = new_distance
    predecessors[neighbor] = current_node
```

This operation progressively updates the shortest known distances.

---

## 10. Interactive Station Selection

The notebook includes an interactive exercise in which users select stations using numerical identifiers.

### Procedure

1. Display the available station list.
2. Enter the number of the origin station.
3. Enter the number of the destination station.
4. Execute the shortest-path calculation.
5. Display the calculated route.
6. Display the total modeled distance.

Example:

```text
Select origin station: 89
Select destination station: 5
```

The station identifiers are mapped to names using the notebook's internal station list.

---

## 11. Experimental Shortest-Path Result

One saved execution demonstrates a shortest-path calculation between:

**Origin:** Ecatepec

**Destination:** Aragón

### Calculated Distance

**9,570 meters (9.57 km)**

### Calculated Route

```text
Ecatepec
   |
Múzquiz
   |
Río de los Remedios
   |
Impulsora
   |
Nezahualcóyotl
   |
Villa de Aragón
   |
Bosque de Aragón
   |
Deportivo Oceanía
   |
Oceanía
   |
Aragón
```

This result is generated from the weights and connections defined in the corresponding notebook experiment.

It is not a real-time passenger itinerary or an official estimate of travel distance or journey duration.

### Interpretation

The example demonstrates that graph algorithms can be used to:

- Identify connected stations.
- Calculate cumulative edge weights.
- Compare possible transportation paths.
- Reconstruct a shortest route.
- Display the sequence of visited stations.

---

## 12. Shortest-Path Visualization

The notebook highlights the calculated route within the graph.

### Visualization Procedure

The full network is drawn using gray edges.

The shortest path is highlighted using:

- Red edges.
- Red nodes.
- A title identifying the origin and destination.

Example:

```python
path_edges = list(
    zip(shortest_path, shortest_path[1:])
)

nx.draw_networkx_edges(
    metro_cdmx,
    pos,
    edgelist=path_edges,
    edge_color="red",
    width=2
)

nx.draw_networkx_nodes(
    metro_cdmx,
    pos,
    nodelist=shortest_path,
    node_color="red",
    node_size=100
)
```

This visualization helps demonstrate how the selected route is embedded within the transportation graph.

---

## 13. Technologies Used

| Technology | Purpose |
|:---|:---|
| Python | Programming language |
| NetworkX | Graph construction and graph analysis |
| Matplotlib | Network and route visualization |
| Pandas | Structured station data and algorithm tables |
| Jupyter Notebook | Interactive computational environment |
| Google Colab | Cloud notebook execution |

---

## 14. How to Run

### Option 1 — Google Colab

[Open the Mexico City Metro Notebook](https://colab.research.google.com/drive/1ezZwlAPUcfNZ5RczY56-5jfWodP-3gma)

### Execution Instructions

1. Open the notebook in Google Colab.
2. Import the required Python libraries.
3. Execute the station and graph construction cells.
4. Generate the Metro network visualizations.
5. Review the vertex-degree analysis.
6. Explore the Eulerian path exercises.
7. Execute the weighted network construction.
8. Select an origin and destination station.
9. Run Dijkstra's shortest-path implementation.
10. Review the calculated route and distance.
11. Generate the highlighted route visualization.

### Option 2 — Local Jupyter Notebook

Install the dependencies:

```bash
pip install networkx matplotlib pandas notebook
```

Launch Jupyter Notebook:

```bash
jupyter notebook
```

Open the notebook and execute the cells in their intended order.

### Important Execution Note

Some cells redefine the graph variable `metro_cdmx` and the `connections` list.

Different sections therefore operate on different network configurations.

For reliable execution, the variables should be managed carefully, and the correct graph should be initialized before each experiment.

---

## 15. Practical Applications

### Public Transportation

- Transportation network representation.
- Station connectivity analysis.
- Shortest-route calculations.
- Transit network research.
- Route planning prototypes.

### Computer Science

- Graph algorithms.
- Data structures.
- Algorithm design.
- Network traversal.
- Computational optimization.

### Data Science

- Graph-based data analysis.
- Network visualization.
- Structured relationship modeling.
- Transportation analytics.

### Urban Mobility

- Connectivity studies.
- Transportation network modeling.
- Research on accessible routes.
- Exploratory infrastructure analysis.

---

## 16. Limitations

This notebook is an educational graph theory experiment.

Important limitations include:

### Different Graph Configurations

The notebook contains multiple graph representations, and their station and edge counts are not identical.

### Partial Route Network

The final interactive shortest-path experiment uses a reduced set of stations and connections.

### Distance Validation

The notebook contains manually defined edge weights.

Their accuracy and consistency should be verified against authoritative transportation data before operational use.

### No Travel-Time Modeling

The algorithm minimizes the sum of edge weights, not actual passenger travel time.

### No Transfer Penalties

The model does not include realistic transfer walking times, waiting times, or transfer penalties.

### No Real-Time Service Information

Closures, service interruptions, operating conditions, and train schedules are not included.

### Abstract Visualization

The NetworkX spring layout does not represent exact geographical station coordinates.

### Eulerian Analysis

The notebook explores Eulerian conditions but does not implement a complete network augmentation optimization procedure.

Therefore, the results should not be used as official travel guidance.

---

## 17. Future Improvements

Potential extensions include:

- Consolidating the entire Metro network into one validated graph.
- Standardizing station names and interchange identifiers.
- Incorporating authoritative station and distance datasets.
- Adding explicit transfer edges.
- Modeling travel times instead of only distances.
- Implementing Dijkstra using NetworkX built-in functions.
- Comparing Dijkstra with A*.
- Adding route connectivity validation.
- Incorporating station coordinates.
- Creating geographically accurate interactive maps.
- Developing a web-based Metro route planner.
- Integrating GTFS transportation data where available.
- Including accessibility and service-status constraints.
- Implementing automated tests for graph consistency.

---

## 18. Project Resources

### Main Google Colab Notebook

[Mexico City Metro — Graph Theory and Dijkstra](https://colab.research.google.com/drive/1ezZwlAPUcfNZ5RczY56-5jfWodP-3gma)

### Additional Station Distance Notebook

[Metro Stations and Distances — Google Colab](https://colab.research.google.com/drive/1p56l-ydatWn78QuA4AIEhFGMK6DQS8uK?usp=sharing)

This supplementary notebook is referenced in the main project.

### NetworkX Documentation

[NetworkX — Graph Algorithms](https://networkx.org/documentation/stable/)

### Mexico City Metro Network Map

[Metro Network Reference Image](https://mapamexicodf360.com.mx/carte/image/es/mapa-metro-mexico.png)

The map is an external visual reference and is credited to its original website.

### Mexico City Metro

[STC Metro — Official Website](https://www.metro.cdmx.gob.mx/)

This independent academic project is not an official Metro routing application.

---

## 19. Conclusion

This project demonstrates how graph theory and shortest-path algorithms can be applied to the computational representation of an urban transportation network.

Using Python, NetworkX, Matplotlib, and Pandas, the notebook explores network connectivity, vertex degrees, Eulerian graph properties, and route calculations.

The Dijkstra experiment demonstrates a calculated distance of 9,570 meters between Ecatepec and Aragón within the modeled network.

The project provides a practical foundation for studying graph algorithms, transportation network analysis, discrete mathematics, and future route-planning applications.

Additional data validation, network consolidation, and travel-time modeling would be required before developing a reliable operational transportation system.

---

## Author

**Data Engineer Luis Barahona**

Mexican Data Engineer and 2026 graduate of Universidad del Caribe, interested in Data Engineering, Data Science, Artificial Intelligence, Graph Theory, Algorithm Design, and Smart Mobility Technologies.

---

## Contact

| Platform | Contact |
|:---|:---|
| Email | [190300395@ucaribe.edu.mx](mailto:190300395@ucaribe.edu.mx) |
| GitHub | [github.com/LuisBarahonaMX](https://github.com/LuisBarahonaMX) |
| LinkedIn | [linkedin.com/in/luis-barahona-mx](https://www.linkedin.com/in/luis-barahona-mx/) |
| Instagram | [@luisbarahonamx](https://www.instagram.com/luisbarahonamx/) |
| X | [@luisbarahonaMX](https://x.com/luisbarahonaMX) |
| Website | [SIKO AI Platform](https://sikoai.web.app/) |
