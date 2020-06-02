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

## Task

The tasks involve:
* Identify the normal operating state of the server
* Identify the threshold levels for various attributes
* Identity the different abnormal states the server has been in and a method to automatically identify the new abnormal states 
when they come up.
* propose a way to identify a change in the normal operating state of the system, i.e. a way to identify the new normal.

## Overview of the techniques used

The task at hand is detecting anamolies in unlabelled data.The following anomaly detection techniques were looked into:
* Probabilistic anamoly detection methods
* Domain based methods
* Reconstruction error based methods
* Distance based novelty detection
* Density based novelty detection

Due to the curse of dimensionality, density and distance based methods might not perform well in high dimensional space, so there were eliminated.

#### <ins>Probability based anomaly detection techniques</ins>









