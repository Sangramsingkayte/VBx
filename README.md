
# VBHMM x-vectors Diarization (aka VBx)

Diarization recipe for CALLHOME. \
The recipe consists of 
- computing x-vectors
- doing agglomerative hierarchical clustering on x-vectors as a first step to produce an initialization
- apply variational Bayes HMM over x-vectors to produce the diarization output
- score the diarization output

More details about the full recipe in\
F. Landini, J. Profant, M. Diez, L. Burget: [Bayesian HMM clustering of x-vector sequences (VBx) in speaker diarization: theory, implementation and analysis on standard tasks](https://arxiv.org/abs/2012.14952)


## Usage
I run the recipe, execute the run scripts for the different datasets with the corresponding parameters. Please refer to the scripts for more details. The CALLHOME recipes require the corresponding datasets and the paths need to be provided.

This repository has x-vector extractors already trained to function as a standalone recipe. However, the recipes for training the extractors can be found [here](https://github.com/phonexiaresearch/VBx-training-recipe).



## Getting started
We recommend to create [anaconda](https://www.anaconda.com/) environment
```bash
conda create -n VBx python=3.6
conda activate VBx
```
Clone the repository
```bash
git clone https://github.com/Sangramsingkayte/VBx.git
```
Install the package
```bash
pip install -e .
```
Initialize submodule `dscore`:
```bash
git submodule init
git submodule update
```
Run the example
```bash
./run_example.sh
```
The output (last few lines) should look like this
```
File               DER    JER    B3-Precision    B3-Recall    B3-F1    GKT(ref, sys)    GKT(sys, ref)    H(ref|sys)    H(sys|ref)    MI    NMI
---------------  -----  -----  --------------  -----------  -------  ---------------  ---------------  ------------  ------------  ----  -----
demo              7.77  38.23            0.80         0.84     0.82             0.77             0.72          0.60          0.42  1.37   0.73
*** OVERALL ***   7.77  38.23            0.80         0.84     0.82             0.77             0.72          0.60          0.42  1.37   0.73
```


