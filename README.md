# 580_TL_Project
Dallin Harwood's Theory of Predictive Modeling (PHSCS 580) final class project. This investigates the ORCA model which calculates the transmission loss of an acoustic signal in an ocean waveguide. This project tested the sensitivity of the model to distance parameters such as depth and range. 

Repository contains:
 - README
 - TL_Project (Jupyter Notebook, main code)
 - ssp_iso1500_hw_110m (reference csv data file)

The TL_Project Jupyter Notebook initializes the ORCA model and then makes various plots demonstrating the significant effect range and depth parameters have on the model. The model requires a specific library called orcalib in order to run, which is found in an 'underwater' python environment that my research group uses. The model also takes parameters such as water sound speed and seabed type. The seabed type is defined by the variable env_file which pulls a sandy seabed profile from a catalog of 34 seabeds located in a folder from our research drive. The water sound speed profile is defined by the ssp_file which uses ssp_iso1500_hw_110m.csv (included in the repository for reference. It has a constant sound speed of 1500 m/s and a depth of 110 m) to characterize the water column. 

Once initialized, ORCA can calculate transmission loss given frequency, range, source depth, and receiver depth. This is done with orcalib.tl.calc_tl_from_orca so it will not work if you don't have access to orcalib. These parameters can either be constant, or an array of values. Several blocks of code deal with plotting different parameters while holding others constant. 

One block of code experiments with a non-linear regression, fitting a transmission loss vs range curve based on a simplified model. 

The blocks of code at the end of the notebook deal with creating cost function contours to vizualize how different combinations of parameters compare to a fixed set. Expect any code where the calc_tl_from_orca function is inside a for loop to take longer to run. THE LAST COST CONTOUR CODE TAKES OVER 10 MINUTES TO RUN. These longer blocks are separated from the plotting commands so that their output from ORCA can be hidden. 
