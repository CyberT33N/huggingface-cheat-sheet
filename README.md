# huggingface cheat sheet




<br><br>

# CLI
- https://huggingface.co/docs/huggingface_hub/guides/cli

<br><br>




## download
- https://huggingface.co/docs/huggingface_hub/guides/cli#huggingface-cli-download


<details><summary>Click to expand..</summary>



## Download a Single File
Download a specific file from a repository:
```bash
huggingface-cli download <repo_id> <filename>
```
Example:
```bash
huggingface-cli download gpt2 config.json
```

## Download an Entire Repository
Download all files from a repository:
```bash
huggingface-cli download <repo_id>
```
Example:
```bash
huggingface-cli download HuggingFaceH4/zephyr-7b-beta
```

## Download Multiple Files
Specify files sequentially:
```bash
huggingface-cli download <repo_id> <file1> <file2> ...
```
Example:
```bash
huggingface-cli download gpt2 config.json model.safetensors
```

Use patterns to filter files:
```bash
huggingface-cli download <repo_id> --include "<pattern>" --exclude "<pattern>"
```
Example:
```bash
huggingface-cli download stabilityai/stable-diffusion-xl-base-1.0 --include "*.safetensors" --exclude "*.fp16.*"
```

## Download a Dataset or Space
Specify the repository type:
```bash
huggingface-cli download <repo_id> --repo-type <type>
```
Examples:
```bash
huggingface-cli download HuggingFaceH4/ultrachat_200k --repo-type dataset
huggingface-cli download HuggingFaceH4/zephyr-chat --repo-type space
```

## Download a Specific Revision
Use the `--revision` option for commits, branches, or tags:
```bash
huggingface-cli download <repo_id> --repo-type <type> --revision <revision>
```
Example:
```bash
huggingface-cli download bigcode/the-stack --repo-type dataset --revision v1.1
```

## Download to a Local Folder
Use `--local-dir` to download files into a specific folder:
```bash
huggingface-cli download <repo_id> <filename> --local-dir <folder>
```
Example:
```bash
huggingface-cli download adept/fuyu-8b model-00001-of-00002.safetensors --local-dir fuyu
```

## Specify Cache Directory
Define a custom cache directory using `--cache-dir`:
```bash
huggingface-cli download <repo_id> --cache-dir <path>
```
Example:
```bash
huggingface-cli download adept/fuyu-8b --cache-dir ./path/to/cache
```

## Use a Token for Private Repositories
Authenticate using the `--token` option:
```bash
huggingface-cli download <repo_id> <filename> --token <token>
```
Example:
```bash
huggingface-cli download gpt2 config.json --token hf_****
```

## Quiet Mode
Silence verbose output with the `--quiet` option:
```bash
huggingface-cli download <repo_id> --quiet
```
Example:
```bash
huggingface-cli download gpt2 --quiet
```

## Download Timeout
Increase the download timeout by setting the environment variable:
```bash
export HF_HUB_DOWNLOAD_TIMEOUT=<seconds>
```
Example:
```bash
export HF_HUB_DOWNLOAD_TIMEOUT=30
```
Then rerun the command.

---

**Pro Tips:**
- Use `huggingface-cli login` to save a token locally for easy access.
- Combine `--quiet` and `--local-dir` for clean scripting workflows.




</details>










<br><br>
___
___
<br><br>

# huggingface_hub

<br><br>

## Download snapshot

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
