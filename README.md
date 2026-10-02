A New Bus Route, and Where to Put the Stops

Project for Data Structures and Algorithms, by Kimunila Zhakata.

There is no direct bus from Curepipe to Pamplemousses. This project:

1. Models the road network as a weighted graph and finds the fastest route with **Dijkstra's algorithm**.
2. Places **6 bus stops** at junctions to cover as many of the 18 residential areas as possible. An area is covered if a stop is within 9 minutes of it.
3. Compares a **greedy** stop placement against an **exhaustive search** of all 18,564 possible sets of six.

## How to run

**In Google Colab (easiest)**

1. Open `NOTEBOOK_NAME.ipynb` in this repository.
2. Click **Open in Colab**, or go to colab.research.google.com → File → Open notebook → GitHub and paste the repository link.
3. Click **Runtime → Run all**.

No upload is needed. The notebook reads the CSV files directly from this repository.

**On your own computer**

```bash
git clone https://github.com/kimunilaz/Data_Structures-Algorithms_Final_Project.git
cd Data_Structures-Algorithms_Final_Project
pip install pandas matplotlib
jupyter notebook NOTEBOOK_NAME.ipynb
```

When the CSV files are in the same folder, the notebook loads them locally instead of from GitHub.

**Requirements:** Python 3.10 or later, `pandas` and `matplotlib`. Everything else is from the standard library (`heapq`, `itertools`, `math`, `time`, `statistics`, `collections`).

## Files

| File | What it is |
|---|---|
| `NOTEBOOK_NAME.ipynb` | All the code, in order, with a short explanation above each cell |
| `Q2_road_network.csv` | 25 roads with travel times in minutes; every road goes both ways |
| `Q2_residential_areas.csv` | 18 residential areas and the junction each one is at |
| `README.md` | This file |

## What the notebook does, in order

1. **Load the data** from the two CSV files.
2. **Build the graph** as an adjacency list (18 junctions, 25 roads).
3. **Dijkstra's algorithm**: the fastest route from Curepipe to Pamplemousses, and the travel time from every junction to every other junction.
4. **Coverage**: for each junction, the set of areas within 9 minutes.
5. **Greedy stop placement**: add the junction covering the most new areas, six times. Ties go to the name that comes first alphabetically.
6. **Exhaustive search**: try all 18,564 sets of six junctions and keep the best.
7. **Helpers**: a quiet version of greedy for timing, and functions to build any small test network.
8. **Timing and operation counts**: median of 5 runs after warm-up, with operation counts beside the times.
9. **Two instances**: a small network where greedy loses, and one where it matches the best answer.
10. **Growth of exhaustive search**: how the cost grows with a fixed number of stops against a growing number.
11. **Optional extensions**: coverage for 1 to 8 stops, and the fewest-roads route found with BFS.

Each step ends with `assert` checks, so the notebook stops with an error if a result is wrong.

## Results

| | Result |
|---|---|
| Fastest route | Curepipe → Forest Side → Phoenix → Quatre Bornes → Rose Hill → Beau Bassin → Port Louis → Terre Rouge → Pamplemousses (8 roads, 59 minutes) |
| Greedy stops | Quatre Bornes, Arsenal, Curepipe, Ebene, Moka, Pailles: 17 of 18 areas |
| Best possible | 18 of 18 areas, for example Arsenal, Curepipe, Moka, Pailles, Quatre Bornes, Trou aux Biches |
| Gap | 1 area |
| Running time | Greedy 0.033 ms (93 operations), exhaustive search 13.2 ms (18,564 combinations) |

Timings come from Google Colab and will vary slightly between runs. The operation counts will not.

