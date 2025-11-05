
# CacheReach - Usage

## Command Line Usage
CacheReach [--help] <filename> [-i <indexfile>] [-l <layout>] [-q <queryfilename>] [-b <indexfile>]


## Parameters
| Parameter | Description |
|-----------|-------------|
| `--help` | Print the help message |
| `-i <indexfile>` | Index construction and output to specified file |
| `-l <layout>` | Set the index layout scheme (0=In-cache, 1=Out-of-cache), default is 1 |
| `-q <queryfilename>` | Set the query file |

## Note
**Kp and Kt parameters are hardcoded in Graph.h and cannot be set via command line.**  
To change Kp or Kt, modify the constants in `Graph.h` and recompile the program.
