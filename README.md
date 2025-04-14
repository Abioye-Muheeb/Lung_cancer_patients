# Lung cancer patients

### Project Overview 

The Lung Cancer Project aims to develop innovative treatment plans that boost survival rates and enhance the quality of life for lung cancer patients.

### Introduction

Lung cancer remains one of the most formidable challenges in global health, claiming countless lives and demanding innovative approaches to prevention, diagnosis, and treatment. This comprehensive lung cancer project leverages a robust dataset of 300,000 patients to uncover critical demographic, lifestyle, environmental, and treatment related trends. By analyzing a wide array of factors from smoking history and air quality exposure to cancer stage and survival outcomes, this initiative aims to provide actionable insights for healthcare professionals, policymakers, and researchers striving to combat this devastating disease.

![Screenshot 2025-04-13 124449](https://github.com/user-attachments/assets/6e8d512f-56c8-4156-94be-4b62fc537eb2)




### Data Sources

Lung Cancer Data: The dataset used for the analysis is the "Lung_cancer_data.csv" file. containing detailed information about lung cancer patients

### Tools

- Excel - Data Cleaning
- SQL server - Data Analysis
- Power BI - Data Visualization

### Data Analysis 

include some codes worked with

```DAX
Occupational Exposure = 
VAR HighRiskOccupations = {"Factory Worker", "Farmer"}
RETURN
    IF(
        OR(
            'lung_cancer_data'[Exposure_to_Toxins] = "True",
            CONTAINS(HighRiskOccupations,[Value], 'lung_cancer_data'[Occupation])
        ),
        "Exposed",
        "Not Exposed"
    )
```

```DAX
Lung Cancer Type = 
 SWITCH(
    TRUE(),
    'lung_cancer_data'[Pack_Years_calc] >= 30 && 'lung_cancer_data'[Stage_of_Cancer] >= "III", "Small Cell Lung Cancer (SCLC)",
    'lung_cancer_data'[Pack_Years_calc] >= 20 && 'lung_cancer_data'[Smoking_History] = "Current", "Squamous Cell Carcinoma (SCC)",
    'lung_cancer_data'[Pack_Years_calc] >= 20 && 'lung_cancer_data'[Smoking_History] = "Former", "Squamous Cell Carcinoma (SCC)",
    'lung_cancer_data'[AQI] >= 100 && 'lung_cancer_data'[Smoking_History] = "Never", "Adenocarcinoma (ACF)",
    'lung_cancer_data'[Metastasis_Status] = "True", "Small Cell Lung Cancer (SCLC)",
    "Non-Small Cell Lung Cancer (NSCLC)"
 )
```

```Sql
SELECT *
FROM lung_cancer_data
WHERE survival_years > 5;
```

### Key Metric

For the purpose of our analysis, we defined long term survival in lung cancer patients as a survival period of five years or more following diagnosis.

### Key Objectives

The primary goal of this project is to dissect the multifaceted nature of lung cancer through advanced data analytics, focusing on:

1.	Demographic Profiling: Understanding how age, gender, and residential area influence lung cancer incidence and outcomes.
2.	Lifestyle and Environmental Impact: Investigating the role of smoking history, occupational exposure, and air quality (AQI) in cancer development and progression.
3.	Cancer Stage and Type Analysis: Examining the distribution of cancer stages (I-IV) and types (e.g., adenocarcinoma, small cell lung cancer) to identify patterns in diagnosis and survival.
4.	Treatment Efficacy: Evaluating the effectiveness of various treatments like chemotherapy, surgery, radiation, and palliative care on survival rates across different patient groups.
5.	Survival Trends: Tracking survival rates over time (2000–2024) to assess improvements in care and identify disparities across demographics and treatment types.

### Data Highlights

The dataset provides a wealth of insights into lung cancer dynamics:

-	Patient Overview: Out of 300,000 total patients, 225,000 have survived, yielding a survival rate of 75.1%. The average age at diagnosis is 53 years, with patients having smoked for an average of 25 years and surviving an average of 10 years post-diagnosis.
-	Demographic Trends: The patient population is nearly evenly split by gender (48% female, 47.97% male, 3.99% other), with the 65–74 age group showing the highest incidence (103,842 patients). Urban areas report the highest number of cases (150,000 patients), likely due to higher population density and environmental factors.
-	Lifestyle Factors: Smoking history is a significant risk factor, with 120,000 current smokers and 90,000 former smokers among the cohort. Occupational exposure also plays a role, with 70.1% of patients having no exposure to workplace toxins, while factory workers (91,000 patients) show a higher incidence compared to other occupations.
-	Environmental Impact: The average AQI exposure level is 254, indicating poor air quality as a potential contributor to lung cancer. Patients with AQI exposure between 100–400 show the highest incidence (61,000 each bin).
-	Cancer Stage and Type: The distribution across stages is balanced, with 25% of patients in each stage (I-IV). Non-small cell lung cancer (NSCLC) dominates at 32.61%, followed by adenocarcinoma (18.9%) and small cell lung cancer (SCLC) at 22.53%.
-	Treatment Outcomes: Chemotherapy is the most common treatment (40%), followed by surgery (30%), radiation (20%), and palliative care (10%). Survival rates vary by treatment, with surgery showing the highest average survival years (10 years), while palliative care averages 9 years.

### Key Findings

1.	Smoking and Survival: Current smokers exhibit the lowest survival rates (72% in recent years), while never-smokers consistently show higher survival rates (up to 76%). Pack-year groups (e.g., 50–70 pack-years) correlate with higher cancer incidence, with 83,000 patients in this category.
2.	Environmental Influence: Patients in urban areas (150,000) and those exposed to high AQI levels (255 on average) are more likely to develop lung cancer, with 180,000 patients reporting toxin exposure.
3.	Stage and Survival Disparities: Early-stage (I-II) patients have a higher survival rate (50.05%) compared to late-stage (III-IV) patients (49.95%). Stage IV patients show the lowest survival years, averaging 9 years.
4.	Treatment Efficacy Over Time: Survival rates have improved slightly from 2000 to 2024, with surgery patients showing the most significant gains (up to 78% survival rate). Chemotherapy, while widely used, shows a more modest improvement (74% survival rate).
5.	Demographic Variations: Females have a slightly higher survival rate (33.47%) compared to males (33.42%), with the 65–74 age group showing the highest survival years (10 years on average).

### Implications and Future Directions

This analysis underscores the complex interplay between modifiable lifestyle factors, environmental exposures, and lung cancer outcomes. The strong association between tobacco use and poor air quality with lung cancer incidence highlights the pressing need for comprehensive public health measures, including robust smoking cessation programs and stricter enforcement of environmental air quality standards. The relatively balanced distribution of cancer stages at diagnosis indicates potential gaps and corresponding opportunities in early detection strategies, particularly within high risk cohorts such as active smokers and individuals residing in urban environments.

Therapeutically, the superior survival outcomes associated with surgical intervention reinforce the critical importance of early-stage diagnosis, while the widespread reliance on chemotherapy underscores the need for ongoing research into optimizing treatment regimens, including biomarker-driven approaches and combination therapies.

Future directions for this work include the integration of predictive analytics to model disease trends and proactively identify at-risk populations. Expanding the dataset to include genomic, socioeconomic, and behavioral health variables will allow for a more nuanced understanding of lung cancer disparities and help inform precision prevention and treatment strategies. Ultimately, by translating epidemiological and clinical insights into targeted interventions, this initiative aims to advance earlier detection, improve therapeutic outcomes, and reduce the overall burden of lung cancer.

### Recommendations
Based on the comprehensive analysis of the lung cancer dataset, the following recommendations aim to address key findings, enhance prevention, improve treatment outcomes, and guide future research:
1.  Strengthen Smoking Cessation Programs
- Rationale: Current smokers (120,000 patients) and former smokers (90,000 patients) constitute a significant portion of the cohort, with current smokers showing the lowest survival rates (72%).
- Action: Implement targeted public health campaigns promoting smoking cessation, particularly for high risk groups (e.g., 50–70 pack-year smokers, 83,000 patients). Offer accessible cessation resources, such as counseling and nicotine replacement therapies, to reduce incidence and improve survival rates.
2.  Enhance Air Quality Regulations and Monitoring
- Rationale: The average AQI exposure level of 254 indicates poor air quality as a risk factor, with 180,000 patients exposed to toxins and urban residents (150,000 patients) showing higher incidence.
- Action: Advocate for stricter air quality regulations in urban areas and industrial zones. Increase AQI monitoring and public awareness campaigns about the link between air pollution and lung cancer, especially for vulnerable populations like factory workers (91,000 patients).
3.  Promote Early Screening for High Risk Groups
- Rationale: The balanced distribution of cancer stages (25% each for I-IV) suggests late diagnoses are common, with stage IV patients having the lowest survival years (9years). High risk groups, such as current smokers and those in urban areas, are prime candidates for early detection.
- Action: Develop screening programs targeting high risk demographics, including current smokers, urban residents, and individuals aged 65–74 (103,842 patients). Use low dose CT scans to detect lung cancer at earlier stages (I-II), where survival rates are higher (50.05%).
4.  Optimize Treatment Strategies
- Rationale: Surgery yields the highest average survival years (10 years) and survival rate (78%), yet only 30% of patients receive it. Chemotherapy, while most common (40%), has a lower survival rate (74%).
-  Action: Prioritize surgical interventions for early-stage patients where feasible, and invest in research to improve chemotherapy outcomes, such as personalized treatment plans based on cancer type (e.g., NSCLC, 32.61% of cases). Expand access to multidisciplinary care to ensure patients receive the most effective treatment combinations.
5.  Address Demographic Disparities in Survival
- Rationale: Females show a slightly higher survival rate (33.47%) than males (33.42%), and the 65–74 age group has the highest survival years (10 years). Urban patients face higher incidence due to environmental factors.
- Action: Tailor interventions to address disparities, such as providing additional support for male patients to improve survival outcomes. Focus on urban health initiatives to mitigate environmental risks, and ensure equitable access to care across all age groups and genders.
6.  Expand Research on Environmental and Occupational Risks
- Rationale: Occupational exposure impacts incidence, with factory workers showing a high case count (91,000), and 70.1% of patients report no exposure, suggesting other environmental factors at play.
- Action: Conduct further studies on occupational hazards and their link to lung cancer, particularly for factory workers. Investigate other environmental factors, such as radon exposure, to better understand their contribution to lung cancer risk.
7.  Leverage Predictive Analytics for Prevention
- Rationale: The dataset reveals clear patterns in risk factors (e.g., smoking, AQI, urban residency) that can be used to predict future cases.
- Action: Develop machine learning models to predict lung cancer risk based on demographic, lifestyle, and environmental data. Use these models to identify at-risk populations for targeted prevention and early intervention strategies.
8.  Increase Public Awareness of Lung Cancer Types and Stages
- Rationale: NSCLC (32.61%) and adenocarcinoma (18.9%) are prevalent, yet public awareness of lung cancer types and their implications may be limited.
- Action: Launch educational campaigns to inform the public about different lung cancer types, their symptoms, and the importance of early diagnosis. Highlight the better prognosis for early stage cancers to encourage timely medical consultations.
9.  Integrate Genetic and Socioeconomic Data for Holistic Insights
- Rationale: The current dataset lacks genetic and socioeconomic factors, which could provide deeper insights into lung cancer disparities and outcomes.
- Action: Expand the dataset to include genetic profiles (e.g., EGFR mutations) and socioeconomic factors (e.g., income, education) to better understand their impact on incidence, treatment access, and survival. This could guide more personalized and equitable healthcare strategies.
10.  Monitor Long-Term Trends and Treatment Innovations
- Rationale: Survival rates have shown slight improvements from 2000 to 2024, but disparities persist across treatment types and demographics. Emerging therapies, such as immunotherapy, are not yet reflected in the data.
- Action: Continue tracking survival trends beyond 2024 to assess the impact of new treatments like immunotherapy. Establish a longitudinal study to evaluate the long term efficacy of current and future interventions, ensuring continuous improvement in patient outcomes.

### Conclusion
This lung cancer study provides a comprehensive analysis of the disease’s multifaceted nature, elucidating the significant influence of demographic, lifestyle, and environmental determinants on patient prognosis. With a survival rate of 75.1% and identifiable avenues for optimization, these findings underscore the imperative for targeted therapeutic strategies and ongoing investigation. Leveraging robust data analytics, we can advance toward a future where the morbidity and mortality associated with lung cancer are markedly diminished, enhancing the potential for extended survival and improved quality of life for all affected individuals.
