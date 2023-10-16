
The link to the Synthetic Financial Fraud Detection Dataset:-

https://dagshub.com/Ln11211/Synthetic_Financial_Fraud_Detection

**Description**:
aySim simulates mobile money transactions based on a sample of real transactions extracted from one month of financial logs from a mobile money service implemented in an African country. The original logs were provided by a multinational company, who is the provider of the mobile financial service which is currently running in more than 14 countries all around the world.

This synthetic dataset is scaled down 1/4 of the original dataset and it is created just for analysis.

*step* - maps a unit of time in the real world. In this case 1 step is 1 hour of time. Total steps 744 (30 days simulation).

*type* - CASH-IN, CASH-OUT, DEBIT, PAYMENT and TRANSFER.

*amount* -
amount of the transaction in local currency.

*nameOrig* - customer who started the transaction

*oldbalanceOrg* - initial balance before the transaction

*newbalanceOrig* - new balance after the transaction.

*nameDest* - customer who is the recipient of the transaction

*oldbalanceDest* - initial balance recipient before the transaction. Note that there is not information for customers that start with M (Merchants).

*newbalanceDest* - new balance recipient after the transaction. Note that there is not information for customers that start with M (Merchants).

*isFraud* - This is the transactions made by the fraudulent agents inside the simulation. In this specific dataset the fraudulent behavior of the agents aims to profit by taking control or customers accounts and try to empty the funds by transferring to another account and then cashing out of the system.

*isFlaggedFraud* - The business model aims to control massive transfers from one account to another and flags illegal attempts. An illegal attempt in this dataset is an attempt to transfer more than 200.000 in a single transaction.



**Citation**:
This work is part of the research project ”Scalable resource-efficient systems for big data analytics” funded
by the Knowledge Foundation (grant: 20140032) in Sweden.

Please refer to this dataset using the following citations:

PaySim first paper of the simulator:

E. A. Lopez-Rojas , A. Elmir, and S. Axelsson. "PaySim: A financial mobile money simulator for fraud detection". In: The 28th European Modeling and Simulation Symposium-EMSS, Larnaca, Cyprus. 2016

**Prerequisite**:
Knowledge of machine learning algorithms and techniques would be beneficial for using this dataset.

**License**:
CC BY-SA 4.0
