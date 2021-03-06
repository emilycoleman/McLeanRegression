These MATLAB files implement and plot the results of straight line regression through data in any number of dimensions to calculate a vector-valued slope and intercept as well as the covariance matrix that describes their uncertainties and uncertainty correlations.  The master script is McLeanLinearRegression.m, which takes the inputs and calculates the outputs described below.  An example workspace is provided.  These codes are implemented in a Microsoft Excel Add-In that is also available in the supporting online materials.  


INPUTS:

'dataunct' is the dataset, formatted as in the provided Excel spreadhsheet:
Each measured data point is placed in a separate row. The first 2*n 
columns are the measured data points, each followed by
its one-sigma uncertainty (absolute or percent).  The final n(n-1)/2 
columns are the correlation coefficients.  If the variables are listed in 
alphabetical order, then these correlation coefficients would be in
alphabetical order as well (e.g. rho_xz comes before rho_yz).
For 2D data, the columns of dataunct are 
x,	±1σx,	y,	±1σy,	ρxy
For 3D data, the columns of dataunct are
x,	±1σx,	y,	±1σy,	z,	±1σz,	ρxy,	ρxz,	ρyz
For 4D data, the columns of dataunct are
x,	±1σx,	y,	±1σy,	z,	±1σz,	w,	±1σw,	ρxy,	ρxz,	ρxw,	ρyz,	ρyw,	ρzw
For 5D data, the columns of dataunct are
o,	±1σo,	p,	±1σp,	q,	±1σq,	r,	±1σr,	s,	±1σs,	ρop	ρoq	ρor	ρos	ρpq	ρpr	ρps	ρqr	ρqs	ρrs
where ρxy is the correlation coefficient between the uncertainties in x and y

'skipv' is a vector of length n where '1' indicates inclusion in
the calculation, and '0' indicates rejection.
'a1' and 'v1' are the assumed values for the first components of the 
two vectors required to describe a line in multiple dimensions: a point 
on the line, and the direction vector, respectively.
'abspct' has a value of 1 if the input uncertainties are absolute, and
a value of 2 if the input uncertainties are expressed as percent.

OUTPUTS:

'a' is the point on the line with first component a1 specified above
'a2s' contains the two-sigma uncertainties in the free components of a
'v' is the direction vector of the line with first component v1 as input
'v2s' contains the two-sigma uncertainties in the free components of v
'Sav' contains the covariance matrix for the free components of a and v
'MSWD' is the mean of the squared weighted deviates (reduced chi-square)
'n' is the number of analyses included in the calculation, = sum(skipv)
