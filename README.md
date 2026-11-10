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
    - name: name
      dtype: string
    - name: mass_g
      dtype: float64
    - name: meteorite_class
      dtype: string
    - name: fall_type
      dtype: string
    - name: latitude
      dtype: float64
    - name: longitude
      dtype: float64
    - name: date
      dtype: string
    - name: year
      dtype: int64
    - name: category
      dtype: string
    - name: description
      dtype: string
  splits:
    - name: train
      num_examples: 4871
---

# Large Meteorites (1kg+) - NASA Catalog

4,871 significant meteorite specimens weighing at least 1 kilogram.

## What's Inside

- 4,871 large meteorites (1kg minimum)
- Coordinates for 4,174 of them
- Mass data in grams
- Petrologic classifications
- Fall vs. found distinction (4,129 found, 742 seen falling)
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
  "name": "Hoba",
  "mass_g": 60000000.0,
  "meteorite_class": "Iron, IVB",
  "fall_type": "Found",
  "latitude": -19.58333,
  "longitude": 17.91667,
  "date": "1920-01-01",
  "year": 1920,
  "category": "large_meteorites",
  "description": "Meteorite Hoba - Iron, IVB. Mass: 60000.00kg. Found."
}
```

- The catalog records a year, not a day. `date` is that year written as January 1, and 54 records have no year at all.
- 697 records have no coordinates. Another 349 sit at latitude 0, longitude 0, which is a placeholder in the source catalog, so filter those out before mapping.

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

Public domain (U.S. government work). Data from the Meteoritical Bulletin by way of NASA's Open Data Portal. The portal page it came from (data.nasa.gov/dataset/meteorite-landings) is no longer online.

## Distribution

- **HuggingFace**: [lukeslp/large-meteorites](https://huggingface.co/datasets/lukeslp/large-meteorites)
- **GitHub Gist**: [Demo Notebook](https://gist.github.com/lukeslp/1e62406b77598b0fc9fefbe3c3d3badb)

## Structured Data (JSON-LD)

```json
{
  "@context": "https://schema.org",
  "@type": "Dataset",
  "name": "Large Meteorites (1kg+) - NASA Catalog",
  "description": "4,871 significant meteorite specimens weighing at least 1 kilogram from NASA's Meteoritical Bulletin. Includes mass, classification, and fall type data.",
  "url": "https://huggingface.co/datasets/lukeslp/large-meteorites",
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
      "contentUrl": "https://huggingface.co/datasets/lukeslp/large-meteorites"
    }
  ]
}
```
