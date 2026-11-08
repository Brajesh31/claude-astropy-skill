# FITS File Operations

Use context managers to ensure FITS resources are closed.

```python
from astropy.io import fits

with fits.open("observation.fits", memmap=True) as hdul:
    hdul.info()
    data = hdul[0].data
    header = hdul[0].header.copy()
```

## Safe handling
- Inspect HDU names, dimensions, and data types before processing.
- Copy header metadata before closing the file if it is needed later.
- Use memory mapping for large files when access patterns permit.
- Validate required header keywords and units.
- Preserve provenance and avoid overwriting source observations.
- When writing modified products, write to a new path and verify the output can be reopened.
