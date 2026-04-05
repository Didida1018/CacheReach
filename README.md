# CacheReach
**CacheReach** is a high-performance reachability query engine designed to break the "performance hard ceiling" in large-scale directed graphs. 

While traditional methods focus on algorithmic complexity, CacheReach addresses the modern hardware bottleneck: **Memory Access Latency**. By shifting the query pipeline from memory-bound to compute-bound, CacheReach achieves **3.17x – 10.82x speedups** over state-of-the-art frameworks.
### Why CacheReach?
*   **Hardware-Conscious Design:** Prioritizes cache residency and instruction-level parallelism (ILP) to overcome the "Memory Wall."
*   **CR-vectors:** A novel "Stage 0" pre-filter that resolves the majority of negative queries using single-cycle bitwise logic.
*   **Optimized Pipeline:** Jointly optimizes stage ordering and data layout to shield downstream stages from expensive memory accesses.

## Dataset
We provide various graph datasets and their corresponding query pairs sourced from the SNAP repository for evaluation and testing.

## Usage
Run the executable using the following syntax:
```bash
./CacheReach [--help] <filename> [-i <indexfile>] [-l <layout>] [-q <queryfilename>] [-b <indexfile>]
```
Command Line Arguments
| Argument | Description |
| :--- | :--- |
| `--help` | Display this help message and exit. |
| `<filename>` | **Required**. The path to the input graph file. |
| `-i <indexfile>` | Construct the index and save it to the specified file. |
| `-l <layout>` | Set the index layout scheme: `0` (In-cache) or `1` (Out-of-cache). Default is `1`. |
| `-q <queryfile>` | Set the query file for reachability testing. |
| `-b <indexfile>` | Load a pre-built index file. |

## File Formats
### 1.Graph File Format (`.gra`)
The input graph must be a **Directed Acyclic Graph (DAG)**. The file structure is defined as follows:
1.  **Header:** The first line must be exactly `graph_for_greach`.
2.  **Vertex Count:** The second line contains an integer $V$, representing the total number of vertices.
3.  **Adjacency List:** $V$ lines follow. Each line describes the edges from a specific vertex $u$ to its successors $v_i$ in the following format:
    `u: v_1, v_2, v_3...`
    
**Example:**
```text
graph_for_greach
3
0: 1, 2 #
1: 2 #
2: #
```
### 2.Query File Format
This format is consistent across many reachability algorithms. Each line contains three numbers: `u`, `v`, and `Reach`. The `Reach` flag is used to verify the correctness of the query results.
1. **u**: Source vertex.
2. **v**: Target vertex.
3. **Reach**: Verification flag.
    `1`: $v$ is reachable from $u$.
    `0`: $v$ is **unreachable** from $u$.
  
**Example:**
```text
0 2 1
2 0 0
```

## Compilation and Run
Build the project using the provided `Makefile`:
```bash
make
```
Sample usage:
```bash
./CacheReach ./example/agrocyc.gra  -i ./example/agrocyc.index -q ./example/agrocyc.txt
```
