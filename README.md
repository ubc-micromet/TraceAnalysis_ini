# Trace Analysis Ini Files - Instructions and guidelines

## First Stage

In the first stage of cleaning the idea is to clean up the data so we can keep only the best measured values (data points) for each sensor. No interpolation is done at this stage so any removed points will not be gap-filled. If the researcher is looking for the best measurements from a particular sensor, this is the data that they want.

The first stage cleaning provides the following features:

1. Selects traces that are needed for future data analysis. Not all the measured variables from a site need to be here - only the ones that will be used in future analysis or that’s needed to improve cleaning.
2. File names from the database can be renamed here. The trace name does not have to be the same as the file name from the database.
3. The original values can be altered (calibrations can be applied, units can be changed).
4. Basic filtering can be done:
  a. Values can be removed if they exceed minMax thresholds.
  b. Values can be clamped to the thresholds if they exceed clampedMinMax values. 
7. This stage creates dependencies between different traces. If one trace gets some points removed here, all its dependent traces will have those points removed too. 

Introduction:
All traces must be enclosed in [Trace] and [End] blocks.
All assignments can be on multiple lines, but should be enclosed in single quotes.
Comments must begin with a percentage sign,%.
The partial path must be included with the inputFileName, when you locate the raw data trace in the database. (Using biomet_path only returns the path: 'year/site/measType/')
Necessary fields are: variableName, inputFileName, measurementType, units, title, and minMax.
All fields must be in Matlab format
All assignments must be to strings in single quotes, or numeric expressions (ex: threshold_const = 6, threshold_const = [6],variableName = 'Some Name')	
