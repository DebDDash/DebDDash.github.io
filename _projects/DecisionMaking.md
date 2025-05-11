---
name: Decision Making
tools: [mne,sklearn,numpy]
image: /assets/decision.png
description: Predict trait anxiety levels using a combination of behavioral patterns and EEG signals collected during a decision-making game.

---
# Decision Making in a foraging task
<p class="text-center">
{% include elements/button.html link="https://github.com/DebDDash/BSE662Decision_Making" text="Github" style="primary" size="sm" %}
</p>

# Problem Statement
Trait anxiety significantly impacts cognitive processes like decision-making, attentional control, and emotional regulation. While tools like the State-Trait Anxiety Inventory (STAI) offer psychological insight, they lack the neurophysiological depth needed for computational psychiatry.
This study integrates EEG data, game-based behavior, and neurophysiological signals (e.g., cortisol, norepinephrine) to build models capable of distinguishing trait anxiety patterns in naturalistic settings.Foraging tasks simulate real-world decisions under uncertainty, ideal for studying anxiety-related cognitive mechanisms.

# Data Preprocessing
<p align = "center">
    <img src="/assets/preprocessing.png" width= "60%"/>
</p>

# Feature Extraction
- Sample Entropy quantifies the unpredictability of EEG signals by measuring how often patterns of brain activity repeat. Higher SampEn indicates more erratic, less predictable brain activity—often linked to anxious states—while lower SampEn reflects more stable neural dynamics, characteristic of relaxation. This makes SampEn a valuable feature for distinguishing anxious individuals from non-anxious ones.
- ERP features, such as N200, FRN, P300, and LPP, capture time-locked neural responses to specific cognitive and emotional events. By extracting peak and mean amplitudes in relevant latency windows, these components reveal individual differences in attention, emotional evaluation, and error processing—key processes that are often altered in those with high trait anxiety.
- PAC measures the interaction between slower theta waves and faster alpha, beta, or gamma waves. Disruptions in PAC suggest impaired cross-frequency communication, which is crucial for integrating emotional and cognitive information. Abnormal PAC patterns are often seen in individuals with high anxiety, making it a sensitive marker for trait anxiety prediction.
- Alpha coherence between frontal electrodes (F3, F4, Fz) reflects functional connectivity related to emotional regulation and cognitive control. Lower coherence in this band is associated with reduced neural synchrony in frontal regions, often observed in anxious individuals, thus serving as a marker of dysregulated affective and executive processing
- Theta coherence in the frontal cortex indicates how well regions involved in executive control and decision-making coordinate during uncertain situations. Altered theta coherence, whether increased or decreased, can reflect how trait anxiety influences neural communication and decision strategies, especially under stress or ambiguity.

# Feature Dendrograms
Dendrograms were generated for the entire dataset to visualize relationships among features. This analysis aids in identifying clusters of related features, facilitating feature selection, redundancy reduction, and a deeper understanding of the dataset’s underlying structure.
<p align = "center">
    <img src="/assets/dendrogram.png" width= "60%"/>
</p>

# Mediation and Moderation
Mediation and Moderation analysis explored how salivary alpha-amylase (SAA), an index of sympathetic nervous system activity, interacts with theta-gamma coupling—linked to cognitive control and memory—to influence reward outcomes. While visual trends indicated that higher SAA levels may strengthen this relationship (with increasingly steep slopes from low to high SAA groups), statistical testing found no significant moderation effect due to high variability and multicollinearity, limiting interpretability.
<p align = "center">
    <img src="/assets/mediation.png" width= "60%"/>
</p>

# Predicting Trait Anxiety Using ML and DL Models
Trait anxiety was predicted using both traditional machine learning models and deep learning methods like EEGNet. After preprocessing and feature engineering, Random Forest and Gradient Boosting were tested, with Gradient Boosting being more reliable due to less overfitting. EEGNet effectively leveraged spatial-temporal EEG features despite limited data. However, predictions using only frontal EEG bands showed moderate accuracy, indicating that trait anxiety is difficult to decode from EEG alone and may require richer multimodal input or more data.

# Prediction of Stay and Leave Decisions
A multimodal deep learning model combining EEG and behavioral data achieved high accuracy in classifying participants’ decisions to stay or leave in a foraging task. The model used a dual-branch architecture and addressed class imbalance effectively. In contrast, a Random Forest model trained on SMOTE-balanced data also performed reasonably well, with feature importance analysis highlighting key EEG and behavioral predictors. A simpler entropy-based neural network also showed good performance, validating the predictive power of EEG entropy features.

# Prediction of Game Parameters and Behavioral Data from EEG Features
EEG-derived features, especially entropy, were used to predict behavioral metrics like patch switching frequency, cortisol variation, and reaction time. EEG entropy successfully predicted patch switching frequency, linking higher entropy to exploratory behavior. However, attempts to predict cortisol variation showed weak results due to low correlation and limited data. Reaction time predictions using a feedforward neural network with advanced regularization showed promising architecture, though evaluation results weren’t detailed. Overall, EEG features can reflect some behavioral tendencies, but are insufficient alone for reliable physiological predictions.
<p align = "center">
    <img src="/assets/results.png" width= "60%"/>
</p>
