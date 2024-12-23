---
name: The Mind's Mirror
tools: [PsychoPy, scipy, mne, seaborn, numpy]
image: /assets/mindsmirror.jpg
description: A viual object classifier using brain signals. Explored preprocessing techniques on EEG data, including FFT, WT, TFD.
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

**Normalization** 
**Interpolation:** To ensure consistency and comparability between the datasets from different devices, the data was resampled using linear interpolation.
**Bandpass Filtering:** It selectively allows a range of frequencies to pass through while attenuating frequencies outside this range.
**Time Frequency Plots:** For a more comprehensive understanding of the data characteristics.

<p align = "center">
    <img src="/assets/tfplot.png" width= "90%"/>
</p>

## Data sources
We collected the data. Please find more information [here.](https://github.com/DebDDash/TheMindsMirror/tree/main/Week%203%20Data%20Collection/data_collected)

The dataset comprises recordings from over **20 trials**, collected using an EEG device with four active electrodes placed to target the optical regions of the brain.

## Data augmentation


## Conclusion
