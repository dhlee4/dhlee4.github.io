---
layout: post
title: AMIA Reflection
---

*This document is still under revision. I'm not sure when I will do the edit so I'm just posting now.*

I attended AMIA Annual Symposium 2017 at Washington D.C. from November 4-8, 2017. I had an honor to share my work "Clustering Vital Sign Observations Using Unsupervised Random Forest". Besides that, I had an awesome insights from other sessions.

# NLP

I mostly have been working with structured clinical data, which includes labs and vital signs, and simply use extracted medical concepts along with assertions from clinical notes as features to improve the performance of my models. Although I knew HMM, LSTM are common ways to build language models, I wasn't sure what is the **norm** of building such models. It looks like most of the submissions in NLP sessions used Conditional Random Field(CRF) and LSTM with some variations. I have been using LSTM for other experiments but didn't have much chance to go over CRF. I might need to write a post to go over CRF for my personal understanding. Perhaps some comparison between CRF and LSTM would be a good learning experience for me since they are both dealing with sequence data.

While I saw the workshop from Hua Xu and their tool on NLP experiments, CLAMP, I saw they used XML for formatting texts with tags and visualized correspondingly. As I'm currently validate some of my predictions, integrating simplified XML viewers with tags will make my life easier when visually validating clinical notes.I'll go through what is available option for me to use in open source. If the existing tools are too heavy, I might start my own open-source project building a light XML viewer with tagged with concepts. As MIMIC 3 data is currently used under DUA, I might build a demo using MIMIC2 demo dataset, which includes 2000 patients, because it doesn't require any agreement.

Moreover, throughout the session, there were other researchers mentioning about existing NLP Corpora which I can potentially use for other purpose. For example, there were mentions about 'Cincinnati Corpora' and I2B2 dataset under DUA. Moreover, there was interesting poster from University of Antwerp built Q/A system using BMJ Case report. According to the author, the dataset includes the description of case as well as some learning points(e.g., how did this patients recovered or how could we save the patients), which have some potentials around building clinical knowledge base.

Yuan Luo presented his work building a language model using LSTM. He presented some improvements by segmenting the sentences and build RNN using LSTM. This might have some insights on my work because this might indicate not all previous information have relevant effect on the future prediction. Perhaps there should be state-specific progression we need to consider.
Lastly, there were a presentation using attention in sequence model and improving the performance on language model. Of course, the interpretability of RNN is known to be bad. However, if the aim of the model is just find out what time period we should focus, adding linear attention component of modeling might improve the interpretability as we merge the time-dependent states with logistic regression(simply will have a form of auto-correlation)

# Clinical implication
During the session, there was few mentions around using ICD 9 code as gold standard. There were some notion that ICD 9 code might be a marker with high PPV but not that specific.

Moreover, there were some mentions around using SNOMED as annotation instead of ICD9 but I'm not sure which SNOMED people mentioning about. In my knowledge, SNOMED is a clinical terminology, or ontology, including clinical concepts. I should investigate further what this means.

There were some potential engagement points of ML models in clinical informatics. Here are some comments presented in the AMIA:

 - Clinical workfolow 1: There was a presentation predicting 6-12 month mortality based on patient's history. Although modeling approach is not fancy, the implication was noticeable. The presentation showed that there are significant increase on medical spending right before patient's death. This makes sense because most of life-supporting interventions are expensive. However, it turns out that some of the patients actually didn't want to sustain the life-support. However, in the care setting, healthcare prefessionals should practice according to default, which is the life-supporting. The core idea of the work was, if we are able to predict the mortality in 6-12 month, we could get advanced clinical directives(such as DNR/DNI or CMO). They suggests this would decrease unnecessary medical spending significantly.
 
 - Clinical workflow 2: There was a whole session from Wells-Cornell school of medicine about CDS. The main focus was **default**. Among various topic they covered around default, change the default of AM order set was the most interesting presentation for me. Dr. Zhang presented what is the effect of defaulting some of the AM lab order set and went over the cognitive burden on different types of defaulting. As I'm currently working on time-series risk prediction model, I could verify how the patient's risk perceived by caregivers. This can be done by comparing the predicted risk and the elements in the order set. The implication of physician's perception can be evaluated by existing gold standard measures related to patient's severity.

 - Research 1: Most of the ML-driven modeling will assign some sort of scores for the instances that it aims to prioritize. If somehow the proposed model could decrease the number of manual chart review, that might have some benefit in clinical research

 - Research 2: There were a lot of generative models using structured part of data. There was a presentation introducing Random Decision Tree, which I believe the extension of unsupervised way of learning the statistical structure of the dataset and generate synthetic dataset. I think if those generative models generates data and those generated dataset doesn't have to follow HIPAA-compliancy, it would accelerate the ML researches using clinical dataset because most of clinical data cannot get out from DBMS due to the HIPAA compliance. Most of DBMS doesn't have sufficient computational resource to conduct machine learning experiments.

 - Financial: There was a suggestion on deploying ML-driven model on the time of billing. Most of the previous attempts on integrating ML models into clinical workflow have not been successful so far, I think this might be another angle to start deploying model in the workflow. If the predicted models could indicate the likelihood of disease and the current code assigned by medical coders, it would help them to reduce errors and identify some of the documentation they need to discuss with physicians. That will ideally maximize the accuracy of medical claim, which will be win-win between hospital and insurance agencies. This would be easier to implement compared to implementing the ML prediction pipeline in the clinical practice as the current compensation structure cannot compensate physician's hours invested for reviewing ML-driven prediction results.
 
During the session, there was a ADR work related to statin and nobody had rebuttal on it. I assume it is common to see ADRs using Statin. It might be interesting to see whether there is anything I can do.

 
# General perception on physicians' response on ML-driven models
 - There was a mention that physicians are more interested on edge cases in predictions from ML-driven models. One of the audience mentioned that physicians might do better than prediction model when the confidence interval is high. The prediction results will be useful when it properly handles edge cases. I agree with this opinion because most of high confidence predictions are based on some significant distortion on physiologic patterns. Most of the hard decision makings are done in edge cases, or grey area. If the ML-driven models could properly handle various variables that could potentially effect on clinical decision making and provide proper level of interpretability, it will improve the quality of the current clinical practice and perhaps make clinicians to be interested in integrating ML-driven models in clinical workflow.

### Side Notes
 - In Acute Care session, IBM Watson did the similar approach we did on the previous AAAI paper. I'm not sure the internal pipeline of the learning, but it looks like they trained hazard model with LASSO, one hazard ration describing patient's trajectory for each patient. Need to revisit the paper.
 - The presentation using MIMIC introduced some of exclusion criteria that I didn't know there exists, such as Code status and organ donor status. I should check that and exclude those patients for my experiments.
 - There was a mention that Gradient Boosted Tree can handle missing data. I believe the missing data handling is done by feature representation space. I should revisit GBT and see whether there exists specific missing value handling during training phase.
 - It looks like CMS has medical spending information. I should look into the resource and check what is available for my research.
 - I was keep forgetting to conduct bootstrapping for CI calculation. I should definitely include that from my next paper.
 - There was a paper underlining the importance of model caliburation. It showed that the model trained by the old dataset tends to loose its accuracy as the time progresses. It could be interesting if we could evaluate what is the right time for model update or proper strategy on updating model in real clinical setting to maximize clinical utility.


