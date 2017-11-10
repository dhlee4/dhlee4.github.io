#AMIA Reflection

 - It looks like CRF is one of the common method used in NLP. Need to organize differences between HMM, CRF and other commonly used ML approaches, such as Yuan Lao's paper.
 - Open source tool for Text annotation viewer via XML or JSON(Probably XML would have better fit). If not, let's make it.
 - There was a mention that using ICD 9 code as gold standard might make us to have high PPV markers but specificity might not as high as we expected.
 - There are some clinical benefit on decreasing the number of charts that needs to be reviewed.
 - Risk prediction model can be used on billing time. Curation and verification can be done by coders. Compared to the MDs, it might be easier to be pushed.
 - Based on the P(Death|Risk) we have, it might have better utility to have P(Death|Risk predicted, Discharge Location). Medical service as a feature might have some generalization when used them as features.
 - Turn over P(Risk|Component) to P(Component|Predicted Risk). If constraints them by predicted risk, the plot might bring some interpretable plots as Riche Caruana showed in the presentation.
 - Generative model can actually generate the data and they might deviate the HIPAA compliancy. GAN and URF to generate data??
 - Existing NLP Corpora: Cincineti Corpora or I2b2 with DUA
 - Statin is known to have high ADR?
 - Segment LSTM based on category. Deploy different LSTM for different category. Merge them using maxpool
 - Use Convolution on word embedding
 - Attention on RNN, might can detect some emphasis on time-series modeling. Interpretation can be done like 'this time series have the most importance on XXX prediction'
 - Change order set default based on the predicted risk. 
	 - Changing some of the stages as default would lower burden and shorten time for order entry and clinicians could do something meaningful the hours besides.
	 - In the model, if P(adverse events|observation) <<<< p(adverse events|!Observation), add them as default. Or check whether it is concordant or not. 
	 - High predicted risk->saw measures in the order entry->death or not death?
	 - High predicted risk->Not saw lab order in the order set->Death or not death?

 - Yiz2014@cornell.edu -> click analysis on defaulting some of the items
 - SNOMED is better than ICD9?
 - IBM did our lambda approach with LASSO
 - Does MIMIC has DNR/DNI directives? Organ Donor?
 - How actually GB handles missing data? did they just saw the missing value as binarization?
 - Again, predicting the need of lab test based on the risk predicted.
 - Physicians like to see some of prediction around grey area. Physicians know how to deal with High predicted probability patients without watching the probability when using it as direct decision making tools.
 - 6-12 month outcome prediction can be used to set DNR directives, preventing life-sustainment when patients admitted without directive instruction.
 - CMS has medical spending informations
	 - Andrew Placona presentation
 - Find some indication that patient's body can't sustain patients by itself.
 - Bootstrap for validation
 - Model caliburation is needed, if the model is trained for old data, the accuracy drops as the time passes.
	 - Caliburation drift
	 - What is the right time for model update then?
	 - 

#Suggestion on SCCM Presentation
 - Start with Case. it is the comfortable way to start pt in their perspective.
 - Key points
	 - How can it help clinical workflow?
	 - How can it help us to do the better research?
	 - How does this improve the quality of care?
	 - How does this improve operation cost?


#IDEA
 - Use generative model to generate data
 1. Generative model on data in HIPAA compliant site
 2. Move the generative model trained
 3. Move to cloud site.
 4. Generate data.
 5. Train model
 6. Move to HIPAA Site
 7. Additional Optimization(Few time)
 8. Evaluation and Validation on HIPAA site.



