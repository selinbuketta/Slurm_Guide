
## How to transfer data to SLURM?

Most clusters provide dedicated high-capacity storage locations, such as:

```bash
/scratch
/work
/fast_storage
```

⚠️ Home directories are usually quota-limited and not intended for large data.

### scp
```bash
scp -r local_folder/ user@cluster:/fast_storage/user/project/
```
### rsync
```bash
rsync -avP local_folder/ user@cluster:/fast_storage/user/project/
```
## How to transfer big data to SLURM?
