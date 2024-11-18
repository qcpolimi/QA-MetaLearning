# QA-MetaLearning

This repository contains the datasets we used in the work: 
"Analyzing the Effectiveness of Quantum Annealing with Meta-Learning".
In particular, we share:
- The dataset of the QUBO instances we generated;
- The dataset of the features used to train the meta-models (Meta-Learning dataset);
- The embeddings of the problems on the Pegasus topology, of D-Wave Advantage6.4;
- The optimal assignments of all small instances, hence their solutions (except for those of Number Partitioning instances, which require too much memory to be shared on GitHub);

If you wish to cite our work, please use the following BibTex format:
```
@article{Pellini2024,
author={Pellini, Riccardo
and {Ferrari Dacrema}, Maurizio},
title={Analyzing the effectiveness of quantum annealing with meta-learning},
journal={Quantum Machine Intelligence},
year={2024},
month={Jul},
day={25},
volume={6},
number={2},
pages={48},
issn={2524-4914},
doi={10.1007/s42484-024-00179-8},
url={https://doi.org/10.1007/s42484-024-00179-8}
}
```


# Installation

We suggest you create an environment for this project using virtualenv (or another tool like conda).
First checkout this repository, then enter the repository folder and run this commands to create and activate a new environment, if you are using conda you can create the environment with all the relevant dependencies in the following way:
```console
conda env create -f environment.yml
```

Then, run the following command to install additional packages:
```console
conda activate QAMetaLearning
pip install dwave-ocean-sdk==6.2.0
```

# How to access the data
## Step 0: unzip the files
Go to the ```data``` folder.
Unzip the ```.zip```files to access the data contained in them.
Do it by using the command:
```
unzip <name>.zip
```
by substituting ```<name>```with the name of the ```.zip```file.

## QUBO instances
All the QUBO instances are saved in folder ```data/qubo_dataset```.
The folder contains a ```.csv``` file for each QUBO instances, where it is saved the QUBO matrix of a certain instance.
The name of these ```.csv``` files is an integer number, which is the ```id``` of a particular instance.
The bindings between such ```id``` number and the instances to which they refer can be seen in file ```data/map_index_to_instance.csv```.
Small instances have ```id``` between 0 and 245, large instances have `id` between 246 and 5359.

## Meta-Learning Dataset
The Meta-Learning dataset contains the features and the labels we computed, for every instance, to train and test the meta-models.
Such dataset is stored in file ```data/metalearning_dataset.csv```.
The first two rows stores the name of the features.
The row of this file represent the features and the labels of a certain instance, identified by the same ```id``` number used in the QUBO dataset.

## Samplesets
The folder ```data/samplesets``` stores the results of the solver we used in the analysis.
Inside this folder, there are other four folder, each one identifies a particular solvers and contains its results.
Of these folders:
- ```QA``` contains the results of Quantum Annealing;
- ```SA``` contains the result of Simulated Annealing;
- ```TS``` contains the results of Tabu Search;
- ```SD``` contains the results of Steepest Descent;

The results of a solver in solving the instance identified by the number ```id``` are saved the file ```<id>.csv```
Each row contains such a file contains a sample obtained with the solver, plus the related values of the cost function.

In folder ```QA```and ```TS```, we saved also the hyperparameters of these solvers that we used to solve the instances.
Such files are saved into folder ```data/samplesets/<solver>/hyperparameters/<small or large>/hyperparameters.csv```.
We distinguish the hyperparameters in those used to solve the large instances and the small instances.
In file ```hyperparameters.csv```, each row contains the hyperparameters used to solve the instances of a certain problem class.

## Embeddings of QUBO Instances
The folder `data/embeddings` contains the embeddings used to map QUBO instances on the topology of D-Wave Advantage6.4 Quantum Annealer.
The file `<id>.csv` in this folder identify the embedding of instance `id`.
Each row of this file represent the list of qubits on which a certain variable of the problem is mapped.



