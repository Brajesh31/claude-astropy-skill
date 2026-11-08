# Astropy Tables

Use `Table` for catalog-like data with metadata and format-aware I/O.

```python
from astropy.table import Table, join

catalog = Table.read("catalog.fits")
bright = catalog[catalog["magnitude"] < 18]
bright.write("bright_catalog.ecsv", overwrite=True)
```

## Operations
- Select columns by name and rows with boolean masks.
- Sort with `sort` and group with `group_by`.
- Join catalogs with explicit keys and validate duplicate behavior.
- Use `QTable` when unit-aware columns should participate in calculations.
- Use masked columns for missing values rather than ambiguous sentinel numbers.

Choose a format that preserves units and metadata when scientific reproducibility matters. ECSV is useful for readable text with Astropy metadata.
