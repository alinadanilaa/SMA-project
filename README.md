# Spotify Artist Network Analysis

This project explores community structures, centrality, genre clustering, and more within a Spotify artist collaboration network. The analysis leverages the Louvain algorithm for community detection and provides benchmarking comparisons between a custom implementation and the standard library-based method.

## Notebooks

### `Spotify_Clean_Run.ipynb`
This notebook performs the complete end-to-end analysis from scratch, including:

- Data import and graph construction  
- Centrality analysis (Degree, Betweenness, PageRank)  
- Louvain community detection  
- Benchmarking of Louvain implementations across varying graph sizes

To run this notebook from scratch, you must ensure that `dataset.csv` is available in the working directory. The benchmarking section runs the Louvain method on subgraphs of sizes ranging from 10 to 1000 nodes, which can take up to **one hour** to complete.

This process will generate:

- `custom_louvain_top{size}.pkl`: Serialized results from the custom Louvain algorithm for reuse  
- `louvain_benchmark_results.csv`: Benchmark results comparing custom vs. standard Louvain  
- `louvain_comparison.png`: A visual plot of the benchmarking results

### `Spotify2.ipynb`
This notebook is optimized for faster execution by reusing precomputed results. It expects the following files to already be present in the same directory:

- `custom_louvain_top1000.pkl`  
- `louvain_benchmark_results.csv`  
- `louvain_comparison.png`

Running `Spotify_preRun_Louvain.ipynb` will take only a few minutes, making it ideal for reviewing results without the extended computation time.

## Requirements

Ensure the following Python libraries are installed:

- `networkx`  
- `pandas`  
- `matplotlib`  
- `community` (for the standard Louvain implementation)  
- `pickle`

You can install any missing dependencies using pip:

`pip install networkx pandas matplotlib python-louvain`


## Usage:

To generate everything from scratch, either open `Spotify_Clean_Run.ipynb` in Google Colab, making sure to upload dataset.csv first, or run:

`jupyter notebook Spotify_Clean_Run.ipynb`

To skip benchmarking and load precomputed results instead, open `Spotify_preRun_Louvain.ipynb` in Google Colab, making sure to upload all files mentioned above, or run:

`jupyter notebook Spotify_preRun_Louvain.ipynb`
