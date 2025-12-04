# Modelos Preditivos para Análise de Dados de Vendas 📈

> Projeto desenvolvido para a disciplina de Inteligência Artificial do curso de Análise e Desenvolvimento de Sistemas (FATEC Mogi Mirim).

## 📌 Sobre o Projeto

Este projeto demonstra a aplicação prática de algoritmos de **Machine Learning** para resolver um problema real de regressão.  
O objetivo foi criar um sistema capaz de prever o volume de vendas semanais de uma rede de varejo, lidando com desafios como **sazonalidade**, **feriados** e **variáveis categóricas**.

O modelo escolhido foi o **Random Forest Regressor**, devido à sua capacidade de lidar com dados não lineares e oferecer robustez contra *overfitting*.

## 🛠 Tecnologias e Bibliotecas

- **Python 3.13.5**
- **Pandas:** engenharia de atributos e manipulação de dados.
- **Scikit-learn:** implementação do algoritmo Random Forest e métricas de avaliação.
- **Matplotlib:** visualização dos resultados (previsão vs. valores reais).
- **NumPy:** computação numérica.
- **Jupyter Notebook:** ambiente interativo para desenvolvimento e visualização dos experimentos.

## 📂 O Dataset

Os dados utilizados são do dataset público **Walmart Sales Forecast** (Kaggle), contendo:

- Histórico de vendas semanais (2010–2012).
- Indicadores econômicos (CPI, desemprego, preço do combustível).
- Dados das lojas (tamanho e tipo).

## 🚀 Como Executar (Jupyter Notebook)

1. **Clone o repositório:**

   ```bash
   git clone https://github.com/jesua07/Trabalho_IA.git
   ```

2. **Entre na pasta do projeto:**

   ```bash
   cd Trabalho_IA
   ```

3. **(Opcional, mas recomendado) Crie e ative um ambiente virtual:**

   ```bash
   python -m venv .venv
   # Windows
   .venv\Scripts\activate
   # Linux / macOS
   source .venv/bin/activate
   ```

4. **Instale as dependências:**

   ```bash
   pip install pandas scikit-learn matplotlib numpy jupyter
   ```

5. **Certifique-se de que os arquivos CSV do dataset estejam na raiz da pasta do projeto.**

6. **Inicie o Jupyter Notebook:**

   ```bash
   jupyter notebook
   ```

7. **Abra o notebook do projeto** (por exemplo, `modelo_vendas.ipynb`) pelo navegador e execute as células em ordem.

> 💡 Caso esteja utilizando Google Colab, basta enviar o notebook (`.ipynb`) e fazer o upload dos arquivos CSV.  
> Nesse caso, o comando de instalação pode ser executado em uma célula do Colab:
>
> ```python
> !pip install pandas scikit-learn matplotlib numpy
> ```

## 🧠 Destaques da Implementação

### 1. Engenharia de Atributos (*Feature Engineering*)

Como os algoritmos não interpretam datas diretamente, foi necessário extrair informações numéricas para capturar a **sazonalidade**:

- Criação de colunas para `Semana_do_Ano`, `Mes` e `Dia`.
- Transformação da coluna `Type` (A, B, C) usando **One-Hot Encoding**.

### 2. Validação Temporal

Para evitar o erro de *data leakage* (usar dados do futuro para prever o passado), não foi utilizado o `train_test_split` aleatório.

- **Treino:** dados de 2010 e 2011.
- **Teste/validação:** dados de 2012 (simulando previsão futura).

## 📊 Resultados

O modelo foi avaliado com dados nunca vistos durante o treinamento (ano de 2012):

| Métrica                             | Resultado       |
| :---------------------------------- | :-------------- |
| **MAE (Erro Médio Absoluto)**      | **R$ 2.212,44** |
| **RMSE (Raiz do Erro Quadrático)** | **R$ 4.914,86** |

### Variáveis mais importantes

O algoritmo identificou que os fatores que mais impactam as vendas são:

1. Departamento (`Dept`)
2. Tamanho da loja (`Size`)
3. Sazonalidade (`Semana_do_Ano`)
