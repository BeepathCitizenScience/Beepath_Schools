# Pedestrian mobility in Schools: Beepath Project

This repository contains the code and the mobility data used for the scientific publication. The data was collected through a citizen science experiment in which students from different schools in Barcelona participated to try to better understand the mobility around schools, as well as to find and solve possible access difficulties and improve urban furniture. Participants used a smartphone app to track their journey from home to school (or the other way around). The data collected for each user consists of an anonymized nickname, the geolocation (latitude and longitude) and the timestamp.

1. The folder "original data" contains the raw data collected in the experiment, composed of 262 csv-files (corresponding to each participant journey) and 161,009 GPS locations. The data-files contain 8 columns, which are:

    - Unnamed 0: Index of each row.
    - course: the direction in which the device is travelling, mesured in degrees and relative to the north.
    - haccuracy: radius of uncertainty for the location, mesured in metres.
    - speed: instantaneous velocity of the device (obtained by the Android/IOS servers) in metres/second.
    - latitude: latitude coordinate in degrees
    - longitude: longitude coordinate in degrees
    - time: timestamp in which the geo-location is recorded
    - nickname: anonymous nickname of the participant
    

2. The folder "processed data" contains the processed and cleaned data (a .csv file for each participant, with the same file-name as the raw data but adding the suffix "_processed" to each .csv file. The data is reduced to 83 users and 36,091 GPS locations. The column "Unnamed 0:" is removed from the data-set and 3 new columns are added corresponding to the time increment, the instantaneous velocity and the distance between GPS records.

    - $\Delta t$: time difference between consecutive records in seconds (computed in advance: $\Delta t (i) = t(i+1) - t(i)$. So the last element is NaN).
    - d: distance between consecutive GPS records in metres (computed in advance, so the last element is NaN).
    - v: instantaneous velcocity of each record in metres/second (distance over time difference). Again, the last element is NaN.
    

3. The folder "processed and interpolated data" contains the processed and cleaned data as in the case above (processed data) but with the data interpolated in order to have all GPS locations uniformly separated by one second. Then the number of GPS locations is increased to 44,662 (83 users). The columns are the same as the processed files, but now all the values of $\Delta t$ are 1.0 and then the columns d (distance) and v (velocity) provide the same value. The file-names are the same as the raw data but adding the suffix "_interpolated" to each .csv file.


4. The folder "Results. txt files" contains several .txt files with the results for the Mean Squared Displacement and the Autocorrelation for several cases (interpolated data, no interpolated data, confidence intervals, etc).

    - The Jupyter Notebook "Mean Squared Displacement.ipynb" generates: 
        
        a. difussion_origin_0.txt: Result for the Mean Squared Displacement MSD(T) for T up to 600 seconds. For the case of origin at T=0.
        b. difussion_origin_0.interpolation.txt: MSD(T) for the case of origin at T=0 but using the interpolated data.
        c. CI_95_origin_0_minus: Confidence interval of 95% for the case of MSD(T) (origin at T=0). Lower part.
        · CI_95_origin_0_minus_interpolation: Confidence interval of 95% for the case of MSD(T) (origin at T=0). Lower part. Interpolated data.
        · CI_95_origin_0_plus: Confidence interval of 95% for the case of MSD(T) (origin at T=0). Upper part.
        · CI_95_origin_0_plus_interpolation:  Confidence interval of 95% for the case of MSD(T) (origin at T=0). Upper part. Interpolated data.
        · difussion.txt: Result for the Mean Squared Displacement MSD(T) for T up to 600 seconds. For the case of averaging over all origins (homogeneous).
        · difussion.interpolation.txt: MSD(T) for the homogeneous case but using the interpolated data.     
        · ci_95_msd_homogenous_minus.txt: Confidence interval of 95% for the case of MSD(T) (homogeneous case). Lower part.
        · ci_95_msd_homogenous_minus_interpolation.txt: Confidence interval of 95% for the case of MSD(T) (homogeneous case). Lower part. Interpolated data.
        · ci_95_msd_homogenous_plus.txt: Confidence interval of 95% for the case of MSD(T) (homogeneous case). Upper part.
        · ci_95_msd_homogenous_plus_interpolation.txt: Confidence interval of 95% for the case of MSD(T) (homogeneous case). Upper part. Interpolated data.



    - The Jupyter Notebook "Autocorrelation velocities.ipynb" generates:

5. Regarding the code, there are several Python Notebooks that reproduce the mobility results and figures. All the notebooks contain a detailed description of the code and of the study.

    - Data processing:  Contains an explanation of the three stages of data processing and cleaning with examples and the linear interpolation procedure. 
    - Functions. Mobility characterisation: Contains a grouping of the functions used to perform the calculations and characterise the mobility (calculation of time increments, distances and velocities. The mean squared displacement, autocorrelation, reorientation, tortuosity...).
    - Instantaneous velocity: Contains the study of the velocities. The Probability density function fitted with a distribution and several tests (moving average), as well as the comparision between the interpolated data and non-interpolated data. 
    - Mean Squared Displacement: Code, figures and FIT of the MSD for several cases (homogenous, heterogeneous, using and without using linear interpolation...)
    - Autocorrelation velocities: Code, figures and FIT of the Autocorrelation of the logarithm of the velocities. Again, it is compared with and without using linear interpolation.
    - Urban planning perspective: Code and figures comparing the velocities of different schools and obtaining the optimal path, the reorientation, the tortuosity...
    - Maximum Likelihood estimation: Code for the estimation of the exponential Ornstein-Uhlenbeck parametres and comparision between schools
