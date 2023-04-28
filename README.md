# OVO Algorithm for Multiclass Classification

This is a Python code that implements the One-Versus-One (OVO) algorithm for multiclass classification. The OVO algorithm trains multiple binary classifiers for each possible pair of classes and then combines their outputs to make the final prediction. In this code, we use the Perceptron Learning Algorithm (PLA) as the binary classifier.

## Requirements

This code requires the following libraries:

numpy

matplotlib

argparse

## Input Data

The code reads in a data file called "data.dat" that contains the following:

X coordinates (float)

Y coordinates (float)

Class labels (int)

The class labels should be integers from 0 to 3.

## Usage

To use the code, simply run the script. The OVO algorithm will be applied to the input data and the resulting decision boundaries will be plotted using matplotlib.

Example usage:

python ovo.py

Authors: Gavin Piva with the help of Proffessor Jingsai Liang

## Implementation

This is an algorithm that takes an image like the one below and uses the process of one-vs-one split a multi-class classification dataset into binary classification problems. The challenges with writing this code were using slices of each point to compare them combine with the PLA implementation. 

![image](https://user-images.githubusercontent.com/65461919/193729616-5d026347-30f1-4bdc-8d2e-c69f1f80d483.png)


## After the code has run it displays and image like the one below.
 
![results](https://user-images.githubusercontent.com/65461919/193730497-d614fc51-405d-414e-8249-7e24a36ce300.png)


