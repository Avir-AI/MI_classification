# EEG Motor Imagery Analysis with Machine Learning Techniques

This repository contains the implementations from my internship project at Avir AI Center and was completed in the last week of July 2024. This project marks my first hands-on experience in training a machine learning model using raw EEG data.

## Table of Contents
1. [Introduction](#introduction)
2. [Project Description](#project-description)
3. [Methodology](#methodology)
4. [Dataset](#dataset)
5. [Implementation](#implementation)
6. [Results](#results)
7. [Conclusion](#conclusion)
8. [References](#references)

## Introduction

This project explores the application of deep neural networks in analyzing EEG signals for motor imagery tasks. The focus is on classifying motor imagery using EEG signals, leveraging techniques like Common Spatial Patterns (CSP) for feature extraction and Linear Discriminant Analysis (LDA) for classification.

## Project Description

### Abstract
The classification of motor imagery using EEG signals has gained significant attention due to its potential applications in Brain-Computer Interfaces (BCIs) and neurorehabilitation. This project addresses the challenge of motor imagery classification, utilizing a dataset that includes four types of motor imagery: imagined thumb movements, arm movements, foot movements, and a no-movement class.

### Signal recording protocol

I utilized the BCI Competition II dataset, which comprises EEG signals from 15 healthy right-handed individuals (5 women and 10 men) with an average age of 31 years were recorded. The signal recording system used 64 channels with a sampling frequency of 2400 Hz, and a power line interference filter was active during data recording. The ground electrode of the signal acquisition system was placed on the forehead, and one of the channels served as a reference channel attached to the right ear (which has been removed from the dataset, leaving 63 channels of data). All electrode signals were filtered with a low-pass filter with a cutoff frequency of 50 Hz. The electrode arrangement by name and row number in the data matrix is shown in Figures 1 and 2, respectively.

### Test protocol

Person 1 is seated comfortably in a chair, with a screen positioned half a meter in front of them. During the test, the person must perform specific movements using their right thumb, right foot, and right arm, as indicated by the test protocol shown in Figure 3.

The test begins with a "+" sign displayed at the center of the screen for 2 seconds. During this time, the individual should clear their mind and prepare to observe the next signal. After the 2 seconds, one of three possible signs appears, each indicating a specific movement to be performed. These signs correspond to the target organs: the right thumb, right foot, or right arm.

Following the appearance of the sign, the word "Go" is displayed for 0.5 seconds, signaling the individual to execute the indicated movement within the next 3 seconds. The person should perform the movement slowly and accurately, according to the type of sign shown.

### Data Format
Each of the 15 individual's data provided in a file named `subject_i.mat`. In each file, there is a structure variable containing two fields: `train` and `test`.

The `train` field is a cell array of size 1x4, where each cell contains EEG signals recorded for 3 seconds from the moment the word "Go" appears. The data in these cells correspond to different movement classes:

1. **Cell 1**: EEG data during arm movement (class 1)
2. **Cell 2**: EEG data during thumb movement (class 2)
3. **Cell 3**: EEG data during foot movement (class 3)
4. **Cell 4**: EEG data during rest (non-moving) state (class 4)

Each cell's data is stored as a three-dimensional array. The dimensions represent the following:

- The first dimension corresponds to the EEG channels.
- The second dimension contains the EEG sample points.
- The third dimension indicates the number of trials for each movement class.

The `train` data will be used to train the algorithm, while the `test` data will be used to evaluate its performance.


## Methodology

### Common Spatial Patterns (CSP)
CSP is a feature extraction method commonly used in EEG signal analysis. It helps in enhancing the signal-to-noise ratio for motor imagery tasks by maximizing the variance for one class while minimizing it for the other.

### Linear Discriminant Analysis (LDA)
LDA is a classification method that finds the linear combination of features that best separates two or more classes. In this project, we implemented a binary LDA classifier to differentiate between the motor imagery tasks.

### Leave-One-Out Cross-Validation (LOO)
We employed LOO as our cross-validation method, which is a standard approach in EEG signal analysis. It involves using one trial as the test set and the remaining trials as the training set, iterating over all trials.

## Implementation

The implementation is done in Python, utilizing libraries such as NumPy, SciPy, and Scikit-learn for data processing, feature extraction, and model training. The code is organized into modules that handle data loading, preprocessing, feature extraction using CSP, and classification using LDA.

## Results

The results section provides a detailed analysis of the classification performance, including accuracy, precision, recall, and other relevant metrics. Graphs and figures illustrating the classifier's performance across different subjects and tasks are included in the full report.

## Conclusion

This project demonstrates the feasibility of using deep neural networks and traditional machine learning techniques for EEG signal analysis in motor imagery classification. The findings contribute to the development of more efficient BCIs and neurorehabilitation tools.

## References

1. [BCI Competition IV 2a Dataset](http://www.bbci.de/competition/iv/)
2. Relevant literature and prior research studies are detailed in the full project report.

---

Feel free to customize this README further based on the specific details and outcomes of your project. Including any images, graphs, or additional links can also enhance the comprehensiveness of the document.
