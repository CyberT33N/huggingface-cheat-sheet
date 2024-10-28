# huggingface cheat sheet




<br><br>

## CLI

<br><br>

### huggingface_hub

<br><br>

#### Download snapshot

Install:
```shell
pyenv local 3.11

python3 -m venv venv
source venv/bin/activate

pip install huggingface_hub
```

app.py
```python
from huggingface_hub import snapshot_download
token = "xxxxxxxxxxx"
snapshot_download(repo_id="black-forest-labs/FLUX.1-dev", local_dir="./downloaded", cache_dir="./cache", local_dir_use_symlinks=False, token=token)
```
