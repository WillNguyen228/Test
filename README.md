Rotation Slicing: Structure-Aware Analysis of Galaxy Clusters

Rotation Slicing is a Python package for analyzing galaxy clusters via rotational slicing of astronomical data cubes.

Will Nguyen*, Franklin & Marshall College
(*core contributor)

[Paper] [Documentation] [Examples] [BibTeX]

Overview

Rotation Slicing is a lightweight, research-oriented Python package designed to analyze galaxy clusters by systematically slicing data across rotational angles. The package enables astronomers and computational researchers to study structural anisotropies, rotational symmetries, and orientation-dependent features in cluster-scale datasets.

The package was developed as part of undergraduate research at Franklin & Marshall College and is built on top of the Astropy ecosystem, prioritizing clarity, reproducibility, and extensibility.

Key goals:

Provide a clean abstraction for rotational slicing of astronomical data

Integrate seamlessly with Astropy tables, coordinates, and units

Enable rapid experimentation and visualization for research workflows

Installation
Prerequisites

Python 3.10+

Git

Conda or Miniforge (recommended)

Clone the Repository
git clone git@github.com:Will220805/RotationSlicing.git
cd RotationSlicing

Create a Conda Environment
conda create -n rotationslicing python=3.11
conda activate rotationslicing

Install the Package
pip install -e .


This installs Rotation Slicing in editable mode, allowing you to modify the source code and immediately test changes.

Getting Started

Below is a minimal example demonstrating how to perform a rotation slice on cluster data.

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

# Perform slicing
results = slicer.run()


The output includes per-angle slices containing spatial and statistical summaries suitable for downstream analysis or visualization.

Examples

The examples/ directory contains notebooks demonstrating common workflows:

basic_rotation_slicing.ipynb
Perform rotational slicing on a galaxy cluster dataset

visualizing_slices.ipynb
Plot density and orientation-dependent features

performance_analysis.ipynb
Benchmark slicing resolution vs. runtime

To run examples:

pip install -e ".[notebooks]"
jupyter notebook examples/

Package Structure
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

Design Philosophy

Rotation Slicing follows three guiding principles:

Explicit geometry — rotations and coordinate transforms are transparent and inspectable

Astropy-native — units, tables, and coordinates are first-class citizens

Research-first ergonomics — optimized for clarity over premature abstraction

Development

To set up a development environment:

pip install -e ".[dev]"


Run tests:

pytest


Format code:

ruff format .

Contributing

Contributions are welcome!
Please open an issue or submit a pull request. For major changes, consider discussing them first.

License

This project is released under the MIT License.
See the LICENSE file for details.

Acknowledgements

This project was developed at Franklin & Marshall College as part of undergraduate research in computational astrophysics.

Special thanks to faculty mentors and the Astropy community.

Citing Rotation Slicing

If you use Rotation Slicing in academic work, please cite:

@software{nguyen_rotationslicing_2025,
  title = {Rotation Slicing: Structure-Aware Analysis of Galaxy Clusters},
  author = {Nguyen, Will},
  year = {2025},
  url = {https://github.com/Will220805/RotationSlicing}
}