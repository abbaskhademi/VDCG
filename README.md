# VCG

This repository contains the official Julia implementation for the paper: **"Voronoi Conditional Gradient Method for Constrained Nonconvex Optimization"**.

## Abstract

While the Conditional Gradient (CG) method is a cornerstone for constrained optimization, its application to non-convex problems is often hindered by convergence to poor local minima. To address this, we introduce the Voronoi Conditional Gradient (VCG), a novel framework that systematically explores the solution space through a geometric strategy. VDCG iteratively constructs a Voronoi partition of the feasible set, using previously identified stationary points as centers. By launching new CG instances from within these Voronoi cells, the method effectively escapes the basins of attraction of known solutions and diversifies the search.

## Method Overview

The VDCG algorithm enhances the standard Conditional Gradient (CG) method with a structured exploration phase to better navigate non-convex landscapes. The core idea is to:

1.  **Find a Stationary Point:** Run a standard CG algorithm to find an initial stationary point.
2.  **Decompose the Space:** Use all unique stationary points found so far as centers for a Voronoi decomposition of the feasible set.
3.  **Explore Cells:** For each Voronoi cell, solve a small auxiliary problem to find a new starting point deep within that cell's interior.
4.  **Launch New Searches:** Run the CG algorithm from these new starting points to discover potentially better stationary points.
5.  **Iterate:** Add any new, unique points to the set of centers and repeat the decomposition and exploration process.

This process allows VDCG to systematically explore the feasible region, escaping the attraction of previously discovered local minima.

## Repository Structure

This repository contains the Jupyter Notebooks to reproduce the experiments from our paper.

* `StQO_VDCG.ipynb`: Implementation and numerical experiments for the **Standard Quadratic Programming (StQP)** problem.
* `LSSR_VDCG.ipynb`: Implementation and numerical experiments for the **Least Squares Sigmoid Regression (LSSR)** problem.

## Requirements

The code is written in the Julia programming language. To run the experiments, you will need a working Julia installation and a Jupyter environment with an IJulia kernel.

The following Julia packages are required:
* `JuMP`
* `HiGHS`
* `Zygote`
* `LIBSVMdata`
* `LinearAlgebra`
* `Statistics`
* `SparseArrays`

You can install them via the Julia package manager:
```julia
using Pkg
Pkg.add(["JuMP", "HiGHS", "Zygote", "LIBSVMdata"])
```

## Usage

1.  Clone this repository to your local machine:
    ```sh
    git clone [https://github.com/abbaskhademi/VDCG.git](https://github.com/abbaskhademi/VDCG.git)
    cd VDCG
    ```
2.  Start a Jupyter Notebook or JupyterLab session.
3.  Open either `StQO_VDCG.ipynb` or `LSSR_VDCG.ipynb`.
4.  Execute the cells in the notebook to run the experiments and see the results.

As of September 2025, the code has been tested with recent versions of Julia and the required packages.

## Citation

If you find this work useful in your research, please consider citing our paper.

```bibtex
@article{khademi2026vdcg,
  author    = {Khademi, Abbas},
  title     = {Voronoi Conditional Gradient Method for Constrained Nonconvex Optimization},
  journal   = {Preparation for Submission},
  year      = {2026}
}
```

## References

The adaptive stepsize strategy used in our implementation is based on the work:

> A. Khademi, A. Silveti-Falls, "Adaptive conditional gradient descent" (2025).
