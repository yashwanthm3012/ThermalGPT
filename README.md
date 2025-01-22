# Heat Equation Language Model Fine-Tuning

This repository contains the code and data pipelines for fine-tuning a large language model (LLM) to interpret and solve problems based on the heat equation in various scenarios. This project is inspired by the Fine-Tuning LM for Physical Interpretation Hackathon on Kaggle.

## Overview
The heat equation is a partial differential equation central to many fields in physics and engineering. This project uses synthetic data generated from different scenarios of the heat equation to fine-tune an LLM, enabling it to:

1. Predict temperature fields under varying boundary and initial conditions.
2. Generate solutions to time-dependent or steady-state heat equations.
3. Understand the physical principles embedded in training datasets.

## Dataset Description

For validation, we are providing solutions to the heat equation for simple cases. Participants are required to generate their own training datasets for fine-tuning, focusing on temporal cases and different thermal conductivity values with varying boundary conditions.

The time-dependent heat equation is given as:


$$\frac{\partial T}{\partial t} - \alpha \left(\frac{\partial^2 T}{\partial x^2} + \frac{\partial^2 T}{\partial y^2}\right) = f(x, y, t)$$


Where:
- $$T$$: Temperature field
- $$\alpha\$$: Thermal conductivity
- $$f(x, y, t)$$: Force function


## Data

The dataset used includes synthetic temperature field data generated under multiple cases:

### Case 1 : Dirichlet boundary conditions with sinusoidal forcing functions.

The equation for this case is:

$$
\frac{\partial^2 T}{\partial x^2} + \frac{\partial^2 T}{\partial y^2} = 8\pi^2 \sin(2\pi x) \sin(2\pi y)
$$

**Boundary Conditions:**
- $$T(0, y) = 0$$
- $$T(1, y) = 0$$
- $$T(x, 0) = 0$$
- $$T(x, 1) = 0$$

### Case 2 : Homogeneous boundary conditions with sinusoidal initial conditions.

The equation for this case is:

$$
\frac{\partial^2 T}{\partial x^2} + \frac{\partial^2 T}{\partial y^2} = 0
$$

**Initial and Boundary Conditions:**
- $$T(0, y) = 0$$
- $$T(1, y) = 0$$
- $$T(x, 0) = 0$$
- $$T(x, 1) = \sin(\pi x)$$

---

### Case 3 : Polynomial boundary conditions for steady-state solutions.

The equation for this case is:

$$
\frac{\partial^2 T}{\partial x^2} + \frac{\partial^2 T}{\partial y^2} = 0
$$

**Boundary Conditions:**
- $$T(0, y) = 0$$
- $$T(1, y) = y(1 - y)$$
- $$T(x, 0) = 0$$
- $$T(x, 1) = 0$$

---

### Case 4 : Time-dependent heat equation simulations with varying conductivity.

The equation for this case is:

$$
\frac{\partial T}{\partial t} = \alpha \left( \frac{\partial^2 T}{\partial x^2} + \frac{\partial^2 T}{\partial y^2} \right)
$$

**Initial and Boundary Conditions:**
- $$T(x, y, 0) = \sin(\pi x) \sin(\pi y)$$
- $$T(0, y, t) = 0$$
- $$T(1, y, t) = 0$$
- $$T(x, 0, t) = 0$$
- $$T(x, 1, t) = 0$$

  
The dataset structure follows the Kaggle hackathon format. Check out the competition [here](https://www.kaggle.com/competitions/fine-tuning-lm-physical-interpretation-hackathon/data).

## Features

- Fine-tune IBM's Granite 3.1 model using **Hugging Face Transformers**.
- Generate synthetic data for training using **PyVista** and **NumPy**.
- Perform evaluation with test datasets reflecting unseen scenarios.

## Repository Structure

ThermalGPT/
│   README.md            # Project documentation
│
├── data/                # Generated VTK files and tokenized datasets
├── gen_data/            # Script for generating synthetic data
├── models/              # Checkpoints and model outputs
├── results/             # Evaluation metrics and visualizations
└── scripts/             # Python scripts for data generation and training
## References

- [Kaggle Competition: Fine-Tuning LM for Physical Interpretation Hackathon](https://www.kaggle.com/competitions/fine-tuning-lm-physical-interpretation-hackathon)
- [IBM Granite 3.1 Model Documentation](https://huggingface.co/ibm-granite/granite-3.1-2b-base)

## License

This project is licensed under the MIT License.


