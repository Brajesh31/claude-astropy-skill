# Celestial Coordinates

Use `SkyCoord` for coordinate parsing, transformations, separations, and catalog matching.

## Create and transform
```python
import astropy.units as u
from astropy.coordinates import SkyCoord

coord = SkyCoord(ra=10.5*u.deg, dec=41.2*u.deg, frame="icrs")
galactic = coord.galactic
print(galactic.l, galactic.b)
```

## Matching catalogs
Use `match_to_catalog_sky` for nearest-neighbor matching and inspect angular separations before accepting matches. Define a scientifically justified maximum separation. Check coordinate epoch, frame, proper motion, and units.

## AltAz
Altitude/azimuth transformations require an observing time and Earth location. Use an explicit `obstime` and `location`; do not rely on implicit defaults.

## Pitfalls
- RA and Dec are not interchangeable with longitude and latitude without a frame transformation.
- Sexagesimal strings must include the correct units.
- Coordinate matching can produce ambiguous nearest neighbors in crowded fields.
