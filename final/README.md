# Projeto COVID-19: Integração de Dados Internacionais para Análise da Pandemia

# Equipe Coviders - CVDRS
* `Fernando dos Reis Santos Filho` - `234471`
* `Renan Hiroki Bastos` - `176573`
* `Vinicius Alves Mancine Dantas` - `188092`

## Resumo do Projeto
O final do ano de 2019 foi marcado pelo surgimento do vírus Sars-CoV-2, responsável pela doença Covid-19 e por uma intensa pandemia com consequências socioeconômicas e sanitárias gravíssimas, graças à sua alta taxa de transmissão. Hoje, quase dois anos depois, grandes bases de dados foram e ainda são construídas ao redor do mundo catalogando os milhões de casos e mortes confirmados por Covid-19 todos os dias.

Durante todo o período de pandemia, recomendações sobre lavar as mãos, evitar aglomeração e utilizar máscara foram fortemente disseminadas. Porém, ao redor do mundo tivemos inúmeros casos de resistência ao uso de máscara, atitude que contribuiu com a alta taxa de transmissão do vírus. Com isso, algumas dúvidas surgiram a respeito de quanto o uso da máscara influencia na disseminação do vírus e se lugares onde o uso de máscara não foi frequente apresentam maiores números de contaminados e mortos por Covid-19.

Logo, nosso objetivo com esse trabalho é extrair, tratar e compilar dados  de fontes distintas relacionados à Covid-19 e a sua prevenção através do uso de máscaras em um único dataset público. Assim, será possível fazer análises sobre a pandemia, a adoção e a eficácia deste método de prevenção em um contexto global através de um único dataset.
## Slides da Apresentação
[slides apresentação](slides/MC536-TrabalhoFinal.pdf)
## Modelo Conceitual Preliminar

> ![Modelo conceitual](assets/modelo-conceitual.png)
## Modelos Lógicos

~~~
CASO(_id_, locations, date, new_cases, total_cases, new_deaths, total_deaths, mask_use_percentage, new_cases_per_million_habitants, new_deaths_per_million_habitants, total_cases_per_million_habitants, total_deaths_per_million_habitants, , population)
POPULACAO(location,  population)
  location chave estrangeira -> CASO(id)
~~~

> ![Modelo Lógico Hierárquico](assets/modelo-logico-hierarquico.png)

## Dataset Publicado

título do arquivo/base | link | breve descrição
----- | ----- | -----
dados_nyt_tratados.csv  | [interim](data/interim/dados_nyt_tratados.csv) | Dados sobre uso de máscara, quantidades de casos e quantidade de mortes por Covid-19 nos Estados Unidos, dividido por estados e cidades.
dados_owid_tratados.csv | [interim](data/interim/dados_owid_tratados.csv) | Dados sobre quantidade de casos e quantidade de mortes por Covid-19 em 196 países, além de informações sobre vacinação, testes e hospitais em cerca de 200 países.
dados_plosone_tratados.csv | [interim](data/interim/dados_plosone_tratados.csv) | Dados sobre o uso de máscaras, quantidade de casos e quantidade de mortes de Covid-19 em 22 estados dos Estados Unidos.
eua_final.csv | [interim](data/interim/eua_final.csv) | Dados sobre o uso de máscaras, quantidade de casos e quantidade de mortes de Covid-19 em 22 estados dos Estados Unidos.
europa_final.csv | [interim](data/interim/europa_final.csv) | Dados sobre o uso de máscaras, quantidade de casos e quantidade de mortes de Covid-19 em 22 estados da Europa.
yougov-tratada.csv | [external](data/external/yougov-tratada.csv) | Dados sobre a porcentagem de uso de máscaras em lugares públicos em 23 países em diferentes regiões do mundo.
nyt.csv | [raw](data/raw/nyt.csv) | Dados sobre uso de máscara, quantidades de casos e quantidade de mortes por Covid-19 nos Estados Unidos, dividido por estados e cidades.
owid-covid-data.csv | [raw](data/raw/owid-covid-data.csv) | Dados sobre quantidade de casos e quantidade de mortes por Covid-19 em 196 países, além de informações sobre vacinação, testes e hospitais em cerca de 200 países.
plosone.csv | [raw](data/raw/plosone.csv) | Dados sobre o uso de máscaras, quantidade de casos e quantidade de mortes de Covid-19 em 22 estados dos Estados Unidos.
yougov-chart.csv | [raw](data/raw/yougov-chart.csv) | Dados sobre a porcentagem de uso de máscaras em lugares públicos em 23 países em diferentes regiões do mundo.
casos.csv | [processed](data/processed/casos.csv) | Dataset finalizado.
populacoes.csv | [processed](data/raw/casos.csv) | Dados sobre a quantidade populacional para cada localização.

## Bases de Dados

título da base | link | breve descrição
----- | ----- | -----
Coronavirus (Covid-19) Data in the United States | https://github.com/nytimes/covid-19-data | Dados sobre uso de máscara, quantidades de casos e quantidade de mortes por Covid-19 nos Estados Unidos, dividido por estados e cidades.
Data on COVID-19 (coronavirus) by Our World in Data | https://github.com/owid/covid-19-data/tree/master/public/data | Dados sobre quantidade de casos e quantidade de mortes por Covid-19 em 196 países, além de informações sobre vacinação, testes e hospitais em cerca de 200 países.
Personal measures taken to avoid COVID-19 | https://today.yougov.com/topics/international/articles-reports/2020/03/17/personal-measures-taken-avoid-covid-19 | Dados sobre a porcentagem de uso de máscaras em lugares públicos em 23 países em diferentes regiões do mundo.
Mask adherence and rate of COVID-19 across the United States | https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0249891#sec011 | Dados sobre o uso de máscaras, quantidade de casos e quantidade de mortes de Covid-19 em 22 estados dos Estados Unidos.

## Detalhamento do Projeto
> Apresente aqui detalhes do processo de construção do dataset e análise. Nesta seção ou na seção de Perguntas podem aparecer destaques de código como indicado a seguir. Note que foi usada uma técnica de highlight de código, que envolve colocar o nome da linguagem na abertura de um trecho com `~~~`, tal como `~~~python`.
> Os destaques de código devem ser trechos pequenos de poucas linhas, que estejam diretamente ligados a alguma explicação. Não utilize trechos extensos de código. Se algum código funcionar online (tal como um Jupyter Notebook), aqui pode haver links. No caso do Jupyter, preferencialmente para o Binder abrindo diretamente o notebook em questão.
~~~python
df = pd.read_excel("/content/drive/My Drive/Colab Notebooks/dataset.xlsx");
sns.set(color_codes=True);
sns.distplot(df.Hemoglobin);
plt.show();
~~~

> Se usar Orange para alguma análise, você pode apresentar uma captura do workflow, como o exemplo a seguir e descrevê-lo:
![Workflow no Orange](images/orange-zombie-meals-prediction.png)
> Coloque um link para o arquivo do notebook, programas ou workflows que executam as operações que você apresentar.
> Aqui devem ser apresentadas as operações de construção do dataset:
* extração de dados de fontes não estruturadas como, por exemplo, páginas Web
* agregação de dados fragmentados obtidos a partir de API
* integração de dados de múltiplas fontes
* tratamento de dados
* transformação de dados para facilitar análise e pesquisa
> Se for notebook, ele estará dentro da pasta `notebook`. Se por alguma razão o código não for executável no Jupyter, coloque na pasta `src` (por exemplo, arquivos do Orange ou Cytoscape). Se as operações envolverem queries executadas atraves de uma interface de um SGBD não executável no Jupyter, como o Cypher, apresente na forma de markdown.
## Evolução do Projeto
> Relatório de evolução, descrevendo as evoluções na modelagem do projeto, dificuldades enfrentadas, mudanças de rumo, melhorias e lições aprendidas. Referências aos diagramas, modelos e recortes de mudanças são bem-vindos.
> Podem ser apresentados destaques na evolução dos modelos conceitual e lógico. O modelo inicial e intermediários (quando relevantes) e explicação de refinamentos, mudanças ou evolução do projeto que fundamentaram as decisões.
> Relatar o processo para se alcançar os resultados é tão importante quanto os resultados.
## Perguntas de Pesquisa/Análise Combinadas e Respectivas Análises

> Apresente os resultados da forma mais rica possível, com gráficos e tabelas. Mesmo que o seu código rode online em um notebook, copie para esta parte a figura estática. A referência a código e links para execução online pode ser feita aqui ou na seção de detalhamento do projeto (o que for mais pertinente).
> Liste aqui as perguntas de pesquisa/análise e respectivas análises. Nem todas as perguntas precisam de queries que as implementam. É possível haver perguntas em que a solução é apenas descrita para demonstrar o potencial da base. Abaixo são ilustradas três perguntas, mas pode ser um número maior a critério da equipe.
>
### Perguntas/Análise com Resposta Implementada

### Pergunta/Análise 1
 * Os locais com maior número de casos são também os lugares com menor índice de uso de máscaras?
 ~~~
SELECT sum(new_cases),
       avg(new_cases)
FROM casos,
WHERE mask_use_percentage < 25;

SELECT sum(new_cases),
       avg(new_cases)
FROM casos,
WHERE mask_use_percentage >= 25 AND mask_use_percentage < 50;

SELECT sum(new_cases),
       avg(new_cases)
FROM casos,
WHERE mask_use_percentage >= 50 AND mask_use_percentage < 75; 

SELECT sum(new_cases),
       avg(new_cases)
FROM casos,
WHERE mask_use_percentage >= 75;
 ~~~


### Pergunta/Análise 2
 * Quais são os locais com maior número de casos por índice de uso de máscaras?
  ~~~
SELECT location,
	   date,
	   mask_use_percentage,
	   new_cases,
	   new_cases/mask_use_percentage as case_mask_rate
FROM casos
WHERE mask_use_percentage > 0 AND new_cases > 0
ORDER BY case_mask_rate DESC
LIMIT 20;
 ~~~
 

### Pergunta/Análise 3
 * Há algum indício de que a frequência de uso de máscara influência na taxa de mortalidade?
  ~~~
SELECT  location,
        date,
        mask_use_percentage,
        new_deaths/new_cases as monthly_death_rate,
        total_deaths/total_cases as overall_death_rate
FROM casos
ORDER BY mask_use_percentage, monthly_death_rate;
 ~~~
 
### Pergunta/Análise 4
 * Locais na mesma faixa de porcentagem de uso de máscara possuem taxas de infecções parecidas?
  ~~~
SELECT location,
       new_cases
FROM casos,
WHERE mask_use_percentage < 10;

SELECT location,
       new_cases
FROM casos,
WHERE mask_use_percentage >= 10 AND mask_user_percentage < 20;

SELECT location,
       new_cases
FROM casos,
WHERE mask_use_percentage >= 20 AND mask_user_percentage < 30;

SELECT location,
       new_cases
FROM casos,
WHERE mask_use_percentage >= 30 AND mask_user_percentage < 40;

SELECT location,
       new_cases
FROM casos,
WHERE mask_use_percentage >= 40 AND mask_user_percentage < 50;

SELECT location,
       new_cases
FROM casos,
WHERE mask_use_percentage >= 50 AND mask_user_percentage < 60;

SELECT location,
       new_cases
FROM casos,
WHERE mask_use_percentage >= 60 AND mask_user_percentage < 70;
SELECT location,
       new_cases
FROM casos,
WHERE mask_use_percentage >= 70 AND mask_user_percentage < 80;

SELECT location,
       new_cases
FROM casos,
WHERE mask_use_percentage >= 80 AND mask_user_percentage < 90;

SELECT location,
       new_cases
FROM casos,
WHERE mask_use_percentage >= 90;
 ~~~

### Pergunta/Análise 5
 * A proporção mortes/casos é influênciada pela frequência no uso de máscara?
  ~~~
SELECT avg(new_deaths*100/new_cases) as avarage_death_rate
FROM casos
WHERE mask_use_percentage < 25;

SELECT avg(new_deaths*100/new_cases) as avarage_death_rate
FROM casos
WHERE mask_use_percentage >= 25 AND mask_use_percentage < 50;

SELECT avg(new_deaths*100/new_cases) as avarage_death_rate
FROM casos
WHERE mask_use_percentage >= 50 AND mask_use_percentage < 75; 

SELECT avg(new_deaths*100/new_cases) as avarage_death_rate
FROM casos
WHERE mask_use_percentage >= 75;
 ~~~
