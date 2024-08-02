# 🌟 Aula de Função Quadrática 🌟

Bem-vindo à nossa aula sobre funções quadráticas e suas aplicações! 🚀
Neste repositório, você encontrará um exemplo de como visualizar e interagir com funções quadráticas usando Python e Matplotlib.

## 📋 Índice

- [Introdução](#🎓-introdução)
- [Pré-requisitos](#🛠-pré-requisitos)
- [Instalação](#🚀-instalação)
- [Código da Função Quadrática](#📝-código-da-função-quadrática)
- [Como Executar](#▶️-como-executar)
- [Recursos Adicionais](#📚-recursos-adicionais)

## 🎓 Introdução

As funções quadráticas são equações polinomiais de segundo grau da forma \( f(x) = ax^2 + bx + c \). Elas descrevem uma parábola no plano cartesiano, que pode abrir para cima ou para baixo, dependendo do coeficiente \( a \). 

Nesta aula, exploraremos como:

- Compreender os coeficientes da função quadrática.
- Encontrar as raízes e o vértice da parábola.
- Aplicar essas funções a problemas reais, como maximização de visualizações em campanhas de mídia.

## 🛠 Pré-requisitos

Antes de começar, certifique-se de ter o seguinte instalado em sua máquina:

- [Python](https://www.python.org/) (versão 3.6 ou superior)
- [pip](https://pip.pypa.io/en/stable/installation/)
- [Matplotlib](https://matplotlib.org/) para visualização gráfica

## 🚀 Instalação

1. Clone este repositório:

    ```bash
    git clone https://github.com/seu-usuario/aula-funcao-quadratica.git
    cd aula-funcao-quadratica
    ```

2. Instale as dependências do Matplotlib:

    ```bash
    pip install matplotlib
    ```

## 📝 Código da Função Quadrática

Crie um arquivo Python chamado `aula_quadratica.py` com o seguinte conteúdo:

```python
import numpy as np
import matplotlib.pyplot as plt
from matplotlib.widgets import TextBox

# Definir a função quadrática
def func(x):
    return -2*x**2 + 80*x

# Criar dados
x = np.linspace(0, 50, 400)  # Ajustar intervalo x para 0 a 50
y = func(x)

# Encontrar o ponto máximo da função
x_max = 80 / 4  # O ponto máximo para a função dada é x = -b/(2a)
y_max = func(x_max)

# Configurar o gráfico
fig, ax = plt.subplots(figsize=(12, 8))
ax.plot(x, y, color='blue', label='V(x) = -2x^2 + 80x')
ax.plot(x_max, y_max, 'ro', markersize=8, label='Máximo')  # Ponto máximo
ax.set_xlim(0, 50)
ax.set_ylim(0, y_max + 10)  # Ajustar intervalo y para uma visualização melhor
ax.set_xlabel('Valor gasto (em reais)')
ax.set_ylabel('Número de visualizações (em centenas)')
ax.set_title('Função Quadrática para Maximização de Views')
ax.legend()
ax.grid(True)

# Adicionar um campo de entrada
def submit(text):
    try:
        x_input = float(text)
        if 0 <= x_input <= 50:
            y_input = func(x_input)
            if y_input < 0:
                y_input = 0  # Garantir que o valor de visualização não seja negativo
            # Atualiza o ponto com base na entrada do usuário
            cursor.set_data([x_input], [y_input])
            # Atualiza o texto de visualizações
            visualizations_text.set_text(f'Número de visualizações: {y_input:.2f} centenas')
            ax.figure.canvas.draw()
        else:
            visualizations_text.set_text('Valor fora do intervalo. Insira um valor entre 0 e 50.')
    except ValueError:
        visualizations_text.set_text('Insira um valor numérico válido.')

# Criar uma caixa de texto para entrada do usuário
axbox = plt.axes([0.15, 0.1, 0.7, 0.05])  # Ajuste da posição da caixa de texto
text_box = TextBox(axbox, 'Valor gasto:', initial='0')
text_box.on_submit(submit)

# Adicionar um cursor ao gráfico
cursor, = ax.plot([], [], 'ro', markersize=8, label='Ponto selecionado')

# Adicionar um texto para mostrar o número de visualizações
visualizations_text = plt.figtext(0.5, 0.02, 'Número de visualizações: 0.00 centenas', 
                                  ha='center', va='center', fontsize=12, 
                                  bbox=dict(facecolor='lightyellow', edgecolor='black', boxstyle='round,pad=0.5'),
                                  style='italic', color='black')

# Mostrar o gráfico
plt.show()
