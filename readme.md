# Anamoly detection using server log data

## Introduction

During my internship, I worked on detecting anamolous servers using server log data. While working on this porject I researched extensively on various anamoly detection / novelty detection techniques. While not giving away an confidential data I will summarize the methodology that I followed to detect anamolies.

## Anamoly detection in servers

Servers can behave abnormally due to many reasons:
* software failures 
* hardware (e.g., some piece of hardware simply breaks down) 
* offered load (an exceptionally high load is offered to the system)
* human errors (e.g., configuration errors). 

Various algorithms were looked into to design an anomaly detection system.

__Assumptions:The model was built assuming the normal operating state of the server is unknown to set thresholds for various parameters.__

## Data
The data contains information of various attributes such as temperature, memory, cpu usage etc. The time dependent data points are obtained at very high frequencies.

## Objective
Research methods to identify the different operational states of  a server utilizing the telemetry data from the server  instrumentation.

## Task
Utilize	Clustering	and	Reconstruction	Error	based	Machine
Learning methods to identify different operational states.

The task can be broken down into the following sub-tasks:
* Identify the normal operating state of the server
* Identify the threshold levels for various attributes
* Identity the different abnormal states the server has been in and a method to automatically identify the new abnormal states 
when they come up.
* propose a way to identify a change in the normal operating state of the system, i.e. a way to identify the new normal.

## Potential Impacts:
* Automate identification: Automatically identify when the  inherent operational state of the server changes.
* Identify sub optimal states: Compare the operating states  obtained for different servers to draw insights to identify sub  optimal hardware, software and environmental conditions.
* Optimal job scheduling: Identify the operating states of a  server under workload and advice orchestrators and job  schedulers in order to optimize the workload execution.
* Accurate billing: Map operating states with job scheduling  information in order to charge customers based on the  amount of resources used and not just based on the time for  which a job is run.

## Approach























## Approach

The task at hand is detecting anamolies in unlabelled data.The following anomaly detection techniques were looked into:
* Probabilistic anamoly detection methods
* Domain based methods
* Reconstruction error based methods
* Distance based novelty detection
* Density based novelty detection

Due to the curse of dimensionality, density and distance based methods might not perform well in high dimensional space, so there were eliminated.

#### <ins>Probability based anomaly detection techniques</ins>
Identified the number of clusters using the change in AIC (Akaike information criterion) and BIC (Bayesian information
criterion) values obtained for each model built for different number of components / clusters.

The graphs did not clearly indicate the number of clusters present. Have set the number of clusters to 5.

The algorithm has split the data up to 20000 data points into 2 clusters and 20000-400,000 data points were split into 3  clusters. But the simulated data between 20000-400,000 data points should have been split into 5 clusters and the data  points up to 20000 should have belonged to one of the 5 clusters.As this was not how the data was clustered, one can conclude that GMM did not cluster well.

Speculations: Why did GMM not work:
The clusters may not be gaussian.
Uneven number of data points in the clusters.
Reference :http://hameddaily.blogspot.com/2015/03/when-not-to-use-gaussian-mixtures-model.html

#### <ins>Domain based novelty detection</ins>
Should split the data into 2 clusters. One cluster which contains observations similar to the data points on which the model is trained and the other cluster which has data points not similar to the training data.

One class SVM failed to split the data properly, in the sense that it was very sensitive to the training data provided. A data  point even slightly different from the training data was assigned to the abnormal class or a different class.

#### <ins>Reconstruction error based</ins>
If a model is trained on data which corresponds to some operating state of a server (which can initially be identified from the  data using some clustering technique) say normal state, then if the server starts operating in a state different than the data  on which the model is trained on, there will be a change in the distribution of the residuals indicating the change in state.

Used auto encoders and trained them on the data which corresponds to the normal operating state of the server.

So the question that is now to be addressed is, how do we indentify the normal operating state?














