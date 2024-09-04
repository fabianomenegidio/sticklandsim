# SticklandSim

**SticklandSim** is a Python-based simulation tool designed to model ATP production and mutation dynamics using Stickland pairs in various environmental and evolutionary scenarios. The tool allows users to explore how different mutation rates, selection pressures, and environmental changes impact the population’s fitness and ATP production over generations.

## Table of Contents

- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
  - [Command-Line Arguments](#command-line-arguments)
  - [Configuration Files](#configuration-files)
  - [Examples](#examples)
- [Simulation Scenarios](#simulation-scenarios)
  - [Available Scenarios](#available-scenarios)
- [Docker Support](#docker-support)
- [Contributing](#contributing)
- [License](#license)

---

## Features

- **Customizable Simulations**: Define mutation rates, ATP production efficiency, fitness thresholds, and more.
- **Predefined Scenarios**: Choose from several pre-built scenarios or create your own.
- **Dynamic Parameter Adjustment**: Use machine learning to optimize parameters during the simulation.
- **Support for Checkpoints**: Resume long simulations from checkpoints.
- **Multiple Output Formats**: Generate reports in PDF, CSV, XLSX, and JSON formats.
- **Parallel Execution**: Run multiple simulations simultaneously for larger datasets.

---

## Installation

You can install **SticklandSim** via pip, Conda, or use the provided Docker image.

### Using pip

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/sticklandsim.git
   cd sticklandsim
