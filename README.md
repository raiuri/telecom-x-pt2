# Challeng_Telecom_x_pt2
Este repositório documenta a segunda fase do projeto da Telecom X, onde desenvolvemos modelos de Machine Learning para prever a evasão de clientes (churn). O projeto aborda desde o pré-processamento dos dados até a interpretação dos resultados, com foco em entregar insights estratégicos que a empresa pode usar para reter clientes.




 """# Análise e Modelagem Preditiva de Evasão de Clientes

## Objetivo
Este projeto tem como objetivo analisar dados de clientes de uma empresa de serviços para:
- Identificar fatores que influenciam a evasão (churn);
- Desenvolver modelos preditivos para prever quais clientes têm maior probabilidade de cancelar o serviço;
- Fornecer insights para criação de estratégias de retenção.

---

## Etapas do Projeto

### 1. Carregamento e Exploração dos Dados
- Leitura do arquivo `dados_tratados.csv`;
- Inspeção inicial para entender estrutura e conteúdo.

### 2. Tratamento de Dados
- Remoção de linhas com valores ausentes na coluna `Cancelou`;
- Salvamento do conjunto tratado como `dados_tratados.csv`.

### 3. Análise da Proporção de Classes
- Cálculo da proporção de clientes que cancelaram (Yes) e que permaneceram (No);
- Identificação de desequilíbrio significativo entre as classes.

### 4. Codificação de Variáveis Categóricas
- Aplicação de One-Hot Encoding (`pd.get_dummies`);
- Exclusão da coluna `ID_Cliente` por não ser relevante.

### 5. Análise de Correlação
- Cálculo da matriz de correlação para variáveis numéricas e a variável alvo (`Cancelou_Yes`);
- Identificação das variáveis mais correlacionadas, como:
  - `Tipo_Internet_Fiber optic`;
  - `Metodo_Pagamento_Electronic check`;
  - `Cobranca_Mensal`;
  - `Fatura_Digital_Yes`;
  - `Meses_Permanencia` (correlação negativa).

### 6. Análise Exploratória de Variáveis-Chave
- Boxplots para `Meses_Permanencia` e `Cobranca_Total` vs `Cancelou_Yes`;
- Conclusão: clientes que cancelam tendem a ter menor tempo de permanência e menor cobrança total.

### 7. Preparação para Modelagem
- Separação de features (`X`) e alvo (`y`);
- Divisão em treino (70%) e teste (30%) com estratificação;
- Aplicação de **SMOTE** para balancear classes no treino.

### 8. Modelagem Preditiva
Modelos utilizados:
- **Random Forest Classifier** (sem normalização);
- **KNeighbors Classifier (KNN)** (com normalização via `StandardScaler`).

Passos:
- Treinamento com conjunto de treino balanceado;
- Avaliação com métricas: *precision*, *recall*, *f1-score*;
- Geração de matrizes de confusão.

### 9. Otimização de Hiperparâmetros (Random Forest)
- Uso do **GridSearchCV** otimizando para `f1-macro`;
- Melhores parâmetros:
{'class_weight': 'balanced', 'max_depth': 15, 'min_samples_split': 2, 'n_estimators': 100}

### 10. Importância das Variáveis (Random Forest)
Variáveis mais relevantes:
- `Meses_Permanencia`;
- `Cobranca_Total`;
- `Cobranca_Mensal`;
- `Tipo_Contrato_Two year`;
- `Tipo_Contrato_One year`;
- `Suporte_Tecnico_Yes`;
- `OnlineSecurity_Yes`.

---

## Resultados
- **Random Forest** superou o KNN, especialmente em recall da classe positiva (`Cancelou_Yes`);
- Identificação clara dos principais fatores de evasão:
  - Tempo de permanência;
  - Tipo de contrato;
  - Valor da cobrança;
  - Uso de serviços adicionais.

---

## Estratégias Recomendadas
1. Criar programas de retenção focados nos primeiros meses de serviço;
2. Incentivar contratos de longo prazo;
3. Promover serviços agregados (Suporte Técnico, Segurança Online);
4. Investigar causas de evasão entre clientes de fibra óptica;
5. Usar o modelo Random Forest para prever clientes de alto risco e oferecer ações de retenção personalizadas.

---

## Tecnologias Utilizadas
- Python (Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn, Imbalanced-learn)
- Jupyter Notebook
- SMOTE para balanceamento
- GridSearchCV para otimização

---

## Estrutura de Arquivos
|-- dados_tratados.csv       # Base de dados tratada
|-- notebook_projeto.ipynb   # Análises e modelagem
|-- README.md                # Documentação do projeto

---

## Autor
Raiuri Santos
"""
