# Exploration of US healthcare spend

---

## Executive Summary

### Problem Statement

Few issues in the United States stir up as much emotion, controversy, and debate as US healthcare. Hailed as one of the best in the world it is also derided for its high costs.  We propose to conduct a high-level exploration of US healthcare spend on two issues:

> 1) One of the common perceptions about the rise in US healthcare costs is concerning the role of Medicare, the federal health insurance for people 65 or older and people with disabilities. Often the perception is that when Medicare pays less for a procedure, the hospital must raise the costs for third party insurers to make up the difference.  Is this true?  What is the correlation, if any, between Medicare payments and overall payments for medical procedures?

> 2) Politicians are often reluctant to address healthcare costs not just because of how it personally affects every citizen, but also because the healthcare sector as a whole often represents big business and one of the largest employers in their district.  Could political lobbying be an influencer?  What is the correlation, if any, of lobbying spend and overall charges and payment for healthcare?


### Methodology

The goal is to explore historic data on US healthcare costs and healthcare lobbying funding and determine if there were any correlations to the data using the Pearson correlation coefficient.


### Results

Regarding issue 1) the role of Medicare:

- For the given data there is a positive correlation of **0.624** between that which is paid by Medicare and that which is paid by all providers.  This means that from 2011 - 2017 for 50 US states and 93 common diagnoses, the amounts paid by Medicare and third parties are 'in sync', i.e. all payments go up / down together.

- A positive correlation between payments can be seen in most individual US states and most individual diagnoses as well.

- Positive correlations contradict common perception of lower Medicare resulting in higher third party payments. 

Regarding issue 2) the role of lobbying:

- For the given data there is a positive correlation of **0.690** between what is lobbied for health and Medicare issues and the amount hospitals charge for diagnoses.  This means that from 2011 - 2017 for 50 US states and 93 common diagnoses, the amount hospitals charge for these diagnoses is 'in sync' with what is lobbied, i.e. all are rising with time. BUT taken historical lobbying data from 1999 - 2019 into , there is a a strong positve correlation of 0.999 between what is lobbied for health and Medicare issues and the amount hospitals charge for diagnoses.
 
- A positive correlation affirms that lobbying by state and national organizations has an impact on healthcare charges for citizens and infers that health costs will continue to rise together with lobby dollars.

- This positive correlation cannot be seen in individual US states or individual diagnoses. The lobbying is highly variable between states.

---

## Conclusions and Recommendations

This exploration is just touching the surface of comparing healthcare costs and lobbying spending.  Although the data is far from complete in representing all fo the United States in the lens of healthcare, there is much more to be inferred. 

Future analysis should focus on specific states or regions of the US to determine how state policies affect healthcare charges and payments.

In addition to looking at individual states, future analysis can compare specific hospital systems - how much they lobby and how much they charge patients.


---


## Notebook contents

Notebook Data 
1. Cleaning inpatient charge data. 
2. High level exploration of inpatient charge data
3. Cleaning Lobbying Disclosure Act data
4. High level exploration of LDA data

Notebook EDA
1. Importing cleaned data
2. Explore Correlation between how much is paid by Medicare vs how much is paid by all providers (including Medicare)
3. Explore correlation between how much hospitals charge for diagnoses vs how much is lobbied.

---

## Data sources

Raw data is sourced from the following sites:

### 1. Inpatient charge data

Source: https://www.cms.gov/Research-Statistics-Data-and-Systems/Statistics-Trends-and-Reports/Medicare-Provider-Charge-Data/Inpatient2017

This data set provides the charges and payments of healthcare procedures for the years 2011-2017 for more than 3,000 U.S. hospitals.  Charges are for 100 common diagnoses in years 2011-2013 and for 560+ common diagnoses for years 2014-2017.  Each year consisted of 160k-200k rows of data.

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

This data set was collected from the US Senate Lobby Disclosure Act (LDA) database.  The LDA database was queried on 'Health Issues' and 'Mediare/Medicaid issues' for each individual US state.  Data is for years 1999 - 2019 for each US state and is based on the clients' home state (and not lobbyists state). Data for each state ranges from 1000 to 13,000 entries.  DC is not included.

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

Although there is a lot of data on healthcare charges/payments as well as lobbying data, this data is far from complete and there are limitations and assumptions being made.

Regarding hospital inpatient charge data:
- Data is for 50 United States and does not include Washington DC or other US Territories.
- Data is for over 3,000 hospitals which accept Medicare payments, which do not represent all hospitals in the US.  To date, there are over 5,500 registered hospitals and care facilities in the US.
- Data is for common diagnoses as it pertains to Medicare, the federal insurance plan largely for elderly and disabled citizens.  These diagnoses may not reflect common diagnoses for the US population as a whole.
- The amount paid by all includes Medicare payments, it is unknown what percentage of total payments is attributed to Medicare.

Regarding US Senate Lobby Disclosure Act data:
- Senate LDA reports are for the US Senate only.  Similar LDA reports exist for the US House of Representatives, but the lobbying activity on the House-level is relatively small as compared to the Senate-level, and therefore not included. 
- LDA reports are collected based on the 'Health Issues' and 'Medicare/Medicaid' categories and do not include 'Medical Research' or 'Pharmaceuticals' categories.
- LDA reports are collected based on the home state of the client making the lobbying request (and not the lobbyist itself). Although many clients represent health organizations within their home state, many represent national associations outside of their home state as well.
- Lobbying is often not directed to the client's state senators, but to the Senate Committee involved with health or Medicare issues.
- Reported lobbying may not be entirely dedicated to health or Medicare issues, but rather distributed across many issues.  The LDA report allows lobbying to be directed to multiple issues, of which health and Medicare were selected as two of many categories.
- Not all lobbying funds are reported.  Activities of less than 5,000 do not have to be reported.
- Not all clients are directly involved with healthcare or hospital facilities. Some are publicly traded corporations and manufacturers, (Ex: Walmart in Arkansas).
- Not all clients are represented by their client state.  Many clients appear to have offices in the VA / DC areas, presumably to be close to lobbyists. DC (and comparatively VA too) is vastly overrepresented due to many clients have having offices in DC.  As a result, DC is not included in this exploration.

---

## References

- https://www.bostonglobe.com/metro/2019/02/02/healthcare-industry-tops-list-state-lobbyist-expenses/bTvc7YWp7Ign2LB6ZaQDRN/story.html
- https://www.healthcaredive.com/news/myth-diagnosis-do-hospitals-charge-more-to-make-up-for-low-government-pay/560021/
- https://www.healthsystemtracker.org/chart-collection/u-s-spending-healthcare-changed-time/#item-nhe-trends_total-national-health-expenditures-us-billions-1970-2018
- https://www.nytimes.com/2019/05/09/health/hospitals-prices-medicare.html
- https://www.healthcaredive.com/news/hospital-lobbying-in-2018-by-the-numbers/548262/
- https://www.senate.gov/legislative/Public_Disclosure/LDA_reports.htm
