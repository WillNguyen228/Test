# Rotation Slicing: Structure-Aware Analysis of Galaxy Clusters

**Rotation Slicing** is a Python package for analyzing galaxy clusters through systematic rotational slicing of astronomical data. It is designed for research workflows that require studying orientation-dependent structure, symmetry, and anisotropy in cluster-scale datasets.

Will Nguyen*, Franklin & Marshall College
(*core contributor)

[Paper] · [Documentation] · [Examples] · [BibTeX]

---

## Overview

Rotation Slicing provides a clean and extensible framework for rotating spatial data around a defined center and extracting slice-based statistics across angular intervals. Built on top of the **Astropy** ecosystem, the package emphasizes clarity, reproducibility, and compatibility with common astronomy data formats.

The project originated as an undergraduate research effort and is intended to be lightweight, readable, and easy to adapt for exploratory analysis or methodological extensions.

**Key features:**

* Explicit rotational geometry and angle control
* Native support for Astropy tables, coordinates, and units
* Research-friendly abstractions suitable for experimentation and visualization

---

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
from rotationslicing import RotationSlicer
from astropy.table import Table

# Load astronomical data
data = Table.read("cluster_data.fits")

# Initialize slicer
slicer = RotationSlicer(
    data=data,
    center=(ra_center, dec_center),
    angles=range(0, 180, 5)
)

# Run slicing
results = slicer.run()
```

The output consists of per-angle slices containing spatial and statistical summaries suitable for downstream analysis or visualization.

---

## Examples

The `examples/` directory contains Jupyter notebooks demonstrating common workflows:

* **basic_rotation_slicing.ipynb**
  Perform rotational slicing on a galaxy cluster dataset

* **visualizing_slices.ipynb**
  Visualize density and orientation-dependent features

* **performance_analysis.ipynb**
  Explore slicing resolution versus runtime tradeoffs

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
│   ├── slicer.py
│   ├── geometry.py
│   └── utils.py
├── examples/
├── tests/
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
@software{nguyen_rotationslicing_2025,
  title = {Rotation Slicing: Structure-Aware Analysis of Galaxy Clusters},
  author = {Nguyen, Will},
  year = {2025},
  url = {https://github.com/Will220805/RotationSlicing}
}
```
