# 1.Business Problem

Rossmann is a German multinational retail company specializing in pharmaceuticals, health, beauty, personal care, and wellness products. Today, the company is one of the largest drugstore chains in Europe, with thousands of stores across several countries. Rossmann is known for offering a wide variety of quality products at affordable prices.

The context for this project is based on a Rossmann meeting in which the company's CFO requested monthly results from all store managers and asked each of them to provide a daily sales forecast for the next six weeks in order to obtain a budget for store renovations. Therefore, obtaining this sales forecast is crucial. The managers then contacted the company's data team, requesting a sales forecast for the stores they manage.

# 2.Context Analysis
The original attributes of the dataset, along with their meanings, include:

Id - an Id that represents a (Store, Date) duple within the test set
Store - a unique Id for each store
Sales - the turnover for any given day (this is what you are predicting)
Customers - the number of customers on a given day
Open - an indicator for whether the store was open: 0 = closed, 1 = open
StateHoliday - indicates a state holiday. Normally all stores, with few exceptions, are closed on state holidays. Note that all schools are closed on public holidays and weekends. a = public holiday, b = Easter holiday, c = Christmas, 0 = None
SchoolHoliday - indicates if the (Store, Date) was affected by the closure of public schools
StoreType - differentiates between 4 different store models: a, b, c, d
Assortment - describes an assortment level: a = basic, b = extra, c = extended
CompetitionDistance - distance in meters to the nearest competitor store
CompetitionOpenSince[Month/Year] - gives the approximate year and month of the time the nearest competitor was opened
Promo - indicates whether a store is running a promo on that day
Promo2 - Promo2 is a continuing and consecutive promotion for some stores: 0 = store is not participating, 1 = store is participating
Promo2Since[Year/Week] - describes the year and calendar week when the store started participating in Promo2
PromoInterval - describes the consecutive intervals Promo2 is started, naming the months the promotion is started anew. E.g. "Feb,May,Aug,Nov" means each round starts in February, May, August, November of any given year for that store

# 3. Solution Strategy
For this project, the CRISP-DM method was used, with the following 10 steps:

1 - Business Problem: Identify the business problem to be solved;

2 - Understanding the Business Problem: Understand the motivation, the cause, and propose a solution strategy for this problem.

3 - Data Collection: Data was obtained through Kaggle. (Rossmann Store Sales)

4 - Data Cleaning: Consists of renaming columns, converting variables to their correct types, verifying and filling in NAs when necessary, following the business motivations, in addition to providing a brief descriptive summary of the data.

5 - Data Exploration: This step seeks to analyze and understand the variables that impact the project's response variable. Variables are also filtered according to the business problem. Here, business hypotheses are also validated using univariate, bivariate, and multivariate analysis, which results in the generation of insights for the business team.

6 - Data Modeling: This step is essential for preparing the data according to the requirements of Machine Learning algorithms. Normalization, Rescaling, and Encoding are performed here to standardize the data on a single scale, in addition to converting categorical variables to numeric ones.

7 - Feature Selection: This stage of the project filters the most relevant features for the subsequent Machine Learning training. It is not beneficial for the project to have a large number of columns that do not impact the explanation of the problem studied.

8 - Machine Learning: Next, the prepared data is trained on various Machine Learning algorithms to obtain the best model to explain the phenomenon. Before the final selection, this stage also involves cross-validation to prevent model bias due to a specific separation of validation data. Once these procedures have been carried out, Hyperparameter Fine Tuning is applied to the model that presents the best results, finding the best parameters for the algorithm and further maximizing the model's performance.

9 - Algorithm Evaluation: Here, the algorithm is evaluated using previously separated test data, according to metrics aligned with the learning style of the Machine Learning models. Finally, the most important part: translating the algorithm's performance into business and revenue results for the company and demonstrating the difference, as well as the impact that the use of the techniques developed here has on the company's development.

10 - Model in Production: Finally, the evaluated model is published (deployed) virtually so that the results can be used by the entire business team. To further enhance this visualization, a bot in the Telegram app automatically delivers the predictions for each store in real time.

# 4. Top 3 Insights
### H1- Stores should sell more over the years.
<img width="830" alt="img1" src="https://github.com/pammagalhaes/Previsao_vendas_Rossmann/assets/113152370/91495ef5-3489-4bb1-ae7d-c1a6180ae0a7">

**False** Stores sell LESS over the years.

### H2 - Stores with promotions running for longer should sell more.
![img2](https://github.com/pammagalhaes/Previsao_vendas_Rossmann/assets/113152370/ffe6017a-a269-489c-b051-dee0def480e6)

**False** Stores with promotions running for longer actually sell LESS after a certain time.

### H3 - Stores with longer-standing competitors should sell more.
![img3](https://github.com/pammagalhaes/Previsao_vendas_Rossmann/assets/113152370/d1dde453-9bb8-4b08-b195-adfc4dc40b3c)

**False** Stores with competitors that have been around for longer actually sell LESS.

# 5. Machine Learning Model
After data preparation, five Machine Learning models were developed and trained to identify the most effective algorithm for describing and solving the proposed problem:

**Average Model**

**Linear Regression Model**

**Lasso Regularized Linear Regression Model**

**Random Forest Regressor**

**XGBoost Regressor**

Each model was trained and evaluated using metrics such as **MAE**, **MAPE** and **RMSE**. Additionally, cross-validation was performed at this stage to ensure that the models were not biased due to the specific separation of the validation data.

The final model chosen was **XGBoost Regressor**, due to its good performance in analyzing the metrics and its lighter processing power than tree models.

# 6. Deployment
To facilitate access to each store's forecasts by the business team, a bot was developed in the Telegram app. Simply save the bot's contact information and send requests through the API, which is hosted on a cloud service provided by Render.

![img7](https://github.com/pammagalhaes/Previsao_vendas_Rossmann/assets/113152370/09ee5cdd-e529-4eef-b3eb-9657c17daab8)

