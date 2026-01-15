# AIML_MiniProjects

A collection of short, self-contained notebooks covering classic ML workflows, generative models, search problems, and a few open-ended explorations. Each notebook is designed to be runnable on a laptop-class machine (CPU is fine unless noted) and to illustrate a specific idea end-to-end.

## Quick Start
- Python 3.10+ recommended. Create a virtual environment, then install common deps: `pip install numpy pandas scikit-learn matplotlib seaborn pillow imageio tensorflow keras openai` (add others as needed per notebook; see notes below).
- Datasets live under `datasets/` and are read with relative paths from each notebook. Keep the repo root as your working directory when running.
- To view TensorBoard logs stored in `activation/`, `optims/`, or `optims2/`: `tensorboard --logdir activation,optims,optims2 --port 6006`.

## Project List

1. **MNIST MLP classifier** ([1.ipynb](1.ipynb))
   Trains a `sklearn.neural_network.MLPClassifier` to classify MNIST handwritten digits and inspects accuracy.

2. **GPT-3 Intellisense** ([2.ipynb](2.ipynb))
   Uses the OpenAI Python SDK to prototype code-completion/intellisense-style prompts.

3. **GPT Coding** ([3. GPT Coding.ipynb](3.%20GPT%20Coding.ipynb))
   Natural-language-to-code experiments (e.g., table generation) with GPT models such as `davinci`.

4. **Naive Bayes digit generator** ([4.ipynb](4.ipynb))
   Fits a Bernoulli Naive Bayes model on MNIST pixel intensities and samples synthetic digits; highlights the limits of this simple generative approach.

5. **Fashion-MNIST DCGAN** ([5.ipynb](5.ipynb))  
   Builds and trains a DCGAN to synthesize clothing images; includes generator/discriminator design, training loop, and sample visualization.

6. **Fashion-MNIST CGAN** ([6.ipynb](6.ipynb))  
   Conditional GAN that generates class-specific fashion items using the label signal during training.

7. **CIFAR-10 CGAN (class-conditional images)** ([7.ipynb](7.ipynb))  
   Conditional GAN on CIFAR-10 that takes a user-selected class (airplane, automobile, bird, cat, deer, dog, frog, horse, ship, truck) and generates matching images.

8. **Fashion-MNIST CNN pipeline** ([8.ipynb](8.ipynb))  
   End-to-end preprocessing, training/validation split, and Keras CNN modeling on Fashion-MNIST (installs `tensorflow`/`keras` inline).

9. **Manual forward/backprop demo** ([9.ipynb](9.ipynb))  
   Implements forward and backward propagation by hand on a tiny regression toy set (fuel, distance → budget) and visualizes the process.

10. **Two-hidden-layer MLP exercise** ([10.ipynb](10.ipynb))  
    Small neural net with two 3-node hidden layers; plots loss over 50 epochs for the provided dataset.

11. **Age detection (Indian actors)** ([11.ipynb](11.ipynb))  
    Loads zipped train/test image data, resizes faces, encodes labels, and trains a Keras model to predict age groups.

12. **Hyperparameter tuning – baseline sweeps** ([12.ipynb](12.ipynb))  
    Systematically varies optimizers, activations, learning rate, regularization, and node counts for the age-detection model; logs runs to TensorBoard.

13. **Hyperparameter tuning – extended sweeps** ([13.ipynb](13.ipynb))  
    Continuation of the tuning workflow with similar search space to refine age-detection performance.

14. **Hyperparameter tuning – learning rate finder** ([14.ipynb](14.ipynb))  
    Adds `keras_lr_finder` to probe learning rates and compares optimizer/activation choices for the age-detection task.

15. **California Housing linear regression** ([15.ipynb](15.ipynb))  
    Cleans and scales the California Housing dataset, fits a baseline linear regression, and reports MAE/MSE/R².

16. **Zomato EDA** ([16.ipynb](16.ipynb))  
    Exploratory analysis of the Zomato restaurant dataset: missing-value checks, numeric/categorical profiling, and basic visualizations.

17. **Water Jug search problem** ([17.ipynb](17.ipynb))  
    Explains the classic 3L–5L jug puzzle and implements BFS search strategies to reach the 4L goal state.

18. **Rat in a Maze (DFS)** ([18.ipynb](18.ipynb))  
    Pathfinding problem where a rat navigates from top-left to bottom-right in a binary maze; uses Depth-First Search to find all valid paths in lexicographic order.

19. **Nepal Earthquake Classification** ([19.ipynb](19.ipynb))  
    Binary classification model to predict major vs. minor earthquakes using the Nepal seismicity dataset; focuses on high-recall detection of major seismic events.

## Data and artifacts
- `datasets/mnist/`, `datasets/fashion-mnist/`, `datasets/california-housing/`, and `datasets/nepal-earthquale/` supply CSVs for the MNIST, Fashion-MNIST, housing, and Nepal earthquake experiments.
- Age detection notebooks expect zipped data at `datasets/agedetectiontrain.zip` and `datasets/agedetectiontest.zip` with `train.csv`/`test.csv` and `Train/`/`Test/` image folders.
- TensorBoard logs from activation/optimizer sweeps are stored in `activation/`, `optims/`, and `optims2/`. Point TensorBoard to these roots to compare runs.

## How to run a notebook
1) Start a fresh virtual environment and install notebook-specific requirements (see the install cells at the top of each notebook).  
2) Open the notebook in VS Code or Jupyter, keep the working directory at the repo root, and run cells top-to-bottom.  
3) For OpenAI examples, export your API key (e.g., `export OPENAI_API_KEY=...`) before running.