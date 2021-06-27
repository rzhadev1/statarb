# statarb
# How does statarb work (Yeo)?
# Step 1. Residual generation using PCA 
# -Residual = Stock return - L(factor loading/weights) * eigensignals
# -L are the returns from the market, residuals are idiosyncratic 
# -Calculate return matrix of N stocks for M time periods
# -Calculate empirical correlation (covariance) matrix
# -Find eigenvectors and eigenvalues using SVD (scikit learn)
# -Use eigenvectors to estimate eigensignals 
# -Use multivariate linear regression to estimate factor loading coefficients 
# Step 2. Portfolio selection by estimating OU model and pick stocks based on confidence 
# Step 3. Trade for tendies 
# TODO 
# -Write PCA function (done) 
# -Fit stock data to the OU differential equation, estimate rate of mean reversion, handle rankings
# - 
