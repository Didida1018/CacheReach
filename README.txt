To compile:
make

To run:
./CacheReach --help

Usage:
CacheReach [--help] <filename> [-i <indexfile>] [-l <layout>] [-q <queryfilename>] [-b <indexfile>]
Description:
	--help 		  print the help message
	-i <indexfile> 	  index construction and output to specified file
	-l <layout> 		  set the index layout scheme (0=In-cache, 1=Out-of-cache), default is 1
	-q <queryfilename> 	 set the query file
Note: Kp and Kt parameters are hardcoded in Graph.h and cannot be set via command line.
    To change Kp or Kt, modify the constants in Graph.h and recompile the program.

Graph File Format:
The graph must be a DAG.
The first line must be "graph_for_greach".
The second line contains V, the number of vertices of the graph.
Then V lines follow.Each line describes edge from a certain vertex, u, to its successors, v_i, in the following format.
u: v_1, v_2, v_3....#

Query File Format:
Each line contains a query
u,v,result
Where result = 0 indicates v is unreachable from u
Where result = 1 indicates v is reachable from u

Sample usage:
./CacheReach "./example/agrocyc.gra"  -i "./example/agrocyc.index" -q "./example/agrocyc.txt"
