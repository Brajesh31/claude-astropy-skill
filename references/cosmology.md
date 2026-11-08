# Cosmological Calculations

Astropy provides named cosmological parameter sets and distance/time calculations.

```python
from astropy.cosmology import Planck18
import astropy.units as u

z = 1.0
luminosity_distance = Planck18.luminosity_distance(z)
angular_distance = Planck18.angular_diameter_distance(z)
lookback = Planck18.lookback_time(z)
age = Planck18.age(z)
print(luminosity_distance.to(u.Gpc), angular_distance.to(u.Gpc))
print(lookback.to(u.Gyr), age.to(u.Gyr))
```

Record the cosmology used with every reported result. Distances and times depend on model parameters. Validate redshift domain and assumptions, especially for custom cosmologies or precision work.
