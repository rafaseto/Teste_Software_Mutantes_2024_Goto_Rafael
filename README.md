### UNIVERSIDADE FEDERAL DE SERGIPE

### CENTRO DE CIÊNCIAS EXATAS E TECNOLOGIA

### DEPARTAMENTO DE COMPUTAÇÃO

### RAFAEL TAKEGUMA GOTO

### ATIVIDADE 2 – TESTES DE MUTAÇÃO

### SÃO CRISTÓVÃO - SERGIPE

### 2024


## 1. Roteiro do vídeo

A primeira etapa desta atividade consistiu em executar como exemplo, o roteiro de
testes de mutação apresentado no vídeo disponibilizado, que pode ser acessado por meio do
seguinte link: https://www.youtube.com/watch?v=FbMpoVOorFI. O primeiro passo foi
acessar o repositório cal_python, do qual é um projeto de calendário inspirado no cal do unix,
disponível por meio do seguinte link: https://github.com/stevaoaa/cal_python. Em seguida, a
fim de criar uma cópia deste repositório, realizou-se um fork. A figura 1 apresenta a criação
do fork do projeto cal_python, realizada por meio da opção “Fork”, seguida de “+ Create a
new fork”.

```
Figura 1 – Realização do fork para o repositório cal_python
```
```
Fonte: Autor
```
Após a realização do fork, foi utilizada a URL do fork para clonar o repositório como
uma cópia local do projeto. A figura 2 mostra a obtenção da URL, por meio da opção “<>
Code”.


```
Figura 2 – Obtenção da URL do projeto copiado
```
```
Fonte: Autor
```
De posse da URL, foi utilizado o comando “git clone <URL>” no terminal para fazer
a clonagem em si do projeto em uma cópia local. Para esta etapa da atividade utilizou-se o
AWS Cloud9 como IDE. A figura 3 mostra a clonagem do repositório no AWS Cloud9.

```
Figura 3 – Clonagem do projeto no AWS Cloud
```
```
Fonte: Autor
```
## 1.1 Preparação do ambiente

Para os fins desta atividade, foram utilizados os seguintes recursos:


- Python 3.10. 12 ;
- python3-venv: Módulo integrado do Python que permite criar ambientes virtuais;
- pytest: Framework de testes para Python;
- pytest-conv: Plugin para o pytest que fornece relatórios de cobertura de código;
- mutmut: Ferramenta de teste de mutação para Python.

Python foi a linguagem de programação utilizada nesta atividade. Foi utilizado o
comando “python --version” para checar a versão do Python no ambiente do AWS Cloud9.
A figura 4 mostra o resultado da checagem da versão do Python.

```
Figura 4 – Versão do Python configurada no ambiente do AWS Cloud
```
```
Fonte: Autor
```
Os demais recursos foram configurados seguindo as instruções definidas no arquivo
README.md do projeto, que podem ser visualizadas na figura 5. A única diferença
observada foi o caminho da linha 17, do qual foi apenas “venv”, visto que o diretório de
trabalho já tinha sido definido como “/cal_python” por meio do comando “cd cal_python”.


```
Figura 5 – Instruções de instalação e configuração
```
```
Fonte: Stevão Andrade
```
Com a utilização do comando “pip3 list” pode ser observado a lista de bibliotecas
instaladas no ambiente virtual. Pode-se notar, por meio da figura 6, que o pytest, pytest-conv
e mutmut estão devidamente instalados.


```
Figura 6 – Lista de bibliotecas instaladas no ambiente virtual
```
```
Fonte: Autor
```
## 1.2 Testes

Depois de configurado o ambiente, juntamente com todas as ferramentas necessárias,
iniciou-se a etapa de testes. O primeiro comando utilizado foi o “pytest -vv test_cal.py”, do
qual executa os casos de teste definidos no arquivo test_cal.py usando o pytest. A figura 7
apresenta os resultados dos testes: dos 21 testes encontrados, 20 passaram e 1 foi ignorado.


```
Figura 7 – Resultados da execução dos casos de teste de test_cal.py
```
```
Fonte: Autor
```
Para verificar a adição de novos casos de teste, foi criado um novo cenário de teste
para o método “test_is_leap”, o parâmetro (1700, True). A figura 8 mostra o método de teste
“test_is_leap” e sua lista de parâmetros após esta adição.

```
Figura 8 – Método de teste test_is_leap e sua lista de parâmetros
```
```
Fonte: Autor
```
A figura 9 expõe os resultados da execução dos testes após a adição do novo
parâmetro para o método “test_is_leap”. Pode-se observar que desta vez 22 casos de teste
foram encontrados, 21 passaram com sucesso, incluindo o “test_is_leap[1700, True]”, e 1 foi


ignorado.

```
Figura 9 – Resultados da execução dos casos de teste de test_cal.py após as mudanças
```
```
Fonte: Autor
```
O próximo comando de teste utilizado foi o “pytest -vv test_cal.py --cov=cal”, que
além de executar os casos de teste, gera um relatório de cobertura de código. É possível notar,
por meio da figura 10, que o código em “cal.py” possui uma porcentagem de cobertura de
código de 55%, isto é, 55% das linhas do arquivo “cal.py” foram cobertas pelos testes.

```
Figura 10 – Relatório de cobertura de código para o arquivo cal.py
```
```
Fonte: Autor
```
Em seguida executou-se o seguinte comando: “pytest -vv test_cal.py --cov=cal --cov-
branch --cov-report html”, do qual executa os casos de teste, gera o relatório de cobertura
mais detalhado e o exporta como um arquivo .html. O arquivo em formato HTML gerado é


o “index.html”, ele pode ser acessado por meio da pasta htmlcov. A figura 11 mostra a tela
principal do relatório. Segundo os dados do relatório, o script “cal.py” possui 109 comandos,
sendo que 49 deles não estão cobertos pelos testes e 1 está parcialmente coberto. Ademais
existem 48 ramificações (branches), e a cobertura é de 61%.

```
Figura 11 – Relatório de cobertura de código em formato HTML para cal.py
```
Fonte: Autor
Uma visualização mais detalhada da cobertura foi acessada por de um clique no nome
do arquivo “cal_py”. Dessa maneira, pode-se visualizar linha por linha, em verde o que está
coberto pelos testes e em vermelho o que não está coberto pelos testes. A figura 12 é um
trecho do relatório neste nível de detalhe.

```
Figura 12 – Relatório de todas as linhas do arquivo “cal.py”
```
```
Fonte: Autor
```

A fim de verificar se o conjunto de casos de teste é suficiente e adequado, foram
utilizados os testes de mutação. Por conseguinte, foi usado o comando “mutmut run –paths-
to-mutate=cal.py” para executar os testes de mutação. Para que o comando seja executado
sem erros, foi necessário mover o arquivo “test_cal.py” para uma nova subpasta chamada
“tests”, de modo que o mutmut pudesse reconhecer onde procurar os casos de teste. A figura
12 mostra os resultados da execução: 123 mutantes “mortos”, 2 “suspeitos” e 108
“sobreviveram”.

```
Figura 13 – Resultados da execução dos testes de mutação
```
Fonte: Autor
A figura 14 demonstra o resultado obtido com o comando “mutmut results”, do qual
permite verificar os mutantes que sobreviveram e o único mutante suspeito encontrado.


```
Figura 14 – Mutantes suspeitos e que sobreviveram
```
Fonte: Autor
Por meio do comando “mutmut show <mutante>”, pode-se visualizar os detalhes da
alteração do mutante passado como argumento. A figura 15 mostra os detalhes do mutante
12.

```
Figura 15 – Alteração feita no mutante 1 2
```
```
Fonte: Autor
```

A fim de obter detalhes das alterações feitas em cada mutante “suspeito” e
“sobrevivente”, executou-se o comando “mutmut html”, do qual gera um arquivo em formato
HTML com informações sobre estes mutantes. A figura 16 apresenta um trecho deste arquivo
gerado.

```
Figura 16 – Trecho do arquivo cal.py.html
```
```
Fonte: Autor
```
Para exemplificar vulnerabilidades encontradas nos casos de teste, observou-se
detalhes do mutante 27. O mutante 27 foi a alteração do operador “>” por “>=” na checagem
comparativa entre “month” e o número 2. Como todos os casos de teste passaram mesmo
com esse mutante inserido no código, significa que os testes não cobrem adequadamente essa
parte específica do código. A figura 17 mostra os detalhes do mutante 27 no arquivo
cal.py.html.


```
Figura 17 – Informações acerca do mutante 27
```
```
Fonte: Autor
```
De acordo com as informações obtidas com esse mutante, foi possível melhorar os casos de
teste relacionados ao método x. Foi criado um novo caso de teste que tem como parâmetros
um ano bissexto e o mês igual a 2, de modo que os casos de teste definidos passam a cobrir
o caso do mutante 27. A figura 18 mostra o novo caso de teste (2, 2020) implementado no
arquivo “test_cal.py”.
Figura 18 – Novo caso de teste (2, 2020) para “matar” o mutante 27

```
Fonte: Autor
```

Ao executar os testes de mutação novamente, pode-se observar, na figura 19, que após
a adição do caso de teste (2, 2020), 127 mutantes foram mortos, 3 a mais do que antes da
adição.

```
Figura 19 – Resultados da execução dos testes de mutação após a adição do caso de teste (2, 2020)
```
```
Fonte: Autor
```
Ao gerar novamente o relatório HTML, nota-se, por meio da figura 20, que o mutante
27 não se encontra mais entre os mutantes “sobreviventes”, pois o próximo mutante
“sobrevivente” depois do 12 é o 28.


```
Figura 20 – Trecho do arquivo cal.py.html após a adição do caso de teste (2, 2020)
```
```
Fonte: Autor
```
## 2. Projeto selecionado

Para a realização da questão 3 da atividade foi selecionado o projeto dirty-equals, do
qual é uma biblioteca implementada em python usada para facilitar a criação de comparações
de igualdade flexíveis e expressivas em testes. O projeto pode ser acessado por meio do
seguinte link: https://github.com/samuelcolvin/dirty-equals. A figura 21 mostra a estrutura
das pastas e arquivos no repositório do projeto. Pode-se observar que existe a pasta “tests”,
da qual possui os casos de teste.


```
Figura 21 – Repositório GitHub da biblioteca dirty-equals
```
```
Fonte: Autor
```
Primeiramente executou-se os casos de testes com o comando “pytest -vv tests”. Por
meio da figura 22, pode-se notar que 550 testes dos 550 coletados passaram com um tempo
de execução de 1.78s.


```
Figura 22 – Resultados da execução dos casos de teste definidos na pasta “tests”
```
```
Fonte: Autor
```
O próximo comando de teste utilizado foi o “pytest - vv tests --cov=dirty_equals”, que
além de executar os casos de teste em “tests”, gera um relatório de cobertura de código acerca
dos arquivos de “dirty_equals”. É possível notar, por meio da figura 23 , a porcentagem de
cobertura em cada um dos arquivos que estão na pasta “dirty_equals”. Apenas o arquivo
datetime.py não atingiu 100% de cobertura, no total o código fonte do projeto possui 99.47%
de cobertura.
Figura 23 – Relatório de cobertura de código para a pasta “dirty_equals”

```
Fonte: Autor
```

Em seguida executou-se o seguinte comando: “pytest -vv tests --cov=dirty_equals --
cov-branch --cov-report html”, do qual executa os casos de teste, gera o relatório de cobertura
mais detalhado e o exporta como um arquivo .html. O arquivo em formato HTML gerado é
o “index.html”, ele pode ser acessado por meio da pasta htmlcov. A figura 24 mostra a tela
principal do relatório. Segundo os dados do relatório, a pasta “dirty_equals” possui um total
de 828 comandos, sendo que apenas 6 deles não estão cobertos pelos testes e 31 comandos
foram excluídos da contagem de cobertura manualmente. Ademais existem 300 ramificações
(branches), e a cobertura total é de 99.47%.

```
Figura 24 – Relatório de cobertura de código em formato HTML para “dirty_equals”
```
```
Fonte: Autor
```
Uma visualização mais detalhada da cobertura pode ser acessada ao selecionar as
opções dos nomes dos arquivos. Dessa maneira, pode-se visualizar linha por linha, em verde
o que está coberto pelos testes e em vermelho o que não está coberto pelos testes. A figura


25 é um trecho do relatório neste nível de detalhe para o arquivo “_boolean.py”.

```
Figura 25 – Relatório de todas as linhas do arquivo “_boolean.py”
```
```
Fonte: Autor
```
A fim de verificar se o conjunto de casos de teste é suficiente e adequado, foram
utilizados os testes de mutação. Desse modo, usou-se o comando “mutmut run –paths-to-
mutate=dirty_equals” para executar os testes de mutação. A figura 26 apresenta os resultados
da execução: 530 mutantes “mortos” e 1 3 8 “sobreviventes”.


```
Figura 26 – Resultados da execução dos testes de mutação nos arquivos de “dirty_equals”
```
```
Fonte: Autor
```
A figura 27 expõe um trecho do resultado obtido com o comando “mutmut results”,
do qual permite verificar os mutantes que sobreviveram.


```
Figura 27 – Trecho do resultado dos mutantes “sobreviventes”
```
```
Fonte: Autor
```
Com o comando “mutmut show <mutante>”, pode-se visualizar os detalhes da
alteração do mutante passado como argumento. A figura 28 mostra os detalhes do mutante
521.
Figura 28 – Alteração feita no mutante 521

```
Fonte: Autor
```

A fim de obter detalhes das alterações feitas em cada mutante “sobrevivente”,
executou-se o comando “mutmut html”, do qual gera um arquivo em formato HTML para
cada arquivo da pasta “dirty_equals”, com informações sobre estes mutantes. A figura 29
apresenta o arquivo index.html que possui um atalho para cada um dos arquivos HTML
associados aos arquivos da pasta “dirty_equals”.

```
Figura 29 – Relatório dos testes de mutação (index.html)
```
```
Fonte: Autor
```
Uma visão detalhada para cada arquivo pode ser acessada por meio do clique nos
atalhos em azul. A figura 30 mostra um trecho dos detalhes dos resultados relatados no
arquivo “_numeric.py”, armazenados no arquivo “_numeric.py.html”.


```
Figura 30 – Trecho do arquivo “_numeric.py.html”
```
```
Fonte: Autor
```
## 3. Melhorando os casos de teste

O objetivo desta última etapa da atividade é identificar limitações e oportunidades de
melhoria nos casos de teste. De acordo com o exposto na figura 29, o arquivo “_numeric.py”
é onde reside o maior número de sobreviventes, logo o foco voltou-se a este arquivo na
questão das melhorias. A principal oportunidade de melhora identificada nos métodos de
teste “test_dirty_equals” e “test_dirty_not_equals”, das quais compara um valor “other” com
uma instância “dirty”. A priori, as classes de asserção como “IsInt” e “IsFloat” estavam
testando majoritariamente o dígito 1, como pode-se observar na figura 31.


```
Figura 31 – Trecho do arquivo “test_numeric.py”
```
```
Fonte: Autor
```
Visto isso, investiu-se em enriquecer esses casos de teste com os demais dígitos. Além
dos dígitos adicionou-se casos de teste que lidam com o valor “None”, do qual está presente
em diversos mutantes inseridos. De acordo o arquivo “_numeric.py.html”, 17 mutantes
englobavam mudanças relacionadas ao valor “None”, dos 30 sobreviventes associados a
“_numeric.py”. A figura 32 mostra um trecho de “_numeric.py.html” que engloba o valor
“None”.


Figura 32 – Mutantes associados ao valor “None”

```
Fonte: Autor
```
A figura 33 mostra um trecho de “_test_numeric.py” modificado com as mudanças
propostas. As mudanças da figura 33 se referem ao método “test_dirty_not_equals”, do qual
testa que o valor passado como parâmetro não é igual a um Int, Float, etc.


```
Figura 33 – Trecho modificado em “_test_numeric.py”
```
```
Fonte: Autor
```
Conforme pode ser visto na figura 34 , após as mudanças propostas, os resultados da
execução dos testes de mutação apontam que 546 mutantes foram “mortos”, 16 a mais
quando comparado com a primeira execução. Como foram feitas mudanças apenas no
arquivo “_test_numeric.py”, 16 dos 30 mutantes sobreviventes associados a esse módulo
foram “mortos”.


```
Figura 34 – Resultados da execução 2 dos testes de mutação nos arquivos de “dirty_equals”
```
```
Fonte: Autor
```
Link para o repositório no GitHub:
https://github.com/rafaseto/Teste_Software_Mutantes_2024_Goto_Rafael

Link para o vídeo tutorial:
https://drive.google.com/file/d/1c2VrOFnHKoVNJPQoporD07G2AZu8S-
CU/view?usp=sharing


