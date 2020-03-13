# Exploration of US healthcare spend

---

## Executive Summary

Few issues in the United States stir up as much emotion, controversy, and debate as US healthcare. Hailed as one of the best in the world it is also derided for its high costs.  We propose to conduct a high level exploration of US healthcare spend on two issues concerning healthcare costs:

> 1) One of the common perceptions about the rise in US healthcare costs is concerning the role of Medicare, the federal health insurance for people 65 or older and people with disabilities. Often the perception is that when Medicare pays less for a procdure, the hospital must raise the costs for thrid party insurers to make up the difference.  Is this true?  What is the correlation, if any, between Medicare payments and overall payments for medical procedures?

> 2) Politicians are often reluctant to address healthcare costs not just because of how it persnally affects every citizen, but also because the healthcare sector as a whole often represents big business and one of the largest employers in their district.  Could political lobbying be an influencer?  What is the correlation, if any, of lobbying spend and overall charges and payment for healthcare?

The goal was explore historic data on US healthcare costs and healthcare lobbying funding and determine if there were any correlations to the data using the Pearson correlation coefficient.

#### Initial results

Regarding issue 1) the role of Medicare:

- On the whole, for the entire United States there is a positive correlation of between Medicare payments and payments by all providers.  This means that Medicare payments, though on average lower than third party payments, move in sync with thrid party payments, i.e. if Medicare payments go down, then all payments go down. This would contradict common perceptions.  BUT the data also yielded a very high p-value to accept this correlation. Driving this uncertatinty is the role of each US state and costs associated with differing procedures.
(0.6238128288078792, 0.1343761207827625)

Regarding issue 2) the role of lobbying:

- On a whole, BOTH lobbying for health issues and the amount hospitals charge for procedures have increased over time. For our analysis from 2011 - 2017 there is a strong correlation between the two.
Entire US: (0.6472017179539473, 0.11610124607018191)

- additional commentary on individual states.

---


 

---

## Notebook contents

RIGHT NOW everything is in one notebook , but will be separated...

Notebook: Data 

- describe ...

Notebook : EDA

- describe ...

---

## Data sources

Raw data is sourced from the following sites:

### 1. Inpatient charge data

Source: https://www.cms.gov/Research-Statistics-Data-and-Systems/Statistics-Trends-and-Reports/Medicare-Provider-Charge-Data/Inpatient2017

This data set provides the charges and payments of healthcare procedures for the years 2011-2017 for more than 3,000 U.S. hospitals.  Charges are for 100 common diagnoses in years 2011-2013 and for 560 common diagnoses for years 2014-2017.  Each year consisted of 160k-200k rows of data.

|Column|Type|Dataset|Description|
|---|---|---|---|
|DRG Definition|string |Inpatient charge data|Code and description of diagnosis|
|Provider Id|int|Inpatient charge data|Id assigned to Medicare-certified facility|
|Provider Name|string|Inpatient charge data|Name of provider/ facility|
|Provider Street Address|string|Inpatient charge data|Provider address|
|Provider City|string|Inpatient charge data|City where provider is located|
|Provider State|string|Inpatient charge data|State where the provider is located|
|Provider Zip Code|int|Inpatient charge data|Zip where the provider is located|
|Hospital Referral Region|string|Inpatient charge data|Region where the provider is located|
|Total Discharges|int|Inpatient charge data|Number of patientsbilled by the provider|
|Average Covered Charges|float|Inpatient charge data|What the provider charges for that DRG/ diagnosis|
|Average Total Payments|float|Inpatient charge data|Average total payments for the DRG. Also included in average total payments are co-payment and deductible amounts that the patient is responsible for and any additional payments by third parties for coordination of benefits|
|Average Medicare Payments|float|Inpatient charge data|Average amount that Medicare pays to the provider for Medicare's share of the DRG|


### 2. United States Senate Lobby Disclosure Act reports

Source: https://www.senate.gov/legislative/Public_Disclosure/LDA_reports.htm

This data set was collected from the US Senate Lobby Disclosure Act (LDA) database.  The LDA database was queried on 'Health Issues' and individual US states.  The data provides lobbyist funding for 50 states from 1999-2019.  Data for each US state ranged from 1000 to 13,000 entries.

|Column|Type|Dataset|Description|
|---|---|---|---|
|State|string|LDA Report|State where client is located|
|Registrant Name|string|LDA Reports|Name of registrant/ lobbyist|
|Client Name|string|LDA Reports|Name client|
|Filing Type|string|LDA Reports|Type of report/ reporting period|
|Amount Reported|float|LDA Reports|Amount of funds client sent thru lobbyist|
|Date Posted|string|LDA Reports|Date report posted|
|Filing Year|int|LDA Reports|Filing year|


### 3. United States census data

Source: https://www.census.gov/data/tables/time-series/demo/popest/2010s-state-total.html

Provides population of 50 states from the 2010 census.

|Column|Type|Dataset|Description|
|---|---|---|---|
|State|string|US Census population|US State|
|Population|int| US Census Population|Population for that US state|

---
### Data assumptions and limitations

List the assumptions and limitations here:

- Inpatient charge data only for US hospitals which recieve US Medicare payments.  Private or military hospitals, clinics, and facilities not included.
- Inpalient charge data for 2011 - 2013 recorded for 100 common diagnoses, 2014-2017 for 560 diagnoses.  Not all US hospitals/ states registered all these diagnoses.  Healthcare spend based on 93 common procedures.
- US lobbying information is base on US Senate LDA database.  
- list more here. ...
- list


---

## Results

What is the correlation between ...





---

## Conclusions and Recommendations

Discuss conclusions here.

Recommendations will be for more future work.


---

## References

- https://www.bostonglobe.com/metro/2019/02/02/healthcare-industry-tops-list-state-lobbyist-expenses/bTvc7YWp7Ign2LB6ZaQDRN/story.html
- https://www.healthcaredive.com/news/myth-diagnosis-do-hospitals-charge-more-to-make-up-for-low-government-pay/560021/
- https://www.healthsystemtracker.org/chart-collection/u-s-spending-healthcare-changed-time/#item-nhe-trends_total-national-health-expenditures-us-billions-1970-2018
- https://www.nytimes.com/2019/05/09/health/hospitals-prices-medicare.html
- https://www.healthcaredive.com/news/hospital-lobbying-in-2018-by-the-numbers/548262/
- https://www.senate.gov/legislative/Public_Disclosure/LDA_reports.htm
- https://factfinder.census.gov/faces/nav/jsf/pages/guided_search.xhtml