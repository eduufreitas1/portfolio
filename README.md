# portfolio
if (!require(reticulate)) {
  install.packages("reticulate")
}
library(reticulate)

# Use a função use_python para especificar o caminho do interpretador Python, se necessário
# use_python("/caminho/para/o/python")

# Agora, você pode começar a escrever seu código Python entre as funções py_run_string() ou py_run_file()

# Exemplo executando uma string de código Python
py_run_string("
print('Olá, mundo do Python no RStudio!')
")

# Exemplo executando um arquivo Python
# py_run_file('/caminho/para/seu_script.py')

# Você também pode interagir com variáveis entre R e Python
# Definindo uma variável em Python e recuperando em R
py_run_string("x = 42")
x <- py$x
print(x)

# Definindo uma variável em R e usando em Python
y <- 100
py$y <- y
py_run_string("print(y)")

library(reticulate)

# Se necessário, especifique o caminho do Python
# use_python("/caminho/para/o/python")

py_run_string("
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np

# Carregando os dados
file_path = 'C:/Users/Acer/Documents/Emissions_per_capita.xlsx'
df = pd.read_excel("C:/Users/Acer/Documents/Emissions_per_capita.xlsx")  

# Ordenar os dados pelo valor de 'Emissions per capita' em ordem decrescente
data_sorted = data.sort_values(by='Emissions per capita', ascending=False)

# Gerar uma paleta de cores aleatórias
colors = np.random.rand(len(data_sorted), 3)

# Criar o gráfico de colunas
plt.figure(figsize=(10, 6))
plt.bar(data_sorted['Country'], data_sorted['Emissions per capita'], color=colors)
plt.xlabel('Country')
plt.ylabel('Emissions per capita')
plt.title('Emissions per capita by Country')
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
")
