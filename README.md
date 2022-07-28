<h1>Intensivão de Python</h1> 

> Status do Projeto: :warning: Em desenvolvimento

### Tópicos 

:small_blue_diamond: [Descrição do projeto](#descrição-do-projeto)

:small_blue_diamond: [Funcionalidades](#funcionalidades)

:small_blue_diamond: [Objetivos](#objetivos)

:small_blue_diamond: [Pré-requisitos](#pré-requisitos)

:small_blue_diamond: [Como rodar a aplicação](#como-rodar-a-aplicação-arrow_forward)

:small_blue_diamond: [Desafio 01](#desafio-01)

## Descrição do projeto 

<p align="justify">
  Meu primeiro projeto de automação de sistemas e automação web utilizando o Jupyter Notebook. 
</p>

## Funcionalidades

:heavy_check_mark: Aula 01 - Automação de Sistemas e Processos com Python 

:heavy_check_mark: Funcionalidade 2  

:heavy_check_mark: Funcionalidade 3  

:heavy_check_mark: Funcionalidade 4  


## Objetivos

- `Aula 01`

Na primeira aula do Intensivão do Python você vai aprender a criar um código de automação de análise de dados e elaboração de
relatórios do absoluto zero. Para isso, vamos passar por conceitos como:
- `Jupyter Notebook`
- `Variáveis, métodos`
- `Importação de bibliotecas`
- `Uso de bibliotecas (pyautogui, time, pandas e pyperclip)`
- `Enviar e-mails automaticamente`

Após todos esses conhecimentos, seremos capazes de transformar uma tabela cheia de informações, nem um pouco fáceis de serem interpretadas, em uma ferramenta automatizada de geração e envio
automático de relatórios para um destinatário pré-definido.
##
- `Aula 02`

Na segunda aula do Intensivão do Python você vai aprender a criar um código de análise de dados. No dia a dia das empresas,
é muito comum dúvidas sobre os resultados da empresa. Um conceito que cada dia mais cresce nas empresas é o data driven.
Basicamente, é dizer que ações são tomadas com base nos dados e não em achismos.
Aprenda como fazer uma super análise do zero com os conceitos abaixo:
- `Importando dados de bases .csv`
- `Tratar dados usando a biblioteca Pandas`
- `Importação de bibliotecas`
- `Criação de gráficos usando o plotly`

Após todos esses conhecimentos, seremos capazes de transformar uma tabela cheia de informações, nem um pouco fáceis de serem 
interpretadas em uma análise super aprofundada que servirão de base para tomada de decisão da gerência. Tudo graças a você! 

## Pré-requisitos

- :warning: [Anaconda](https://www.anaconda.com/)
- :warning: [Jupyter Notebook](https://jupyter.org/)
- :warning: [Time](https://www.pythoncentral.io/pythons-time-sleep-pause-wait-sleep-stop-your-code/#:~:text=The%20time.sleep%20%28%29command%20is%20the%20equivalent%20to%20the,of%20seconds%20the%20Python%20program%20should%20pause%20execution.)
- :warning: [Pandas](https://www.w3schools.com/python/pandas/default.asp)
- :warning: [Pyperclip](https://pypi.org/project/pyperclip/)

## Como rodar a aplicação :arrow_forward:

No terminal, clone o projeto: 

```
git clone https://github.com/Leocbm/Intensivao-De-Python.git
```
- Vá até o seu terminal, caso não saiba basta pesquisar por 'Prompt De Comando' na barra de pesquisa:
- Navegue até a pasta desejada com o comando 'cd', exemplo se sua pasta estiver no Desktop:
``` 
cd Desktop/Pasta
```
- Na pasta, basta escrever o comando acima.
- Lembre-se de ter o <a href="https://git-scm.com/">git</a> instalado.

## Desafio 01

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

## Desafio 02

Para início, nos deparamos com o seguinte desafio:

- `Desafio`: Você trabalha em uma empresa de telecom e tem clientes de vários serviços diferentes, entre os principais: internet e telefone.
O problema é que, analisando o histórico dos clientes dos últimos anos, você percebeu que a empresa está com Churn de mais de 26% dos clientes.
Isso representa uma perda de milhões para a empresa.
O que a empresa precisa fazer para resolver isso?
- Base de Dados: https://drive.google.com/drive/folders/1T7D0BlWkNuy_MDpUHuBG44kT80EmRYIs?usp=sharing
- Link Original do Kaggle: https://www.kaggle.com/radmirzosimov/telecom-users-dataset

##

Agora o próximo passo é pensar em como seria o processo necessário para chegar a solução, e chegamos a essa conclusão:

- `Passo 1`: Importar a base de dados
- `Passo 2`: Visualizar a base de dados
- `Passo 3`: Tratamento de dados (resolver os problemas da base de dados)
- `Passo 4`: Análise inicial dos dados (entender os cancelamentos)
- `Passo 5`: Descobrir o motivo dos cancelamentos
- `Passo 6`: Conclusões e Ações

##

O `Passo 1` possui apenas uma etapa necessária:
- [x] Importar a base de dados

Para resolver isso, vamos usar o pandas, uma biblioteca para leitura e manipulação de dados.

Comandos pandas: https://pandas.pydata.org/docs/
- A biblioteca pandas já vem instalada junto ao Jupyter.

Agora podemos realizar os comandos necessários para concluir o `Passo 1`:
- Primeiramente importamos a biblioteca do pandas com o comando 'import pandas as pd'.
- Após importar a biblioteca basta armazenar a sua base de dados dentro de uma variável.
- Nessa etapa utilizamos o atalho para o arquivo sem o caminho completo "telecom_users.csv" pois o arquivo estava localizado na mesma pasta em que o projeto está.
```
import pandas as pd

tabela = pd.read_csv("telecom_users.csv")
```
##

Para `Passo 2` teremos 4 etapas:
- [x] Visualizar a base de dados.
- [x] Entender as informações que você tem disponivel.
- [x] Descobrir o problema da base de dados.
- [x] Excluir colunas inúteis (informações que não te ajudam, te atrapalham).

Para isso devemos dar um display na tabela e verificar as informações.
```
display(tabela)
```
Agora que analisamos a tabela, percebemos que a coluna 'Unnamed' não nos servirá para nada, então teremos q excluir ela.
- Para excluir uma informação de uma tabela, devemos utilizar o comando tabela.drop() e informar um "nome" e um eixo.
- Para isso devemos saber que o "nome" pode ser o nome ou a linha da tabela, e o eixo utilizamos axis=o -> para o eixo da linha e axis=1 -> para o eixo da coluna.
- ex: se fosse uma linha especifica ex: 3 / tabela = tabela.drop(3, axis=0)
```
tabela["TotalGasto"] = pd.to_numeric(tabela["TotalGasto"], errors="coerce")
```
##

Para o `Passo 3` precisaremos tratar os dados e isso possui 2 etapas:
- [x] Resumir sua base de dados
- [x] Verificar se as informações são tipo correto.
- [x] Eliminar informações vazias, podem ser colunas ou linhas.
Para resumir a base de dados utilizamos o comando print(tabela.info())
```
print(tabela.info())
```
Notamos que a coluta 'Total Gasto' está sendo reconhecida como object(texto) mas ela é do tipo float(com casas decimais), e para isso precisaremos corrigi-la
com o comando pd.to_numeric() para transformá-la em números e o metodo errors="coerce" para forçar o erro a virar número.
```
tabela["TotalGasto"] = pd.to_numeric(tabela["TotalGasto"], errors="coerce")
```
Após corrigir nosso erro deveremos eliminar qualquer informação vazia que não te prejudique em sua base de dados.
- O comando dropna() exclui informações vazias, para isso deveremos informar o how="" e o axis.
- O axis já vimos acima, o how="" pode ser "all" para excluir a linha/coluna se todas as informações dela estiverem vazias ou "any" para excluir a linha/coluna
se qualquer informação dela estiver vazia.
- Excluindo tabelas completamentes vazias.
```
tabela = tabela.dropna(how="all", axis=1)
```
- Excluindo linhas com alguma coisa vazia.
```
tabela = tabela.dropna(how="any", axis=0)
```

##

Agora no `Passo 4` teremos a análise inicial dos dados e nisso deveremos conferir os cancelamentos
- [x] como estão os cancelamentos? 26%

Analizaremos a coluna 'Churn' que são os cancelamentos das pessoas e utilizaremos o comando .value_counts() para contar com precisão a ocorrencia de cancelamento.
- Também existem outras funções como .sum(soma) / .average(media) / mean(mediana) / value_counts(quantidade) mas utilizaremos apenas o counts.
```
print(tabela["Churn"].value_counts())
```
- E também podemos usar o método (normalize=True) para verificar a porcentagem (se for da sua preferência é possível utilizar o comando .map("{:.1%}".format) para 
formatar a porcentagem.
```
print(tabela["Churn"].value_counts(normalize=True).map("{:.1%}".format))
```
- E com isso confirmamos os 26% de cancelamento.

##

No `Passo 5` precisaremos descobrir o motivo dos cancelamentos e para isso transformaremos cada uma das colunas em gráficos e analisaremos os dados.
- Para isso precisaremos instalar plotly, que é um biblioteca de gráficos.
- Caso você já não tenha o plotly instalado em seu computador, basta ir até uma célula e escrever o comando: 
```
!pip install plotly
```
- E em seguida basta importá-lo em seu projeto, para isso vamos utilizar o comando:
```
import plotly.express as px
```
Para transformar todas as colunas de uma vez em gráfico, precisaremos utilizar o método 'for' e passar o seu parâmetro dentro do x= a seguir.
- Iremos utilizar o comando px.histogram() para criar um gráfico do tipo histograma, e passar nele (nossa tabela, x="a coluna(a nossa está no 'for')", e a color="que é a coluna em relação a outra")
- Existem outros tipos de gráfico como grafico de barra .bar / linha .line / histograma .histogram, mas só usaremos o histograma.
- Exemplo de gráficos: https://plotly.com/python/histograms/
- E iremos exibir o gráfico
```
for coluna in tabela.columns:
    grafico = px.histogram(tabela, x=coluna, color="Churn")
    grafico.show()
```

##

E por fim no `Passo 6` basta análisar os dados e anotar suas Conclusões.
- `Conclusões`:

Clientes que estão há pouco tempo estão cancelando muito
- Pode estar fazendo alguma promoção que dá o primeiro mês de graça
- O inicio do serviço pro cliente está sendo muito confuso
- A primeira experiencia pro cliente ta ruim
- Podemos criar incentivos nos primeiros mêses - primeiro ano mais barato

Boleto Eletronico tem muito mais cancelamento que as outras formas de pagamento
- Oferecer desconto nas outras formas de pagamento

Pessoas com contrato mensal tem muito mais chance de cancelar
- Desconto para pagar a anuídade

Mais serviços o cliente tem (suporte) menos ele cancela
- Pode oferecer serviços extras quase de graça

Clientes com familia maior tem menos chance de cancelar
- 2° linha de graça ou desconto

##

- PRONTO! AGORA É SÓ IMPRESSIONAR O CHEFE 😁

## Desenvolvedores/Contribuintes :octocat:

| [<img src="https://avatars.githubusercontent.com/u/54343955?v=4" width=115><br><sub>Leonardo Cunha</sub>](https://github.com/Leocbm) |  [<img src="https://avatars.githubusercontent.com/u/54343955?v=4" width=115><br><sub>Leonardo Cunha</sub>](https://github.com/Leocbm) |  [<img src="https://avatars.githubusercontent.com/u/54343955?v=4" width=115><br><sub>Leonardo Cunha</sub>](https://github.com/Leocbm) |
| :---: | :---: | :---: 
