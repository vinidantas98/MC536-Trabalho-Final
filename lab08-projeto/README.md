# Modelo para Apresentação do Lab08 - Modelo Lógico e Análise de Dados em Grafos

# Equipe `Coviders` - `CVDRS`
* `Fernando dos Reis Santos Filho` - `234471`
* `Renan Hiroki Bastos` - `176573`
* `Vinicius Alves Mancine Dantas` - `188092`

## Modelo Lógico Combinado do Banco de Dados de Grafos
> ![Modelo Lógico de Grafos](images/modelo-logico-grafos.jpeg)

## Perguntas de Pesquisa/Análise Combinadas e Respectivas Análises
### Pergunta/Análise 1
> *  Locais com frequência de uso de máscara próximas possuem taxas de infecções parecidas?
>   
>   * Dada a estrutura criada para o modelo, comunidades de locais com taxas de uso de máscara próximas devem surgir, possibilitando a verificação da proximidade das taxas de infecção dentro destas comunidades.

### Pergunta/Análise 2
> * Os locais com maior número de casos são também os lugares com menor índice de uso de máscaras?
>   
>   * Para podermos identificar se os locais com maior número de casos são também os lugares com menor índice de uso de máscaras podemos utilizar uma análise das comunidade que serão formadas. Identificando as comunidades que apresentam as menores taxas de uso de máscara e comparando-as com uma listagem de locais que apresentam os maiores números de casos podemos responder a pergunta.

### Pergunta/Análise 3
> * A proporção mortes/casos é influênciada pela frequência no uso de máscara?
>   
>   * Para verificar a influência do uso de máscaras na relação M/C (número de mortes / número de casos confirmados) será necessário calcular essa proporção para cada comunidade de locais. Para isso será necessário encontrar uma comunidade com taxa de uso de máscara semelhante, percorrer os seus nós locais e calcular a proporção M/C para cada nó e, por fim, calcular a média dessas proporções a fim de encontrar a relação M/C que representa aquela comunidade. Assim, tendo a relação M/C média para cada comunidade é possível realizar a comparação dessas relações com a taxa de uso de máscara.