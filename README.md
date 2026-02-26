Predicting When Customers Will Churn Using Survival Analysis

Project Overview



Most churn models try to answer a simple question:



Will a customer leave or not?



But in reality, retention teams need a different answer:



How long will a customer stay before they leave?



This project focuses on estimating customer lifetime rather than just churn likelihood.



Using telecom customer data, I built a survival analysis model to understand how long customers remain active and what factors influence early churn.



Instead of treating all active customers the same, this approach recognises that many customers haven’t churned yet — meaning their true churn time is unknown.



Business Objective



The goal is to move beyond churn prediction and towards churn timing.



This allows a company to:



Identify customers likely to leave soon



Estimate how much time is left before churn



Prioritise retention efforts based on urgency



Key Modelling Approach



To achieve this, I structured the problem as a time-to-event task:



Duration → Tenure in months



Event → Whether churn has occurred



Active customers are treated as censored observations, since their churn time is not yet observed.



This makes survival analysis the appropriate modelling framework.



Data Preparation



Rather than dropping missing values, I handled them using business logic.



For example:



Customers without internet service cannot have streaming or security features



Customers without phone service cannot incur long-distance charges



Missing churn reasons indicate non-churned customers



This ensured the dataset reflected real customer behaviour instead of artificial assumptions.



Data leakage was also prevented by removing:



Post-churn information



Identifiers



Revenue totals that accumulate over time



Categorical variables were one-hot encoded, and heavily skewed usage variables were log-transformed.



Model Used



I used a Cox Proportional Hazards model to estimate churn risk over time.



This model:



Uses tenure information



Handles censored customers



Estimates how features accelerate or delay churn



The dataset was split using stratification on churn events to preserve the real churn proportion.



Model Performance



The model achieved a Concordance Index of ~0.90, indicating strong ability to correctly rank which customers are likely to churn sooner.



Key Insights



Some of the strongest retention drivers were:



Long-term contracts



Security and support add-ons



Marketing offers



Customer ties (dependents and referrals)



Factors associated with faster churn included:



Certain promotional offers



Mailed check payments



High data usage



Fiber internet usage



Demographics showed relatively weak influence compared to service engagement.



Business Output



The model produces:



Survival curves for each customer



Predicted time until churn



Practical churn risk groups:



Risk Level	Meaning

High Risk	Likely to churn soon

Medium Risk	Moderate churn horizon

Low Risk	Long remaining lifetime



This makes it possible to prioritise retention actions instead of treating all customers equally.



**Tools Used**



Python



Pandas \& NumPy



Scikit-learn



Lifelines



Matplotlib \& Seaborn



The project environment can be recreated using the provided environment.yml file.



Project Value



This project demonstrates how churn can be treated as a timing problem rather than just a classification task.



By estimating customer lifetime instead of churn probability, organisations can act earlier and allocate retention resources more effectively.

