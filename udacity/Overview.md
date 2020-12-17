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
**Customer Funnel** Homepage visits (most population) > explore website > create account > complete course/made purchase (least population).
Initial hypothesis: Changing the color of the start now button from orange to pink will ~~increase the number of people exploring the course page~~ increase the click through probability of the button (and assume that this will increase the final business metric - total course completed)
Which metrics?
1. # of users completed course -> takes time.
2. # of clicks. -> too much noise
  2.1: **click-through-rate**: # of clicks / # of page views
  2.2: **click-through-probability**: # unique visitors who click / # unique visitors to page.  
  e.g. 2 visitors, a clicks 0 times b clicks 5 times, CTR = 5/2; CTP = 1/2
  
> Use a rate to measure **usability** and use a probability to measure **total impact**.
e.g. usability measures how often a user find that button on a variety of buttons that they can click on. probability to measure how often a user went to the second page - we don't care if the user double-clicked, reload etc.
  
