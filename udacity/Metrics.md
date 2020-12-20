## Define
Sanity checking metrics (invariant metrics) - check we are conducting the experiment correctly. E.G. same distribution of population characteristics across control and test group, same proportion etc.
Business metrics - how many revenue you make, \# users > detailed metrics: \# users complete a class, dig into user experience, e.g. do they get a job/skill improvement.

Summary of the metric > details
e.g. active users > 7 days/28 days active? which event counts as active

Evaluation:
you can do a combination metric or a weighted summary of metric, but pratically is problemetic because too many business parties involved and difficult to explain.

Difficult metrics
- Takes too long
- Don't have access to data
Other data:
- user survey
- external data
- academic data
These proxies are also good for brianstorming and validation of our own experiments, e.g. compare against industry/research expectations.

Other techniques:
1. External data
2. User exprerience research (UER). we want to validate results
3. Focus group. risk of group thinking
4. Survey. may have bias
5. Retrospective analysis / observation. Compare against past behaviors, spikes etc. helping brainstorm/validations. We can't know the *causation* using such analysis because we are not running a/b testing to see whether the change causes the effect.
6. Experiment

Also keep in mind of the company culture - innovative/user experience/revenue driven?

## Build intuition
What data we capture for the metric? What summarize my metric - avg? medium? and some more complicated ones? Think about business cases and logics.

e.g. MEF - metric + analysis level + frequency. 
Or we can choose to track the child page click of the parent page view.

**Filtering and segmentation**
Compute the analysis on a segment of the trafic - e.g. english users/mobile users. Filter out long sessions, and keep in mind of doing the validation such as compare with the baseline to make sure that these are not caused by the experiment itself.

E.G. if we see a spike and it does not smooth out after the validation like week over week comparison/year over year data, the spike actually exists during our experiment. We can analyze each segment to see which segment is causing the spike, and compare prob/rate to track abnormals. Talk to engineering team to figure out what is the cause of the spike of that particular segment to eliminate the cause of bug/spams/abnormals. 

**Summary Metric**
- Sum and counts
- Distribution metrics: mean, median, x percentile.
- Probability and rate
- Ratios

Sensitivity and robustness
sensitive enough to pickup the change we care about, and robust enough to not influencing our test when something not interesting happens. E.G. choose medium if we want to track loading time because mean is heavily influenced by outliers that are very possible to happen. Choose 90th percentile if the change happen to the upper percentile of the group.

## Characterize

Calculating variability

|Type of metric|Distribution|Est. variance|
|probability|binomial(normal)|p_hat(1-p_hat) / N|
|mean|normal|std/N|
|median/percentile|depends|depends|
|count/difference|normal(maybe)|var(x) + var(y)|
|rates|poisson|x_bar|
|ratios|depends|depends|

non-parametric methods: analyze data without making assumption about the data. may be noisier.
e.g. sign test. can't test out the size.

Emperical estimate:
complicated metric distribution hard to measure. A/A testing to test the underlying variability, and validations. e.g. test if your random function is truly random, test sensitivity and the robustness of the metric. We can consider doing **bootstrap** before consider A/A test.

Summary of the uses of A/A tests:
- Sanity check - compare results to what you expect
- estimate variance and calculate confidence
- estimate confidence interval

Summary:
1. different metrics have different variablility. They might not be useful because the var is so high even if it makes perfect product / business sense.
2. understand the distribution to estimate the var, using analytical and emperical methods.
