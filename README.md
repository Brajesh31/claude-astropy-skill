# claude-astropy-skill

A Claude Code skill for astronomy and astrophysics workflows built with Python and Astropy.

## Overview

Astropy provides core tools for scientific astronomy, including unit-aware calculations, celestial coordinate transformations, FITS data handling, cosmological calculations, time systems, tables, and world coordinate systems.

This skill helps an assistant select the appropriate Astropy modules, construct reliable analysis workflows, and avoid common mistakes involving units, coordinate frames, time scales, and scientific data formats.

## Main Capabilities

### Units and Quantities

- Represent physical values with explicit units.
- Convert between compatible units.
- Use equivalencies for domain-specific conversions.
- Perform calculations while preserving dimensional consistency.
- Work with logarithmic and specialized units.

### Celestial Coordinates

- Create and transform coordinate objects.
- Work with common frames such as ICRS, Galactic, FK5, and AltAz.
- Calculate angular separations and position angles.
- Match coordinates against catalogs.
- Include observer location and observation time when required.

### FITS Data

- Read and write FITS files.
- Inspect HDUs and headers.
- Access image arrays and table extensions.
- Update metadata carefully.
- Handle large files with suitable memory strategies.

### Cosmology

- Use built-in cosmological models.
- Calculate luminosity, comoving, and angular-diameter distances.
- Compute lookback time and age at a given redshift.
- Evaluate cosmological parameters and compare model assumptions.

### Time Systems

- Represent observation times precisely.
- Convert between time scales such as UTC, TAI, TT, and TDB.
- Work with Julian Date and Modified Julian Date.
- Perform time arithmetic and observer-dependent calculations.

### Tables and WCS

- Read, filter, join, and write astronomical catalogs.
- Preserve units and metadata in table columns.
- Transform between image pixel coordinates and world coordinates.
- Inspect and validate WCS metadata before using transformations.

## Installation

Install Astropy:

```bash
python -m pip install astropy
```

For a project managed with uv:

```bash
uv add astropy
```

Optional functionality may require additional dependencies. Install only the extras needed by the project.

## Install the Skill

```bash
git clone https://github.com/Brajesh31/claude-astropy-skill.git ~/.claude/skills/astropy
```

Use the skills directory recognized by your Claude-compatible environment.

## Usage

Invoke the skill for astronomy-related tasks:

```text
/astropy
```

Include the data format, coordinate frame, units, time scale, and scientific objective whenever those details affect the result.

## Quick Examples

### Unit-aware calculation

```python
import astropy.units as u

distance = 100 * u.parsec
distance_km = distance.to(u.km)
print(distance_km)
```

### Coordinate transformation

```python
import astropy.units as u
from astropy.coordinates import SkyCoord

source = SkyCoord(ra=10.5 * u.deg, dec=41.2 * u.deg, frame="icrs")
galactic = source.galactic
print(galactic.l, galactic.b)
```

### FITS inspection

```python
from astropy.io import fits

with fits.open("observation.fits") as hdus:
    hdus.info()
    image_data = hdus[0].data
    header = hdus[0].header
```

These examples are starting points. Adapt file names, HDU selection, coordinate values, and units to the actual observation.

## Repository Structure

```text
claude-astropy-skill/
├── SKILL.md
├── references/
│   ├── units.md
│   ├── coordinates.md
│   ├── cosmology.md
│   ├── fits.md
│   ├── tables.md
│   ├── time.md
│   └── wcs_and_other_modules.md
└── README.md
```

The root skill file provides the overall workflow. The reference documents provide focused guidance for individual Astropy modules.

## Recommended Workflow

1. Inspect the input data and its metadata.
2. Identify the scientific quantity, coordinate frame, or time convention involved.
3. Use explicit units and avoid silently mixing incompatible quantities.
4. Choose the relevant Astropy module.
5. Preserve source metadata when transforming files or tables.
6. Validate results with known values, dimensional checks, or independent calculations.
7. Record assumptions such as cosmological model, epoch, observer location, and coordinate frame.

## Scientific Reliability Checklist

- Attach units to physical quantities.
- Confirm coordinate frames before transforming positions.
- Supply observation time and location for observer-dependent frames.
- Check FITS HDU indices and header values before processing.
- State the cosmological model used in calculations.
- Specify time scales explicitly.
- Validate WCS transformations against the image metadata.
- Preserve provenance and assumptions in the scientific analysis record.

## Reference Guide

| File | Focus |
|---|---|
| `references/units.md` | Units, quantities, and equivalencies |
| `references/coordinates.md` | Coordinate frames and transformations |
| `references/cosmology.md` | Cosmological models and distances |
| `references/fits.md` | FITS files, HDUs, and headers |
| `references/tables.md` | Scientific tables and catalog operations |
| `references/time.md` | Time formats and scales |
| `references/wcs_and_other_modules.md` | WCS and related Astropy modules |

## Repository Contents

- `SKILL.md`: Main skill instructions.
- `references/`: Module-specific technical guidance.
- `README.md`: Installation, examples, and workflow overview.
