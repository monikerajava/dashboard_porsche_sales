# Porsche Sales Intelligence Dashboard

Dashboard interativa de Business Intelligence desenvolvida para analisar o desempenho comercial de veículos Porsche, com foco em faturamento, comportamento regional das vendas, participação de modelos eletrificados e evolução temporal.

O projeto utiliza HTML, CSS e JavaScript, com uma interface inspirada na linguagem visual premium da Porsche: fundo escuro, detalhes em vermelho, tipografia elegante e imagem automotiva de destaque.

## Dashboard publicada

**Acesse a dashboard online:**

[https://monikerajava.github.io/dashboard_porsche_sales/porsche_sales_intelligence_v2.html](https://monikerajava.github.io/dashboard_porsche_sales/porsche_sales_intelligence_v2.html)

## 1. Perguntas de negócio escolhidas

As perguntas foram selecionadas para transformar os dados de vendas em informações úteis para decisões comerciais e estratégicas.

### 1.1. Qual família de modelos gera mais receita por estado?

A análise considera as famílias:

- Porsche 911
- Porsche 718
- Porsche Cayenne
- Porsche Macan
- Porsche Panamera
- Porsche Taycan

**Objetivo de negócio:** identificar as famílias com maior contribuição para o faturamento em cada estado, permitindo compreender diferenças regionais de demanda e apoiar decisões de planejamento comercial.

### 1.2. Os modelos elétricos e híbridos estão ganhando participação em relação aos modelos a combustão?

A análise considera os modelos eletrificados identificáveis na base, incluindo Taycan, Macan Electric e versões E-Hybrid.

O indicador de participação por cidade é calculado pela proporção de vendas classificadas como eletrificadas em relação ao total de registros da cidade.

**Objetivo de negócio:** identificar cidades com maior participação de veículos eletrificados e apoiar estudos sobre a evolução da demanda por tecnologias de menor dependência de combustíveis fósseis.

A participação calculada representa o comportamento observado na base analisada. Para afirmar que os eletrificados estão efetivamente ganhando participação ao longo do tempo, é necessário comparar essa proporção entre diferentes períodos.

### 1.3. Como o faturamento e o número de vendas evoluem por mês, trimestre e ano?

A dashboard permite alternar entre as visões mensal, trimestral e anual.

Os indicadores analisados são:

- Faturamento total por período.
- Quantidade de vendas por período.
- Ticket médio.
- Evolução temporal do desempenho comercial.

**Objetivo de negócio:** identificar tendências, sazonalidade e alterações no volume de vendas e no faturamento, apoiando o planejamento comercial e a avaliação de desempenho.

## 2. Análise, Indicadores e filtros

### KPIs

- **Faturamento total:** soma dos valores das vendas.
- **Quantidade de vendas:** número de registros considerados.
- **Ticket médio:** faturamento dividido pela quantidade de vendas.
- **Participação de eletrificados:** percentual de registros classificados como elétricos ou híbridos.

### Filtros interativos

A versão final possui quatro filtros:

- Modelo da Porsche.
- Model Year.
- City.
- Pay Method.

O filtro por estado foi removido durante o refinamento da interface. A análise por estado permanece disponível nas visualizações correspondentes.

## 3. Prompt utilizado para gerar a dashboard

O prompt inicial utilizado como referência para a criação foi:

> Crie uma dashboard interativa em HTML para analisar uma base de vendas de veículos Porsche. Inclua filtros por Modelo da Porsche, Model Year, City, Pay Method e State; indicadores de faturamento, quantidade de vendas e ticket médio; análise de receita por família de modelos e estado; participação de modelos elétricos e híbridos por cidade; e evolução de faturamento e número de vendas por mês, trimestre e ano. Inspire-se na identidade visual do site oficial da Porsche, com aparência elegante, refinada e premium. Utilize gráficos claros, filtros interativos e uma organização adequada para análise executiva.

### Evolução do prompt até a versão final

O desenvolvimento ocorreu em etapas iterativas, com ajustes orientados pelos requisitos do projeto.

**Etapa 1 — Estrutura analítica**

Foram definidos os indicadores, filtros, gráficos e perguntas de negócio. A prioridade foi criar uma visão executiva que permitisse explorar os dados de vendas por diferentes perspectivas.

**Etapa 2 — Refinamento visual**

Foi adotada uma identidade visual inspirada no site oficial da Porsche, com cores sóbrias, contrastes, detalhes em vermelho e uma composição visual elegante.

**Etapa 3 — Inclusão de imagem automotiva**

Foi solicitado um banner com imagem de um Porsche para dar mais vida à página e reforçar a identidade visual premium. A imagem foi incorporada ao próprio HTML, evitando a dependência de um arquivo externo separado.

**Etapa 4 — Revisão dos filtros**

O filtro por estado foi removido a pedido, mantendo-se os filtros de modelo, ano, cidade e forma de pagamento. As análises relacionadas aos estados foram preservadas.

**Etapa 5 — Tratamento das datas e validação**

Foi considerada a existência de datas inválidas na base. Esses registros continuam nos indicadores gerais quando os demais dados estão disponíveis, mas não participam do gráfico temporal, pois não podem ser posicionados corretamente na série histórica.

O resultado final é uma dashboard independente, com filtros interativos, indicadores dinâmicos e visualizações desenvolvidas para responder às perguntas de negócio propostas.

## 4. Tratamento e preparação da base de dados

A base utilizada foi uma planilha Excel sanitizada, denominada `planilha_sanitizada.xlsx`, contendo 100 registros.

Antes de incorporar os dados à dashboard, foram considerados os seguintes aspectos:

### 4.1. Sanitização

Foi utilizada a versão sanitizada da planilha disponibilizada para o projeto, evitando a exposição desnecessária de dados pessoais identificáveis.

### 4.2. Conversão dos dados

Os registros foram transformados em uma estrutura compatível com HTML e JavaScript, contendo os seguintes campos:

- Data da venda.
- Modelo Porsche.
- Ano do modelo.
- Preço da venda.
- Forma de pagamento.
- Cidade.
- Estado.

### 4.3. Tratamento de valores ausentes

Os campos vazios foram tratados para evitar falhas de leitura e processamento. A ausência de um valor não deve ser interpretada como informação confirmada.

### 4.4. Tratamento de datas inválidas

Foram identificadas 24 datas que não correspondiam ao formato esperado `AAAA-MM-DD`.

Esses registros permanecem nos indicadores gerais quando os demais dados permitem o cálculo, mas são excluídos da série temporal. Essa decisão evita atribuir datas incorretas às vendas.

### 4.5. Classificação das famílias de modelos

A família de cada veículo é inferida pelo nome do modelo, considerando as categorias 911, 718, Cayenne, Macan, Panamera e Taycan.

Modelos que não correspondem às regras de identificação podem ser classificados como “Outros”.

### 4.6. Classificação dos veículos eletrificados

A classificação utiliza palavras identificadas no nome do modelo, como `Taycan`, `Electric`, `E-Hybrid` e `E Hybrid`.

Essa regra é uma aproximação baseada no texto disponível. Para análises oficiais, recomenda-se validar as versões dos veículos e sua motorização com uma fonte de referência confiável.

### 4.7. Limitações identificadas

- O gráfico temporal utiliza apenas os registros com datas válidas.
- A classificação dos veículos eletrificados depende da identificação textual dos modelos.
- A qualidade dos resultados depende da consistência dos valores de venda e das demais dimensões.
- Os indicadores refletem a base fornecida e não representam necessariamente todo o mercado Porsche.

## 5. Ferramentas e recursos de inteligência artificial

### ChatGPT

O ChatGPT foi utilizado para apoiar o planejamento da interface, a elaboração do código e o refinamento da dashboard.

### Geração de imagem por inteligência artificial

Foi utilizada geração de imagem por IA para criar o banner automotivo incorporado à página.

### Canvas

O Canvas não foi utilizado na entrega final. O resultado foi desenvolvido e entregue como um arquivo HTML independente, que pode ser aberto em um navegador.

### Agente com skill

Não foi utilizado um agente com skill específico para a construção da dashboard.

Portanto, a solução foi desenvolvida com apoio do ChatGPT e de recursos de geração de imagem por IA, sem utilização de um agente especializado com skill.

## 6. Tecnologias utilizadas

- **HTML5:** estrutura da página.
- **CSS3:** identidade visual, organização dos componentes e responsividade.
- **JavaScript:** filtros interativos, cálculos dos indicadores e renderização dos gráficos.
- **Excel:** fonte original dos dados.
- **ChatGPT:** apoio à análise, ao desenvolvimento e ao refinamento.
- **GitHub Pages:** publicação da dashboard na internet.

## 7. Publicação no GitHub Pages

O projeto está associado ao repositório público `dashboard_porsche_sales`

A dashboard publicada pode ser acessada pelo endereço:

[https://monikerajava.github.io/dashboard_porsche_sales/porsche_sales_intelligence_v2.html](https://monikerajava.github.io/dashboard_porsche_sales/porsche_sales_intelligence_v2.html)

## 8. Conclusão

O projeto demonstra como a combinação de dados, programação e inteligência artificial pode acelerar a criação de uma solução de Business Intelligence.

A dashboard transforma uma planilha de vendas em uma interface interativa para explorar faturamento, volume de vendas, desempenho por família de modelos, diferenças regionais e participação de veículos eletrificados.

Além do resultado visual, o projeto evidencia a importância de definir perguntas de negócio relevantes, preparar os dados antes da análise e validar as regras utilizadas nos indicadores.

**Observação:** a dashboard é um projeto demonstrativo e não possui vínculo oficial com a Porsche. A identidade visual é inspirada em referências de design automotivo premium.

---

Desenvolvido como projeto de análise de dados e visualização interativa com apoio de inteligência artificial.
