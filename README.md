# Predictive Image Regression For Longitudinal Studies with Missing Data

Abstract:
---------
A predictive regression model for longitudinal images with missing data based on large deformation diffeomorphic metric mapping (LDDMM) and deep recurrent neural network. Instead of directly predicting image scans, the model predicts a vector momentum sequence of an baseline image, because it parameterizes the corresponding image sequence and lies in the tangent space of the baseline images, which is Euclidean. A neural network with long term-short memory (LSTM) units is applied to learn the time-varying changes from the vector- momentum sequences, which are generated by using LDDMM. For the baseline image that the vector momenta are associated with, it is encoded by a convolutional neural network (CNN). Both features from the LSTM and CNN are fed into a decoder network to reconstruct the vector momentum sequence, which will be used to deform the baseline image and generate the corresponding image sequence with LDDMM shooting. To handle the missing images at some time points, a mask is adopted to ignore their reconstructions. We show our results on synthetically generated images and the brain MRIs from the OASIS dataset. Our method accurately predicts the spatio-temporal changes in both datasets, irrespective of large or subtle changes in longitudinal image sequences.

Tools Used:
-----------
- Python 2.7
- Keras
- PyCA https://bitbucket.org/scicompanat/pyca.git
- vectorMomentum https://bitbucket.org/scicompanat/vectormomentum

Execution Procedure:
--------------------
- The images used were preprocessed by down-sampling, skull-stripping, intensity normalization to the range [0,1], histogram equalization and co-registration with affine transformations.
- Run CAvmMatching from the vectorMomentum library to record the phi values for every image into a numpy array. It requires a configuration file named matching.yaml from the preprocessing directory, to be provided as a command line argument.
- Next, run prepareData.py from the preprocessing directory. This will prepare data ready for training.
- Finally execute model.py to start with the training and make predictions on the test data.

#### This repository contains code for "Predictive Image Regression for Longitudinal Studies with Missing Data", Conference on Medical Imaging with Deep Learning Conference, 2018.
