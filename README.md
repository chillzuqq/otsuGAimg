# Optimal Image Thresholding with a Genetic Algorithm

![Python Version](https://img.shields.io/badge/python-3.9+-blue.svg)

This repository contains a Python implementation of an advanced image thresholding technique that uses a **Genetic Algorithm (GA)** to discover the optimal threshold for binarizing a grayscale image. The fitness of each potential threshold is evaluated using **Otsu's method**, which minimizes the intra-class variance to achieve the best possible separation between foreground and background pixels.

## ✨ Features

-   **Intelligent Thresholding**: Moves beyond static methods by using a GA to search for the best threshold.
-   **Otsu's Method Fitness**: Leverages a proven statistical method to guide the optimization process.
-   **Customizable GA Parameters**: Easily tune the population size, number of generations, and mutation rate to fit different needs.
-   **Visual Output**: Generates a side-by-side comparison of the original and thresholded images.

## 🔬 Methodology Explained

The core of this project is the synergy between a powerful search heuristic (the GA) and a robust statistical method (Otsu's).

### 1. Otsu's Method as the Fitness Function

Otsu's method provides a way to measure how "good" a given threshold is. It automatically finds a threshold that minimizes the weighted sum of within-class variances. A lower variance signifies a better-defined separation between the two classes of pixels (foreground and background). This variance value serves as the **fitness score** for our Genetic Algorithm, where the goal is to find the threshold that results in the *lowest* score.

### 2. The Genetic Algorithm

The GA explores the space of all possible thresholds (0-255) to find the optimal one.

-   **Chromosome Encoding**: Each potential threshold is an "individual" represented as an **8-bit binary string** (e.g., `10110101`), which directly maps to an integer between 0 and 255.

-   **Evolutionary Process**: The algorithm evolves a population of these individuals over several generations:
    1.  **Initialization**: A random population of potential thresholds (chromosomes) is created.
    2.  **Fitness Evaluation**: Each chromosome's fitness is calculated using the Otsu's variance function.
    3.  **Selection**: **Tournament Selection** is used to choose parent chromosomes for the next generation. The fittest individuals in random subgroups are more likely to be selected.
    4.  **Crossover**: Selected parents are combined using **single-point crossover** to create offspring, mixing their genetic material.
    5.  **Mutation**: A small probability of **bit-flipping** is applied to the offspring to introduce new genetic variations and prevent premature convergence.
    6.  **Elitism**: The best individual from each generation is automatically preserved, ensuring that the best solution found is never lost.

-   **Termination**: After a set number of generations, the algorithm returns the best chromosome found, which represents the optimal threshold value.

### GA Parameters
The algorithm's performance can be fine-tuned via these constants in the code:

| Parameter         | Default Value | Description                                          |
| ----------------- | :-----------: | ---------------------------------------------------- |
| `POPULATION_SIZE` |      20       | The number of chromosomes in each generation.        |
| `N_GENERATIONS`   |      50       | The number of cycles the evolution will run.         |
| `MUTATION_RATE`   |     0.002     | The probability of a single bit flip during mutation. |
| `TOURNAMENT_SIZE` |       5       | The size of the selection tournament.                |


---

## 🚀 Getting Started

Follow these steps to run the project on your local machine.

### Prerequisites

Make sure you have Python 3.9+ installed. You will also need the following libraries:

-   NumPy
-   Pillow
-   Matplotlib
-   Seaborn (optional, used in the original notebook but not essential for the core logic)

### Installation

1.  Clone the repository:
    ```bash
    git clone [https://github.com/your-username/ga-otsu-thresholding.git](https://github.com/your-username/ga-otsu-thresholding.git)
    cd ga-otsu-thresholding
    ```

2.  Install the required packages:
    ```bash
    pip install numpy Pillow matplotlib
    ```

### Usage

1.  Add the image you wish to process to the project directory.
2.  Open the `OtsuGAcode.ipynb` notebook in a Jupyter environment (like Jupyter Lab or VS Code).
3.  Locate the following line and update the path to your image:
    ```python
    path_image = 'CIMG5004.JPG'  # <-- Change this to your image file
    ```
4.  Run all cells in the notebook. The output will show the GA's progress and display the final comparison image.

## 🤝 Contributing

Contributions are welcome! If you have suggestions for improvements or want to add new features, feel free to fork the repository and submit a pull request.

1.  Fork the Project
2.  Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3.  Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4.  Push to the Branch (`git push origin feature/AmazingFeature`)
5.  Open a Pull Request

## 📜 License

This project is distributed under the MIT License. See `LICENSE.txt` for more information.
