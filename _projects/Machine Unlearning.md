---
name: Machine Unlearning
# tools: [Support, Author, VVG]
image:
description: Implemented fine-tuning for unlearning data subsets, strengthening model privacy and security.
# external_url: https://github.com/yousinix
---
# Machine Unlearning
<p class="text-center">
{% include elements/button.html link="https://github.com/DebDDash/MachineUnlearning" text="Github" style="primary" size="sm" %}
</p>

## Description
This project explores machine unlearning, a paradigm that enables machine learning models to selectively forget specific training data points while preserving their performance on the rest of the dataset. The method is particularly relevant for applications requiring data privacy.

## Dataset
Images used were from CIFAR10 Dataset.Each image is represented as a 32x32x3 tensor.
<p align = "center">
    <img src="/assets/cifar10.png" width= "60%"/>
</p>
The dataset is divided into two primary subsets:
1. Forgotten Data: Subset of the dataset to be unlearned.
2. Retained Data: Subset of the dataset that remains in the model's memory.

## Model training and workflow
1. Initial model training : A machine learning model (e.g., neural network) is trained on the complete dataset.
2. Unlearning Process: A selective forgetting mechanism is applied by modifying the model’s weights or using influence functions and gradient-based updates to neutralize the impact of forgotten data
3. Fine-Tuning with Retained Data: The model is re-trained or fine-tuned on the retained dataset to recover performance where necessary.

## Evaluation
Membership Inference Attack is a way to determine whether a particular sample was part of the training dataset used to train a machine learning model.MIA calculates the loss for both the training and test datasets, with lower losses indicating higher confidence that the data was part of the training set. By plotting the loss distributions, distinct patterns emerge for training and test sets, showing the model's confidence.
<p align = "center">
    <img src="/assets/loss.png" width= "60%"/>
</p>
 Higher MIA accuracy indicates the model retains information from the forget set, while lower accuracy suggests effective unlearning.After fine-tuning to unlearn the forget set, the MIA accuracy dropped, indicating reduced ability to differentiate between forgotten and unseen data. Histograms of the forget and test sets became more similar, confirming the unlearning process was effective.
 <p align = "center">
    <img src="/assets/unlearning.png" width= "60%"/>
</p>

## Conclusion
The machine unlearning approach implemented in this code demonstrates a balance between compliance and efficiency. By enabling selective forgetting, it provides a scalable solution to meet privacy and adaptability demands
