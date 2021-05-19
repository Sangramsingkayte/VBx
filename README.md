
# VBHMM x-vectors Diarization (aka VBx)

Diarization recipe for CALLHOME, AMI and DIHARD II by Brno University of Technology. \
The recipe consists of 
- computing x-vectors
- doing agglomerative hierarchical clustering on x-vectors as a first step to produce an initialization
- apply variational Bayes HMM over x-vectors to produce the diarization output
- score the diarization output

More details about the full recipe in\
F. Landini, J. Profant, M. Diez, L. Burget: [Bayesian HMM clustering of x-vector sequences (VBx) in speaker diarization: theory, implementation and analysis on standard tasks](https://arxiv.org/abs/2012.14952)

If you are interested in the original version of VBx (prepared for the Second DIHARD Challenge), please refer to the [corresponding branch](https://github.com/BUTSpeechFIT/VBx/tree/v1.0_DIHARDII).\
If you are interested in the VBx recipe prepared for the track 4 of VoxSRC-20 Challenge (on VoxConverse), please refer to the [corresponding branch](https://github.com/BUTSpeechFIT/VBx/tree/v1.1_VoxConverse2020).



## Usage
To run the recipe, execute the run scripts for the different datasets with the corresponding parameters. Please refer to the scripts for more details. The CALLHOME and DIHARD II recipes require the corresponding datasets and the paths need to be provided. For AMI, the recordings need to be downloaded (for free) but the VAD segments and reference rttms are obtained from [our proposed setup](https://github.com/BUTSpeechFIT/AMI-diarization-setup).

This repository has x-vector extractors already trained to function as a standalone recipe. However, the recipes for training the extractors can be found [here](https://github.com/phonexiaresearch/VBx-training-recipe).



## Getting started
We recommend to create [anaconda](https://www.anaconda.com/) environment
```bash
conda create -n VBx python=3.6
conda activate VBx
```
Clone the repository
```bash
git clone https://github.com/BUTSpeechFIT/VBx.git
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

## Citations
In case of using the software please cite:\
F. Landini, J. Profant, M. Diez, L. Burget: [Bayesian HMM clustering of x-vector sequences (VBx) in speaker diarization: theory, implementation and analysis on standard tasks](https://arxiv.org/abs/2012.14952)



## Results
We present here the results of our systems for the different datasets and different evaluation protocols. A more thorough discussion on the protocols and results can be found in the paper. All results are obtained using oracle VAD.

```
CALLHOME                         DIHARD II
-----------------                -------------------------
Protocol    DER                  Protocol        DER
Forgiving   4.42	                      dev    eval
Fair        14.21                Full        18.19   18.55
Full        21.77                Fair        12.23   12.29

AMI beamformed                   AMI Mix-Headset
-------------------------        -------------------------
Protocol         DER             Protocol         DER 
             dev     eval                     dev     eval
Forgiving    2.80    3.90        Forgiving    1.56    2.10
Fair        10.81   14.23        Fair         9.68   12.53
Full        17.66   20.84        Full        16.33   18.99
```


## License

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at http://www.apache.org/licenses/LICENSE-2.0 Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.
