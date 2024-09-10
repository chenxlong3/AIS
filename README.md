# AIS (Augmenting the Influence of Seeds)
This repo tries to augment the influence diffusion by the seed set by recommending links.

# File Structure
```
.
|-- CMakeLists.txt
|-- README.md
|-- build
|   |-- CMakeCache.txt
|   |-- CMakeFiles
|   |-- IMA_only
|   |-- MCGreedy_only
|   |-- Makefile
|   |-- RW
|   |-- cmake_install.cmake
|   |-- eval_by_mc
|   `-- format_graph
|-- data
|   |-- GRQC
|-- data_process.ipynb
|-- exec_files
|   |-- IMA_only.cpp
|   |-- evaluate.cpp
|   `-- main.cpp
|-- include
|   |-- Algs.h
|   |-- CommonFuncs.h
|   |-- Experiments.h
|   |-- GraphBase.h
|   |-- IOcontroller.h
|   |-- InfGraph.h
|   |-- SFMT
|   |-- Timer.h
|   |-- headers.h
|   `-- serialize.h
`-- scripts
    |-- clear_build.sh
```


# Usage
## Cmake Compile
```
cd ./scripts
./clear_build
```
## Format Graph
In the folder of one dataset, two files should be included - `attr.txt` and `edgelist_ic.txt`.
`attr.txt` gives the number of nodes and edges in the following format.
```
n=5242
m=28980
```

`edgelist_ic.txt` stores the edge list of the graph. An example is shown below.
```
3466	937 0.1
3466	5233    0.1
3466	826 0.1
```

```shell
cd ../build
./format_graph -dataset ../data/GRQC -filename edgelist_ic.txt
```

## Run the algorithm
```shell
./IMA_only -dataset ../data/GRQC -epsilon 0.5 -delta 0.001 -k_edges 50 -rand_seed 0 -num_cand_edges 0 -fast True -probability WC -seed_mode "IM"
```