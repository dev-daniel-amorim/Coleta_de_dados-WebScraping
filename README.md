# Coleta de dados - Web Scraping

Uma das etapas de um projeto data science é a coleta de dados, Web Scraping é um método de coleta onde podemos usar a ferramenta Selenium do Python para realizar automação web.<br>
O intuito deste material é apresentar a biblioteca Selenium do python, com ela vamos aprender métodos e módulos para extração de dados via web.<br>

# Instalando o Selenium

No Jupyter Notebook ou no prompt de comando do anaconda digite o comando abaixo para instalar o Selenium:

        - pip install --upgrade selenium
        
Para fazer automação web o navegador mais indicado é o Google Chrome, se não tiver use o link abaixo:

- <a href="https://www.google.com/chrome/"> Clique para baixar o Google Chrome</a>

Após instalado abra o navegador e digite para saber a versão do seu Chrome:

        - chrome://settings/help

# Instalando o web driver

O WebDriver manipula um navegador nativamente, como um usuário faria, seja localmente ou em uma máquina remota usando o servidor Selenium, marca um salto em termos de automação do navegador.<br>
- Selenium WebDriver é uma recomendação W3C
- WebDriver é projetado como uma interface de programação simples e mais concisa.
- WebDriver é uma API compacta orientada a objetos. 
- Ele manipula o navegador de forma eficaz.

No link abaixo podemos baixar o web driver, porém tenha em mãos a versão do seu navegador e baixe a versão web driver compatível:<br>
Exemplo: Se seu crome é versão 108.xxxx.xx baixe a versão 108 do web driver (baixe 32bits independente de ser 64).

- <a href="https://chromedriver.chromium.org/downloads"> Clique para baixar o Web Driver</a>

Com o download em mãos, voçê irá ter o arquivo (chromedriver.exe) copie e cole este arquivo na mesma pasta onde está instalado o PYTHON, geralmente em c:/user/anaconda3, feito isso seu web drive está pronto.<br>

Para garantir que o web driver está instalado corretamente, abra o jupyter notebook e vamos importa-lo, digite o comando abaixo deverá abrir o navegador automatizado, se não abrir há erros na instalação.

        from selenium import webdriver
        navegador = webdriver.Chrome()

Tudo pronto! as etapas acima só precisam ser feitas uma vez, a partir de agora o Selenium e web drive estão prontos para por a mão na massa!

## Observações
O webdriver tem que ser atualizado sempre que atualizar o chrome, ou o serviço irá parar de funcionar, outra alternativa é baixar o gerenciador de webdriver, uma biblioteca que faz todo serviço por você:

        !pip install webdriver-manager

logo em seguida devemos rodar as linhas de código abaixo que irá instalar automáticamente o webdriver:

        From selenium import webdriver
        from selenium.webdriver.chrome.service import Service
        from webdriver_manager.chrome import ChromeDriverManager

        servico = Service(ChromeDriverManager().install())
        driver = Webdriver.Chrome(service=servico)

# Utilizando recursos do Selenium

Abrindo um site (get)

        navegador = webdriver.Chrome()
        navegador.get("https://www.google.com/")
     
 # Selecionando elementos (find_element)
Usaremos o (find_element) para selecionar algum elemento em uma página web, mas pra isso precisamos importar o BY:<Br>

from selenium.webdriver.common.by import By
