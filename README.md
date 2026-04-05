# CacheReach

An efficient reachability query tool designed for Directed Acyclic Graphs (DAGs), featuring cache-optimized index layouts.

## Compilation
Build the project using the provided `Makefile`:
```bash
make
```

## Usage
Run the executable using the following syntax:
```bash
./CacheReach [--help] <filename> [-i <indexfile>] [-l <layout>] [-q <queryfilename>] [-b <indexfile>]

Argument,Description
--help,Display this help message and exit.
<filename>,Required. The path to the input graph file.
-i <indexfile>,Construct the index and save it to the specified file.
-l <layout>,Set the index layout scheme: 0 (In-cache) or 1 (Out-of-cache). Default is 1.
-q <queryfile>,Set the query file for reachability testing.
-b <indexfile>,Load a pre-built index file.
