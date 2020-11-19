# Proteogenomics connects somatic mutations in breast cancer

Lucy Lu, Elaine Xu, Xiaoxue Lou

Abstract
------------

For decades, breast cancer rates have risen faster in rich countries than in poor ones. Scientists are beginning to learn more about why, but questions remain unanswered. In this project, we used two datasets: one dataset profiled 77 breast cancer samples, the other one contains detailed information about 106 breast cancers patients. We combined and coded two given datasets by R, focusing on two cancer types of luminal A and luminal B. Compared correlations of proteins by drawing the heatmap and applied Bonferroni correction, we screen out four proteins that are most significant in our target cancer subtypes.

Background and Significance
------------------------------------

Breast cancer is the most prevalent cancer type in women and one of the most common death causes in women worldwide.[1] In 2019, an estimated 268,600 new cases of invasive
breast cancer will be diagnosed among women. Approximately 41,760 women were expected to die from breast cancer in 2019.[2] Breast cancer is a disease with multiple causes due to molecular alterations, cellular composition and clinical outcome which creates a challenge in developing tumor classification. Based on our research, we decided to pick two out of the four main molecular subtypes: Luminal A and Luminal B. By using the known factors and analyzing given data, we want to find out the proteins that are significantly related to the two breast cancer subtypes.

Data
------------
  Our data are provided by Kajot from Kaggle. The data were used to assess how the mutations in the DNA are affecting the protein expression landscape in breast cancer. In the original study, the proteomics data were acquired for 105 tumors. Researchers used dozens of different parameters to assess the quality of people, 28 samples didn't qualify for the requirement and have been removed from the final data.
By observing the two datasets, we found out that the first column of the clinical dataset and the first row of the proteomics dataset both represent the patient ID. Since the protein and patient names are not formatted exactly the same as needed for downstream analysis in two datasets. We first unified the patient ID using the same format and then combined the two datasets by letting the patient ID be the y-axis and let the protein be x-axis. We only keep the data of the level of protein and omit the proteins that have missing data.


Methods and Results
------------

* __Linear Regression__

    We began by using linear regressions to find if there exist relationships between proteins and cancer types. We defined each protein as y variables and cancer types, Luminal A and Luminal B as x variables.After building the linear regression model, we summarized all models and tested hypotheses about each coefficient. We assumed the null hypothesis was the cancer type x and protein y are not associated. 
We assumed the significance level alpha of the test is 0.05. After creating and filtering the p-value table, we found 2416 proteins have significant relationships with Luminal A, 2308 proteins have significant relationships with Luminal B, and 1361 proteins have significant relationships with both Luminal A and Luminal B.

    After ordering the p-value table and subset the data remaining only 50 proteins with the lowest p-value. The smaller the p-value, the stronger the evidence that there exists a relation between the protein and the cancer type. With the top 50 significant proteins being selected, we computed the linear model of each protein of each cancer type. We delivered 100 linear models including 50 Luminal A models and 50 Luminal B models.

* __Correlation Heat Map__

    The correlation heat map was based on two subsetted tables of Luminal A and Luminal B with only 50 least p-value proteins. We generated the correlation table and plotted the heat map of each cancer type. 

    The cluster showed up after we ordered the correlation table of each cancer type. The axis was proteins and the values were correlations for the heat map of Luminal A and Luminal B. A red and blue notation represents a position and negative correlation, respectively. All crosses represent non-significant correlations. Both cancer types show two clusters. We found out the proteins clustered were not the same protein in Luminal A and Luminal B. 
    
* __Bonferroni Correction__

    Bonferroni correction is a statistical method that's been used to control the family-wise error rate with increased numbers of tests. Because of the large number of tests we performed, we want to apply bonferroni correction to control for p-values that simply appeared by chance. 
    
    By building simple linear regression models between all proteins and the two cancer subtypes in the dataset, we identified 50 proteins that are most significant in this study for each sub cancer type. From those two sets of proteins, we identified four proteins that are most significant in both Luminal A, B cancer subtypes: NP_653304, NP_612208, NP_00318, and NP_001257810. 
	  
    For proteins in the left figure, we applied the bonferroni correction to conclude proteins with p-values that are actually significant: after
applied the bonferroni correction, we compared p-values with corrected p-values, that is, calculated by dividing the alpha, 0.05, by the total number of tests performed. Proteins that are significant should have p-values less than corrected p-values after bonferroni correction.

    The result of the application of bonferroni correction on all existing proteins concluded that all four proteins that have significant p-values.

* __Hypothesis Test__

    To determine if there exists any difference in the mean of protein level between Luminal A, B cancer subtypes, we ran t-test for all models. Based on the t-tests, there exists some significant evidence to support the hypothesis that there is a difference in the mean of protein level between Luminal A, B cancer subtypes. 
    
Conclusion
------------
For our project, we first built simple linear regression models by treated proteins as the predictor variables and cancer subtypes as the dependent variables. To simplify the project, we also decided to only focus on the cancer subtypes of Luminal A and Luminal B. Based on the linear regression models, we would pick 50 proteins with most significant p-values from each cancer subtypes, then find the four proteins that are both significant in the two cancer subtypes: NP_653304, NP_612208, NP_003128 and NP_001257810. To reduce the number of p-values that appear by chance, we applied bonferroni correction and concluded that these four proteins have significant p-values that proved the strong relationship between these four proteins and the Luminal A, B cancer subtypes.

We also ran the t-tests for the hypothesis test and determined that there exists some significant evidence to support the hypothesis that there is a difference in the mean of protein level between Luminal A, B cancer subtypes. However, when we looked into the documents listed 100 proteins with their gene names, we couldn't identify the four proteins from the list. The heat map has similar results, where the proteins we studied were not listed as well. We suspect that there may be some human error or other unknown reasons to cause the proteins not being in the documented proteins. Or, the conclusion may simply be that they are part of the proteins or genes that are not listed in the documented source. 
