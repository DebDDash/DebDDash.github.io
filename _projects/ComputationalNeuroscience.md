---
name: Computational Neuroscience
# tools: [Ignore me]
image: 
description:  Investigate the structure of mouse social behaviour through a resident-intruder assay
# external_url: https://www.google.com
---
# Computational Neuroscience
<p class="text-center">
{% include elements/button.html link="https://github.com/DebDDash/BCS_Introductory_Comp_Neuro/blob/main/Mini_Project_BCS.ipynb" text="Github" style="primary" size="sm" %}
</p>

## Description
This code is adapted from a notebook created by Dipam Chakraborty at AIcrowd for the [Multi-Agent Behavior Challenge.](https://www.aicrowd.com/challenges/multi-agent-behavior-representation-modeling-measurement-and-applications)

## Data sources
The [CalMS21 dataset](https://data.caltech.edu/records/1991) is hosted by Caltech.
The dataset files are stored as json files. For ease of handling, it was first converted to .npy files which contained 32 features.

## Dataset specifications
The dataset includes `training_data` and `test_data`, each as dictionaries with Sequences representing resident-intruder assays. Each Sequence contains:
### Fields
1. **`keypoints`**: Tracked body part locations for two mice using a Stacked Hourglass network.  
   - **Dimensions**: (# frames) x (mouse ID) x (x, y) x (body part)  
   - **Units**: Pixels, relative to image size (1024 x 570).
2. **`scores`**: Confidence estimates for `keypoints`.  
   - **Dimensions**: (# frames) x (mouse ID) x (body part)  
   - **Range**: 0 (low) to 1 (high).
3. **`annotations`**: Behavior IDs for each frame, provided by experts.  
   - **Dimensions**: (# frames).
4. **`metadata`**: Includes `annotator_id` (integer) and `vocab` (behavior-to-ID mapping).
#### `taskprog_features`
Includes pre-computed `features` from a task-programming model.  
- **Dimensions**: (# frames) x (feature dim = 32).
#### Notes
- **Mouse 0**: Resident (black); **Mouse 1**: Intruder (white).  
- **Tracked Body Parts** (7): Nose, left ear, right ear, neck, left hip, right hip, tail base.

    
##  Conclusion
