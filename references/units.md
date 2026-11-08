# Astropy Units and Quantities

Use `astropy.units` to make physical dimensions explicit and catch invalid operations.

## Create and convert
```python
import astropy.units as u

distance = 3.2 * u.kpc
distance_pc = distance.to(u.pc)
velocity = 250 * u.km / u.s
```

## Equivalencies
Some conversions require domain assumptions. For example, wavelength and frequency conversion requires a spectral equivalency:
```python
wavelength = 500 * u.nm
frequency = wavelength.to(u.Hz, equivalencies=u.spectral())
```
Do not apply an equivalency unless its physical assumptions fit the data.

## Best practices
- Attach units at ingestion boundaries.
- Convert to a common unit before combining measurements.
- Use `.to_value(unit)` only when a plain numeric value is required.
- Preserve uncertainty and metadata alongside values.
- Avoid stripping units merely to silence an exception.
