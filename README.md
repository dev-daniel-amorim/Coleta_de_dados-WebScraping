# Coleta de dados - Web Scraping

Uma das etapas de um projeto data science é a coleta de dados, Web Scraping é um método de coleta onde podemos usar a ferramenta Selenium do Python para realizar automação web assim podemos coletar dados da internet para diversas finalidades detro de um projeto data science.<br>
O intuito deste material é apresentar a biblioteca Selenium do python, com ela vamos aprender métodos e módulos para extração de dados via web mas atenção, esse tutorial é superficial, apenas para demostrar o "caminho das pedras", para mais leia a documentação do Selenium em:.<br>

- <a href="https://selenium-python.readthedocs.io/"> Ver documentação Selenium </a>

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
        
Cada elemento de uma página possui atributos, sabendo disso o selenium é capaz de selecionar algo por seus atributos, são eles:
       
        ID = "id"
        NAME = "name"
        XPATH = "xpath"
        LINK_TEXT = "link text"
        PARTIAL_LINK_TEXT = "partial link text"
        TAG_NAME = "tag name"
        CLASS_NAME = "class name"
        CSS_SELECTOR = "css selector"
        
# Exercicio 01 - Automatizando uma pesquisa
### Vamos abrir o site do google, digitar "selenium do python" no campo de busca e apertar o botão "pesquisar" tudo isso de forma automatizada com selenium:
        
- Pra isso iremos selecionar o campo de busca do google usando o atributo XPATH deste campo, vejao vídeo abaixo para aprender como pegar o XPATH (ou qqualquer outro atributo) de um elemento:
        
https://user-images.githubusercontent.com/115194365/208697662-b19e4db3-5a62-463a-b3e9-d3e521afcfd2.mp4

- Com XPATH do campo de busca em mãos vamos:
        
        navegador = webdriver.Chrome()
        # abre o google
        navegador.get("https://www.google.com/")
        # Seleciona o xpath do campo de busca e digita a procura
        navegador.find_element(By.XPATH, "/html/body/div[1]/div[3]/form/div[1]/div[1]/div[1]/div/div[2]/input").send_keys("selenium do python")
        # clica no botão pesquisar
        navegador.find_element(By.XPATH, "/html/body/div[1]/div[3]/form/div[1]/div[1]/div[4]/center/input[1]").click()

# Exercício 01 - Pegando informações de elementos
- Pegando Texto

        navegador = webdriver.Chrome()
        navegador.get("https://www.google.com/")
        texto = navegador.find_element(By.XPATH, "/html/body/div[1]/div[4]/div/div/a").text
        print(texto)
        
        **** IRÁ RETONAR O TEXTO: "buscas que marcaram 2022" que é o texto do elemento.

- Pegando atributos: vamos pegar link da logo do google, que está no attr "SRC"
        
        navegador = webdriver.Chrome()
        navegador.get("https://www.google.com/")
        link = navegador.find_element(By.XPATH, '//*[@id="hplogo"]').get_attribute('src')
        print(link)
        
Retorna o link da logo:
        
        https://www.google.com/logos/doodles/2022/seasonal-holidays-2022-6753651837109831.4-law.gif
<p align="center">
        <img src="https://www.google.com/logos/doodles/2022/seasonal-holidays-2022-6753651837109831.4-law.gif"/>
</p>   
        
# Métodos de condições
O Selenium fornece diversas métodos condiçionais facilitando a automação em navegadores, são eles:
        
        title_is
        title_contains
        presence_of_element_located
        visibility_of_element_located
        visibility_of
        presence_of_all_elements_located
        text_to_be_present_in_element
        text_to_be_present_in_element_value
        frame_to_be_available_and_switch_to_it
        invisibility_of_element_located
        element_to_be_clickable
        staleness_of
        element_to_be_selected
        element_located_to_be_selected
        element_selection_state_to_be
        element_located_selection_state_to_be
        alert_is_present


