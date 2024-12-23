---
name: The Mind's Mirror
tools: [PsychoPy, scipy, mne, seaborn, numpy]
image: /assets/mindsmirror.jpg
description: A viual object classifier using brain signals.
# external_url: https://www.google.com
---
# The Mind's Mirror
<p class="text-center">
{% include elements/button.html link="https://github.com/DebDDash/TheMindsMirror" text="Github" style="primary" size="sm" %}
</p>

## Description
This project leverages EEG signals to classify brain responses to visual stimuli using **1D Convolutional Neural Networks (CNNs)**. These networks are well-suited for capturing temporal dependencies in sequential data, making them ideal for analyzing the dynamic nature of EEG signals. To enhance data representation, various feature extraction techniques are employed, including spectral features like power spectral density (PSD) for frequency-domain analysis, time-domain features such as mean and variance, and advanced statistical measures to quantify the complexity and patterns within the signals.

The ability to classify EEG responses based on visual stimuli holds significant potential. It provides valuable insights into brain activity patterns, aiding the study of neural functions, cognitive processes, and neurological disorders. In healthcare, this capability could transform diagnostic methods, enabling personalized treatment protocols and advancing our understanding of how the brain processes visual information.

## Experiment Description
The experiment involves displaying 10 numbers (0-9) and one non-numerical image in a random sequence, each for 5 seconds. To ensure attention, a cross will randomly appear on the screen. Clicking the cross returns it to the center, and clicking again reveals the image, keeping participants engaged. An EEG device with four electrodes on the head and two behind the ears was used for recording brain activity.

### Preprocessing:

1. **Normalization** 
2. **Interpolation:** To ensure consistency and comparability between the datasets from different devices, the data was resampled using linear interpolation.
3. **Bandpass Filtering:** It selectively allows a range of frequencies to pass through while attenuating frequencies outside this range.
4. **Time Frequency Plots:** For a more comprehensive understanding of the data characteristics.

<p align = "center">
    <img src="/assets/tfplot.png" width= "80%"/>
</p>

## Data sources
We collected the data. Please find more information [here.](https://github.com/DebDDash/TheMindsMirror/tree/main/Week%203%20Data%20Collection/data_collected)

The dataset comprises recordings from over **20 trials**, collected using an EEG device with four active electrodes placed to target the optical regions of the brain.

## Data augmentation
1. **SMOTE :** It generates synthetic data by selecting random samples from the minority class and identifying their k-nearest neighbors. It then combines the selected sample with a randomly chosen neighbor to create synthetic data points.
2. **Time Slicing :** This involves selecting N trials and make every trail into N equal time slices. Then, will generate a new trial by recombining using one time slice from each of the selected trials in an order.
3. **Bootstrap Sampling :** It is a technique used to estimate the distribution of a statistic (like mean, median) from a dataset by drawing random samples with replacement.
<p align = "center">
    <img src="/assets/dataaug.png" width= "80%"/>
</p>

## Classification
 1. **1D CNN :** It is designed to process sequential data like time-series or signals by applying convolutional filters along one dimension to capture temporal or spatial dependencies. It is suitable for classifying brain signals in this experiment as it efficiently learns patterns and features from the sequential data, distinguishing between numeric and non-numeric stimuli.

##  Feature Extraction
 1. **Auto Correlation Method**
 2. **STFT**
 3. **DWT**
    

