# Assessing the Impact of New Advertising Campaign vs Old Campaign: An A/B testing Portfolio Project
Dataset source from Kaggle: https://www.kaggle.com/datasets/osuolaleemmanuel/ad-ab-testing

## Overview
Advertising plays a pivotal role in any business, contributing significantly to its success. While the creation of new advertisements is a common practice, it is important to note that the effectiveness of an ad is not solely determined by its novelty. To make informed decisions regarding advertising strategies, conducting research, such as A/B testing, is essential.

The dataset contains information related to auction_id, experiment, date, hour, browser, device, operating system (OS), and response. This dataset is utilized for research purposes to assess whether a company should implement new ad designs to enhance its performance or not.

## Data Description
| Field         | Description                                                                   |
|---------------|-------------------------------------------------------------------------------|
| auction_id    | The unique ID of the online user who has been presented the BIO. In standard terminologies, this is called an impression ID. The user may see the BIO questionnaire but choose not to respond. In that case, both the 'yes' and 'no' columns are zero.  |
| experiment    | Which group the user belongs to - control or exposed.                         |
| control       | Users who have been shown a dummy ad.                                        |
| exposed       | Users who have been shown a creative, online interactive ad, with the SmartAd brand.  |
| date          | The date in YYYY-MM-DD format.                                               |
| hour          | The hour of the day in HH format.                                            |
| device_make   | The name of the type of device the user has, e.g., Samsung.                   |
| platform_os   | The ID of the OS the user has.                                                |
| browser       | The name of the browser the user uses to see the BIO questionnaire.          |
| yes           | 1 if the user chooses the “Yes” radio button for the BIO questionnaire.      |
| no            | 1 if the user chooses the “No” radio button for the BIO questionnaire.       |

- Rows: 8077
- Columns: 8
- Null values: 0
- Duplicates: 0

## Experiment Approach
The objective of this study is to analyze the outcomes of the A/B test and determine the optimal advertising strategy. It aims to assess how such a strategy might impact customer behavior, specifically their responses to the BIO questionnaire.

- Null Hypothesis (H<sub>o</sub>): *p* = *p*<sub>o</sub>​ - There is no statistically significant difference in the success rate of the advertising strategies between the two groups.
- Alternative Hypothesis (H<sub>a</sub>): *p* &ne; *p*<sub>o</sub> - There is a statistically significant difference in the success rate of the advertising strategies between the two groups. It is important to note that we are not making any assumptions about whether the new design will perform better, worse, or equally to the current design; we are simply conducting a two-tailed test to explore the differences.
- Confidence Level: 95%(α=0.05)
- In this context, *p* and *p*<sub>o</sub>​ represent the conversion rate of the new and old advertising strategy designs, respectively.

### Explarotary Data Analysis
#### Response
![no_response](image/no_res.png)

| Response % |  Yes  |   No   |
|------------|-------|-------|
| Experiment |       |       |
| Control    | 45.05 | 54.95 |
| Exposed    | 46.88 | 53.12 |

The graph illustrates that a substantial portion of the BIO questionnaires received no response, with only 14.39% in the control group and 16.40% in the exposed group providing answers. As a result, our analysis primarily focuses on individuals who responded to the BIO questionnaire.

![response](image/res.png)
| Response % |  Yes  |   No   |
|------------|-------|-------|
| Experiment |       |       |
| Control    | 45.05 | 54.95 |
| Exposed    | 46.88 | 53.12 |
Both groups now exhibit similar conversion rates, approximately in the range of 45-47%.

#### Hour
![anomaly](image/anomaly.png)

The graph depicts variations in hours between the two groups during experiments conducted on different days. Notably, there are extreme values observed for users in the control group during a 15-hour period on the first day of the experiment.

#### Device
![wc1](image/wc1.png)
![wc2](image/wc2.png)

The most commonly used device in both test groups is dominated by:
- Generic Smartphone
- Samsung
- Iphone
- Nokia
- Pixel
  
#### Browser
![browser](image/browser.png)

| browser usage % | Samsung | Chrome | Facebook | Safari |
|-----------------|---------|--------|----------|-------|
| Experiment      |         |        |          |       |
| Control         | 15.02   | 63.65  | 19.11    | 2.22  |
| Exposed         | 8.68    | 84.02  | 6.70     | 0.61  |

The chart and table below depict the predominant browser usage in both experimental groups, with Chrome emerging as the most commonly used browser.

#### Operating System(OS)

![os](image/os.png)

The preeminent operating system in both groups is OS 6.

#### Summary EDA

- Approximately 83-86% of users did not respond to the questionnaire.
- Both groups exhibited similar conversion rates with only a 2% difference.
- The sizes of the control and exposed groups are comparable.
- The experiment spanned a week.
- Anomalously, there were 249 users in the control group on March 7, 2020, at 15:00 hours, while the mean value remained at 24.
- The most frequently used devices in both the control and exposed groups are as follows:
    - Generic Smartphone
    - Samsung
    - iPhone
    - Nokia
    - Pixel
- The Chrome browser was the most popular choice for most users in both groups:
    - 63.65% for the control group
    - 84.02% for the exposed group
- The majority of users in both groups used platform_os version 6.


### Statistical Analysis
To assess whether the new advertising campaign has a significant impact on the conversion rate, we need to estimate the significance of the difference between the results obtained with the old and new ads.

**Formula**
- Null Hypothesis (H<sub>o</sub>): *p* = *p*<sub>o</sub>​ - There is no statistically significant difference in the success rate of the advertising strategies between the two groups.
- Alternative Hypothesis (H<sub>a</sub>): *p* &ne; *p*<sub>o</sub> - There is a statistically significant difference in the success rate of the advertising strategies between the two groups. It is important to note that we are not making any assumptions about whether the new design will perform better, worse, or equally to the current design; we are simply conducting a two-tailed test to explore the differences.
- Confidence Level: 95%(α=0.05)
- In this context, *p* and *p*<sub>o</sub>​ represent the conversion rate of the new and old advertising strategy designs, respectively.

#### Chi-square Contingency
- The Chi-square Contingency test can be employed to assess the association or independence between both groups.
- There are several assumptions to consider when conducting the Chi-square Contingency test:
    - Random sampling - data in each group should be randomly sampled.
    - Independence - each observation should not influence other observations significantly.
    - Mutually exclusive groups - each group should be mutually exclusive.
- All of these assumptions are met in this case:
    - The data is collected randomly without any particular bias.
    - Each user's decision is independent of others.
    - The responses are binary, either 'yes' or 'no.'

##### Homogeneity Test
###### Test 'yes', 'no' and 'no response'
| Statistic | Value            |
|-----------|------------------|
|Chi-square statistic | 6.6549 |
|p-value    | 0.0359           |
|DOF        | 2                |
|Expected Frequencies | [[ 283.6984,  332.8000 3389.5015 ] <br> [ 288.3016,  338.1999, 3444.4984 ]]                             |

Conducting a Chi-square Homogeneity test on the 'yes,' 'no,' and 'no_response' data groups resulted in a p-value less than the predetermined alpha level of 0.05, signifying statistical significance. Consequently, we reject the null hypothesis (H<sub>o</sub) and infer that the two groups manifest distinct response proportions

###### Test 'yes', and 'no'
| Statistic | Value            |
|-----------|------------------|
|Chi-square statistic | 0.3465 |
|p-value    | 0.5561           |
|DOF        | 1                |
|Expected Frequencies | [[269.6637, 316.3363] <br> [302.3363, 354.6637]]      |

Among all respondents, there is no significant difference observed between the exposed and control groups concerning 'yes' and 'no' data. This is reflected in the p-value of 0.5561, which exceeds the predetermined alpha level of 0.05. Consequently, we cannot reject the null hypothesis (H<sub>o</sub>).

##### Proportion Test Two-sided
###### Two-sided Test 'yes', 'no', and 'no response'
| Data | Value  |
|------|--------|
|Stat   | 2.1083 |
|p-value| 0.035  |

###### Two-sided Test 'yes', and 'no'
| Data | Value  |
|------|--------|
|Stat   | 1.3063 |
|p-value| 0.191  |

##### One-sided Proportion Test
###### Two-sided Test 'yes', 'no', and 'no response'
`Larger Test`
| Data | Value  |
|------|--------|
|Stat   | 2.1083 |
|p-value| 0.018  |

`Smaller Test`
| Data | Value  |
|------|--------|
|Stat   | 2.1083 |
|p-value| 0.982  |

###### Two-sided Test 'yes', and 'no'
`Larger Test`
| Data | Value  |
|------|--------|
|Stat   | -0.6457 |
|p-value| 0.518   |

`Smaller Test`
| Data | Value  |
|------|--------|
|Stat   | -0.6457 |
|p-value| 0.741   |

**Conclusion of proportion test:**
- To reject the null hypothesis, a p-value below the alpha level of 0.05 is required. Based on the data, the following p-values were obtained:
    - Statistically Significant
        - Proportion test two-sided 'yes', 'no', and 'no_response': 0.035
        - Proportion test one-sided (larger) 'yes', 'no', and 'no_response': 0.018
    - Not Statistically Significant
        - Proportion test two-sided 'yes', 'no': 0.191
        - Proportion test one-sided (smaller) 'yes', 'no', and 'no_response': 0.982
        - Proportion test one-sided (larger) 'yes', 'no': 0.518
        - Proportion test one-sided (smaller) 'yes', 'no': 0.741

### Conclusion
- If the main goal is to enhance the overall success rate among individuals, implementing new advertising designs to attract new customers may prove effective.
- However, if the main goal is to focus on the individuals who respond to the advertisement, maintaining the existing ad within the advertising strategies is recommended.
