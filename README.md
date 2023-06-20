# Sample Tensorflow Project setup for Apple Silicon

This provides a sample project that uses Tensorflow Datasets and Tensorflow on MacOS, along with Tensorflow
Metal acceleration.

## Motivation

Setting up of Conda dependencies on Apple Silicon (M-series chip devices) has been traditionally very difficult. Using this repo, we hope to
de-mystify and simplify the setup of Tensorflow environments on Apple ARM architecture.

## Prerequisites - MacOS

This setup is catered for Apple Silicon architecture users on MacOS.
For Windows or Linux, there may be a separate set of steps.

1. Ensure that you have [conda](https://conda.io/projects/conda/en/latest/user-guide/install/macos.html) installed.
  To verify this, run this command:

  ```bash
  conda --version

  #output: conda {version} i.e., conda 4.13.0
  ```

2. Ensure [`miniforge`](https://github.com/conda-forge/miniforge) has been installed. This enables the installation of packages compiled for Apple Silicon.

## Setup - YAML - MacOS

Run these commands in this sequence:

1. Set up the conda environment.

```bash
conda env create -f environment.yml
```

This should give you a functional environment. To use, simply run:

```bash
jupyter notebook
```

Or, you can use the kernel in VSCode.

1. `code .`
2. Open the `plant_diseases/detect_plant_diseases.ipynb` notebook.
3. <kbd>Cmd+Shift+P</kbd>
4. `>Python: Select kernel`
5. Select the conda environment we just created, "`tf-mac`"

## Setup - Command Line - MacOS

Follow these steps on the command line:

```bash
#0 - If Xcode tools have not yet been installed
xcode-select --install

#1 - create the conda environment (Python 3.8)
conda env create --name tf-mac python=3.8

#2 - activate the environment
conda activate tf-mac

#3 - Install Tensorflow-MacOS
conda install -c apple tensorflow-deps

# IMPORTANT: `pip` packages
pip install tensorflow-macos
pip install tensorflow-metal

#4 Install Jupyter Notebook, Pandas, numpy, matplotlib
conda install -c conda-forge -y pandas jupyter numpy matplotlib

#5 Install Tensorflow Datasets with `pip`
pip install tensorflow_datasets
```

When you're done, you can export the environment for sharing:

```bash
conda env export > environment.yml
```
