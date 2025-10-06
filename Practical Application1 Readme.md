# **Takeaway Coupon Acceptance Analysis**
This project analyzes a dataset to identify the target demographic most likely to accept a coupon for a takeaway meal. T

# **Link to Jupyter Notebook **
https://github.com/rooparb-cyber/MLPortfolio/blob/4890e534bac9ddc474f558f3c01ae28f7a66f388/Practical%20Application1%20Independent.ipynb

# ** Key Findings**
The analysis focused on multiple demographic features: gender, age, marital status, children, takeout frequency.  Coupon expiration was also considered as a possible factor.

## _Analysis by Gender_
When comparing coupon acceptance rates between genders, a noticeable difference emerged.

Males showed a 4.5% higher acceptance rate than females for the takeaway coupon in this dataset.

It's important to note that while there is an observable difference, further tests would be required to confirm if this result is statistically significant and not due to random chance.

## _Analysis by Age and Gender_
Drilling down into specific age groups revealed distinct patterns within each gender.

46-year-old females had a notably high acceptance rate compared to other females.

36-year-old males stood out with a particularly high acceptance rate among all male age groups.

These specific age brackets appear to be sweet spots for this type of promotion.

## _Analysis by Gender and Marital Status_
Marital status also appears to be a significant factor in coupon acceptance, with clear trends among different groups.

Divorced men showed the highest acceptance rates among all male groups and a very high rate overall.

Widowed females also demonstrated a high acceptance rate, though slightly lower than that of divorced males.

A key limitation here is the small sample size for widowed individuals (19 females and 7 males). The data for this group may not be as representative as for larger demographic segments.

## _Analysis By Children_
There doesn't appear to be a large or practically significant difference in coupon acceptance rates between drivers with and without children for 'Carry out & Take away' coupons in this dataset.

## _Analysis By Past Take out frequency_
There is a higher acceptance rate for 'Carry out & Take away' coupons among drivers with at least one carry away visit in the past month.

## _Analysis By Coupon Expiration_
Analysing by grouping the dataset into over 25 minute expiration v/s under did not show a significant difference in acceptance rates, but the samples seem skewed more towards the under 25 bucket.  Splicing by more granular expiration seems to show a higher acceptance rate in the 5 minute expiration bucket.  However, while there appears to be a correlation, particularly for the 'under 5 minutes' bucket,  the relationship isn't a simple step-wise increase as the same pattern seems to be asbsent in the next bucket.  Further the differing sample sizes across groups makes this observation discountable.

## _Income Levels_
Income levels show some fluctuations in acceptance rates across different income brackets and genders for "Carry out & Take away" coupons.

# ** Tying findings together**
## Overall Impact of Carry Away Frequency: 
The most striking observation is the significant difference in acceptance rates between the two carry away frequency groups. Drivers who had 'AtleastOnce' carry away in the past month generally show much higher acceptance rates across most age and gender combinations compared to those in the 'neverLess1' group. This reinforces our earlier finding that prior carry away behavior is a strong indicator of coupon acceptance for this type of coupon.
### Age and Gender within 'AtleastOnce' Group: 
Within the 'AtleastOnce' group, acceptance rates are relatively high across most age groups and for both genders. There are some variations, but the rates are generally clustered in the 0.7 to 0.9 range.
### Age and Gender within 'neverLess1' Group: 
In the 'neverLess1' group, acceptance rates are generally lower. The patterns across age and gender in this group appear more variable, possibly due to smaller sample sizes in some bins.
### Specific Age/Gender Highlights (revisiting previous observations):
- For 36-year-old males, their high acceptance rate is visible in both frequency groups, being particularly high in the 'AtleastOnce' group.
- For 46-year-old females, their high overall acceptance rate seems to be notably high in the 'neverLess1' group in this breakdown, although their rate in the 'AtleastOnce' group is also strong. This highlights that even among those who don't frequently get carry away, 46-year-old females who are offered a 'Carry out & Take away' coupon have a high propensity to accept it.
In essence, the graph reveals that prior carry away frequency is a major differentiator in acceptance rates, and while age and gender play a role, their influence is seen within the context of this frequency. The high acceptance rates for certain age/gender groups (like 36-year-old males and 46-year-old females) are evident, and the plot helps to see how these rates break down based on their carry away frequency.

# ** Conclusion & Target Profile**
Based on the analysis, customers who have ordered takeaway in the past month are the most likely group to accept a coupon.

Within that group, 36-year-old males represent a key target, while 46-year-old females are a prime target for converting infrequent users.

# ** Potential Follow-up Actions and Hypotheses for Carry out & Take away Coupons**
Based on the analysis, which showed generally high acceptance rates with some variations across demographics and behaviors, here are some follow-up actions you could consider:

## Explore Income Level Nuances

### Action
While overall acceptance is high, the income level analysis shows some fluctuations. Investigate the reasons behind the lower acceptance rates in certain income brackets, such as females in the $62,500 - $74,999 income bracket or males in the $75,000 - $87,499 bracket.
Hypothesis: Factors beyond income, such as lifestyle, location, or specific needs within these income groups, might be influencing their coupon acceptance. Tailored offers or partnerships could be beneficial.

## Analyze Coupon Redemption vs. Acceptance

### Action
If redemption data is available, compare coupon acceptance rates with actual redemption rates to understand if there are any significant drop-offs between someone accepting a coupon and actually using it.
Hypothesis: There might be other factors influencing whether an accepted coupon is redeemed, such as the convenience of the location, the timing of the offer, or the specific terms and conditions of the coupon.
