# telco-project

OVERVIEW

This repo contains a presentation jupyter notebook as well as a working notebook and two modules to obtain and prepare data from the Telco data.

The goal of this project is to find drivers of churn in order to provide actionable data to Telco Management.

The ML models herein are developed using SKLEARN and PANDAS to predict churn.

The final report is assembled in final_report.ipynb.

From past analysis without ML modeling it was discovered there is a high correlation between payment method and churn. This correlation and many others will be tested via the modeling to see if payment type is the best predictor or if other features make for a better model.

GOAL

Identify features that can be used to predict churn using ML models to provide actionable data to stakeholders.

INITIAL QUESTIONS

I will look at all features individually and through certain combinations. 
Does autopay effect churn?

Do additional services reduce churn?

Is there a correlation between number of services (phone, internet or phone and internet) and churn?

Is there a correlation between monthly charges and churn?

DATA DICTIONARY

 #   Column                                Meaning          
---  ------                                --------------    
 0   is_female                             1 = female, 0 = male     
 1   senior_citizen                        1 = senior citizen, 0 = not     
 2   partner                               1 = partner on plan     
 3   dependents                            1 = dependents on plan     
 4   tenure                                tenure in months     
 5   phone_service                         1 = has phone     
 6   multiple_lines                        1 = has more than one phone line     
 7   online_security                       1 = has online security     
 8   online_backup                         1 = has online back up     
 9   device_protection                     1 = has device protection    
 10  tech_support                          1 = has tech support     
 11  streaming_tv                          1 = has streaming tv    
 12  streaming_movies                      1 = has streaming movies    
 13  paperless_billing                     1 = has paperless billing     
 14  monthly_charges                       monthly charges in dollar and cents dd.cc   
 15  total_charges                         total charges over total contract
 16  churn                                 1 = churned
 DUMMY VARIABLES
 17  contract_type_One year                1 = one year contract     
 18  contract_type_Two year                1 = two year contract (both 0 means month to month)    
 19  internet_service_type_Fiber optic     1 = fiber     
 20  internet_service_type_None            1 = no internet (both 0 = dsl)    
 21  payment_type_Credit card (automatic)  1 = credit card     
 22  payment_type_Electronic check         1 = electronic check     
 23  payment_type_Mailed check             1 = mailed check (all 0 = bank transfer(automatic)

THE PLAN

1. Acquire
    Using the acquire.py module I am able to query SQL and pull the data which I then store in a .csv for future use

2. Prepare
    A lot of preparation is done via the prepare.py module which drops less useful columns and converts data to a more ML learning format. Inside prepare is also a function to split the data into TRAIN, VALIDATE, TEST in order to preseve integrity and reduce overfitting. NOTE: 11 customers with total charges = 0 have 0 tenure and havent had a chance to churn, they are removed from the df during prep. Other options would include putting their monthly charges as total charges. but given that they make up <1% of the dataset I feel confident removing them. no other null or empty values were present after this deletion

3. Explore
    In the telco_work.ipynb you can see the initial data analysis and statistical testing while looking for the what features to use in my modeling process

4. Modeling
    Models are made using different SKLEARN options with a variety of features and hyperparameters.

5. Model Evalution
    Models are all trained on the train split, validated on validate split and the best model is evaluated on the test split

6. Findings
    Findings are documented along the way and organized in the final_report.ipynb