# WCS and Other Astropy Modules

## World Coordinate Systems
Use `astropy.wcs.WCS` to map image pixels to celestial coordinates and back.
```python
from astropy.io import fits
from astropy.wcs import WCS

with fits.open("image.fits") as hdul:
    wcs = WCS(hdul[0].header)
    sky = wcs.pixel_to_world(100, 100)
    x, y = wcs.world_to_pixel(sky)
```
Check axis order, origin conventions, projection validity, and whether the WCS corresponds to the selected image extension.

## NDData and CCDData
Use these containers when arrays need associated uncertainty, masks, units, and metadata. Keep those attributes aligned through transformations.

## Modeling
Astropy modeling provides model objects and fitters. Inspect fit convergence, residuals, parameter constraints, and uncertainty assumptions.

## Visualization and statistics
Use astronomy-aware visualization tools for image stretching and robust statistics such as sigma clipping when appropriate. Document any clipping or normalization because it changes the displayed or analyzed distribution.

## Constants
Use `astropy.constants` for physical constants and retain units through calculations.
