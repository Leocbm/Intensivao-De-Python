# Aula 01 - Automação de Sistemas e Processos com Python

Na primeira aula da Semana do Python você vai aprender a criar um código de automação de análise de dados e elaboração de
relatórios do absoluto zero. Para isso, vamos passar por conceitos como:
- `Jupyter Notebook`
- `Variáveis, métodos`
- `Importação de bibliotecas`
- `Uso de bibliotecas (pyautogui, time, pandas e pyperclip)`
- `Enviar e-mails automaticamente`

Após todos esses conhecimentos, seremos capazes de transformar uma tabela cheia de informações, nem um pouco fáceis de serem interpretadas, em uma ferramenta automatizada de geração e envio
automático de relatórios para um destinatário pré-definido.

##

Para início, nos deparamos com o seguinte desafio:

- `Desafio`: Todos os dias, o nosso sistema atualiza as vendas do dia anterior. O seu trabalho diário, como analista, é enviar um e-mail para a diretoria, assim que começar a trabalhar, com o faturamento e a quantidade de produtos vendidos no dia anterior

- E-mail da diretoria: seugmail+diretoria@gmail.com
- Local onde o sistema disponibiliza as vendas do dia anterior: https://drive.google.com/drive/folders/149xknr9JvrlEnhNWO49zPcw0PW5icxga?usp=sharing

##

Agora o próximo passo é pensar em como seria o processo necessário para chegar a solução, e chegamos a essa conclusão:

- `Passo 1`: Entrar no sistema (no nosso caso, entrar no link)
- `Passo 2`: Navegar até o local do relatório (entrar na pasta Exportar)
- `Passo 3`: Fazer o download do relatório
- `Passo 4`: Calcular os indicadores
- `Passo 5`: Entrar no email
- `Passo 6`: Enviar por e-mail o resultado

##

O `Passo 1` possui três etapas necessárias:
- [x] Abrir uma nova aba do navegador
- [x] Escrever o link no navegador
- [x] Apertar 'Enter'

Para resolver isso, vamos usar o pyautogui, uma biblioteca de automação de comandos do mouse e do teclado

Comandos pyautogui: https://pyautogui.readthedocs.io/en/latest/quickstart.html

- Caso você já não tenha o pyautogui instalado em seu computador, basta ir até uma célula e escrever o comando: 
```
!pip install pyautogui
```
- E em seguida basta importá-lo em seu projeto, mas como o pyautogui por si só não reproduz caracteres especiais, importaremos também o pyperclip que é instalado junto com o pyautogui para realizar as cópias de texto necessárias.
```
import pyautogui
import pyperclip
```
Agora podemos realizar os comandos necessários para concluir o `Passo 1`:
- Como o pyautogui realiza várias ações rapidamente, o navegador não consegue acompanhar os comandos, então o comando pyautogui.PAUSE = 1 faz com que seja realizado uma pausa de 1 segundo entre cada comando realizado. 
- Agora precisamos abrir uma nova aba do navegador, para isso usamos o atalho "ctrl", "t" dentro do comando pyautogui.hotkey().
- Realizamos a cópia do link fornecido utilizando o pyperclip.copy().
- Em seguida utilizamos novamente a função pyautogui.hotkey() mas dessa vez com o atalho "ctrl", "v" que é o atalho colar.
- Utilizamos o comando pyautogui.press() para pressionar a tecla "enter" e entrar no link.
```
pyautogui.PAUSE = 1
pyautogui.hotkey("ctrl", "t")
pyperclip.copy("https://drive.google.com/drive/folders/149xknr9JvrlEnhNWO49zPcw0PW5icxga?usp=sharing")
pyautogui.hotkey("ctrl", "v")
pyautogui.press("enter")
```
- E por fim importaremos a biblioteca time para utilizar a função time.sleep() e colocar o tempo desejado para que a página carregue por completo.
```
import time
```
```
time.sleep(5)
```
- Consideramos que o seu navegador ja esteja aberto para os comandos acima, mas caso queira abrir o programa do zero basta acrescentar ao inicio do código:
```
# pyautogui.press("win")
# pyautogui.write("chrome")
# pyautogui.press("enter")
```

##

Para `Passo 2` será necessário clicar nas pastas desejadas, então um macete para descobrir a localização do mouse são os seguintes comandos:
```
time.sleep(5)
pyautogui.position()
```
- Com esse comando você terá 5 segundos para ficar com o mouse no local desejado e a posição será mostrada no comando pyautogui.position()
- Lembrando que a posição varia para cada tipo de resolução de tela, e também abas menores ou em tela cheia, então o comando utilizado nesse exemplo pode não funcionar em seu computador e será necessário atualizar as posições de acordo com a sua situação.
Com a posição do local do click descoberta, vamos agora utilizar o comando pyautogui.click("posição descoberta", clicks=2) para clicar duas vezes na pasta e também o time.sleep(2) para o carregamento da página.
```
pyautogui.click(x=878, y=676, clicks=2)
time.sleep(2)
```

##

O `Passo 3` agora é realizar o download do arquivo, para isso precisaremos descobrir a posição do arquivo + a posição do 'Mais Ações'(conhecido com 3 pontos) + a opção de baixar(dentro dos 3 pontos) utilizando o pyautogui.click(x=, y=), e por fim mais um sleep para dar tempo do arquivo baixar.
```
pyautogui.click(x=1000, y=919)
pyautogui.click(x=3323, y=406)
pyautogui.click(x=2748, y=1529)
time.sleep(5)
```

##

Agora o `Passo 4` é calcular os indicadores, para isso precisaremos importar a biblioteca pandas que ja vem instalada com o Jupyter, e aproveitamos e usamos o 'as pd' para apelidar a biblioteca e facilitar o uso.
```
import pandas as pd
```
- E agora importaremos nossa tabela baixada do link, para isso armazenaremos ela dentro de uma variável com nome de sua escolha e utilizaremos o comando pd.read_excel(r" ") informando o local exato em que o arquivo está localizado em seu computador (Varia de caso para caso), e usaremos um display() com a variável criada para mostrar a tabela na tela.
```
tabela = pd.read_excel(r"C://Users/joaol/Downloads/Vendas - Dez.xlsx")
display(tabela)
```
- Com a tabela na tela, analisaremos seus dados e pegaremos os dados que precisamos, e para isso usaremos os comandos a seguir para somar as colunas desejadas.
```
faturamento = tabela["Valor Final"].sum()
quantidade = tabela["Quantidade"].sum()
```

##

Para o `Passo 5` vamos repetir alguns comandos já utilizados, mas dessa vez para abrir uma nova aba e ir até o gmail
```
pyautogui.hotkey("ctrl", "t")
pyperclip.copy("https://mail.google.com/mail/u/0/#inbox")
pyautogui.hotkey("ctrl", "v")
pyautogui.press("enter")
time.sleep(5)
```
## 

E enfim para o `Passo 6` iremos enviar por e-mail o resultado da nossa análise, e para isso precisamos:
- [x] Clicar no + para escrever nova mensagem.
- [x] Escrever o email do destinatário.
- [x] Precionar tab para selecionar o email.
- [x] Precionar tab novamente para mudar para o bloco descrição.
- [x] Copiar a mensagem desejada.
- [x] Utilizar o comando de atalho para colar a mensagem.
- [x] Pressionar tab novamente para mudar de bloco.
```
pyautogui.click(x=40, y=173)
pyautogui.write("seugmail+diretoria@gmail.com")
pyautogui.press("tab")
pyautogui.press("tab")
pyperclip.copy("Relatório De Vendas")
pyautogui.hotkey("ctrl", "v")
pyautogui.press("tab")
```
- [x] Criar uma variavel texto formatada com os dados calculados no `Passo 4`
```texto = f"""
Prezados, bom dia

O faturamento de ontem foi de: R${faturamento:,.2f}
A quantidade de produtos foi de: {quantidade:,}

Abs
Leo"""
```
- [x] Copiar e colar o texto na mensagem do gmail e enviar para a diretoria.
```
pyperclip.copy(texto)
pyautogui.hotkey("ctrl", "v")
pyautogui.hotkey("ctrl", "enter")
```
- PRONTO! AGORA É SÓ IMPRESSIONAR O CHEFE 😁
