# Análise de dados utilizando Python

Análise do dataset Churn_Modelling, buscando destrinchar as variáveis e como se relacionam com os dados de saída.

### Passo a passo

### 0. Imports

- Inicialmente, importei as bibliotecas pandas, seaborn e o método pyplot da biblioteca matplotlib.

### 1. Carregando o conjunto de dados

- Carreguei o conjunto de dados Churn_Modelling.csv;
- Apresentei informações e as primeiras linhas do conjunto de dados, observando que nenhuma coluna apresentava valor nulos entre seus dados.

### 2. Pré-processamento de dados

- Verifiquei a quantidade de valores ausentes (nulos) nas colunas do dataframe, com todas sendo 0, como percebido anteriormente, não necessitando de tratamento;
- Plotei boxplot das colunas com valores numéricos que valiam a pena identificar possíveis outliers (colunas com valores sendo 0 ou 1 não entraram), fazendo a seguintes análises:

1. **CreditScore:** Há clientes que possuem pontos de créditos abaixo do considerado comum;
2. **Age:** Há muitos clientes que possuem idades muito avançadas, passando do considerado comum;
3. **Tenure:** A maioria dos clientes possuem entre 3 a 7 anos de filiação;
4. **Balance:** A grande maioria dos clientes possuem entre 0 e 150 mil reais;
5. **NumOfProducts:** A maioria dos clientes utiliza entre 1 e 2 produtos, mas há excessão com maior número de produtos; 
6. **EstimatedSalary:** A maioria possue salário entre 50 e 150 mil;

- Explorei as estatísticas básicas das colunas numéricas, fazendo as seguintes análises: 

1. **CreditScore:** 
- Média: 650,5288
- Máximo: 850
- 50% dos clientes possuem pontuação de crédito abaixo de 652;
2. **Age:**
- Média: 38,9218
- Máximo: 92
- 75% dos clientes possuem idade inferior a 44;
3. **Tenure:**        
- Média: 5,0128
- Máximo: 10
- Tempo de filiação uniforme;
4. **Balance:**  
- Média: 76.485,889288
- Máximo: 250.898,09
- Pelo menos 25% dos clientes possuem saldo igual a 0, e dispersão igual a aproximadamente 0,82, indicando valores muito espalhados e heterogêneos;
5. **NumOfProducts:**
- Média: 1,5302
- Máximo: 4
- Mais de 50% (menos de 75%) dos clientes estão abaixo da média;
6. **HasCrCard:**
- Pelo menos 50% dos clientes possuem cartão de crédito;
7. **IsActiveMember:**
- Pelo menos 50% dos clientes são ativos;
8. **EstimatedSalary:** 
- Média: 100.090,239881
- Máximo: 199.992,480000 
- Valores aparentemente uniforme, porém o salário estimado com menor valor é de 11,58;     
9. **Exited:**
- Ao menos 75% não saíram do banco.

### 3. Transformação de dados

- As colunas presentes no conjunto de dados já contam a bem a história dos clientes, portanto não utilizei a engenharia de funcionalidades;
- Não houve necessidade de padronização ou normalização, pois nenhum algoritmo de aprendizado de máquina será utilizado.

### 4. Mineração de dados

- Para a análise univariada, plotei histogramas e gráficos de barras das colunas-chave, fazendo a seguintes análises:

1. **CreditScore:** A distibuição é simétrica, com maioria da pontuação de crédito dos clientes se concentrando entre 600 e 700. Há casos atípicos com um número elevado de pontuação de crédito;
2. **Age:** A distribuição é assimétrica à esquerda, o que significa que a maioria dos clientes tem uma idade menor, concentrada bastante entre 30 a 50 anos, com algumas quantidades bem maiores que outras no mesmo intervalo, havendo também casos de pessoas com muita idade;
3. **Tenure:** A distribuição de tempo em anos de filiação dos clientes é aproximadamente uniforme. Há casos atípicos com clientes tendo bem pouco tempo (entre 0 e 1) e muito tempo (entre 9 e 10);
4. **EstimatedSalary:** A distribuição de salário estimado dos clientes é muito uniforme;
5. **Gender:** A distribuCreditScoreição é levemente uniforme entre os sexos, com o masculino se sobressaindo;
6. **Geography:** A distribuição concentra aproximadamente 50% dos clientes morando na França, com a outra metade sendo dividida uniformente entre os restantes;
7. **IsActiveMember:** A distribuição é uniforme, com pouco mais de 50% dos clientes sendo ativos;
8. **HasCrCard:** A maioria dos clientes possuem cartão, cerca do dobro em comparação aos que não possuem;

- Para a análise bivariada/multivariada, explorei as relações entre: 

1. **Exited x :** A saída ou permanência é uniforme em relação à pontuação de crédito, ou seja, não há diferença clara entre quem saiu ou ficou. Há alguns casos atípicos em relação a quem saiu, indicando clientes com valores que se desviam da tendência geral;
2. **Exited x Age:** A classificação mediana dos clientes que não saíram oscila entre 30 e 40 anos, com metade dos que continuaram estando entre por volta de 30 e pouco mais de 40 anos, havendo idades avançadas (50+) entre os que ficaram. Já a classificação mediana dos clientes que saíram oscila entre 40 e 50 anos, com metade dos que saíram oscilando entre pouco menos de 40 e 50 anos, havendo algumas poucas idades avançadas (70+) entre os que saíram;
3. **Exited x Tenure:** A classificação mediana dos clientes que não saíram está por volta de 5 anos de filiação, com metade dos que continuaram oscilando entre 3 e 7 anos de filiação. A classificação mediana dos clientes que saíram está por volta de 5 anos de filiação, com metade dos que continuaram oscilando entre pouco mais de 2 e pouco menos de 7 anos de filiação;
4. **Exited x EstimatedSalary:** A saída ou permanência é uniforme em relação ao salário estimado, portanto, o salário não parece influenciar a decisão de sair.
5. **Exited x Gender:** Por volta de 25% das clientes do sexo feminino deixaram o banco, enquanto pouco mais de 15% dos clientes masculinos deixaram o banco; 
6. **Exited x Geography:** Pouco mais de 15% dos clientes franceses e espanhóis saíram do banco (com espanhóis tendo saído um pouco mais) e entre 30% e 35% dos clientes alemães saíram do banco;
7. **Exited x IsActiveMember:** Entre os clientes não ativos, por volta de 10-15% saíram, já entre os ativos, por volta de 5-10% saíram. Os inativos têm taxa de churn aproximadamente 2x maior que os ativos;
8. **Exited x HasCrCard:** Entre os clientes sem cartão de crédito, por volta de 5% saíram, já entre os com, por volta de 15% saíram. Os sem cartão têm taxa de churn aproximadamente 3x maior que os que possuem.

### 5. Avaliação de padrões

- Age, Tenure, Gender, Geography, IsActiveMember e HasCrCard fornecem dados interessantes em relação à saída;
- Fatores diversos influenciam à saída, não havendo padrão quanto a fatores categóricos ou numéricos;
- CreditScore, Age e NumOfProducts apresentam outliers, com todos representando valores discrepantes genuínos.