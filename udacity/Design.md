## Choose subject
Unit of Diversion
1. User id
   - Stable, unchanging
   - personally identifiable
2. Anonymous id (cookie)
   - Changes when you switch browser or device
   - users can clear cookies
3. Event
   - No consistent experience
   - use only for non user visable changes

Less common:
- Device id
  only available for mobie, tied to specific device, unchangeable by user. persnonally id
- IP address
  change when address changes

How to choose between these units? These considerations
- consistency across the things you want to test. go for user id/cookies if we do user visibility changes.
  what do you want to measure. choose user id/cookies/event based even for changes that are not visible, like latency, ranking change.
- ethical considerations. don't include PII
- variability

 

## Choose population
Intra-user experiment
Inter-user experiment - what we usually do with A/B testing. Different users in different groups.
Target population.

Populations vs Cohort.
Cohort: subset of the population of people enter certain event with same character, eg.at the same time/.
Use cases of cohort:
- learning effect
- user retention
- increase user activity
- anything requiring user to be estabilished

## Size


## Duration

**learning effects**
- change aversion - don't try anything
- novelty effect - accept everything 
It takes time for users to adapt to a change and measure the learning effect. We don't have that much time to wait for it.
smaller proportion of users and longer period of time if we want to test it out.
Risk and duration

