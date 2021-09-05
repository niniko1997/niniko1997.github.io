---
title: "Parsimony and Machine Learning in Neuroimaging"
excerpt: "Predicting cognitive impairment using machine learning methods on MRI images<br/><img src='/images/portfolioOne.png'>"
collection: portfolio
---

## Background

The brain undergoes changes throughout an individual’s life. With aging in adulthood, the cortex thins, gray matter decreases and CSF volume increases, and subcortical structures and overall brain volume decrease. Changes also occur during development before adulthood.

The modulations and development patterns in adult brains provide the framework for identifying clinically applicable deviations. Studies show that structural and functional developments in the brain relate to cognitive development. Thus brain-based age predictions have the potential to identify and capture aberrant changes from natural brain development.

![Brain Scan](/images/brainScanOne.png "Figure 1")

Figure 1. On the right, a brain with severe dementia is depicted. On the left, a healthy brain is depicted.

![Brain Scan](/images/brainScanTwo.png "Figure 2")

Figure 2. On the right, a senior brain is depicted. On the left, a young brain Is depicted

The present study, seeks to predict chronological age with the application of a more parsimonious version of the structural portion of the machine learning model built in Liem et al. without losing predictive ability. This parsimonious model seeks to improve accuracy and generalizability of previous unimodal models while also being computationally inexpensive for predicting brain age. As with other models, the approach to building a machine learning model seeks to balance difficulty of the problem with the complexity of the model. Creating a model that is parsimonious and does not overfit, while also incorporating information relevant to the target prediction is crucial for optimal model performance and generalizability. The goal of parsimony is to match used features to the most salient characteristics that show changes with aging.

## Data

1. NNDSP data: This dataset contains MRI and fMRI brain scans of healthy controls scanned. This data represents an independent sample collected from individuals across a broad range of ages (ages 5-77). 

2. HCP data: Data used in the preparation of this work were obtained from the [Human Connectome Project](http://www.humanconnectomeproject.org/). The data were already collected before the commencement of this study. This data represents an independent sample collected from individuals across a small age range (ages 22-37).

3. NKI data: The Rockland sample contains MRI and fMRI brain scans from the Enhanced Nathan Kline Institute. The NKI data represents an independent sample collected from individuals across a broad age range (ages 6-85). The NKI dataset can be downloaded from the [Nathan Kline Institute's online repository](http://fcon_1000.projects.nitrc.org/indi/enhanced/data.html}{http://fcon-1000.projects.nitrc.org/indi/enhanced/data.html).

## Methods

![Method](/images/methodOne.png "Figure 3")

Figure 3. For each subject in the NNDSP Data, cortical thickness, cortical surface area and subcortical volume feature vectors are extracted along with white matter, grey matter, CSF and intracranial volume measurements. 2) The feature vectors are concatenated and the volume measurements are concatenated to obtain input data. 3) Data is split into training set and a hold out set. 

### Complex Model
In this study, we took the structural model designed by Liem et al. but trained it on the NNDSP data instead of the LIFE data. The inputs for the complex model were:
1. Cortical thickness at 2,562 vertices for each hemisphere (5,124 vertices total)
2. Cortical surface area at 2,562 vertices for each hemisphere (5,124 vertices total)
3. Subcortical volume for 66 structures

The cortical thickness and cortical surface area measurements were randomly reduced from the original 5,124 vertices to 2,562 measurements from the total freesurfer output.  Thus there were a total of 10,314 ([5,124 vertices * 2 measures] + 66 subcortical) input features used to construct four machine learning models:
1. A unimodal cortical thickness model trained on cortical thickness features via support vector regression
2. A unimodal cortical surface area model trained on cortical surface area features via support vector regression
3. A unimodal subcortical volume model trained on subcortical volume via support vector regression
4. A complex model that stacks the single modal cortical thickness, cortical surface area and subcortical volume models via random forest. This is the model we refer to as the complex model. 

### Simple Model
The simple model attempted to achieve the same predictive ability as the complex model with fewer input features. The four features in this model, white matter fraction, gray matter fraction, CSF fraction and total intracranial volume, were chosen in advance based on evidence in the literature that these measurements are correlated with age. The inputs for the simple model were extracted from FreeSurfer (v5.3) aseg file:
1. White matter fraction, which was calculated from the sum of cerebral and cerebellar white matter measurements for both hemisphere divided by the total intracranial volume.
2. Gray matter fraction, which was calculated from the subcortical gray matter volume measurement divided by the total intracranial volume.
3. CSF fraction, which was calculated from the CSF measurement divided by the total intracranial volume.
4. Total intracranial volume, which is simply extracted from the FreeSurfer aseg file
We built a simple machine learning model with support vector regression on these four features to predict age. This is the model we refer to as the simple model.

![Method](/images/methodTwo.png "Figure 4")

Figure 4. 4) The complex model (blue) is built with single modal cortical thickness, cortical surface area and subcortical volume feature vectors with SVR and then stacked with Random Forest. 5) The simple model (green) is an SVR model on the white matter, grey matter, CSF fraction and intracranial volume measurement inputs. 6) All three models are tested on new data, such as the hold out data and the NKI data.

We applied the complex and simple model to novel data such as HCP and NKI. The purpose of this step was to test the generalizability of each model by evaluating the performance of each model on unseen data. To conclude the analysis, we performed statistical tests and evaluated the predictive ability of each model on out of sample and novel data. Following the construction of the complex and simple models, we evaluated each of our hypotheses. 

## Citation

Liem,  F.,  Varoquaux,  G.,  Kynast,  J.,  Beyer,  F.,  Masouleh,  S.  K.,  Huntenburg,  J.  M.,  Lampe,542L.,   Rahim,   M.,   Abraham,   A.,   Craddock,   R.  C.,   Riedel-Heller,   S.,   Luck,   T.,   Loeffler,   M.,543Schroeter,  M.  L.,  Witte,  A.  V.,  Villringer,  A.,  and  Margulies,  D.  S.  (2017).    Predicting brain-544age  from  multimodal  imaging  data  captures  cognitive  impairment.NeuroImage,  148:179  –545188,  ISSN:1053-8119,  DOI:10.1016/j.neuroimage.2016.11.005,http://www.546sciencedirect.com/science/article/pii/S1053811916306103.
