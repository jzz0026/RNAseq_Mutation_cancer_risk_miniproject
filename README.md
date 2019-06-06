# Convergent Genomics Data Science Challenge
## The Challenge
It is the mission of Convergent Genomics to bring clear and actionable insight to cancer patients and their physicians. One way you can support this mission is by leveraging the combination of clinical, laboratory, and sequencing data to create algorithms or classifiers that help diagnose disease and better understand risk, or aggressiveness of a patient’s cancer. Through this challenge we are providing you an opportunity to demonstrate the raw power of your data ninja skills on a real world human cancer genomic and clinical feature dataset. Using the associated clear cell kidney cancer data sets provided, construct a program in python and/or R that:
1. Uses your choice of regression, clustering, or dimensionality reduction approaches to identify features underlying disease-associated risk.
2. Using best practices, create a classification algorithm that predicts risk.
3. Compare and contrast the optimal features identified in tasks 1 & 2.

## Target
- Utilize unsupervised clustering to create a label reflecting disease-associated risk from cancer stage, grade, overall survival in days following diagnosis, and vital status (alive/dead).
- Clean and QA/QC of clinical, mRNA and mutation data as well as fill in missing data.
- Train the model to predict risk using clinical, mRNA and mutation data

## Learning methods for classification
      1. Logistic regression
      2. SVM 
      3. Random forest 
      4. Gradient boosting
      5. Neural network

## Unsupervised clustering for categories of risks

As we known, a clinician uses a combination of **cancer stage, grade**, **overall survival in months following diagnosis**, and **vital status (alive/dead)** to establish risk. Since this risk was not provided, we should also look into these features and try to build risk as the label for modeling. Intuitively, both doctor and patients care about length of the remaining life most, so **overall survival in months** should be the most **indicative** to build risk desipte **68% of individuals are still alive** and could cause bias if only using overall survival as risk. Cancer stage and grade are also very meaningful to represent danger and risk, but could be incomplete and cause misleading if used alone. Many individuals could have a high cancer grade but low stage and live fairly long after diagnosis, vice versa.

<p align="center">
   <img src="Plot/plot_stag_grade_vital_survival.png" alt="alternate text" width="1500"> 
</p>

No significantly strong corralation of overall survival in months was observed against cancer stage and grade (converted to danger level, 0 to 4), which reflected a high variance in clinical population. 

