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
dataset_info:
  features:
    - name: latitude
      dtype: float64
    - name: longitude
      dtype: float64
    - name: name
      dtype: string
    - name: description
      dtype: string
    - name: category
      dtype: string
    - name: date
      dtype: string
    - name: mass_g
      dtype: float64
    - name: meteorite_class
      dtype: string
    - name: fall_type
      dtype: string
  splits:
    - name: train
      num_examples: 4871
---

# Large Meteorites (1kg+) - NASA Catalog

4,871 significant meteorite specimens weighing at least 1 kilogram.

## What's Inside

- 4,871 large meteorites (1kg minimum)
- Complete coordinates for mapping
- Mass data in grams
- Petrologic classifications
- Fall vs. found distinction
- Date range: 1399-2013

## Filtering Criteria

- Mass threshold: 1,000+ grams (1 kg)
- Reduces NASA catalog by 89.3%
- All records have valid mass data

## Mass Statistics

| Metric | Value |
|--------|-------|
| Minimum | 1.0 kg |
| Median | 3.6 kg |
| Maximum | 60,000 kg (60 tonnes) |

## Record Structure

```json
{
  "latitude": -27.5,
  "longitude": 132.0,
  "name": "Hoba",
  "description": "Iron, IVB - 60000000g",
  "category": "large_meteorites",
  "date": "1920-01-01",
  "mass_g": 60000000,
  "meteorite_class": "Iron, IVB",
  "fall_type": "Found"
}
```

## Usage

```python
import json
import pandas as pd

with open('large_meteorites.json') as f:
    meteorites = json.load(f)

df = pd.DataFrame(meteorites)
print(f"Total meteorites: {len(df):,}")

# Find the heaviest
heaviest = df.nlargest(10, 'mass_g')[['name', 'mass_g', 'meteorite_class']]

# Filter by type
irons = df[df['meteorite_class'].str.contains('Iron', na=False)]
```

## Source & License

Public Domain -- U.S. Government Work. Data from NASA Meteoritical Bulletin via Open Data Portal.

~~https://data.nasa.gov/dataset/meteorite-landings~~ (URL no longer active; original data sourced from NASA's Meteoritical Bulletin)

## Distribution

- **Kaggle**: [lucassteuber/large-meteorites](https://www.kaggle.com/datasets/lucassteuber/large-meteorites)
- **HuggingFace**: [lukeslp/large-meteorites](https://huggingface.co/datasets/lukeslp/large-meteorites)
- **GitHub Gist**: [Demo Notebook](https://gist.github.com/lukeslp/1e62406b77598b0fc9fefbe3c3d3badb)

## Author

Luke Steuber | luke@lukesteuber.com | @lukesteuber.com (Bluesky)

## Structured Data (JSON-LD)

```json
{
  "@context": "https://schema.org",
  "@type": "Dataset",
  "name": "Large Meteorites (1kg+) - NASA Catalog",
  "description": "4,871 significant meteorite specimens weighing at least 1 kilogram from NASA's Meteoritical Bulletin. Includes mass, classification, and fall type data.",
  "url": "https://www.kaggle.com/datasets/lucassteuber/large-meteorites",
  "sameAs": "https://huggingface.co/datasets/lukeslp/large-meteorites",
  "license": "https://creativecommons.org/publicdomain/zero/1.0/",
  "creator": {
    "@type": "Person",
    "name": "Luke Steuber",
    "url": "https://lukesteuber.com"
  },
  "keywords": ["meteorites", "NASA", "astronomy", "space", "planetary science", "geospatial"],
  "temporalCoverage": "1399/2013",
  "spatialCoverage": {
    "@type": "Place",
    "name": "Global"
  },
  "distribution": [
    {
      "@type": "DataDownload",
      "encodingFormat": "application/json",
      "contentUrl": "https://www.kaggle.com/datasets/lucassteuber/large-meteorites"
    }
  ]
}
```
