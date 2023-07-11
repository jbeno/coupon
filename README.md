# coupon
This is an analysis of [in-vehicle coupon recommendations](https://archive.ics.uci.edu/dataset/603/in+vehicle+coupon+recommendation) data from Amazon Mechanical Turk. It was done as a project for the U.C. Berkeley Certificate in Machine Learning & Artificial Intelligence. The entire process is documented in this Jupyter notebook file:
* [coupon.ipynb](coupon.ipynb)

# Summary of Findings

## Participant Demographics

Here's what we learned about the participants of this survey:

* Most participants were **Employed** (68.67%)
* A number of them were Unemployed (15.02%) or Students (12.39%) or Retired (3.92%)
* **Computer & Mathematical** was the top occupation (11.33%) for those employed
* Most had **Some College** (34.93%) or a **Bachelor's degree** (33.29%)
* Most had an income in the range of **\$25,000 - \\$37,499** (15.87%)
* Most were in the between the **Ages of 21-30** (41%)
* There's about an even split between Married (40%) and Single (37.98%)
* It was also an even split between Males (48.68%) and Females (51.32%)
* Most had **no children** (59.15%)
* Most never went to bars (40.97%)
* Most went to cheap restaurants 1-3 times a month (42.38%)
* Most went to \$20-\\$50 restaurants less than once a month (47.91%)

## General Correlations

We saw the following correlations between variables in this study:

* The strongest positive correlation is between **Age and Has Children**, it's moderate at 0.44. This is not suprising, the older you are, the more likely you are to have children.
* The strongest negative correlation is between **Distance and Direction**, it's moderate at -0.32. This is between 2 scenario variables, and not a participant's response to a scenario variable, so not very meaningful (I'll exclude any other correlations between survey scenario variables)
* **Income and Education Years** had a moderate positive correlation at 0.3
* **Age and Employed** had a weak positive correlation at 0.21
* **Age and Education Years** had a weak positive correlation at 0.18
* **Bar and Has Children** had a weak negative correlation at -0.17, suggesting people with children frequent bars less
* **Bar and Age** had a weak negative correlation at -0.15, suggesting younger people frequent bars more often

## Coupon Acceptance

Here's what we learned about Accepted Coupon (Yes or No) our main variable of interest:

* **Most said "Yes"** - The majority (56.93%) of the participants in the study chose to accept the coupon.
* **Heat made a Difference** – When it was 80 degrees, 59.96% of coupons were accepted, which is larger than 53.71% in the other temperature conditions

We also saw the following correlations, which could be clues to variables with predictive power:

* **Carry Out Coupons** had a weak positive correlation at 0.16, suggesting people were more likely to accept a coupon for take-out. It's probably easier to be spontaneous for picking up take-out vs. a dine-in experience. This was the strongest positive correlation with coupon acceptance.
* **Cheap Restaurants** had a weak positive correlation at 0.15, contrasting with **Restaurants** \$20-\\$50, which had a weak negative correlation at -0.09. This suggests people were more likely to accept a coupon for cheap vs. more expensive restaurants.
* **Expiration** had a weak positive correlation at 0.13, meaning people were more likely to accept a coupon if they had more time before it expired.
* **Friend as a Passenger** had a weak positive correlation at 0.13, contrasting with **Driving Alone**, which had a weak negative correlation at -0.1. This suggests people were more likely to accept a coupon if they had a friend in the passenger seat vs. being alone. Perhaps it would viewed as a fun thing to do with a friend.
* **Sunny Weather** had a weak positive correlation at 0.1, which suggests a slight tendency to accept coupons more if it was sunny out.
* **Bar Coupons** had a weak negative correlation at -0.14, which suggests people were less likely to accept coupons for a bar. Given that most participants in this survey never went to bars (40.97%), this makes sense. This was the strongest negative correlation with coupon acceptance.
* **Distance** had a weak negative correlation at -0.11, which suggests the further away the coupon destination was, the less likely they were to accept. This makes sense for a spontaneous decision.
* **Coffee Coupons** had a weak negative correlation at -0.1, which suggests people were less likely to accept a coupon for a Coffee House. When we look at the demographic data, we see that more than half of the participants in this survey never go to a Coffee House, or go less than once a month. So this is not surprising.
* **Work Destination** had a weak negative correlation at -0.08, which suggests people were less likely to accept a coupon while on their way to work. This is understandable, as you usually have to show up at work on time. There is less of an opportunity to be spontaneous in that scenario.

## Bar Coupons

Here's what we've learned from our investigation of Bar Coupons:

* **Most bar coupons were accepted by frequent bar visitors** – 76.17% of those who went to a bar 4 times a month or more accepted the coupon, vs. 52.79% for those that went 3 or fewer times a month. This suggests that the more people typically visit a bar, the greater chance that they will accept a bar coupon.
* **Most had passengers that were not a child** – 71.43% of those that went to a bar 1 or more times a month, had passengers that were not a kid. 
* **Most were between the ages of 25-30** – Now we have a few data points to support this:
    * 68.98% of those who went to a bar 1 or more times a month, and were over the age of 25, accepted the coupon.
    * 71.95% of those who went to a bar 1 or more times a month, and were under the age of 30, accepted the coupon.
    * Based on the encoded Age data, the **mean age is 30.75** for those that accepted. The mean age for those that declined was 33.45
     * There is a significant change in behavior once you are over 50. We'd have to interview them to understand the driver, but perhaps its related to health concerns or lifestyle changes

## Coffee Coupons

Here's what we've learned from our investigation of Coffee Coupons:

* **Coffee coupon accepts/declines were evenly split** - 49.63% of the Coffee coupons were accepted. This is less than the overall acceptance rate of 56.93%, but higher that what we saw for Bars (41.19%). Looks like buying a coffee might be more of a spontaneous purchase than going to a bar.
* **Frequency of Visits, No Urgent Place, and Student had positive correlations** with acceptance of coffee coupons.
    * **Frequency of visits to Coffee Houses** had a weak positive correlation at 0.21, suggesting people were more likely to accept a coffee coupon the more frequently they visit a coffee shop. 65.90% of those who went to a coffee shop 1 or more times a month accepted the coupon, vs. 48.10% that went less (not including those that went never). 
    * **No Urgent Place destination** had a weak positive correlation at 0.18, contrasting with **Home**, which had a weak negative correlation at -0.15. This suggests people were more likely to accept a coffee coupon when they had no urgent destination to reach, and less likely to accept when they were heading home (perhaps because it's the end of an excursion). There were more accepts than declines in one condition only: "No Urgent Place".
    * **Student as an occupation** had a weak positive correlation at 0.09, which suggests students may be more likely to accept a coupon for coffee. "Student" was the second largest occupation when ranked by number of accepts, and there were substantially more accepts than declines compared to the other occupations.
* **Younger people accepted coffee coupons more than older people**. There was roughly an equal ratio of accepts vs. declines in most age brackets. The exception was "50 plus", which has more declines, and "below 21", which had more accepts.
* **Males that accepted coffee coupons were younger than females that accepted**. "Males" that Accepted the coffee coupon had a median age of 26 years. The rest had a median age of 31 years.

## Hypotheses Evaluation

We had a number of hypotheses at the start of this project. Let's review them now, and see if our analysis supports them or not.

* People that frequent bars more often are more likely to accept a bar coupon
    * &#x2705; **Supported**: Most bar coupons were accepted by frequent bar visitors – 76.17% of those who went to a bar 4 times a month or more accepted the coupon, vs. 52.79% for those that went 3 or fewer times a month. This suggests that the more people typically visit a bar, the greater chance that they will accept a bar coupon.
* People with lower income are more likely to accept a coupon for lower-cost restaurants
    * **Not Evaluated**: Due to limitations in time, this relationship was not explored. It can be a topic for future research.
* Bad weather would decrease the probability of accepting a coupon
    * &#x2705; **Supported**: Sunny weather had a weak positive correlation at 0.1, while Rainy and Snowy weather both ahd a weak negative correlation at -0.7. This suggests a slight tendency to accept coupons more if it was sunny out, and decline them if the weather was bad.
* People that often buy take-out would more likely accept a take-out copon
    * **Not Evaluated**: Due to limitations in time, this relationship was not explored. It can be a topic for future research.
* People that frequent coffee shops would be more likely to accept a coffee coupon
    * &#x2705; **Supported**: Frequency of visits to Coffee Houses had a weak positive correlation at 0.21, suggesting people were more likely to accept a coffee coupon the more frequently they visit a coffee shop. 65.90% of those who went to a coffee shop 1 or more times a month accepted the coupon, vs. 48.10% that went less. 
* People driving alone would be more likely to accept a coupon for a bar in 2 hours
    * &#x274C; **Not Supported**: For all coupons (not just bar coupons), Friend as a Passenger had a weak positive correlation at 0.13, contrasting with Driving Alone, which had a weak negative correlation at -0.1. This suggests people were more likely to accept a coupon if they had a friend in the passenger seat vs. being alone.
* People driving with kids would be more likely to accept a coupon for a cheap restaurant in 2 hours
    * **Not Evaluated**: Due to limitations in time, this relationship was not explored. It can be a topic for future research.
* Close proximity would increase the chance of accepting a coupon in 2 hours
    * **Partially Supported**: Distance had a weak negative correlation at -0.11, which suggests the further away the coupon destination was, the less likely they were to accept. However, expiration time was not evaluated, and should be explored in future research.
* No urgent destination would increase the chance of accepting a coupon in 2 hours
    * **Partially Supported**: For coffee coupons, No Urgent Place destination had a weak positive correlation at 0.18, contrasting with Home, which had a weak negative correlation at -0.15.
* People that are unemployed would be more likely to accept a coupon
    * **Partially Supported**: For coffee coupons, "Unemployed" had the largest amount of people accepting coupons, and more people accepted coupons than declined. But it was not the strongest correlation with occupation.
