# ohw20-proj-Argo-interpolation
GP regression to interpolate/map Argo profile data

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
