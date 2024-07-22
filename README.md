🌟 Aula de Teste com Selenium 🌟
Bem-vindo à nossa aula de teste automatizado usando Selenium! 🚀 Este repositório contém um exemplo simples de como usar Selenium para interagir com um formulário HTML.
📋 Índice

    Introdução
    Pré-requisitos
    Instalação
    Código do Formulário
    Script de Teste
    Como Executar
    Recursos Adicionais
    
🎓 Introdução

Selenium é uma ferramenta poderosa para automação de navegadores web. Com Selenium, você pode realizar tarefas como:

    Automação de testes para aplicações web.
    Web scraping (extração de dados).
    Automação de tarefas repetitivas no navegador.

🛠 Pré-requisitos

Antes de começar, certifique-se de ter o seguinte instalado em sua máquina:

Python (versão 3.6 ou superior)
pip
Google Chrome (ou outro navegador de sua escolha)
ChromeDriver (compatível com a versão do seu Chrome)

🚀 Instalação

Clone este repositório:
    ``git clone https://github.com/seu-usuario/aula-teste-selenium.git
    cd aula-teste-selenium``

Instale as dependências do Selenium:`
    ``pip install selenium``

Coloque o ChromeDriver no seu PATH ou na mesma pasta do script Python.

🧪 Script de Teste

Crie um arquivo Python chamado aulateste.py com o seguinte conteúdo:

```
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
import time

# Criar um webdriver para Chrome
driver = webdriver.Chrome()

# Acessar a página da Bipo

driver.get("http://bipoconcursos.com.br")
time.sleep(5)

#Clicar em fazer inscrição

driver.find_element(By.XPATH, "/html/body/div[1]/div/a[1]")
time.sleep(5)


#Clicar no campo nome e preencher o nome

def preenche_formulario():
    #preenche o nome
    driver.find_element(By.XPATH, '//*[@id="nome"]').send_keys("Cássio de Albuquerque")
    time.sleep(2)

    #preehche o campo cpf
    driver.find_element(By.XPATH, '//*[@id="cpf"]').send_keys('31205370803')
    time.sleep(2)

    #preenche o campo e-mail
    driver.find_element( By.XPATH, '//*[@id="email"]').send_keys("cassio.matematematica@gmail.com")
    time.sleep(2)
    
    #preenche o campo cep
    driver.find_element(By.XPATH,'//*[@id="cep"]').send_keys('03180060')
    time.sleep(2)

    #preenche o campo número do endereço
    driver.find_element(By.XPATH, '//*[@id="numero"]').send_keys('6')
    time.sleep(2)

    #clica no botão para enviar o formulário
    driver.find_element(By.XPATH, '/html/body/div[3]/form/button').click()
    time.sleep(5)
```

▶️ Como Executar
  #Chamamos a função para executar o teste
  ```preenche_formulario()```

O navegador abrirá, preencherá o formulário e você verá o resultado.

📚 Recursos Adicionais

Documentação do Selenium
Tutoriais de Selenium com Python

Divirta-se automatizando seus testes e explorando o poder do Selenium! 🚀

Se tiver dúvidas ou sugestões, fique à vontade para abrir uma issue ou um pull request.

Happy Coding! 💻✨




