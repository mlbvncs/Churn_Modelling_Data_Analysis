# Análise de dados utilizando Python

### Passo a passo

### 0. Imports

1. Inicialmente importei as bibliotecas pandas, seaborn e o método pyplot da biblioteca matplotlib.

### 1. Carregando o conjunto de dados

1. Carreguei o conjunto de dados Churn_Modelling.csv;
2. Apresentei informações e as primeiras linhas do conjunto de dados, observando que nenhuma coluna apresentava valor nulos entre seus dados.

### 2. Pré-processamento de dados

1. Verifiquei a quantidade de valores ausentes (nulos) nas colunas do dataframe, com todas sendo 0, como percebido anteriormente, não necessitando de tratamento;
2. Plotei boxplot das colunas com valores numéricos que valiam a pena identificar possíveis outliers (colunas com valores sendo 0 ou 1 não entraram), fazendo a seguintes análises:

**CreditScore:** Alguns clientes possuem pontos de créditos bem baixos;
**Age:** Muitos clientes possuem idades avançadas (60+), chegando a passar dos 90 anos;
**Tenure:** A maioria dos clientes possuem entre 3 a 7 anos de filiação;
**Balance:** A grande maioria dos clientes possuem entre 0 e 150 mil reais;
**NumOfProducts:** A maioria dos clientes utiliza entre 1 e 2 produtos, mas há excessão com maior número de produtos; 
**EstimatedSalary:** A maioria possue salário entre 50 e 150 mil;
3. Explorei as estatísticas básicas das colunas numéricas, fazendo as seguintes análises: 

**CreditScore:** 
- Média: 650,5288
- Máximo: 850
- 75% dos clientes possuem pontuação de crédito abaixo de 718;
**Age:**
- Média: 38,9218
- Máximo: 92
- 75% dos clientes possuem idade inferior a 44;
**Tenure:**        
- Média: 5,0128
- Máximo: 10
- 50% dos clientes possuem tempo de filiação inferior a 5 anos;
**Balance:**  
- Média: 76.485,889288
- Máximo: 250.898,09
- Pelo menos 25% dos clientes possuem saldo igual a 0, e dispersão igual a aproximadamente 0,82, indicando valores muito espalhados e heterogêneos;
**NumOfProducts:**
- Média: 1,5302
- Máximo: 4
- 50% dos clientes utilizam somente 1 produto;
**HasCrCard:**
- Pelo menos 50% dos clientes possuem cartão de crédito;
**IsActiveMember:**
- Pelo menos 50% dos clientes são ativos;
**EstimatedSalary:** 
- Média: 100.090,239881
- Máximo: 199.992,480000 
- O salário estimado com menor valor é de 11,58;     
**Exited:**
- Ao menos 75% não saíram do banco.

### 3. Transformação de dados

1. As colunas presentes no conjunto de dados já contam a bem a história dos clientes, portanto não utilizei a engenharia de funcionalidades;
2. Não houve necessidade de padronização ou normalização, pois nenhum algoritmo de aprendizado de máquina será utilizado.

### 4. Mineração de dados

1. Para a análise univariada, plotei histogramas e gráficos de barras das colunas-chave, fazendo a seguintes análises:

**CreditScore:** A distibuição é simétrica, com maioria da pontuação de crédito dos clientes se concentrando entre 600 e 700. Há casos atípicos com um número elevado de pontuação de crédito;
**Age:** A distribuição é assimétrica à esquerda, o que significa que a maioria dos clientes tem uma idade menor, concentrada bastante entre 30 a 50 anos, com algumas quantidades bem maiores que outras no mesmo intervalo, havendo também casos de pessoas com muita idade;
**Tenure:** A distribuição de tempo em anos de filiação dos clientes é aproximadamente uniforme. Há casos atípicos com clientes tendo bem pouco tempo (entre 0 e 1) e muito tempo (entre 9 e 10);
**EstimatedSalary:** A distribuição de salário estimado dos clientes é muito uniforme;
**Gender:** A distribuição é levemente uniforme entre os sexos, com o masculino se sobressaindo;
**Geography:** A distribuição concentra aproximadamente 50% dos clientes morando na França, com a outra metade sendo dividida uniformente entre os restantes;
**HasCrCard:** A maioria dos clientes possuem cartão, cerca do dobro em comparação aos que não possuem;
IsActiveMember: A distribuição é uniforme, com pouco mais de 50% dos clientes sendo ativos;
**Exited:** A grande maioria dos clientes que o banco já teve continuam filiados.

2. Para a análise bivariada/multivariada, explorei as relações entre: 

**Exited x CreditScore:** A saída ou permanência é uniforme em relação à pontuação de crédito. Há alguns casos atípicos em relação a quem saiu, indicando clientes com valores que se desviam da tendência geral;
**Exited x Age:** A classificação mediana dos clientes que não saíram oscila entre 30 e 40 anos, com metade dos que continuaram estando entre por volta de 30 e pouco mais de 40 anos; havendo idades avançadas (50+) entre os que ficaram. Já a classificação mediana dos que clientes que saíram oscila entre 40 e 50 anos, com metade dos que saíram oscilando entre pouco menos de 40 e 50 anos; havendo algumas poucas idades avançadas (70+) entre os que saíram;
**Exited x Tenure:** A classificação mediana dos clientes que não saíram está por volta de 5 anos de filiação, com metade dos que continuaram oscilando entre 3 e 7 anos de filiação. A classificação mediana dos clientes que saíram está por volta de 5 anos de filiação, com metade dos que continuaram oscilando entre pouco mais de 2 e pouco menos de 7 anos de filiação;
**Exited x EstimatedSalary:** A saída ou permanência é uniforme em relação ao salário estimado.
**Exited x Gender:** Por volta de 25% das clientes do sexo feminino deixaram o banco, enquanto pouco mais de 15% dos clientes masculinos deixaram o banco; 
**Exited x Geography:** Pouco mais de 15% dos clientes franceses e espanhóis saíram do banco (com espanhóis tendo saído um pouco mais) e entre 30% e 35% dos clientes alemães saíram do banco;
**Exited x IsActiveMember:** Entre os clientes não ativos, por volta de 3500 permaneceram e por volta de 1000 e 1500 saíram, Já entre os ativos, por volta de 4000 e 4500 não saíram e pouco menos de 1000 saíram;
**Exited x HasCrCard:** Entre os clientes sem cartão de crédito, entre 2000 e 3000 não saíram e entre 500 e 1000 saíram. Já entre os com, entre 5000 e 6000 continuaram e entre 1000 e 2000 saíram.

### 5. Avaliação de padrões