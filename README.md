# HQAN Hackathon: Team 3

Here is a list of all our attempts to beat the Polyadic Quantum Classifier (https://arxiv.org/abs/2007.14044) using different circuits and methods. A classical machine learning method can also be found in the source/classical/ directory.

## COBYLA-based circuits
Any algorithm that uses a quantum circuit defined by features and parameters that outputs a class. The parameters are optimized by using the COBYLA algorithm on the relevant loss function. These algorithms include: 
- The original quantum circuit from the paper:

![iris_circuit](https://user-images.githubusercontent.com/49004387/177741855-f2b7559c-db8d-4847-a29d-4423fe8ae223.png)

- An extended circuit with increased depth over the original:

![iris_ext_circuit](https://user-images.githubusercontent.com/49004387/177741894-ad64a0e0-d905-497b-bc4a-6eec6060795f.png)

- A QCNN approach (https://arxiv.org/abs/1810.03787) to introduce nonlinearities into the circuit.

![qcnn_circuit](https://user-images.githubusercontent.com/49004387/177736899-82d6f91b-0b5d-459b-9a5a-095b7a4751c0.png)

Where the parameterized gates are the same as in the Polyadic Quantum Classifier paper, i.e. a Z-rotation in between two half-X gates; F1-F4 are the feature variables, and P1-P12 are the parameter variables.

There is a version of the file which tests all three methods for 30 different random choices of training samples (making sure that the number of training points per class is even), and a version which tests all three methods for 5 different starting parameters in the optimization function. 

## Enhanced SVM
Based on https://arxiv.org/abs/1804.11326, this algorithm uses quantum circuits to generate a kernel matrix between different training vectors, but uses a classical SVM approach to find optimized parameters. This file is designed to generate the full kernel matrix of all points (both training and test data), then slice it based on the training set to quickly optimize the parameters and test new data points without having to recalculate any kernels. This is to allow us to redo the optimization on hundreds of different training sets very quickly, but in general the full kernel matrix is not required to optimize the program based on a single training set.

The kernel is the overlap between two wavefunctions created by a parameterized quantum circuit - the overlap between features [1,2,3,4] and parameters [5,6,7,8] can be computed with the circuit below:

![kernel_circuit](https://user-images.githubusercontent.com/49004387/177737063-ad9e8688-ae01-488a-9611-67ae2c7d7c97.png)

Where ZZ(N) is an Ising rotation e^(i Sz_i Sz_j x_N) for feature/parameter x_N and sites i,j.
