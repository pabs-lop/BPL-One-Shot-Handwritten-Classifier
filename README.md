# One-Shot Handwritten Character Classifier with Bayesian Program Learning

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python Version](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/downloads/)

---

## Table of Contents

  - [About the Project](#about-the-project)
    - [What is it?](#what-is-it)
    - [How It Works](#how-it-works)
  - [Features](#features)
  - [Getting Started](#getting-started)
    - [Prerequisites](#prerequisites)
    - [Folder Structure](#folder-structure)
  - [Data Organization](#data-organization)
  - [Running Script](#running-script)
  - [Expectations When Running This Script](#expectations-when-running-this-script)
  - [Acknowledgments](#acknowledgments)
    - [Research Paper](#research-paper)
    - [Original GitHub Code](#original-github-code)
  - [License](#license)

---

## About the Project

### What is it?

This project is a **Python implementation** of a one-shot handwritten character classifier using **Bayesian Program Learning (BPL)** and the **Modified Hausdorff Distance** as a similarity metric, simulating human-level concept learning by classifying new characters based on just **one example**. The system implements a **one-shot learning** classifier for handwritten characters, learning probabilistic programs from a small number of examples and using them to classify new, unseen characters.

### How It Works

1. **Data Preparation**: Handwritten character images are organized into labeled runs.
2. **Program Learning**: For each example, a probabilistic program representing the character's structure is learned.
3. **Classification**: New characters are classified by comparing them to previously learned programs using the **Modified Hausdorff Distance (MHD)**.

---

## Features

- **One-shot learning**: Classify new characters using only a single example.
- **Probabilistic Program Induction**: Uses BPL to learn and classify handwritten characters.
- **Flexible data preparation** with a customizable folder structure. The system requires preparing datasets using a specific folder structure for easy processing

---

## Getting Started

### Prerequisites

- Python 3.8 or higher
- `requirements.txt` (install via pip)

```bash
pip install -r requirements.txt
```

### Folder Structure

The project expects a specific directory structure for input data:

```
📂 Project Root/
├── 📁 all_runs/            # Directory containing *all* your data runs
│   ├── run01/              # Individual data run 1
│   ├── run02/              # Individual data run 2
│   └── ...                 # Each run has its own label file (`class_labels.txt`)
│
├── 📄 README.md           # This file
└── 📘 main.py              # Main implementation script
```

---

## Data Organization

*   **Store your handwritten character images** in the `all_runs/` directory, organized into subfolders (`run01`, `run02`, etc.). *Note*: Add more character images to create more runs.
*   **Ensure each run subfolder** (e.g., `run01/`) contains a file named `class_labels.txt`.
*   **The `class_labels.txt` format** should be a list of pairs, each line representing one training/test example: `image_test_path image_train_path`.

Here is a concrete example of what the `class_labels.txt` file should look like for one run:

```text
run01/images/image_test_01.png run01/images/image_train_01.png
run01/images/image_test_02.png run01/images/image_train_02.png
run01/images/image_test_03.png run01/images/image_train_03.png
...
```

## Running Script

To run the classifier, use:

```bash
python main.py [number_of_runs]
```

- The script reads data from `all_runs/` and performs classification.
- It displays error rates for each run, concluding with the average across all runs.

---

## Expectations When Running This Script

- **Input**: Organized data in `all_runs/` with `class_labels.txt` files.
- **Output**:
  - Error rates for each run
  - Final average error rate across all runs

Example Output:
```bash
Running one-shot handwritten character classifier

[INFO] Run 01: Error rate X.X%
[INFO] Run 02: Error rate X.X%
...
[INFO] Run 20: Error rate Y.Y%

[RESULT] Average error rate across *n* independent experiments (where n is the number of runs): Z.Z%
```

---

## Acknowledgments

This project builds on the **Bayesian Program Learning (BPL)** framework from academic research.

### Research Paper

> Lake, B. M., Salakhutdinov, R., and Tenenbaum, J. B. (2015).  
> **Human-level concept learning through probabilistic program induction**.  
> [*Science*, 350(6266), 1332-1338.](https://www.science.org/doi/abs/10.1126/science.aab3050)

### Original GitHub Code

> This is an adaptation based on the MATLAB code from [Brenden Lake's BPL repository](https://github.com/brendenlake/BPL).

---

## License

This project is licensed under the **MIT License**.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

> For details, please refer to the `LICENSE` file included in this project's root directory.
