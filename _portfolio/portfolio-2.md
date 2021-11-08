---
title: "Homelessness in LA County"
excerpt: "Working with state and local agencies to develop and evaluate evidence-based solutions to homelessness. The California Policy Lab leverages expertise in data integration, predictive analytics, screening tools, and program evaluation to share real-time insights and build empirical evidence to improve outcomes for homeless individuals and families.<br/><br/><img src='/images/la_graphic_light.png'>"
collection: portfolio
---

## Overview 

On any given night, nearly 60,000 [1] people experience homelessness in Los Angeles County, and an estimated 141,000 [2] are homeless in any given year.

For the past three years, I have been working at the California Policy Lab on various projects around homelessness to respond to this need, such as predicting homelessness among single adults receiving mainstream county services. The purpose of this work is to help identify people at high risk of homelessness and then get an understanding of risk factors to design and test homelessness prevention strategies. 

## Projects

The pathways into homelessness are dynamic and complicated, as are the pathways to receiving county resources in LA County. Figure 1 displays a generalized overview of the homeless system flow. Individuals in LA County who are at risk of homelessness or are homeless interact with the county system (i.e. by utilizing a public hospital, or even, for instance, by interacting with a street outreach team). Some of these individuals are assessed to determine their risk and then get allocated potential resources such as food stamps, entrance into job training programs or even housing. 

![Figure 1](/images/hlOne.png "Figure 1")
**Figure 1.** depicts a crude graph of the homeless system flow. (1) The HL Universe includes all individuals in LA who are at risk of homelessness or already homeless. (2) Some of these individuals interact with county agencies, such as the Department of Health Services or the Coordinated Entry System. (3) A subset of those individuals receive assessments such as the Vulnerability Index – Service Prioritization Decision Assistance Prescreen Tool (VI-SPDAT), the results of which are then used to (4) receiving assistance, such as permanent housing. 

At the California Policy Lab, I have been working on project at each of these system flow points:
1. Predicting and Preventing Homelessness: The aim of this project is to identify individuals who are at risk of becoming homelessness and intervene before these individuals end up on the streets. By leveraging linked data from county agencies and applying machine learning models, we are hoping to predict homelessness amongst different populations, such as single adults as well as families, and intervene. 
2. Evaluating Assessment Tool: Several surveys, such as the Vulnerability Index – Service Prioritization Decision Assistance Prescreen Tool (VI-SPDAT) or the Prevention Targeting Tool (PTT) are utilized in LA County to allocate resources to vulnerable populations. In this project, we evaluate the efficacy of these tools, while also improving the tool's predictive abilities. 
3. Evaluating Homeless Prevention Measures in LA: This project focuses on evaluating Los Angeles Homelessness Prevention Strategies A1 (focused on families) and A5 (focused on single adults and transition-aged youth). The evaluation focused on who was being served and how; if there were ways to improve the services; and whether prevention programs are reducing inflows to homelessness. 

### Data Sources
The data comes from an integrated, longitudinal dataset linked at the individual level across seven LA County agencies, such as Department of Health Services (DHS), Department of Public Social Services (DPSS), or Department of Mental Health (DMH), to name a few. We developed a pipeline for ingesting the data and linking it to other sources such as the Homelessness Management Information System (HMIS).

### Operationalizing Homelessness 
Accurately measuring homelessness as an outcome is extremely challenging due to a variety of existing legal definitions. Homelessness is also a temporally dynamic outcome, so that defining a homeless spell or an outcome window for modeling requires a lot of policy input. Furthermore, we can only observe individuals as experiencing homelessness if they have received homeless services through a county service agency and thus appear in our data, leading to a biased sample.

To help better understand the outcome, we have performed descriptive work on the data and documented the homelessness flow. Thus, when thinking about a proxy measure for homelessness, we've also looked at what adverse events in the future we would like to prevent. 

### Machine Learning and Modeling
The main challenge was transforming longitudinal service utilization data into numerical risk factors that could be fed to a machine learning model. In our model, for instance, we periodized service utilization into recent (within the last six months) and earlier (more than six months ago) features. Additionally, we converted medical diagnosis data into risk scores by merging our data with the Charlson and Elixhauser indexes.

### Sources

* [1] 2019 Greater Los Angeles Homeless Count, available at https://www.lahsa.org/documents?id=3423-2019-greater-los-angeles-homeless-count-los-angelesCounty.pdf.
* [2] This figure is calculated using a combination of enrollment data in homeless projects from LAHSA’s HMIS system, and the homeless flag in DPSS’s data for
General Relief (GR) recipients. Note that while individuals who are homeless in the HMIS are required to meet the HUD definition of homelessness, this is not
a requirement to be flagged as homeless in the GR data.
* [3] “The Homeless Initiative,” Los Angeles County, available at http://homeless.laCounty.gov/


