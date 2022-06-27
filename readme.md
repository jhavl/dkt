# A Tutorial on Manipulator Differential Kinematics

![PyPI - Python Version](https://img.shields.io/pypi/pyversions/roboticstoolbox-python.svg)
[![QUT Centre for Robotics Open Source](https://github.com/qcr/qcr.github.io/raw/master/misc/badge.svg)](https://qcr.github.io)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

This repository contains a collection of Jupyter Notebooks designed to accompany the two-part Tutorial on Manipulator Differential Kinematics, where each Notebook corresponds to a Section within the Tutorial articles. The notebooks are easily extensible to encourage experimentation. The intention is that you read a Section of the Tutorial and then complete the corresponding Notebook. The articles can be accessed via PDF or rendered as HTML as shown below.

<table style="border:0px">
<tr style="border:0px">
<td style="border:0px">
<img src="https://github.com/jhavl/dkt/raw/main/img/article1.png" width="250">
</td>
<td style="border:0px">
Part I: Kinematics, Velocity, and Applications
<ul>
<li><a href="https://github.com/jhavl/TODO">Access Article PDF from Arxiv </a></li>
<li><a href="https://github.com/jhavl/TODO">Web Page Version of Article</a></li>
</ul>
Jupyter Notebooks:
<ul>
<li><a href="https://github.com/jhavl/dkt/blob/main/Part%201/1%20Manipulator%20Kinematics.ipynb">1 Manipulator Kinematics </a></li>
<li><a href="https://github.com/jhavl/dkt/blob/main/Part%201/2%20The%20Manipulator%20Jacobian.ipynb">2 The Manipulator Jacobian </a></li>
<li><a href="https://github.com/jhavl/dkt/blob/main/Part%201/3%20Resolved-Rate%20Motion%20Control.ipynb">3 Resolved-Rate Motion Control </a></li>
<li><a href="https://github.com/jhavl/dkt/blob/main/Part%201/4%20Numerical%20Inverse%20Kinematics.ipynb">4 Numerical Inverse Kinematics </a></li>
<li><a href="https://github.com/jhavl/dkt/blob/main/Part%201/5%20Manipulator%20Performance%20Measures.ipynb">5 Manipulator Performance Measures </a></li>
</ul>
</td>
</tr>
</table>

<table style="border:0px">
<tr style="border:0px">
<td style="border:0px">
<img src="https://github.com/jhavl/dkt/raw/main/img/article2.png" width="250">
</td>
<td style="border:0px">
Part II: Acceleration and Advanced Applications
<ul>
<li><a href="https://github.com/jhavl/TODO">Access Article PDF from Arxiv </a></li>
<li><a href="https://github.com/jhavl/TODO">Web Page Version of Article</a></li>
</ul>
Jupyter Notebooks:
<ul>
<li><a href="https://github.com/jhavl/dkt/blob/main/Part%202/">1 The Manipulator Hessian  </a></li>
<li><a href="https://github.com/jhavl/dkt/blob/main/Part%202/">2 Higher Order Derivatives  </a></li>
<li><a href="https://github.com/jhavl/dkt/blob/main/Part%202/">3 Analytic Forms  </a></li>
<li><a href="https://github.com/jhavl/dkt/blob/main/Part%202/">4 Null-Space Projection for Motion Control  </a></li>
<li><a href="https://github.com/jhavl/dkt/blob/main/Part%202/">5 Quadratic Programming for Motion Control  </a></li>
<li><a href="https://github.com/jhavl/dkt/blob/main/Part%202/">6 Advanced Numerical Inverse Kinematics  </a></li>
<li><a href="https://github.com/jhavl/dkt/blob/main/Part%202/">7 Quadratic-Rate Motion Control  </a></li>
</ul>
</td>
</tr>
</table>

<br>

## Contents

- [Synopsis](#1)
- [Python Setup Guide](#2)
- [Running Notebooks Locally](#3)
- [Running Notebooks on Google Colab](#4)


<br>

<a id='1'></a>

## Synopsis

Manipulator kinematics is concerned with the motion of each link within a manipulator without considering mass or force. A serial-link manipulator, which we refer to as a manipulator, is the formal name for a robot that comprises a chain of rigid links and joints, it may contain branches, but it can not have closed loops. Each joint provides one degree of freedom, which may be a prismatic joint providing translational freedom or a revolute joint providing rotational freedom. The base frame of a manipulator represents the reference frame of the first link in the chain, while the last link is known as the end-effector.

In Part I of the two-part Tutorial, we provide an introduction to modelling manipulator kinematics using the elementary transform sequence (ETS). Then we formulate the first-order differential kinematics, which leads to the manipulator Jacobian, which is the basis for velocity control and inverse kinematics. We describe essential classical techniques which rely on the manipulator Jacobian before exhibiting some contemporary applications.

In Part II of the Tutorial, we formulate the second-order differential kinematics, leading to a definition of manipulator Hessian. We then describe the differential kinematics' analytical forms, which are essential to dynamics applications. Subsequently, we provide a general formula for higher-order derivatives. The first application we consider is advanced velocity control. In this Section, we extend resolved-rate motion control to perform sub-tasks while still achieving the goal before redefining the algorithm as a quadratic program to enable greater flexibility and additional constraints. We then take another look at numerical inverse kinematics with an emphasis on adding constraints. Finally, we analyse how the manipulator Hessian can help to escape singularities.

<br>

<a id='2'></a>

## Python Setup Guide

The Notebooks are written using Python and we use several python packages. We recommend that you set up a virtual environment/Python environment manager. We provide a guide to setting up Conda below but feel free to use any alternative such as `virtualenv` or `venv`.

The Notebooks have been tested to run on Ubuntu, Windows and Mac OS with any currently supported version of Python (currently 3.7, 3.8 3.9 and 3.10).

### Conda Environment Setup Guide

Download `miniconda` from [here](https://docs.conda.io/en/latest/miniconda.html#latest-miniconda-installer-links) while choosing the link for your operating system and architecture.

Follow the Conda install instructions from [here](https://conda.io/projects/conda/en/latest/user-guide/install/index.html#installation).

In the terminal, make a new `conda` environment. We called our environment `dktutorial` and recommend choosing Python version `3.10`

```bash
conda create --name dktutorial python=3.10
```

We need to activate our environment to use it

```bash
conda activate dktutorial
```

Check out this [link](https://docs.conda.io/projects/conda/en/4.6.0/_downloads/52a95608c49671267e40c689e0bc00ca/conda-cheatsheet.pdf) for a handy Conda command cheat sheet. There is also a ~30 minute Conda Tutorial available [here](https://conda.io/projects/conda/en/latest/user-guide/getting-started.html).

### Python Package Install Guide

We require several Python packages to run the Notebooks. You should activate the Conda environment before completing this stage.

We use IPython and Jupyter notebook

```bash
pip install ipython notebook
```

Install the Robotics Toolbox for Python and associated packages. This will also install other requirements such as Swift and Spatialmath-Python.

```bash
pip install "roboticstoolbox-python>=1.0.1"
```

For Notebooks in Part II we need `sympy` and `qpsolvers`

```bash
pip install sympy qpsolvers
```

<br>

<a id='3'></a>

## Running Notebooks Locally

We have tested the Notebooks in the default Jupyter Notebook web interface and the VSCode Notebook extension.

### Clone the Repository

Firstly, you must clone the repository

```bash
git clone https://github.com/jhavl/dkt.git
cd dkt
```

### Running in the Jupyter Notebook Web Interface

In terminal, activate the conda environment, navigate to the repository folder and run

```bash
conda activate dktutorial
cd "path_to_repo/dkt"
jupyter-notebook
```

### Running in the VSCode Interface

Download and install VSCode from [here](https://code.visualstudio.com/).

Add the `Python` extension, see this [link](https://marketplace.visualstudio.com/items?itemName=ms-python.python) (if not already installed).

Add the `Jupyter` extension, see this [link](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.jupyter) (if not already installed).

From VSCode, select `Open Folder...` and navigate to and select the repository folder. You may be prompted to select if you trust the contents of the folder. **Warning** If you decline to trust the folder, it is unlikely that you will be able to run any of the Notebooks.

After selecting the folder, choose which Notebook you would like to run from the Explorer menu on the left side of the screen.

Once a Notebook is open, you must select the kernel from the `Select Kernel` button in the top right side of the screen. Choose the conda environment we created earlier `dktutorial (Python 3.10.X)`.

<br>

<a id='4'></a>

## Running Notebooks on Google Colab

For the fastest and smoothest experience, it is recommended to run the Notebooks locally. However, most Notebooks can be run online on the Google Colab platform. Click the links in the table below to open on Google Colab:

### Part 1

| Notebook                           | Link                  |
| ---------------------------------- | --------------------- |
| 1 Manipulator Kinematics           | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/jhavl/dkt/blob/main/Part%201/1%20Manipulator%20Kinematics.ipynb) |
| 2 The Manipulator Jacobian         | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/jhavl/dkt/blob/main/Part%201/2%20The%20Manipulator%20Jacobian.ipynb) | 
| 3 Resolved-Rate Motion Control     | Will not run on Colab |
| 4 Numerical Inverse Kinematics     | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/jhavl/dkt/blob/main/Part%201/4%20Numerical%20Inverse%20Kinematics.ipynb) |
| 5 Manipulator Performance Measures | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/jhavl/dkt/blob/main/Part%201/5%20Manipulator%20Performance%20Measures.ipynb) | 

### Part 2

| Notebook                           | Link                  |
| ---------------------------------- | --------------------- |
| 1 The Manipulator Hessian | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/jhavl/dkt/blob/main/Part%201/1%20Manipulator%20Kinematics.ipynb) |
| 2 Higher Order Derivatives | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/jhavl/dkt/blob/main/Part%201/2%20The%20Manipulator%20Jacobian.ipynb) | 
| 3 Analytic Forms | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/jhavl/dkt/blob/main/Part%201/2%20The%20Manipulator%20Jacobian.ipynb) | 
| 4 Null-Space Projection for Motion Control | Will not run on Colab |
| 5 Quadratic Programming for Motion Control | Will not run on Colab | 
| 6 Advanced Numerical Inverse Kinematics | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/jhavl/dkt/blob/main/Part%201/5%20Manipulator%20Performance%20Measures.ipynb) |
| 7 Quadratic-Rate Motion Control | Will not run on Colab |

