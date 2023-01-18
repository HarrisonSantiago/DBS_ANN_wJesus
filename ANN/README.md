## Overview

Code for creating and using ANN-based predictor models. ANN models are created via [TensorFlow](https://www.tensorflow.org/). Models are trained and validated with datasets generated from simulations of the MRG axon model. The optimal hyperparameters are identified through a random search that is parallelized on [HiPerGator](https://www.rc.ufl.edu/about/hipergator/). Two types of models can be created: (1) Classification models, where the output is a prediction of axonal activation, or (2) Regression models, where the output is a prediction of stimulus activation threshold.



## Guide

This is only tested on tensorflow 2.7.0, it should work for other versions but those are not guaranteed. 
If on HPG, use 
```bash
module load tensorflow/2.7.0
```

###To Use
Identify a desired hyperparameter combination, and modify [ann_train.py](ann_train.py) with the these hyperparameter values and the desired datasets with which to train/evaluate. Run while specifying the desired name of the model (should store in the [saved_models](saved_models) directory along with the normalization parameters):

```bash
python ann_train.py <model_name>
```

[ann_predict_lib.py](ann_predict_lib.py) provides a class with functions that make using the ANNs easier. Alternatively, use [custom_predict.py](custom_predict.py). 

Here the ANN should be trained on input/output data from the Comsol model and Neuron(see example data in onedrive). Line 27 in ann_train_lib.py will tell you what each column in that csv means.