## Intro to AB Testing - what can and can't do with AB testing
Used to test out new product/features. How do these users repond differently - determine which version is better. 

There are certain limitations to what we cannot test:
A. *new experience* 
- **Novelty effect**
- **Change aversion**

Two issues to consider for testing out new experience:
1. baseline for comparison.
2. how much time needed for users to adapt to new experience - what is the plateaued experience to make a robust decision.

B. Time can be a problem for short term a/b testing, e.g. rental referrals. We don't know how much time needed for users to come back with a referral etc. There are certain proxies that we can use and will talk more in later sessions.

C. A/B testing can't tell you if you are missing something. We can know through AB testing that which review to show is better, but can't know if we are missing another review at all.

More examples:
- Can't test if a website is complete/missing anything. We can test a specific feature, but can't know if there's anything more missing. What we can do is ask users for anything they feel missing.
- Can't test if we want to add premium service. Users have to opt in for premium usage. So ab testing wouldn't work when we assign people to different groups - wouldn't have a control to compare against. We can test how many users read about the terms when given options, and how many would upgrade, but we can't test the impact.
- Can't test for a car selling website for repeating users/referrals of a new feature - time too long for people to buy a new car.
- Might can't test the change of logo too - people are surprisingly subjective/emotional for logo/brand changes.
- we can test out a new ranking algorithm - clear control and testing group, and clear metrics.
- we can probably test out backend features (like page load time) if we have enough computing powers to run both group at the same time.

## Business Example
We have a online course learing website.
### Choose a metric
**Customer Funnel** Homepage visits (most population) > explore website > create account > complete course/made purchase (least population).
Initial hypothesis: Changing the color of the start now button from orange to pink will ~~increase the number of people exploring the course page~~ increase the click through probability of the button (and assume that this will increase the final business metric - total course completed)
Which metrics?
1. \# of users completed course -> takes time.
2. \# of clicks. -> too much noise
  2.1: **click-through-rate**: # of clicks / # of page views
  2.2: **click-through-probability**: # unique visitors who click / # unique visitors to page.  
  e.g. 2 visitors, a clicks 0 times b clicks 5 times, CTR = 5/2; CTP = 1/2
  
> Use a rate to measure **usability** and use a probability to measure **total impact**.

e.g. usability measures how often a user find that button on a variety of buttons that they can click on. probability to measure how often a user went to the second page - we don't care if the user double-clicked, reload etc.
implementation of probability: count the unique one child page click of one page view.

### Review statistics
CTP follow a binomial distribution.
**Binomial distribution**
- 2 types of outcomes (success, failure)
- Independent events
- Identical distribution

Ex.
1. draw 20 cards from a shuffled deck, outcome red or black. Not binomial, not independent. Would be independent when we increase to a large sample size.
2. roll a die 50 times, outcome 6 or other. Binomial
3. clicks on a search result page, outcome click or not click. Not independent. Search one word and then would search again with slightly different words. 
4. complete course after 2 weeks, outcome complete or not complete. Very close to independent - students are often not related.
5. purchase of item within one week, outcome purchase or not purchase. Not independent. The items in the shopping cart are related.

**Confidence interval**
If N * P = 5 AND N*(1-P) > 5, assume a normal distribution.
If we have a p = 100/1000 (# users clicked / # users (N)) 

...
Standard deviation of binomial
If you look up a binomial distribution elsewhere, you may find that it has a mean of np and a standard deviation of \sqrt{np(1-p)} 
This is for a binomial distribution defined as the total number of successes, whereas we will use the fraction or proportion of successes throughout this class. In this cas, the mean is p and standard deviation is \sqrt{\frac{p(1-p)}{n}} 

Useful equations
You may find these equations helpful in solving the quiz:
p_hat = X/N  
SE = sqrt(p_hat (1-p_hat) / N)  
m = z* SE


**Two-tailed vs. one-tailed tests**
The null hypothesis and alternative hypothesis proposed here correspond to a two-tailed test, which allows you to distinguish between three cases:

A statistically significant positive result
A statistically significant negative result
No statistically significant difference.
Sometimes when people run A/B tests, they will use a one-tailed test, which only allows you to distinguish between two cases:

A statistically significant positive result
No statistically significant result
Which one you should use depends on what action you will take based on the results. If you're going to launch the experiment for a statistically significant positive change, and otherwise not, then you don't need to distinguish between a negative result and no result, so a one-tailed test is good enough. If you want to learn the direction of the difference, then a two-tailed test is necessary.

...
### What change is practically significant?
Statistically, what's substantive in addition to being statistically significant. Different rules for different businesses. E.G.
### Design
Power has an inverse trade-off with size. 
### Analyze
...

### Keeping mind of the policy and ethics for running experiments
Consent is not needed if data is at minimal risk and can't be identified.
Summary: it is a grey area as to whether many of these Internet studies should be subject to IRB review or not and whether informed consent is required. Neither has been common to date.

Most studies, due to the nature of the online service, are likely minimal risk, and the bigger question is about data collection with regards to identifiability, privacy, and confidentiality / security. That said, arguably, a neutral third party outside of the company should be making these calls rather than someone with a vested interest in the outcome. One growing risk in online studies is that of bias and the potential for discrimination, such as differential pricing and whether that is discriminatory to a particular population for example. Discussing those types of biases is beyond the scope of this course.

Our recommendation is that there should be internal reviews of all proposed studies by experts regarding the questions:

Are participants facing more than minimal risk?
Do participants understand what data is being gathered?
Is that data identifiable?
How is the data handled?
And if enough flags are raised, that an external review happen.
Four principles
- **Risk**
what risk is the participant undertaking? The main threshold is whether the risk exceeds that of “minimal risk”. Minimal risk is defined as the probability and magnitude of harm that a participant would encounter in normal daily life. The harm considered encompasses physical, psychological and emotional, social, and economic concerns. If the risk exceeds minimal risk, then informed consent is required. E.G. health and financials of the participants.
- **Benefits**
what benefits might result from the study? Even if the risk is minimal, how might the results help? In most online A/B testing, the benefits are around improving the product. In other social sciences, it is about understanding the human condition in ways that might help, for example in education and development. In medicine, the risks are often higher but the benefits are often around improved health outcomes.

It is important to be able to state what the benefit would be from completing the study.
- **Alternatives**
what other choices do participants have? For example, if you are testing out changes to a search engine, participants always have the choice to use another search engine. The main issue is that the fewer alternatives that participants have, the more issue that there is around coercion and whether participants really have a choice in whether to participate or not, and how that balances against the risks and benefits.

For example, in medical clinical trials testing out new drugs for cancer, given that the other main choice that most participants face is death, the risk allowable for participants, given informed consent, is quite high.

In online experiments, the issues to consider are what the other alternative services that a user might have, and what the switching costs might be, in terms of time, money, information, etc.
- **Data sensitivity**
hat data is being collected, and what is the expectation of privacy and confidentiality? This last question is quite nuanced, encompassing numerous questions:

Do participants understand what data is being collected about them?
What harm would befall them should that data be made public?
Would they expect that data to be considered private and confidential?
For example, if participants are being observed in a public setting (e.g., a football stadium), there is really no expectation of privacy. If the study is on existing public data, then there is also no expectation of further confidentiality.

If, however, new data is being gathered, then the questions come down to:

What data is being gathered? How sensitive is it? Does it include financial and health data?
Can the data being gathered be tied to the individual, i.e., is it considered personally identifiable?
How is the data being handled, with what security? What level of confidentiality can participants expect?
What harm would befall the individual should the data become public, where the harm would encompass health, psychological / emotional, social, and financial concerns?
For example, often times, collected data from observed “public” behavior, surveys, and interviews, if the data were not personally identifiable, would be considered exempt from IRB review (reference: NSF FAQ below).

To summarize, there are really three main issues with data collection with regards to experiments:

For new data being collected and stored, how sensitive is the data and what are the internal safeguards for handling that data? E.g., what access controls are there, how are breaches to that security caught and managed, etc.?
Then, for that data, how will it be used and how will participants’ data be protected? How are participants guaranteed that their data, which was collected for use in the study, will not be used for some other purpose? This becomes more important as the sensitivity of the data increases.
Finally, what data may be published more broadly, and does that introduce any additional risk to the participants?
Difference between pseudonymous and anonymous data
One question that frequently gets asked is what the difference is between identified, pseudonymous, and anonymous data is.

Identified data means that data is stored and collected with personally identifiable information. This can be names, IDs such as a social security number or driver’s license ID, phone numbers, etc. HIPAA is a common standard, and that standard has 18 identifiers (see the Safe Harbor method) that it considers personally identifiable. Device id, such as a smartphone’s device id, are considered personally identifiable in many instances.

Anonymous data means that data is stored and collected without any personally identifiable information. This data can be considered pseudonymous if it is stored with a randomly generated id such as a cookie that gets assigned on some event, such as the first time that a user goes to an app or website and does not have such an id stored.

In most cases, anonymous data still has time-stamps -- which is one of the HIPAA 18 identifiers. Why? Well, we need to distinguish between anonymous data and anonymized data. Anonymized data is identified or anonymous data that has been looked at and guaranteed in some way that the re-identification risk is low to non-existent, i.e., that given the data, it would be hard to impossible for someone to be able to figure out which individual this data refers to. Often times, this guarantee is done statistically, and looks at how many individuals would fall into every possible bucket (i.e., combination of values).

What this means is that anonymous data may still have high re-identification risk (see AOL example).

So, if we go back to the data being gathered, collected, stored, and used in the experiment, the questions are:

How sensitive is the data?
What is the re-identification risk of individuals from the data?
As the sensitivity and the risk increases, then the level of data protection must increase: confidentiality, access control, security, monitoring & auditing, etc.
