# Overview

The Multi-Layer Canopy Model version 1 (MLCMv1) for the Energy Exascale Earth System Model (E3SM)
Land Model (ELM), which is based on [CLM-ml v1](https://github.com/gbonan/CLM-ml_v1)[@bonan2021moving],
resolves the micro-climate created by the vegetation canopies. 
The MLCMv1 has been benchmarked against the CLM-ml v1 for the Ameriflux US-Unversity of Michigan
Biological Station site.

The MLCMv1 uses [PETSc](https://petsc.org) to provide support for heterogeneous computing architectures.
The performance portability of the model has been studied on NVIDIA and AMD GPUs, and a speedup of
25-50 times has been shown on a GPU relative to a CPU.