# HQAN Hackathon: Team 3

Here is a list of all our attempts to beat the Polyadic Quantum Classifier (https://arxiv.org/abs/2007.14044) using different circuits and methods. A classical machine learning method can also be found in the source/classical/ directory.

## COBYLA-based circuits
Any algorithm that uses a quantum circuit defined by features and parameters that outputs a class. The parameters are optimized by using the COBYLA algorithm on the relevant loss function. These algorithms include: 
- The original quantum circuit from the paper
- An extended circuit with increased depth over the original
- A QCNN approach that uses measurements to make the circuit less trivial

## Enhanced SVM
This algorithm uses quantum circuits to generate a kernel matrix between different training vectors, but uses a classical SVM approach to find optimized parameters. 
