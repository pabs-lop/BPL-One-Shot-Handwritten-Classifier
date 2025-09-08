# One-Shot Handwritten Character Classifier with Bayesian Program Learning

This project is a python implementation of a one-shot handwritten character classifier utilizing **Bayesian Program Learning (BPL)** and a modified Hausdorff distance as its similarity metric. This script assesses the ability to classify new characters based on a single example, simulating a "one-shot" learning scenario.

## Features

*   **One-Shot Learning:** Classify new characters using only a single example.
*   **Probabilistic Program Induction:** Uses the core BPL algorithm to learn and classify handwritten characters.
*   **Flexible Data Preparation:** The system requires preparing datasets using a specific folder structure for easy processing.

---

## Approach & Methodology

The classifier works by learning generative models of handwritten characters from a small number of examples and then using these models to classify new, unseen instances. Key steps include:

1.  **Data Preparation:** Prepare your handwritten character data according to the structure described below.
2.  **Program Learning:** For each provided example (test character), learn a probabilistic program representing its structure.
3.  **Classification:** Use the learned programs to classify new characters presented later.

The classification is performed using a pixel-coordinate-based approach and relies on the Modified Hausdorff Distance (MHD) metric for comparing character structures.

---

### Python Version

Python 3.8 or higher is required.


## Requirements

To run this project, ensure you have Python installed along with the dependencies specified on the pip file:

- Install dependencies:

```bash
pip install numpy imageio scipy
```

- or run the `requirements.txt` file:
```bash
pip install -r requirements.txt
```

---

## Directory Structure

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

### Data Organization

*   **Store your handwritten character images** in the `all_runs/` directory, organized into subfolders (`run01`, `run02`, etc.).
*   **Ensure each run subfolder** (e.g., `run01/`) contains a file named `class_labels.txt`.
*   **The `class_labels.txt` format** should be a list of pairs, each line representing one training/test example: `image_test_path image_train_path`.

### Example class_labels.txt Format

Here is a concrete example of what the `class_labels.txt` file should look like for one run:

```text
run01/images/image_test_01.png run01/images/image_train_01.png
run01/images/image_test_02.png run01/images/image_train_02.png
run01/images/image_test_03.png run01/images/image_train_03.png
...
```

---

## How to Use

### Step-by-step Instructions:

1.  **Prepare your data**:
    *   Organize your handwritten character images into individual run folders within `all_runs/`.
    *   Create a `class_labels.txt` file for each run, specifying the test and training image paths (see example above). Ensure you have at least one valid test-train pair per run.
    *   Place all your data runs (folders like `run01`, `run02`) inside the `all_runs/` directory.

2.  **Run the classifier**:

```bash
python main.py # the number of runs to test (default is 200)
```

    *   The script will read the data from `all_runs/` and perform classification. (add more data for more runs)
    *   It displays error rates for each run, concluding with the average across all runs.

3.  **Output**:
    *   The program output shows error rates for each run and the final average.
        *Example Output (assuming 20 runs):*
    ```bash
    Running one-shot handwritten character classifier
    
    [START OF RESULTS]
    Run 01: Error rate X.X%
    Run 02: Error rate X.X%
    ...
    Run 20: Error rate Y.Y%
    
    [RESULT] Average error rate across *n* independent experiments (where n is the number of runs): Z.Z%
    ```
    *   The average error rate `Z.Z%` is calculated based on the results from all specified runs. Each run uses a distinct set of test examples.

---

## Citation & Acknowledgments

This project adapts the core principles of the Bayesian Program Learning framework.

### Research Paper:

> Lake, B. M., Salakhutdinov, R., and Tenenbaum, J. B. (2015).  
> **Human-level concept learning through probabilistic program induction**.  
> [*Science*, 350(6266), 1332-1338.](https://www.science.org/doi/abs/10.1126/science.aab3050)

### Original GitHub Code:

> This implementation is based on the MATLAB code from [Brenden Lake's BPL repository](https://github.com/brendenlake/BPL).

---

## License

This project is licensed under the **MIT License**.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

> For details, please refer to the `LICENSE` file included in this project's root directory.
