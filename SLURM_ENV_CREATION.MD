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

## How to create MiniConda environment in SLURM?

Step 1: Move to Your Project Storage Directory

Always install software in a **project or fast storage directory**, not in `$HOME`.

```bash
cd /fast_storage/<username>/Projects/Slurm
```
Step 2: Download Miniconda Installer
```bash
wget https://repo.anaconda.com/miniconda/Miniconda3-py38_23.5.2-0-Linux-x86_64.sh
```
Step 3: Install Miniconda (Batch Mode)
```bash
bash Miniconda3-py38_23.5.2-0-Linux-x86_64.sh -b -p /fast_storage/<username>/miniconda38
```
Step 4: Activate Miniconda
```bash
source /fast_storage/<username>/miniconda38/bin/activate
```
Verify the installation:
```bash
python --version
``` 
Step 5: Create a Conda Environment and Activate the Environment
```bash
conda create -n tf26 python=3.8 -y
conda activate tf26
```

Deactivate the Environment:
```bash
conda deactivate tf26
```
