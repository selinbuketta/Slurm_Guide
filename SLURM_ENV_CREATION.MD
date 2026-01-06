## Can I Use My Docker Image in SLURM?

**Direct Docker usage is usually NOT allowed on HPC clusters.**

Reasons include:
- Docker requires root privileges
- Security risks in multi-user environments
- Conflicts with cluster resource isolation

### The Correct Alternative
Most SLURM clusters support **Apptainer (formerly Singularity)**, which allows you to:

- Run Docker images **without root access**
- Maintain full environment reproducibility
- Integrate cleanly with SLURM scheduling
- Access GPUs, MPI, and shared filesystems

In practice:
- You **build with Docker**
- You **run with Apptainer**

This is the industry-standard HPC workflow.

---

## How to create Conda environment in SLURM?

