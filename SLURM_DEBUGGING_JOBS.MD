## Interactive Jobs (Debugging Purpose Only)

### Why Use an Interactive Debug Job?

Interactive jobs are intended for:
- Verifying GPU access
- Testing CUDA / TensorFlow / PyTorch installation
- Debugging environment issues
- Running short test jobs

⚠️ **They are NOT for long training runs.**  
Always use batch jobs (`sbatch`) for production workloads.

---

Step 1: Start From the Login Node

You should always begin on a **login node**, which is used for:
- Editing code
- Submitting jobs
- Light inspection tasks

Never run GPU workloads directly on the login node.


Step 2: Interactive Debug Job

Use `srun` to request resources and open an interactive shell on a compute node.

```bash
srun \
  --partition=debugging \
  --qos=debugging \
  --account=debugging \
  --gres=gpu:1g.10gb:1 \
  --cpus-per-task=4 \
  --mem=32G \
  --time=01:00:00 \
  --job-name=tf_gpu_check \
  --pty bash -i
```
Step 3: Activate Your Conda Environment
```bash
source /fast_storage/<username>/miniconda38/bin/activate
conda activate tf26
```

Step 4: Verify GPU Allocation
```bash
nvidia-smi
```
Step 5: Validate Framework GPU Access
```bash
python - <<'EOF'
import tensorflow as tf
print("TF version:", tf.__version__)
print("Visible GPUs:", tf.config.list_physical_devices("GPU"))
EOF
```
Step 6: Run a Short Test Job
```bash
cd /fast_storage/<username>/Projects/Slurm

python train.py \
  --data_dir /fast_storage/<username>/Data/train/ \
  --checkpoint_dir /fast_storage/<username>/Checkpoints/debug_gpu_test \
  --rep 9D \
  --encoder cvt \
  --batch 2 \
  --n_epoch 1 \
  --lr 1e-3
```