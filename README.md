# SticklandSim

**SticklandSim** is a Python-based simulation tool designed to model ATP production and mutation dynamics using Stickland pairs in various environmental and evolutionary scenarios. The tool allows users to explore how different mutation rates, selection pressures, and environmental changes impact the population’s fitness and ATP production over generations.

## Table of Contents

- [Features](#features)
- [Installation](#installation)
  - [Using pip](#using-pip)
  - [Using Conda](#using-conda)
  - [Using Docker](#using-docker)
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
   \`\`\`bash
   git clone https://github.com/yourusername/sticklandsim.git
   cd sticklandsim
   \`\`\`

2. Install the required Python packages:
   \`\`\`bash
   pip install -r requirements.txt
   \`\`\`

### Using Conda

1. Create a Conda environment and install the dependencies:
   \`\`\`bash
   conda create --name sticklandsim python=3.10
   conda activate sticklandsim
   conda install --file requirements.txt
   \`\`\`

### Using Docker

1. Build the Docker image:
   \`\`\`bash
   docker build -t sticklandsim:latest .
   \`\`\`

2. Run the tool inside a Docker container:
   \`\`\`bash
   docker run --rm -v \$(pwd)/configs:/app/configs -v \$(pwd)/results:/app/results sticklandsim:latest --config configs/scenario1.json --output results/output.pdf
   \`\`\`

---

## Usage

Once installed, **SticklandSim** can be used through the command line. You can pass in configuration files, select predefined scenarios, and generate reports in different formats.

### Command-Line Arguments

\`\`\`bash
python sticklandsim.py --help
\`\`\`

The main options are:

- \`--config\`: Path to one or more JSON configuration files that define the simulation scenarios.
- \`--template\`: Choose from predefined templates such as \`high_mutation\`, \`high_selection\`, etc.
- \`--output\`: Base name for the output report (default is \`simulation_output\`).
- \`--format\`: Specify the output format: \`pdf\`, \`csv\`, \`xlsx\`, \`json\`.
- \`--parallel\`: Run multiple simulations in parallel (if multiple scenarios are provided).
- \`--workers\`: Number of parallel workers (defaults to the number of available CPUs).
- \`--checkpoint-interval\`: Number of generations after which a checkpoint is saved.
- \`--resume-from\`: Path to a checkpoint file to resume a previous simulation.
- \`--ml\`: Enable dynamic parameter adjustment using machine learning.

---

### Configuration Files

Configuration files are JSON files that define the parameters for a simulation scenario. Below is an example:

\`\`\`json
{
  "scenarios": [
    {
      "name": "Standard Mutation and ATP Production",
      "mutation_rate": 0.05,
      "generations": 100,
      "fitness_threshold": 10,
      "environment_factor": 1.0,
      "stickland_pairs": [
        {
          "amino_acid_pair": "Ala-Leu",
          "efficiency": 1.2,
          "count": 10
        },
        {
          "amino_acid_pair": "Pro-Val",
          "efficiency": 1.5,
          "count": 8
        }
      ],
      "event_schedule": {
        "20": "mutation",
        "50": "selection",
        "75": "environment_change"
      }
    }
  ]
}
\`\`\`

### Examples

#### Running a Standard Simulation

\`\`\`bash
python sticklandsim.py --config configs/scenario1_standard_mutation.json --output results/standard_simulation.pdf
\`\`\`

#### Running a High Mutation Simulation

\`\`\`bash
python sticklandsim.py --config configs/scenario2_high_mutation.json --output results/high_mutation_output.csv --format csv
\`\`\`

#### Running a Simulation with Machine Learning Optimizations

\`\`\`bash
python sticklandsim.py --config configs/scenario3_high_selection.json --ml --output results/high_selection_optimized.pdf
\`\`\`

---

## Simulation Scenarios

### Available Scenarios

The tool provides several predefined simulation scenarios, each with its own unique characteristics.

| Scenario Name                           | File Name                               | Summary                                            |
|-----------------------------------------|-----------------------------------------|----------------------------------------------------|
| Standard Mutation and ATP Production    | \`scenario1_standard_mutation.json\`      | Basic simulation with moderate mutation rate.       |
| High Mutation Rate Simulation           | \`scenario2_high_mutation.json\`          | Frequent mutations with faster adaptation.          |
| High Selection Pressure Simulation      | \`scenario3_high_selection.json\`         | High selection threshold, simulating strong pressure.|
| Frequent Environmental Changes          | \`scenario4_frequent_environmental_changes.json\` | Rapid environmental changes throughout the simulation. |
| Custom Scenario                         | \`scenario5_custom_simulation.json\`      | A customizable scenario with adjustable parameters. |
| Low Mutation Rate Simulation            | \`scenario6_low_mutation.json\`           | Very low mutation rate, slow evolutionary pace.     |
| High Environmental Variability          | \`scenario7_high_environmental_variability.json\` | High environmental fluctuations affecting ATP production. |
| Extreme Environmental Stress            | \`scenario8_extreme_environmental_stress.json\` | Stressful conditions and survival challenges.       |
| Adaptive Mutation Rate                  | \`scenario9_adaptive_mutation.json\`      | Dynamic mutation rates responding to environmental changes. |
| Stable Environment with High ATP        | \`scenario10_stable_high_atp.json\`       | A stable environment with high ATP production.      |
| Gradual Mutation Increase               | \`scenario11_gradual_mutation_increase.json\` | Gradual increase in mutation rate over time.       |

---

## Docker Support

**SticklandSim** can be run inside a Docker container. This allows for a consistent environment regardless of the host machine’s setup.

### Building the Docker Image

\`\`\`bash
docker build -t sticklandsim:latest .
\`\`\`

### Running a Simulation with Docker

\`\`\`bash
docker run --rm -v \$(pwd)/configs:/app/configs -v \$(pwd)/results:/app/results sticklandsim:latest --config configs/scenario1_standard_mutation.json --output results/standard_simulation.pdf
\`\`\`

### Multi-stage Build (Optimization)

The Dockerfile uses a multi-stage build process to ensure that the final image is as lightweight as possible, containing only the necessary runtime dependencies.

---

## Contributing

We welcome contributions to improve the tool! Here's how you can get involved:

1. Fork the repository.
2. Create a new branch (\`git checkout -b feature-branch\`).
3. Make your changes and commit them (\`git commit -m "Add feature"\`).
4. Push to the branch (\`git push origin feature-branch\`).
5. Open a pull request.

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
