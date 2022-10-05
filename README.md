# Pedestrian mobility in Schools: Beepath Project

This repository contains the code and the mobility data used for the scientific publication. The data was collected through a citizen science experiment in which students from different schools in Barcelona participated to try to better understand the mobility around schools, as well as to find and solve possible access difficulties and improve urban furniture. Participants used a smartphone app to track their journey from home to school (or the other way around). The data collected for each user consists of an anonymized nickname, the geolocation (latitude and longitude) and the timestamp.

1. The folder "original data" contains the original data collected in the experiment.

2. The folder "processed data" contains the processed and cleaned data (a .csv file for each participant) with the geo-location and timestamp data and the time difference, the distance and the instantaneous velocity.

3. The folder "processed and interpolated data" contains the processed and cleaned data as in the case above but with the data interpolated in order to have all GPS locations uniformly separated by one second.

4. The folder "Results. txt files" contains several .txt files with the results for the Mean Squared Displacement and the Autocorrelation for several cases (interpolated data, no interpolated data, confidence intervals, etc).

5. Regarding the code, there are several Python Notebooks that reproduce the mobility results and figures. All the notebooks contain a detailed description of the code and of the study.

    - Data processing:  Contains an explanation of the three stages of data processing and cleaning with examples and the linear interpolation procedure. 
    - Functions. Mobility characterisation: Contains a grouping of the functions used to perform the calculations and characterise the mobility (calculation of time increments, distances and velocities. The mean squared displacement, autocorrelation, reorientation, tortuosity...).
    - Instantaneous velocity: Contains the study of the velocities. The Probability density function fitted with a distribution and several tests (moving average), as well as the comparision between the interpolated data and non-interpolated data. 
    - Mean Squared Displacement: Code, figures and FIT of the MSD for several cases (homogenous, heterogeneous, using and without using linear interpolation...)
    - Autocorrelation velocities: Code, figures and FIT of the Autocorrelation of the logarithm of the velocities. Again, it is compared with and without using linear interpolation.
    - Urban planning perspective: Code and figures comparing the velocities of different schools and obtaining the optimal path, the reorientation, the tortuosity...
    - Maximum Likelihood estimation: Code for the estimation of the exponential Ornstein-Uhlenbeck parametres and comparision between schools
