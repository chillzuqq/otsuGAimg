Optimal Image Thresholding using a Genetic Algorithm with Otsu's Method
This project demonstrates a sophisticated approach to image thresholding by employing a Genetic Algorithm (GA) to find the optimal threshold value for binarizing a grayscale image. The fitness of each potential threshold is evaluated using Otsu's method, which aims to minimize the intra-class variance.

📖 Methodology
The process is divided into two main parts: the implementation of a Genetic Algorithm and the application of Otsu's method as its fitness function.

1. Otsu's Method (Fitness Function)
Otsu's method is a well-regarded technique in image processing for automatic thresholding. It works by finding a threshold that separates the image into two classes (foreground and background) in a way that minimizes their combined spread (within-class variance).

The compute_otsu_criteria function calculates this variance for a given threshold. A lower value indicates a better separation, making it the perfect objective for our GA to minimize.

2. Genetic Algorithm (GA)
The GA is a search heuristic inspired by the process of natural selection. It is used here to efficiently search the entire range of possible thresholds (0-255) to find the one that performs best according to Otsu's method.

Encoding: Each potential threshold value (an integer from 0 to 255) is represented as a "chromosome" or "individual" in the form of an 8-bit binary list.

Initialization: The algorithm starts with an initial population of 20 random individuals.

Evolutionary Cycle: The algorithm evolves the population over 50 generations. In each generation:

Fitness Evaluation: Each individual's binary string is converted to its integer equivalent, and its fitness is calculated using the Otsu's method function.

Selection: Parents are chosen for reproduction using Tournament Selection. A small, random subset of the population competes, and the fittest individual from this group is selected.

Elitism: The single best individual from the current generation is preserved and automatically passed to the next generation, ensuring progress is never lost.

Crossover: Two parent individuals create a new "child" using single-point crossover, where the binary strings of the parents are split at a random point and recombined.

Mutation: Each bit in the new child's binary string has a small chance (0.2%) of being flipped. This maintains genetic diversity and helps the algorithm explore the entire search space.

Termination: After 50 generations, the algorithm concludes. The best-performing individual (the one with the lowest Otsu variance) across all generations is selected as the optimal threshold.

🚀 How to Use
This project is implemented in a Jupyter Notebook (.ipynb) file.

1. Dependencies
This script requires the following Python libraries. You can install them using pip:

pip install numpy Pillow matplotlib

NumPy: For numerical operations on the image array.

Pillow (PIL Fork): For opening, converting, and resizing the image.

Matplotlib: For visualizing the results.

2. Running the Code
Place the image you want to process in the same directory as the notebook or provide the full path.

Open the uas_siskonlanjut.ipynb file in a Jupyter environment.

In the fourth code cell, modify the path_image variable to point to your image file:

path_image = 'your_image_name.JPG' # Change this to your image path

Run all the cells in the notebook.

3. Output
The notebook will print the progress of the Genetic Algorithm for each generation, showing the best fitness score and the corresponding threshold. Finally, it will display a plot comparing the original image with the final binarized image produced using the optimal threshold.

⚙️ Parameters
The Genetic Algorithm's behavior can be tuned by adjusting these parameters at the beginning of the third code cell:

POPULATION_SIZE: The number of individuals in the population (default: 20).

N_GENERATIONS: The number of evolutionary cycles (default: 50).

MUTATION_RATE: The probability of a bit being flipped during mutation (default: 0.002).

TOURNAMENT_SIZE: The number of individuals competing in each selection tournament (default: 5).
