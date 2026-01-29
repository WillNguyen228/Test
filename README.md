# Rotation Slicing: Structure-Aware Analysis of Galaxy Clusters

**Rotation Slicing** is a Python package for analyzing galaxy clusters through systematic rotational slicing of astronomical data. It is designed for research workflows that require studying orientation-dependent structure, symmetry, and anisotropy in cluster-scale datasets.

Elizabeth Praton*, Franklin & Marshall College
(*core contributor)

[Paper] · [Documentation] · [Examples] · [BibTeX]

---

## Overview

**RotationSlicing** is a Python package developed at Franklin & Marshall College to support the exploration of galaxy clusters and large-scale structure through *arbitrarily oriented sky slices*. Built to integrate tightly with **Astropy**, the package allows users to select galaxies distributed along any great circle on the celestial sphere and visualize them simultaneously in projected sky coordinates and redshift space.

Unlike standard RA/Dec–aligned slicing or line-of-sight convolution methods, RotationSlicing enables slices at *any orientation*, making it possible to reveal tilted infall regions, asymmetries, and signatures of transverse or rotational motion that are otherwise obscured in redshift space. This capability is especially valuable for studying redshift-space distortions in galaxy clusters and group environments.

At its core, RotationSlicing defines custom coordinate frames that rotate the sky into a user-specified orientation, producing uniform, flat slices rather than conic sections. The package provides both low-level building blocks—such as the `RotSlice` transformation class and specialized plotting axes—and higher-level interactive tools that combine sky projections and redshift ("pie") plots for rapid exploratory analysis.

Recent development has focused on improving usability, visualization, and maintainability in preparation for broader community use. New features include full-sky and hemisphere Aitoff projections, interactive explorer classes for real-time rotation and slicing, and a modern, test-driven development workflow aligned with Astropy contribution standards.

RotationSlicing is designed for astronomers who want flexible, interpretable visualizations of galaxy distributions—from targeted cluster studies to wide-area survey data such as SDSS and DESI.

## Installation

### Prerequisites

* Python 3.10 or higher
* Git
* Conda / Miniforge (recommended)

### Clone the Repository

```bash
git clone git@github.com:Will220805/RotationSlicing.git
cd RotationSlicing
```

### Create a Conda Environment

```bash
conda create -n rotationslicing python=3.11
conda activate rotationslicing
```

### Install the Package

```bash
pip install -e .
```

This installs Rotation Slicing in **editable mode**, allowing local source code changes to take effect immediately.

---

## Getting Started

Below is a minimal example demonstrating how to perform rotational slicing on cluster data.

```python
import matplotlib.pyplot as plt
from astropy.coordinates import SkyCoord
from astropy import units as u
from rotationslicing import RotSlice, SkyframeAxes

# create RotSlice object `rs` centered on the given `lon0lat0` longitude, latitude spot on the sky,
# and oriented at the given `spin0`angle measured clockwise from horizontal.
rs = RotSlice(lon0lat0=SkyCoord(180, 20, unit="deg"),  # defaults to ICRS frame
              spin0=30*u.deg)

# create a SkyframeAxes centered on the `lon0lat0` stored in `rs`
# keep the sky unrotated

rect = [0.1,0.1,0.8,0.8] # rectangle to draw the axes into, relative to the figure
fig = plt.figure(figsize=(5, 5))

ax = SkyframeAxes(fig,rect, lon0lat0=rs.lon0lat0, plot_size=130*u.deg, sky_rotation=0*u.deg)
ax.grid()  # turn on a graticule

# add a slice boundary showing the slice orientation and default dimensions stored in `rs`
ax.plot_coord(rs.slicebound_inSkyframe())
fig.add_axes(ax)

---

## Examples

The `examples/` directory contains Jupyter notebooks demonstrating common workflows:

* **basic_rotation_slicing.ipynb**
  Perform rotational slicing on a galaxy cluster dataset

* **ways_to_visualize_slices.ipynb**
  Visualize your results using different frames

* **convenience_functions.ipynb**
  Explore slicing functions that merge multiple functionalities together

To run the examples:

```bash
pip install -e ".[notebooks]"
jupyter notebook examples/
```

---

## Package Structure

```
RotationSlicing/
├── rotationslicing/
│   ├── __init__.py
│   ├── <Fill later>
│   ├── <Fill later>
│   └── <Fill later>
├── <Fill later>
├── <Fill later>
├── pyproject.toml
└── README.md
```

---

## Design Philosophy

Rotation Slicing follows three guiding principles:

1. **Explicit geometry** — rotational transformations are transparent and inspectable
2. **Astropy-native** — units, tables, and coordinates are first-class objects
3. **Research-first ergonomics** — optimized for clarity and flexibility over premature abstraction

---

## Development

To set up a development environment:

```bash
pip install -e ".[dev]"
```

Run tests:

```bash
pytest
```

Format code:

```bash
ruff format .
```

---

## Contributing

Contributions are welcome. Please open an issue or submit a pull request. For substantial changes, consider starting a discussion first.

---

## License

This project is released under the MIT License. See the `LICENSE` file for details.

---

## Acknowledgements

This project was developed at **Franklin & Marshall College** as part of undergraduate research in computational astrophysics.

Special thanks to faculty mentors and the Astropy community.

---

## Citing Rotation Slicing

If you use Rotation Slicing in academic work, please cite:

```bibtex
@software{rotationslicing_2026,
  title = {Rotation Slicing: Structure-Aware Analysis of Galaxy Clusters},
  author = {Praton, Elizabeth},
  year = {2025},
  url = {https://github.com/epraton/rotationslicing}
}
```
