## Creating Slurm Job Script
A SLURM job script is a **Bash script with scheduler directives** that describe:
- What resources you need
- How long the job may run
- What command(s) should be executed

```bash
#!/bin/bash
#SBATCH --job-name=my_job
#SBATCH --partition=gpu
#SBATCH --gres=gpu:1
#SBATCH --cpus-per-task=4
#SBATCH --mem=32G
#SBATCH --time=02:00:00
#SBATCH --output=logs/%j.out
#SBATCH --error=logs/%j.err

set -e
set -u

source ~/miniconda3/bin/activate
conda activate my_env

python train.py
```
## Pushing Slurm Job
```bash
sbatch job.sh
```
Submitted batch job 123456

## Monitoring Slurm Job
Check Job Status
```bash
squeue -u $USER
```
Inspect Job Details
```bash
scontrol show job <job_id>
```
Monitor Logs in Real Time
```bash
tail -f logs/123456.out
tail -300 train_R_215.err
```
Resource Usage After Completion
```bash
sacct -j <job_id> --format=JobID,State,Elapsed,MaxRSS,AllocGRES
```
```bash
srun --jobid=216 --pty nvidia-smi -l 2
```