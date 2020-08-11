# Ocean Hackweek 2020: Project to map Argo data
GP regression to interpolate/map Argo profile data. Follow the algorithm from [Kuusela and Stein 2018](https://royalsocietypublishing.org/doi/10.1098/rspa.2018.0400).

Project 5: Local spatio-temporal interpolation of Argo data

Mentors:
[Alison Gray](http://alisonrgray.com/), [Dhruv Balwada](https://github.com/dhruvbalwada/), [Spencer Jones](https://github.com/cspencerjones)

Specific tasks
1. Import Argo T or S data from a specific region
2. Fit the data to a mean function via least squares or loess and subtract the result from the data
3. Estimate autocovariance parameters for the resulting anomaly field via maximum likelihood estimation
4. Use those parameters to estimate the anomaly field via "objective mapping"
The problem
Optimal space-time interpolation of scattered oceanographic data in python; follows on methods from Kuusela and Stein (2018).  Can use existing package (george) to compute likelihood and mapping.
Application example
Could be focused on any fairly small region (~5-10-degree box) in the part of the global open ocean well-sampled by Argo. 

Practical steps:
1. Import Argo data from selected region of interest (lat/long/depth).
-- We could skip this initially and just make a script that takes an input dataset consisting of (lat, lon, time, data), which would be more easily applicable to any given dataset. [Use Argopy](https://argopy.readthedocs.io/en/latest/data_fetching.html)
2.  Compute mean (large-scale signal). 
-- This can be done simply using a least squares fit to data, with a given set of basis functions such as 2D polynomial in space and a seasonal cycle in time. [Can potentially use Scipy to do this](https://docs.scipy.org/doc/scipy/reference/generated/scipy.optimize.curve_fit.html).
3.  Subtract mean at data points from data values to get residuals.
4.  Determine parameters of the covariance function that describes the residual field via maximum likelihood estimation (optimize hyperparameters via [george package](https://george.readthedocs.io/en/latest/)).
5.  Use Gaussian process regression with optimized covariance parameters to compute an estimate at a given set of points (lat, lon, time) (via [george package](https://george.readthedocs.io/en/latest/)). Add this to the estimate of the large-scale mean to get final estimate. 

Additional resources:
- Tutorials from George: https://george.readthedocs.io/en/latest/tutorials/first/ ; https://george.readthedocs.io/en/latest/tutorials/hyper/
- George example for 2D interpolation :https://gist.github.com/shoyer/80aa06f5ad44aacd9187 
- List of useful links to learn more :https://hackmd.io/@eHN2gDGTS7uR1j3KZ26AJQ/ry8VfkAVL
- Argo: https://argo.ucsd.edu/

