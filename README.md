## Abstract
Modern portfolio theory(MPT) states that an investor can duild a portfolio of diverse stocks to maximize returns for a given level of risk.
Risk can be reduced using diversification, the idea behid diversification is to split investment between varying companies so that if a few stocks one owned decrease in value, the others would not, thus reducing the loss.
The plunge in a stock price can be due to various factors such as management change, global econmic decisions or company's annual report. Thus, by selecting stocks that are different from each other optimizes returns. <br/>
As we observe two stocks in the same industry move together such as IT stocks which have similar pattern. If industry performs better they all surge together and if not they plunge, so by having stocks from different industries will be a good investment as it mitigates risk involved.<br/>
<br/>Machine learning can be used to diversify portfolio. Therefore, a method to cluster stocks would help in efficient decision making and to have diverse portfolio.

## Environment
Used Jupyter Notebook which is an open-source web application.
Performed data cleaning and transformation and machine learning in this environment.

## Data Collection and Wrangling
The Standard & Poor’s 500, or the S&P 500, is an American stock market index based on 500
large companies with stock listed on the NYSE or NASDAQ. The S&P 500 is one of the most
commonly followed equity indices and is considered the best representation of the US stock market.<br/>
  *  In this project I am fetching the pricing data for the S&P 500 stocks from google finance api from Jan 1, 2018 to current date.<br/>

  * Upon validating the consistency, it is found that there are few "Nan" values in the data we got from google api which needs to be fixed. I have assigned 0 to such records.<br/>
  * Then I am calculatin their historic returns and volatility and then proceed to use the **K-Means clustering**
algorithm to divide the stocks into distinct groups based upon said returns and volatilities.
## Workflow
In K-means clustering the critical part is to decide how many clusters do we want to divide our data into.<br/>
For this purpose "Elbow Curve" is used. It is a relationship between number of clusters we select and
the Sum of Squared Errors (SSE) resulting from using that number of clusters called as within cluster sum of squares.<br/>
**Note:** WCSS -Within Cluster Sum of Squares. For e.g, let’s assume there are 5 clusters. That means, we have 5 center points (C1, C2, C3, C4, C5) for our 5 clusters.
Each data point(here each stock) falls into the zone of either C1 or C2 or C3 or C4 or C4 or C5. <br/>
First we calculate the sum of squares of the distance of each data point in cluster 1 from their 
center point C1. Let’s say there are 3 points in cluster 1 (c1p1, c1p2, c1p3).
[dist(C1, c1p1) ]² + [dist(C1, c1p2)]² + [dist(C1, c1p3)]². This is cluster 1 sum of squares.<br/>
Similarly we do the same for C2, C3, C4 and C5. Now, we add the sum of all 5 ‘clusters sum of squares’ to get WCSS.
<br/>
We want to find number of clusters which gives minimal Sum of Squares error(SSE) i.e, the sum of squares of data points(stocks) from centroid  of ith cluster should be minimum.
  * Upon observing elbow curve starts the reduction in the SSE begins to slow down for each increase in cluster number. <br/>
   Optimal number of clusters would be "5".<br/>
  * Scatter plot is then used to visualize the clusters. Constructed a dataframe with stock symbol and the cluster it belongs.<br/>
  * Exported the data into a csv file, which can be used to build diverse portfolio.

## Conclusion
Thus dividing stocks into groups with “similar characteristics” can help in portfolio construction to 
ensure we choose a collection of stocks with sufficient diversification between them. 



## References
T. Kanungo, D. M.Mount, N. Netanyahu, C. Piatko, R. Silverman, and A. Y. Wu, "An efficient k-means clustering algorithm: Analysis and implementation", PatternAnalysis
and Machine Intelligence, 24 (2002), 881-892<br/>
Modern Portfolio Theory, https://www.investopedia.com/terms/m/modernportfoliotheory.asp#ixzz59m0MvqoA 
