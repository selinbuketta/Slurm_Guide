# Slurm_Guide

This repository provides a **complete, practical, and professional guide to SLURM**, aimed at users running **data-intensive and GPU-accelerated workloads** on shared HPC systems.  
The guide focuses on **concepts, best practices, and real-world workflows**, especially for machine learning and research environments.

---

## Table of Contents

- [SLURM Jobs](SLURM_JOBS.MD)
- [SLURM Environment Creation](SLURM_ENV_CREATION.MD)
- [SLURM Data Transfer](SLURM_DATA_TRANSFER.MD)
- [SLURM Debugging Jobs](SLURM_DEBUGGING_JOBS.MD)

## What is SLURM?

**SLURM (Simple Linux Utility for Resource Management)** is an open-source workload manager used on **high-performance computing (HPC) clusters**. It is responsible for:

- Scheduling jobs submitted by multiple users
- Allocating compute resources (CPU, GPU, memory, time)
- Enforcing fair usage and isolation
- Tracking resource usage and job history

In short, **SLURM decides who runs what, where, and when** on a cluster.

### Why SLURM Is Required
On shared systems, running jobs directly via SSH would cause:
- GPU and CPU oversubscription
- Memory conflicts
- Uncontrolled runtimes
- No accountability or fairness

SLURM solves these problems by requiring users to **declare resource needs upfront**, allowing the scheduler to manage execution safely and efficiently.

---




