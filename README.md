# BP-Rossmann-Sales-Model

![](/home/leonardo/DSProducao/negocio-digital-800x445.jpg)


Este é um projeto de machine learning de previsão de vendas para Drogarias Rossmann.
Rossmann opera mais de 3.000 drogarias em 7 países europeus.  As vendas da loja são influenciadas por muitos fatores, incluindo promoções, competição, feriados escolares e estaduais, sazonalidade e localidade. 

# Problema de negócios
O CFO da Rossmann Drug Stores solicitou uma previsão de vendas de cada loja para as próximas seis semanas, a fim de definir um orçamento para a reforma das lojas. A previsão atual não era satisfatória, pois havia várias inconsistências. Nesse contexto, desenvolvi um modelo de aprendizado de máquina com o objetivo de fornecer previsões de vendas da loja com mais precisão.

# Caracteristicas de base de dados
Base de dados retirada do site kaggle

## Lista de Atributos
- Id - um Id que representa um (armazenamento, data) 
- Loja - um ID único para cada loja
- Vendas - o volume de negócios para qualquer dia
- Clientes - o número de clientes em um determinado dia
- Aberta - um indicador para saber se a loja estava aberta: 0 = fechada, 1 = aberta
- StateHoliday - indica um feriado. Normalmente todas as lojas, com poucas exceções, fecham nos feriados estaduais. Observe que todas as escolas fecham nos feriados e finais de semana. a = feriado, b = feriado da Páscoa, c = Natal, 0 = Nenhum
- SchoolHoliday - indica se (Loja, Data) foi afetado pelo fechamento de escolas públicas
- StoreType - diferencia entre 4 modelos de loja diferentes: a, b, c, d
- Sortimento - descreve um nível de sortimento: a = básico, b = extra, c = estendido
- CompetitionDistance - distância em metros até a loja concorrente mais próxima
- CompetitionOpenSince [Mês / Ano] - fornece o ano e mês aproximados em que o concorrente mais próximo foi aberto
- Promo - indica se uma loja está fazendo uma promoção naquele dia
- Promo2 - Promo2 é uma promoção contínua e consecutiva para algumas lojas: 0 = a loja não está participando, 1 = a loja está participando
- Promo2Since [Ano / Semana] - descreve o ano e a semana em que a loja começou a participar da Promo2
- PromoInterval - descreve os intervalos consecutivos em que a Promo2 é iniciada, nomeando os meses em que a promoção é reiniciada. Por exemplo. "Fev, maio, agosto, novembro" significa que cada rodada começa em fevereiro, maio, agosto, novembro de qualquer ano para aquela loja

# Estratégia de Solução
O método utilizado para o projeto foi o CRISP-DM, aplicar conforme as etapas abaixo:

** Etapa 01 - **Data Description:**  O objetivo é usar métricas estatísticas para identificar outliers no escopo do negócio e também analisar métricas estatísticas básicas como: mean, median, maximum, minimum, range, skew, curtosis and standard deviation.

** Etapa 02 **Feature Engineering**: O objetivo desta etapa é obter novos atributos a partir das variáveis ​​originais, a fim de melhor descrever o fenômeno a ser modelado.

** Etapa 03  **Data Filtering**: o objetivo desta etapa é filtrar linhas e excluir colunas que não são relevantes para o modelo ou não fazem parte do escopo do negócio.

** Etapa 04  **Exploratory Data Analysis**: o objetivo desta etapa é explorar os dados para encontrar insights e entender melhor o impacto das variáveis ​​no aprendizado do modelo.

** Etapa 05  **Data Preparation**: o objetivo desta etapa é preparar os dados de preparação de dados para aplicação do modelo de aprendizado de máquina.

** Etapa 06  **Feature Selection**: o objetivo desta etapa é selecionar os melhores atributos para treinar o modelo. Foi utilizado o Algoritmo Boruta para fazer a seleção.

** Etapa 07  **Machine Learning Modeling**: o objetivo desta etapa é fazer o treinamento do modelo de aprendizado de máquina.

** Etapa 08  **Hyperparameter Fine Tunning**: O objetivo desta etapa é escolher os melhores valores para cada um dos parâmetros do modelo selecionado na etapa anterior.

** Etapa 09  **Convert model performance to business values**: o objetivo desta etapa é converter o desempenho do modelo em um resultado de negócios.

** Etapa 10  **Deploy Model to Production**: o objetivo desta etapa é publicar o modelo em um ambiente de nuvem para que outras pessoas ou serviços possam usar os resultados para melhorar a decisão de negócios. A plataforma de aplicativo em nuvem escolhida foi o Heroku.

# Três principais insigths de dados
**H1**: Lojas com sortimento maior devem vender mais.

**FALSO**: Lojas com maior variedade vendem MENOS.

imagem

**H9**: As lojas devem vender mais com o passar dos anos.

**FALSO**: As lojas vendem menos com o passar dos anos.

imagem

 **H11**: As lojas devem vender mais a partir do dia 10 de cada mês.
 
**VERDADEIRO**: As lojas vendem mais a partir do dia 10 de cada mês.

imagem

# Modelos de aprendizado de máquina testados

- Modelo Médio
- Modelo de regressão linear
- Modelo Regularizado de Regressão Linear (Laço)
- Random Forest Regressor
- Regressor XGBoost

# Desempenho de modelos de aprendizado de máquina

imagem

# Desempenho de aprendizado da máquina após o ajuste fino de hiperparâmetro

imagem

Embora o Random Forest Regressor Model tenha apresentado melhor desempenho, este modelo geralmente requer uma grande quantidade de espaço no servidor na etapa de implantação, gerando um aumento significativo de custo para a empresa. Para tanto, optou-se pelo modelo XGBoost Regressor, que após o ajuste fino do hiperparâmetro apresentou desempenho semelhante e requer menos espaço no servidor, gerando um menor custo para a empresa.

# Modelo de desempenho x valores de negócios

Além da previsão geral de vendas, também foi calculada a previsão de vendas para o pior e o melhor cenário.

**Modelo com regressão XGBoost**

imagem


# Conclusão

Considerando o primeiro ciclo de CRISP-DS, o modelo final apresentou um desempenho útil, considerando o MAPE (Erro Médio Porcentagem Absoluto) de 0,11. Porém, para algumas lojas, foram observados valores de MAPE mais elevados, como 0,37 e 0,52, mas este é um ponto que poderá ser melhorado no próximo ciclo de CRISP.

# Technologies
- Jupyter notebook
- Python

# Deploy into production
- Back end: Heroku
- Database: Kaggle

# Autor
Leonardo Canuto Chaves
