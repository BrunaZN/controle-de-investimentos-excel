# controle-de-investimentos-excel
Projeto de controle de investimentos desenvolvido no excel 
Projeto desenvolvido no Excel para o desafio da DIO, seguindo as aulas de Felipe Aguiar (Felipão).

## Objetivo e funcionamento

A ferramenta permite informar aporte mensal, prazo e taxa de rendimento para calcular o patrimônio acumulado e os dividendos mensais estimados.

Na aba Investimento, as cinco perguntas estão nestas células:

- Quanto investir por mês: D16.
- Por quantos anos: D17.
- Qual a taxa de rendimento mensal: D18.
- Quanto de patrimônio vai acumular: D19.
- Quanto receber de dividendos por mês: D20.

Também apresenta projeções para 2, 5, 10, 20 e 30 anos, em C23:D27, e distribui o aporte entre seis tipos de FII conforme o perfil escolhido em C32.

## Fórmulas utilizadas

A função VF calcula o patrimônio futuro:

=VF(taxa_mensal;qtd_anos*12;aporte*-1)

O prazo é convertido em meses. O aporte negativo representa a saída de dinheiro, permitindo apresentar o patrimônio como valor positivo. São considerados aportes ao final de cada mês e patrimônio inicial zero.

Os dividendos são calculados multiplicando o patrimônio pela taxa mensal de dividendos:

=patrimonio*rendimento_carteira

O PROCV busca o percentual de cada tipo de fundo na aba Perfis, usando uma chave que combina perfil e tipo de FII:

=PROCV($C$32&"-"&B36;Perfis!$A$3:$D$20;4;FALSO)

O argumento FALSO exige correspondência exata. Cada percentual é multiplicado pelo aporte mensal para calcular o valor destinado ao tipo de fundo.

## Intervalos nomeados

Todos estão na aba Investimento:

| Nome | Célula |
|---|---|
| salario | D11 |
| rendimento_carteira | D12 |
| sugestao_investimento | D13 |
| aporte | D16 |
| qtd_anos | D17 |
| taxa_mensal | D18 |
| patrimonio | D19 |
| dividendos | D20 |

## Distribuição por perfil

| Tipo de FII | Conservador | Moderado | Agressivo |
|---|---:|---:|---:|
| Papel | 25% | 20% | 15% |
| Tijolo | 35% | 40% | 45% |
| Híbridos | 15% | 12% | 12% |
| FOFs | 12% | 15% | 8% |
| Desenvolvimento | 8% | 10% | 11% |
| Hotelarias | 5% | 3% | 9% |
| Total | 100% | 100% | 100% |

Os percentuais são exemplos educacionais, não recomendações de investimento.

Origem dos percentuais: Os percentuais foram definidos por mim seguindo a orientação do desafio da DIO, que permite personalizar a distribuição entre os tipos de FII, desde que cada perfil some 100%. São valores ilustrativos para fins de aprendizagem, não recomendações de investimento.

## Melhorias realizadas na revisão do projeto

- Padronização da lista de perfis.
- Uso explícito da busca exata no PROCV.
- Células calculadas em cinza e campos de entrada em branco.
- Inclusão do total de 100% na distribuição.
- Explicação das taxas de acumulação e de dividendos.
- Inclusão de orientações de preenchimento.

Essas melhorias foram realizadas sobre a versão inicial deste projeto.

## Exemplo de resultado

Com aporte mensal de R$ 750,00, prazo de 3 anos e taxa de acumulação de 1,78% ao mês:

- Patrimônio acumulado: R$ 37.387,54.
- Dividendos mensais estimados, à taxa de 0,70%: R$ 261,71.

A troca de perfil altera a distribuição do aporte, mantendo o total de R$ 750,00. Ela não altera as taxas informadas nem o patrimônio projetado.

A simulação utiliza taxas constantes e não calcula separadamente inflação, impostos ou custos.
