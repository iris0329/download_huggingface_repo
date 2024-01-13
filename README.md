# download_huggingface_repo

```
pip install huggingface_hub
```

```python
from huggingface_hub import hf_hub_url
from huggingface_hub.utils import filter_repo_objects
from huggingface_hub.hf_api import HfApi
from huggingface_hub import snapshot_download

repo_id = "tiange/Cap3D"
repo_type = "model"  # "dataset"

# way 1: print urls
repo_info = HfApi().repo_info(repo_id=repo_id, repo_type=repo_type)
files = list(filter_repo_objects(items=[f.rfilename for f in repo_info.siblings]))
urls = [hf_hub_url(repo_id, filename=file, repo_type=repo_type) for file in files]
print("\n".join(urls))

# way 2: download repo directly
snapshot_download(repo_id=repo_id, repo_type=repo_type)
```
