---
license: cc0-1.0
task_categories:
  - feature-extraction
language:
  - en
tags:
  - meteorites
  - nasa
  - astronomy
  - space
  - geospatial
  - earth-science
  - specimens
  - planetary-science
pretty_name: Large Meteorites (1kg+) - NASA Catalog
size_categories:
  - 1K<n<10K
---

# Large Meteorites (1kg+) - NASA Catalog

4,871 significant meteorite specimens weighing at least 1 kilogram

NASA meteorite catalog filtered to substantial specimens (1kg+). These larger meteorites are rare, scientifically valuable, and often found in museum collections worldwide.

## Dataset Structure

[Check the demo notebook for data exploration examples]

## Usage

```python
from datasets import load_dataset

# Load the dataset
dataset = load_dataset("lukeslp/large-meteorites")

# Or load from local files
import json
with open('data.json') as f:
    data = json.load(f)
```

## Citation

```bibtex
@dataset{large_meteorites_2026,
  title = {Large Meteorites (1kg+) - NASA Catalog},
  author = {Steuber, Luke},
  year = {2026},
  url = {https://huggingface.co/datasets/lukeslp/large-meteorites}
}
```

## Author

**Luke Steuber**
- Website: [lukesteuber.com](https://lukesteuber.com)
- Bluesky: [@lukesteuber.com](https://bsky.app/profile/lukesteuber.com)
- Email: luke@lukesteuber.com

## License

CC0-1.0
