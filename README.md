🧠 Mentor

> “Um mentor de dados impulsionado por IA local, que não apenas faz — mas te ensina o porquê.”




---

🚀 Visão Geral

LLaMA Data Mentor é uma biblioteca Python projetada para analisar e tratar dados com explicações educativas, utilizando o poder do modelo LLaMA local (via Ollama ou HuggingFace).

O objetivo não é apenas automatizar tarefas de limpeza e transformação de dados, mas também ensinar o usuário o raciocínio por trás de cada etapa, com código comentado e abordagens alternativas quando aplicável.


---

🧩 Funcionalidades

📂 Aceita arquivos .csv, .xlsx ou DataFrame (pandas).

🧠 Interpreta prompts em linguagem natural (ex: "Quero remover outliers e normalizar colunas numéricas.").

🧾 Gera código Python comentado e explicativo.

💬 Explica o motivo de cada decisão e mostra formas alternativas.

⚙ Permite executar o código gerado com segurança (modo sandbox).

🧰 Suporte local via LLaMA/Ollama (sem necessidade de API externa).



---

💻 Exemplo de Uso

from llama_data_mentor import DataMentor
import pandas as pd

# Carrega dados
df = pd.read_csv("clientes.csv")

# Inicializa o mentor
mentor = DataMentor(model="llama3", host="http://localhost:11434")

# Prompt em linguagem natural
prompt = "Quero limpar valores nulos e normalizar colunas numéricas"

# Gera código e explicação
response = mentor.explain_and_propose(df, prompt)

print("=== Código Gerado ===")
print(response["code"])

print("\n=== Explicação ===")
print(response["explanation"])

# Executa o código proposto (opcional)
mentor.execute(df, response["code"])

🧠 Exemplo de Saída

Código gerado:

# ⿡ Identificar colunas com valores nulos
print(df.isnull().sum())

# ⿢ Remover linhas com valores nulos
df = df.dropna()

# ⿣ Normalizar colunas numéricas usando MinMaxScaler
from sklearn.preprocessing import MinMaxScaler
scaler = MinMaxScaler()
df[df.select_dtypes(include=['float', 'int']).columns] = scaler.fit_transform(
    df.select_dtypes(include=['float', 'int'])
)

Explicação:

> Primeiro identificamos colunas com valores ausentes.
Se houver poucos valores nulos, dropna() é simples e eficaz.
Em seguida, aplicamos MinMaxScaler para normalizar os dados numéricos entre 0 e 1, garantindo que diferentes escalas não prejudiquem modelos de aprendizado.
Alternativamente, você poderia usar StandardScaler para padronizar os dados (média 0, desvio padrão 1).




---

⚙ Instalação

🔸 Pré-requisitos

Python 3.10+

Ollama instalado e com o modelo LLaMA disponível:

ollama pull llama3


🔸 Instalar dependências

pip install -r requirements.txt

🔸 Instalar localmente (modo dev)

pip install -e .


---

🧱 Estrutura do Projeto

llama_data_mentor/
│
├── llama_data_mentor/
│   ├── _init_.py
│   ├── mentor.py          # Classe principal
│   ├── llm_interface.py   # Comunicação com LLaMA
│   ├── formatters.py      # Formatação e parsing das respostas
│   ├── sandbox.py         # Execução segura do código
│   ├── utils.py           # Funções auxiliares
│
├── examples/
│   ├── tratamento_nulos.ipynb
│
├── tests/
│   ├── test_mentor.py
│
├── requirements.txt
├── setup.py
└── README.md


---

🔬 Tecnologias Utilizadas

Função	Biblioteca

Manipulação de dados	pandas, openpyxl
IA local	ollama, requests
Execução segura de código	RestrictedPython
Parsing e formatação	json, re
CLI interativa (futuro)	typer, rich



---
