# Time Handling

Use `astropy.time.Time` for astronomical time representations and scale conversions.

```python
from astropy.time import Time

t = Time("2025-01-15T12:30:00", scale="utc")
print(t.jd, t.mjd, t.tai.iso, t.tt.iso)
```

## Guidance
- Always specify the input format and scale when they are not unambiguous.
- Distinguish UTC, TAI, TT, and TDB according to the measurement.
- Use `TimeDelta` for elapsed time arithmetic.
- Include observer location and observation time for sidereal calculations.
- Preserve precision and avoid converting high-precision timestamps to ordinary floating-point seconds unnecessarily.
