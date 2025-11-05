# CacheReach
Usage:
CacheReach [--help] <filename> [-i <indexfile>] [-l <layout>] [-q <queryfilename>] [-b <indexfile>]
Description:
	 --help 		  print the help message
	 -i <indexfile> 	  index construction and output to specified file
	 -l <layout> 		  set the index layout scheme (0=In-cache, 1=Out-of-cache), default is 1
	 -q <queryfilename> 	 set the query file
Note: Kp and Kt parameters are hardcoded in Graph.h and cannot be set via command line.
      To change Kp or Kt, modify the constants in Graph.h and recompile the program.
