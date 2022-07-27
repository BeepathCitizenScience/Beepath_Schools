# Beepath-Schools

1. The folder "original data" contains the original data collected in the experiment.

2. The folder "processed data" contains the processed and cleaned data (a .csv file for each participant) with the geo-location and timestamp data and the time difference, the distance and the instantaneous velocity.

3. The dolfer "processed and interpolated data" contains the processed and cleaned data as in the case above but with the data interpolated in order to have all GPS locations uniformly separated by one second.

4. The folder "Results. txt files" contains several .txt files with the results for the Mean Squared Displacement and the Autocorrelation for several cases (interpolated data, no interpolated data, confidence intervals, etc).

5. Regarding the code, there are several Python Notebooks. 
  - Data processing:  Contains an explanation of the three stages of data processing and cleaning and the linear interpolation.
  - Functions. Mobility characterisation: Contains a grouping of the functions used to perform the calculations and characterise the mobility (calculation of time increments, distances and velocities. The mean squared displacement, autocorrelation, reorientation, tortuosity...).
  - Instantaneous velocity: Contains the study of the velocities. The PDF's, the moving average...
  - Temporal gaps. Linear interpolation: Contains the study of the different temporal gaps present in the data and the study of the velocities after performing the linear interpolation.
  - Mean Squared Displacement: Code, figures and FIT of the MSD for several cases (homogenous, heterogeneous, using and without using linear interpolation...)
  - Autocorrelation velocities: Code, figures and FIT of the Autocorrelation of the velocities.
  - Urban planning perspective: Code and figures comparing the velocities of different schools and obtaining the optimal path, the reorientation, the tortuosity...
