---
layout: post
title:  "Organ Failure Guideline Review"
categories: jekyll update
---

# Why did I do the guideline review?

There are two main questions I'm trying to find answers for my dissertation: 1) Can we predict the acute onset of severe diseases, and 2) How can those prediction models could improve the quality of the current clinical workflow.

In the most of existing ML methodologies for supervised and semi-supervised learning, they aim to fit a model that minimizes the loss function while satisfying specific constraints, such as regularization or inherent limitation of each modeling approach. When the training is done, perhaps showing enough evidence that the loss is converged, we normally evaluate with traditional ML evaluation criteria, such as AUROC, AUPRC, or F1. This is a common quantitative means to estimate how well the model performs when it encounters new instances.

In addition to those common language talking about model's performance in general, the model need to ensure that predicted risks are concordant to medical consensus. When models can ensure that the predicted risks are concordant to gold standard measures used for diagnoses, it will gain more interst from clinicians, thereby opening up some potential opportunities to deploy ML models in the practice. It will help physicians to understand better on how they should percieve the predicted risk for the practice.

Identifying gold standard measures for diseases are challenging. I personally believe, and was taught, the best source of such information was from clinical guidelines. Still, there are more than one guidelines for one disease. For example, AHA and ESC have separate clinical guideline for acute heart failure. I just briefly went over the contents but I believe they didn't published as one clinical guideline because they might have some conflict on some contents (e.g., the definition of acute heart failure, or level of evidence for recommendations). Therefore, as a researcher who don't have medical training, should decide which guideline I should follow for my research with limited medical knowledge. I believe this heterogeniety for contents in clinical guideline should vary more for diseases that consensus is less converged.

In order to have a level of integrity in the model validation using clinical guideline, it would be preferrable to have a single resource that is validated by domain experts. In AMIA last November, there was a presentation using clinical guidelines from *guidelines.gov* as gold standard for specific diseases, and physicians in the audience didn't raise any concern for the trustworthniess of the source. Therefore, I decided to invest some time for reviewing the usability of guidelines in the website. I went over guidelines for four different diseases I'm interested in: Acute Heart Failure, Acute Respiratory Failure, Acute Liver Failure and Acute Kidney Failure(Injury)

# Overall Contents

For my research, I only went over contents under *major recommendation* section. I focused more on which variables I should consider for clinical validation and what interventions I should see when patients deteriorate due to the disease in interest. I didn't focused on patient management after the onset, and I put more weigh on the initial treatments for the disease onset.

# Acute Heart Failure

https://www.guideline.gov/summaries/summary/48752/acute-heart-failure-diagnosing-and-managing-acute-heart-failure-in-adults?q=acute+heart+failure

## Suggested means of diagnoses
 - According to the NICE guideline chronic heart failure:
	 - Patient History
	 - ECG
	 - CXR
	 - Blood test
 - For new suspected acute heart failure:
	 - Suspect AHF when
		 - BNP less than 100 ng/litre
		 - NT-proBNP less than 300 ng/litre
	 - and consider performing transthoracic Doppler 2D echocardiography
	 - Do not routinely offer pulmonary artery catheterisation to people with AHF

## Initial pharmacological treatment
 - Do not routinely offer opiates to people with AHF
 - Offer IV diuretic therapy. Start treatment using either bolus or infusion
	 - Closely monitor renal function, weight and urine output during diuretic therapy
 - Do not routinely offer nitrates for AHF
	 - For people that necessitates intravenous nitrates(e.g., concomitant MI, severe hypotension, or regurgitant aortic or mitral valve disease), closer monitor on BP
 - Do not offer sodium nitroprusside to people w/ AHF
 - Do not routinely offer inotropes or vasopressors to people w/ AHF
 - Consider inotropes or vasopressors for AHF with potentially reversible cardiogenic shock

## Initial Non-pharmacological treatment
 - Do not routinely NI ventilation(CPAP or NIPPV) in people with AHF and cardiogenic pulmonary oedema.
 - If a person has cardiogenic pulmonary oedema w/ severe dysponea and acidaemia, consider starting NI ventilation w/o delay
	 - Acute presentation or
	 - adjunct to medical therapy if the person's condition has failed to respond
 - Consider Invasive ventilation in people w/ AHF that, despite treatment, is leading to or is complicated by
	 - Respiratory failure or
	 - Reduced consciousness or physical exhaustion
 - Do not routinely offer ultrafiltration to people w/ AHF
	 - consider ultrafiltration w/ confirmed diuretic resistance.

## Source to check
Acute heart failure: diagnosing and managing acute heart failure in adults. Full guideline. London (UK): National Institute for Health and Care Excellence (NICE); 2014 Mar. 325 p. (Clinical guideline; no. 187). Available from the National Institute for Health and Care Excellence (NICE) Web site External Web Site Policy.

Acute heart failure: diagnosing and managing acute heart failure in adults. Appendices. London (UK): National Institute for Health and Care Excellence (NICE); 2014 Mar. 497 p. (Clinical guideline; no. 187). Available from the NICE Web site External Web Site Policy.

# Acute Respiratory Failure

https://www.guideline.gov/summaries/summary/50176/btsics-guideline-for-the-ventilatory-management-of-acute-hypercapnic-respiratory-failure-in-adults?q=acute+respiratory+failure

There were two guidelines that meets the criteria and I chose "BTS/ICS guideline for the ventilatory management of acute hypercapnic respiratory failure in adults" over ACR's guideline on acute respiratory illness in immunocompetent patients. I think the former is more focusing on ventilatory management while the latter put more weigh on radiology imaging. Moreover, I should further read about difference between Acute Hypercapnic Respiratory Failure and ARF if there is any. I didn't went over Grade D recommendations. 

There was no mention around pharmacologic treatments for the disease. I think it is either there is no other means to intervene respiratory deterioration or the guideline is solely focusing on ventilatory support.

## Prevention of AHRF in Acute Exacerbation in COPD
 - Controlled oxygen therapy should be used to achieve target saturation of 88% to 92%
 - NIV should be started when pH <7.35 and pCO2 > 6.5 kPa persist or developed despite optimal medical therapy
 - Severe acidosis alone does not preclude a trial of NIV in an appropreate area with ready access to staff who can perform safe endotracheal intubation
 - ABG measurement is needed prior to and following starting NIV
 - CXR is recommended but should not delay initiation of NIV in severe acidosis
 - Advanced age alone should not preclude a trial of NIV
 - Worsening physiological parameters, particularly pH and respiratory rate (RR), indicate the need to change the management strategy. This includes clinical review, change of interface, adjustment of ventilator settings and considering proceeding to endotracheal intubation
 - NIV(Non-Invasive Ventilation) can be discontinued when there has been normalization of pH and pCO2
 - IMV(Invasive Mechanical Ventilation) should be considered if there is persistent or deteriorating acidosis depite attempts to optimize delivery of NIV

# Acute Liver Failure

https://www.guideline.gov/summaries/summary/51036/american-gastroenterological-association-institute-guidelines-for-the-diagnosis-and-management-of-acute-liver-failure?q=acute+liver+failure

## Overall

 All of major recommendations were annotated with 'very-low-quality evidence'
 
 AGA stands for American Gastroenterological Association Institute
 
 Need to review MELD and KCC scores
 
## Testing Criteria
 - ALF patients, AGA suggests testing for herpes simplex virus and treatment of patients with herpes simplex virus
 - In immunocompetent patients w/ ALF, AGA suggests against routinely testing all patients for varicella zoster virus
 - In patients presenting with ALS, AGA suggests using Model for End-Stage Liver Disease (MELD) score rather than Kings Colleage Criteria(KCC) as a prognostic scoring system
 - AGA suggests against the routine use of liver biopsy
 - AGA suggests autoantibody testing be performed
 - AGA suggests against the empiric use of treatments to reduce intracranial pressure(ICP)
 - In patients presenting w/ acetaminophen-associated ALF, AGA recommends the use of N-acetyl cysteine in acetaminophen-associated ALF

# Acute Kidney Injury(Failure)

https://www.guideline.gov/summaries/summary/47080/acute-kidney-injury-prevention-detection-and-management-of-acute-kidney-injury-up-to-the-point-of-renal-replacement-therapy?q=acute+kidney+injury

## Detecting AKI in line with RIFLE, AKIN or KDIGO definitions
 - Rise in serum creatinine of 26 micro mol/litre or greater within 48 hours
 - 50% or greater rise in serum creatinine known or presumed to have occurred within the past 7 days
 - A fail in urine output to less than 0.5 ml/kg/hour for more than 6 hours in adults

## Identifying the cause of AKI
 - Urinalysis
	 - Urine dipstick
 - Ultrasound

## Managing AKI
 - Relieving Urological Obstruction
	 - Nephrostomy or stenting
 - Do not routinely offer loop diuretics to treat AKI
 - Consider loop diuretics for treating fluid overload or oedema while:
	 - Patients are awaiting renal replacement therapy, or
	 - Renal function is recovering in patients not receiving renal replacement therapy
 - Do not offer low-dose dopamine to treat AKI
 - Monitor eGFR. Conisder referral to a nephrologists when eGFR is 30 ml/min/1.73 m^2 or less in adults


# Reflection

## Overall
 - There are some ways to visualize predicted risks vs. variables. I'm considering adopting one of two visualization other researchers used for the following publications
	 - Caruana R, Lou Y, Gehrke J, Koch P, Sturm M, Elhadad N. Intelligible models for healthcare: Predicting pneumonia risk and hospital 30-day readmission. InProceedings of the 21th ACM SIGKDD International Conference on Knowledge Discovery and Data Mining 2015 Aug 10 (pp. 1721-1730). ACM.

![Caruana Image]({{ "/assets/2017-11-21_1.png" | absolute_url }})

	 
	 - Suresh H, Hunt N, Johnson A, Celi LA, Szolovits P, Ghassemi M. Clinical Intervention Prediction and Understanding using Deep Networks. arXiv preprint arXiv:1705.08498. 2017 May 23.


![Suresh Image]({{ "/assets/2017-11-21_2.png" | absolute_url }})