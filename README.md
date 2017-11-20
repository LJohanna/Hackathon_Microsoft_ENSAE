# Hackathon_Microsoft_ENSAE
Explanation of the strategy used by my team to win the Hackathon

The Hackathon required 12 groups divided into two competitions. We used data from the Red Cross, wchich is a charity organisation. We chose the competition consisting on predicting where to add new centers of the Red Cross in France. 
There will not be any code or data in this repository, since the competition required strict confidentiality.

Our team consisted of the following members:

David AZOULAY
Alexandre COMBESSIE
Gabriel DUCROCQ
Johanna LALOU
Alize PAPP

We started with a large database (~10GB) on the distribution of social help by all centers of the Red Cross in France. The database was loaded on a SQL Server hosted by Microsoft Azure, and we interacted with it using Python Jupyter notebooks on a virtual machine with 32GB of RAM.

We decided to concentrate on two axis: extract relevant data from the Red Cross internal database and collect Open Data on socio-economic indicators in France, mostly from the INSEE website.

The idea was to build a regression model explaining the need for social help by a set of socio-economic indicators such as the poverty and unemployment rates. The need for social help was measured either by the number of Croix-Rouge centers per capita or by the ratio of Red Cross beneficiaries in the population.

We used the following socio-economic indicators: population density, overall poverty rate, poverty rate below 30 year old, ratio of home owners, ratio of taxable households, ratio of households on social allowances, unemployment rate, ratio of high/middle-class, ratio of employees and factory workers, ratio of agriculture workers, crime rate, ratio of medical urgency units. Finally, we added the ratio of Secours Populaire centers on the department population to account for other social help institutions.

Thanks to all this data, we were able to run several regression models: Ordinary Least Square (OLS), Ridge regression, and Random Forest. We also tried Leave-One-Out cross-validation for the Ridge. Overall the models' fits were very good (R-squared of 0.48 for the OLS regression, 0.57 for the Ridge). This is not surprising as factors like poverty and unemployment are strongly linked with the need for social help.

We used our OLS regression model as a way to "predict" the theoretical need for social help in each department. We assumed that a negative difference between predicted and observed values meant that the department did not have enough Red Cross centers. We plotted these gap values on an interactive map of France using Microsoft Excel PowerMap. We also established a "Top 5 List" of priority departments by sorting the highest gaps in terms of both number of centers and beneficiaries.

We were very honored to receive the first prize in our competition category by the jury who was quite happy with our presentation. We have the regret of not having performed our analysis at the city level.
