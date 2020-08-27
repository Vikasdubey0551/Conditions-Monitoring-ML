# Conditions Monitoring of Wind Turbines using Machine Learning and Data Analysis 


Ball bearings are a crucial component in any wind turbine. The condition of the ball bearings is monitored to ensure no unexpected downtime of the turbine.

 The ball bearings consists of an outer ring, balls, cage and the inner ring. The ball bearing can be damaged in several ways, where the most common is a dent in either the inner or the outer ring.


_Figure 1 - Ball bearing_

![ball bearing](images/title1.png)

Such a dent will cause distinct failure frequencies to appear as a function of the rotation speed of the shaft inside the ball bearing. The &quot;Ball Pass Frequency Outer&quot;(BPFO) is the frequencies which the balls passes over a single dent in the outer ring, this is typically specified as a multiple of rotation speed by the manufacturer.
 Every time the ball passes over a dent, it will cause a spike in vibration captured by the data acquisition equipment. This will cause harmonics of the fault frequency(BPFO) to appear in the vibration data as seen in Figure 2. Sometimes these harmonics will also appear at much higher frequencies than seen here, such as and often the low harmonics are not observed.


_Figure 2 - BPFO fault frequencies_

In this project the Case Western Reserve University Ball bearings dataset is used. 

## Material

In the Python file &quot;case\_western.py&quot; it is shown how to import two HDF5 files containing vibration data from both a good and a faulty bearing. The data from the good bearing is found in &quot;x\_baseline.h5&quot; where 40 samples of 1 second each are found. The data from the faulty bearing is found in &quot;x\_fault.h5&quot; where 10 samples of 1 second each are found.

## Goals

1. Find the difference between a good bearing and a faulty one? Maybe try to identify the BPFO.
2. Use machine learning techniques to distinguish the good bearing from the faulty one.

## Results 

![comparision](images/title2.png)


* The distribution of baseline and faulty data is different in the time domain.
* The distribution remains identical even for 1000 samples.
* Statistically, both of the distributions are not skewed. However, faulty one has a very high kurtosis (more outliers) (i.e. not close to gaussian distribution).

![envelope signal](images/title3.png)


I used the following machine Learning methods for this project : 

1.  Unsupervised Machine learning

    1.1  Principal Components Analysis
    1.2  t-SNE
    1.3  Clustering (OPTICS)

2.  Supervised Machine learning

    2.1  Support Vector Machine (SVM) on Reduced Data
    2.2  XGBoost
    2.3  Recurrents neural networks


![clustering](images/title4.png)

PCA and t-SNE both successfully reduced the dimensionality of the data and separate baseline and faulty data into different regions, which can be easily clustered.OPTICS nicely predicts faulty and baselines clusters. Also, detects outliers within data (shown in green). 

![class distribution](images/title5.png)

There is a clear class imbalance in the data. Faulty data is 4 times lower than baseline data.

![confusion matrix](images/title6.png)


