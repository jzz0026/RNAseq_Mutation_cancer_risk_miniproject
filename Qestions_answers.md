## 1.What features of the data are most important for QC/QA?
a.	Missing data are important to be considered. In this case, drop the columns full of nan for both mRNA expression and mutation sequencing data as well as individuals with labels containing missing data (e.g. Neoplasm Histologic Grade and Patient's Vital Status).

b. Since mRNA expression, mutation sequencing and clinical data would be combined together for modeling, it is important to make sure sample IDs were consistent between each other. Here I noticed only 432 samples existed in all three types of data, so in this study only intersection part among three were selected for further modeling in order to combine all features together.

c. Some outliers could be potential errors during sequencing or sampling. The high variability in clinical population could also cause outliers and affect the performance of models. Here Isolation Forest was applied to drop outliers since it was based on random forest and can handle large, high-dimensional datasets. PCA was then used for visualization of this filtering step. About 10.11% observations were filtered and PCA showed a more acceptable variance than before filtering.

## 2. Generally speaking, what are potential sources of ambiguity arising from your approach?
a. In unsupervised clustering, we assumed each of four features was equally to indicate risk due to limited domain knowledge. However, the four features didn’t correlated closely. Many individuals could have a high cancer grade but low stage and live fairly long after diagnosis, vice versa. They could contribute to risk differently, so it might be worth to changing weight to achieve a better balance of four features for unsupervised clustering. This step is fairly critical since it generate labels for downstream modeling and might a major source of ambiguity.

b. Clinical and sequencing data of human population could be distinct from individual to individual. The sample size we had right now could still be small, could lead to the problem of high variance. Despite the step of feature selection was applied, it could still be lack of enough information from individuals to indicate disease-associated risk, causing the ambiguity in our approach.


c. It could be from lack of environmental data. As we know, phenotype = clinical data + transcriptome + genotype + environmental data. The environmental data could include information of individuals’ diets, life styles, habits and so on, which would have potential affect on causation of cancers.  This could be a big source of ambiguity in our approach. 


## 3. What other data might we collect to enhance risk quantification? What quantitative proof do you have?
a. If we do whole genome sequencing, whole transcriptome and collected more samples of patients, I think it will be greatly helpful to enhance risk quantification. The heatmap of mRNA expression didn’t show any obvious pattern among both features and observations. It confirmed that observations had a high variance and we need a larger sample size. Also, lack of pattern in features could indicate some strong predictors might not be covered in this study and we probably need to include more genes for sequencing.

b. In unsupervised clustering, we have imbalanced classes for four features, especially cancer grade (G1: 14, G2: 227, G3: 205, G4: 76, GX: 5) and stage (T1: 270, T2: 68, T3, 178, T4: 11). For example, most of patients were diagnosed at G2 and G3. Assume we had a native classifier that just randomly predict G2 and G3, it will still achieve an about 80% accuracy. This is pretty common to observed in cancer detection, since many people at late grade were already dead. So increasing samples size will definitely increase statistical power and freedom, leading to achieving a better performance of model. For the clustering step, this imbalance could also cause problem to label risk, since we didn’t have enough data in these categories. So it will be good that we can collect more individuals belonging to small classes (e.g. GX and T4).

c. Another quantitative approach is to use rarefaction curve that plotted sample size against train and test accuracies/errors.  If train and test curves were very different and not converged together, adding more samples will help to reduce variance. If train and test curves were converged, adding samples will not be help to improve this model but it could still be helpful if we switched to a more complex model.


## 4. Describe your approach to filing IP claims around your unique classification of risk?
Here the random forest was used to train the dataset, achieving an 0.36, 0.5, 0.69 accuracies. 


## 5.	How would you communicate your findings to a clinician?
The model we built had a good performance on Disease-associated risk. The model was trained based on genome, transcription and clinical data, which was directly derived from urine and noninvasive. The prediction result could be an additional support for doctors’ diagnose. Despite prediction score is not perfect, we have confidence to achieve a better performance if we can collect more patience data. The more data (both examples and useful features) will help to find similarities and differences within and between classes.  So we are looking forwards to more opportunities to collaborate with you!

