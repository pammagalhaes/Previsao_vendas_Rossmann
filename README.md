# 1.Business Problem

A Rossmann é uma empresa multinacional alemã do setor de varejo, especializada em produtos farmacêuticos, saúde, beleza, cuidados pessoais e bem-estar. Hoje, a empresa é uma das maiores redes de drogarias da Europa, com milhares de lojas espalhadas por diversos países. A Rossmann é conhecida por oferecer uma ampla variedade de produtos de qualidade a preços acessíveis.

O contexto deste projeto é baseado em uma reunião da Rossmann, na qual o CFO da empresa fez uma solicitação de resultados mensais com todos os gerentes de loja e requisitou que cada um deles trouxesse uma previsão diária das próximas 6 semanas de vendas, a fim de obter um orçamento para realizar uma reforma nas lojas. Portanto, é de fundamental importância obter essa previsão nas vendas. Em seguida, os gerentes entraram em contato com o time de dados da empresa, solicitando uma previsão de vendas das lojas as quais gerenciam.

# 2.Context Analysis
Os atributos originais do conjunto de dados, juntamente com seus significados, incluem:

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
Para este projeto, o método CRISP-DM foi utilizado, contando com os 10 passos abaixo:
1 - Problema de Negócio: Identificar o problema de negócio a ser solucionado;

2 - Entendimento do Problema de Negócio: Compreender a motivação, a causa e propor a estratégia de solução para este problema.

3 - Coleta de Dados: Os dados foram obtidos através do Kaggle. (Rossmann Store Sales)

4 - Limpeza dos Dados: Consiste em renomear colunas, converter as variáveis para seus tipos corretos, verificar e preencher NA´s quando necessário, seguindo as motivações do negócio, além de fornecer um breve resumo descritivo dos dados.

5 - Exploração dos Dados: Esta etapa busca analisar e compreender as variáveis que impactam a variável resposta do projeto. Também ocorre a filtragem de variáveis, de acordo com a problemática de negócio. Aqui também são validadas as hipóteses de negócio com a utilização de análise univariada, bivariada e multivariada, o que acarreta na geração de insights para o time de negócios.

6 - Modelagem dos Dados: Esta etapa é fundamental para preparar os dados conforme os requisitos dos algoritmos de Machine Learning. Aqui, são realizadas Normalização, Rescaling e Encoding, com o objetivo de padronizar os dados em uma mesma escala, além de converter variáveis categóricas em numéricas.

7 - Seleção de Features: Esta etapa do projeto filtra as features mais relevantes para o treinamento de Machine Learning que vem a seguir. Não é interessante para o projeto ter um número muito grande de colunas que não impactam na explicação do problema estudado.

8 - Machine Learning: Em seguida, os dados preparados são treinados em diversos algoritmos de Machine Learning, a fim de obter o melhor modelo para explicar o fenômeno. Antes da escolha final, nesta etapa também é realizado o processo de Cross-Validation (validação cruzada) visando impedir que o modelo esteja enviesado, devido a uma separação específica para os dados de validação. Realizados esses procedimentos, aplica-se o Hyperparameter Fine Tuning para o modelo que apresentar melhor resultado, encontrando os melhores parâmetros para o algoritmo e maximizando ainda mais a performance do modelo.

9 - Avaliação do Algoritmo: Aqui, avalia-se o algoritmo com os dados de teste previamente separados, de acordo com métricas alinhadas ao tipo de aprendizado dos modelos de Machine Learning. Ao final, a parte mais importante: traduzir a performance do algoritmo para resultados em termos de negócio e receitas para a empresa e mostrar a diferença, além do impacto que a utilização das técnicas trabalhadas aqui proporcionam para o desenvolvimento da empresa.

10 - Modelo em Produção: Por fim, o modelo avaliado é publicado (Deploy) virtualmentepara que os resultados sejam utilizados por toda a equipe de negócio. Pra melhorar ainda mais esta visualização, um Bot no aplicativo Telegram traz, em tempo real, a predição para cada loja automaticamente.

# 4. Top 3 Insights
### H1- Lojas deveriam vender mais ao longo dos anos.
<img width="830" alt="img1" src="https://github.com/pammagalhaes/Previsao_vendas_Rossmann/assets/113152370/91495ef5-3489-4bb1-ae7d-c1a6180ae0a7">

**False** Lojas vendem MENOS ao longo dos anos.

### H2 - Lojas com promoçoes ativas por mais tempo, deveriam vender mais.
![img2](https://github.com/pammagalhaes/Previsao_vendas_Rossmann/assets/113152370/ffe6017a-a269-489c-b051-dee0def480e6)

**False** Lojas com promocoes ativas por mais tempo, na verdade vendem MENOS depois de um certo tempo.

### H3 - Lojas com competidores a mais tempo, deveriam vender mais.
![img3](https://github.com/pammagalhaes/Previsao_vendas_Rossmann/assets/113152370/d1dde453-9bb8-4b08-b195-adfc4dc40b3c)

**False** Lojas com competidores ha mais tempo, na verdade vendem MENOS.

# 5. Machine Learning Model
Após a preparação dos dados, foram desenvolvidos e treinados cinco modelos de Aprendizado de Máquina para identificar o algoritmo mais eficaz em descrever e resolver o problema proposto:

**Average Model**
**Linear Regression Model**
**Lasso Regularized Linear Regression Model**
**Random Forest Regressor**
**XGBoost Regressor**
Cada modelo foi treinado e avaliado usando métricas como **MAE**, **MAPE** e **RMSE**. Além disso, foi realizado o processo de Cross-Validation (validação cruzada) nesta etapa para garantir que os modelos não apresentassem viés devido à separação específica dos dados de validação.

O modelo final escolhido foi o **XGBoost Regressor**, devido a um bom desempenho na análise das métricas e por ter um processamento mais leve que os modelos de árvore.

# 6. Deploy do modelo
Para facilitar o acesso às previsões de cada loja pela equipe de negócios, um Bot foi desenvolvido no aplicativo Telegram. Bastando apenas salvar o contato do Bot e enviar as solicitações através da API, a qual está hospedada em um serviço de nuvem fornecido pela Render.

![img7](https://github.com/pammagalhaes/Previsao_vendas_Rossmann/assets/113152370/09ee5cdd-e529-4eef-b3eb-9657c17daab8)

