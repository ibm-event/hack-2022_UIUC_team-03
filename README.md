# HQAN Hackathon: Team 3

Here is a list of all our attempts to beat the Polyadic Quantum Classifier (https://arxiv.org/abs/2007.14044) using different circuits and methods. A classical machine learning method can also be found in the source/classical/ directory.

## COBYLA-based circuits
Any algorithm that uses a quantum circuit defined by features and parameters that outputs a class. The parameters are optimized by using the COBYLA algorithm on the relevant loss function. These algorithms include: 
- The original quantum circuit from the paper
- An extended circuit with increased depth over the original
- A QCNN approach that uses measurements to make the circuit less trivial
There is a version of the file which tests all three methods for different random choices of training samples (making sure that the number of training points per class is even), and a version which tests all three methods for different starting parameters in the optimization function. 

## Enhanced SVM
This algorithm uses quantum circuits to generate a kernel matrix between different training vectors, but uses a classical SVM approach to find optimized parameters. This file is designed to generate the full kernel matrix of all points (both training and test data), then slice it based on the training set to quickly optimize the parameters and test new data points without having to recalculate any kernels. This is to allow us to redo the optimization on hundreds of different training sets very quickly, but in general the full kernel matrix is not required to optimize the program based on a single training set.
