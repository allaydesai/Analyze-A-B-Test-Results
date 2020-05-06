# Analyze-A-B-Test-Results
Analyze A/B test run by an e-commerce website

**UDACITY** | Data Analyst Nanodegree Program

---

### OVERVIEW

A/B tests are very commonly performed by data analysts and data scientists. The goal of this project is to understand the results of an A/B test run by an e-commerce website. 

The company has developed a new web page in order to try and increase the number of users who "convert," meaning the number of users who decide to pay for the company's product.

Using the analysis, help the company understand if they should implement this new page, keep the old page, or perhaps run the experiment longer to make their decision.

### PROJECT FILES
<ul>
  <li>Analyze_ab_test_results_notebook.ipynb</li>
  <li>Analyze_ab_test_results_notebook.pdf</li>
  <li>ab_data.csv</li>
  <li>countries.csv</li>
  <li>README.MD</li>
</ul>

### DATASET
There are two datasets we used for our analysis:

1. ab_data.csv

![alt text](https://github.com/allaydesai/Analyze-A-B-Test-Results/blob/master/images/ab_data.PNG)

2. countries.csv

![alt text](https://github.com/allaydesai/Analyze-A-B-Test-Results/blob/master/images/Country.PNG)

### ANALYSIS

1. A/B Test

![alt text](https://github.com/allaydesai/Analyze-A-B-Test-Results/blob/master/images/A_B_test.PNG)

histogram of the p_diffs

![alt text](https://github.com/allaydesai/Analyze-A-B-Test-Results/blob/master/images/test_plot.PNG)

we computed the P-value which is the probability of observing your statistic (or one more extreme in favor of the alternative) if the null hypothesis is true.

Here we observe a P-value of 0.9, remember that large p-value suggests that we shouldn't move away from the null hypothesis

Which in this case would mean we fail to reject the hull hypothesis in favor of an alternative, which means the old landing page has a conversion rate better or equal to new landing page.

stats.proportions_ztest to compute your test statistic and p-value:
z_score: 1.3109
p_value: 0.9051

check significance of our z-score using norm function:
cdf: 0.9051
ppf: 1.6449

Here we find that the z_score of 1.31 is less than critical value of 95% confidence resulting in 1.64. Hence we fail to reject null hypothesis.

2. Regression Test

![alt text](https://github.com/allaydesai/Analyze-A-B-Test-Results/blob/master/images/RegHyp.PNG)

logit = sm.Logit( df2['converted'], df2[['intercept' ,'treatment']] )

![alt text](https://github.com/allaydesai/Analyze-A-B-Test-Results/blob/master/images/RegressionResult.PNG)

Adding more factors:

Country added to the dataframe:

![alt text](https://github.com/allaydesai/Analyze-A-B-Test-Results/blob/master/images/combined.PNG)

model = sm.Logit(df_new['converted'], df_new[['intercept', 'US', 'CA']])

![alt text](https://github.com/allaydesai/Analyze-A-B-Test-Results/blob/master/images/RegressionResult2.PNG)

The above findings conclude that there is not enough evidence to show interaction between the two country variables and page coversion rate since they both have a low p value. Hence once again we fail to reject the null hypothesis.

### Conclusion

Through the various analysis we have performed so far, there isnt sufficient evidence to suggest the the new webpage has a higher conversion rate.

Other factors can certainly be added which may indicate weather or not an individual might convert. Some of these factors can be age, gender and location. Each of these provide insights that may help improve the accuracy. At the same time we need to keep in mind that some of these factors may have unexpected consequences and affect the trends that are detected from the data.
