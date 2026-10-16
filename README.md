Análise Preditiva e Comportamental dos Meios de Pagamento Eletrônicos no Brasil: Um Estudo Comparativo entre TED e PIX com Dados do Banco Central
Kelly Cristina Rodrigues
Especialização em Ciência de Dados – Universidade Tecnológica Federal do Paraná (UTFPR)
kellyrodrigues@alunos.utfpr.edu.br
Abstract
This study analyzes the temporal evolution and behavioral transition of electronic payment systems in Brazil, focusing on the comparison between TED (Available Electronic Transfer) and PIX (Brazilian Instant Payment System). Utilizing public monthly data from the Central Bank of Brazil (BCB) spanning 104 months (January 2018 to August 2026), we performed data cleaning, feature engineering, exploratory data analysis, and predictive modeling using Linear Regression, Random Forest Regressor, and Gradient Boosting Regressor. The empirical findings demonstrate a structural shift in consumer behavior: PIX established absolute dominance in total transaction count (reaching a 95.36% market share in August 2026), while TED remains predominant for high-value corporate transactions with an average ticket of R$ 58,030.07. Machine learning models captured the growth dynamics of PIX transaction volume, achieving R² scores exceeding 0.98.
Resumo
Este estudo analisa a evolução temporal e a transição comportamental dos meios de pagamento eletrônicos no Brasil, focando na comparação entre a Transferência Eletrônica Disponível (TED) e o PIX. Utilizando dados públicos mensais do Banco Central do Brasil (BCB) abrangendo 104 meses (de janeiro de 2018 a agosto de 2026), foram executadas etapas de tratamento de dados, engenharia de atributos, análise exploratória e modelagem preditiva com algoritmos de Regressão Linear, Random Forest Regressor e Gradient Boosting Regressor. Os resultados empíricos evidenciam uma mudança estrutural no comportamento do consumidor: o PIX estabeleceu dominância absoluta na quantidade de operações (alcançando 95,36% de participação em agosto de 2026), enquanto a TED permaneceu concentrada em transações corporativas de elevado valor unitário (ticket médio de R$ 58.030,07). Os modelos de aprendizado de máquina capturaram a trajetória do volume financeiro do PIX com R² superior a 0,98.


1. Introdução
A modernização do Sistema Financeiro Nacional (SFN) passou por uma transformação sem precedentes com o lançamento do sistema de pagamentos instantâneos (PIX), implementado pelo Banco Central do Brasil (BCB) em novembro de 2020. 

Antes da criação do PIX, as transferências bancárias no país eram amplamente dominadas pela Transferência Eletrônica Disponível (TED) e pelo Documento de Ordem de Crédito (DOC), instrumentos caracterizados por tarifação, horários bancários restritos e prazos de compensação [Duarte et al. 2021].

Com a disponibilização do repositório público de Estatísticas de Meios de Pagamentos Mensais no portal de Dados Abertos do BCB, tornou-se possível mensurar a transição digital com alta precisão temporal [Brandt et al. 2022]. 

O problema de pesquisa abordado neste trabalho consiste em avaliar os padrões de substituição e especialização entre a TED e o PIX, verificando em que medida a ascensão do PIX afetou a quantidade de transações e a evolução dos tickets médios de transferência no Brasil.

O objetivo principal deste projeto integrador é analisar a série temporal de movimentações financeiras por TED e PIX de janeiro de 2018 a agosto de 2026 (104 meses) e desenvolver modelos preditivos para estimar o volume financeiro movimentado pelo PIX. 

A abordagem metodológica fundamenta-se no fluxo de Ciência de Dados, englobando a conversão e limpeza de dados numéricos em Python, a engenharia de atributos (cálculo de ticket médio e market share), a divisão de conjuntos de treinamento e teste e a avaliação de algoritmos de regressão e aprendizado supervisionado [McKinney 2010, Pedregosa et al. 2011].

Este trabalho está estruturado da seguinte forma: a Seção 2 revisa a literatura acadêmica relevante; a Seção 3 detalha a metodologia de tratamento e modelagem dos dados; a Seção 4 apresenta os resultados experimentais com tabelas explicativas; a Seção 5 expõe a conclusão e trabalhos futuros; e a Seção 6 disponibiliza os links de acesso ao código e à apresentação.
2. Trabalhos Relacionados
A ascensão dos pagamentos instantâneos no Brasil e o seu impacto no ecossistema bancário e de varejo têm sido investigados em diversos estudos recentes do setor financeiro [Duarte et al. 2021, Brandt et al. 2022, Silva e Araujo 2023].

Duarte et al. (2021) analisaram o papel da gratuidade para pessoas físicas e o funcionamento 24/7 do PIX como indutores da inclusão financeira no Brasil. Os autores observaram que o PIX substituiu rapidamente pagamentos em papel-moeda e transferências tarifadas no varejo cotidiano.

Brandt et al. (2022) investigaram a coexistência funcional entre a TED e o PIX sob a perspectiva de risco e volumetria. O estudo destacou que, enquanto o PIX absorveu a imensa maioria das operações diárias de pequeno e médio valor (C2C e B2C), a TED manteve sua dominância em operações corporativas e de tesouraria de grande porte (B2B).

Silva e Araujo (2023) aplicaram modelos de aprendizado de máquina em dados abertos do Banco Central para prever a curva de adoção de serviços financeiros digitais. Os autores comprovaram a eficiência de algoritmos de regressão e ensemble na modelagem do crescimento de arranjos de pagamentos instantâneos. 

Este projeto integrador complementa a literatura ao disponibilizar um pipeline analítico completo e reprodutível em Python, alinhado às disciplinas da especialização em Ciência de Dados da UTFPR.
3. Metodologia
A condução do projeto dividiu-se em quatro etapas: carga e higienização dos dados do BCB, engenharia de atributos, análise exploratória e modelagem preditiva.
3.1 Fonte e Estrutura dos Dados
Os dados foram extraídos do arquivo oficial Meios de Pagamentos Mensais.csv do portal de Dados Abertos do Banco Central, acessível no link: https://dadosabertos.bcb.gov.br/dataset/estatisticas-meios-pagamentos.

O dataset contém 104 registros mensais referentes ao período de janeiro de 2018 a agosto de 2026, com dados de quantidade de transações (em milhares) e volume financeiro (em milhões de Reais) para PIX, TED, Boleto, Cheque e DOC.
3.2 Engenharia de Atributos e Pré-processamento em Python
Por meio das bibliotecas Pandas e NumPy em linguagem Python [McKinney 2010], foi realizada a conversão dos campos numéricos formatados com vírgula decimal. 

Em seguida, foram calculadas as seguintes variáveis derivadas:
●	Ticket Médio (R$): Razão entre o volume total em Reais e a quantidade total de transações para TED, PIX e DOC.
●	Market Share de Quantidade (%): Proporção das transações via PIX em relação ao somatório de meios de transferência eletrônica.
●	Flag Pós-PIX: Variável binária identificando o período a partir de novembro de 2020.
3.3 Divisão dos Dados e Algoritmos Preditivos
Para a modelagem preditiva do volume do PIX (em milhões de R$), utilizou-se o subconjunto de dados a partir de novembro de 2020 (70 observações mensais), dividido na proporção de 80% para treinamento e 20% para teste. 

Foram implementados três algoritmos através da biblioteca Scikit-Learn [Pedregosa et al. 2011]:
1.	1. Regressão Linear: Modelo baseline parametrizado com padronização via StandardScaler.
2.	2. Random Forest Regressor: Algoritmo ensemble baseado em 100 árvores de decisão.
3.	3. Gradient Boosting Regressor: Algoritmo de impulsionamento por gradiente.
4. Resultados Experimentais
A Tabela 1 apresenta a síntese dos indicadores médios mensais no período pós-lançamento do PIX (novembro de 2020 a agosto de 2026).

Tabela 1. Indicadores Médios Mensais dos Meios de Pagamento (Nov/2020 a Ago/2026)

Meio de Pagamento	Quantidade Média Mensal (Milhares)	Volume Médio Mensal (R$ Milhões)	Ticket Médio Médio (R$)
PIX	3.978.046,11	1.754.321,56	R$ 475,25
TED	81.305,49	3.468.441,86	R$ 45.841,18
Os números da Tabela 1 revelam uma clara divisão de mercado: enquanto o PIX lidera em volume absoluto de operações diárias (com média de 3,97 bilhões de transações/mês e ticket médio de R$ 475,25), a TED concentra a movimentação de grandes valores por transação, registrando ticket médio superior a R$ 45 mil. 

No último mês da série (agosto de 2026), o PIX atingiu 8,11 bilhões de transações mensais (95,36% de participação em quantidade) com ticket de R$ 460,33, enquanto a TED atingiu ticket médio de R$ 58.030,07. O DOC apresentou zeramento a partir de fevereiro de 2024, refletindo a sua descontinuação oficial pelo mercado bancário.
A Tabela 2 apresenta o desempenho dos modelos de aprendizado de máquina treinados para prever o volume financeiro do PIX no conjunto de teste.

Tabela 2. Desempenho dos Modelos Preditivos no Conjunto de Teste

Algoritmo	MAE (R$ Milhões)	RMSE (R$ Milhões)	R² Score
Regressão Linear	75.647,18	84.249,66	0,9939
Random Forest Regressor	83.843,03	125.249,37	0,9866
Gradient Boosting Regressor	88.746,18	116.873,51	0,9883

Como demonstrado na Tabela 2, todos os algoritmos obtiveram coeficiente de determinação R² superior a 0,98, sendo a Regressão Linear o modelo de menor erro absoluto médio (MAE de R$ 75,64 bilhões sobre uma movimentação mensal superior a R$ 3,7 trilhões).
5. Conclusão
Este estudo teve por objetivo analisar a transição comportamental dos meios de pagamento no Brasil utilizando o arquivo oficial de dados abertos do Banco Central. 

Ficou demonstrado que a popularização do PIX promoveu uma massiva inclusão digital no varejo sem extinguir a TED, que se consolidou no segmento de liquidação de grandes valores corporativos.

Como contribuição prática, este projeto integrou conhecimentos de manipulação de dados em Python, engenharia de atributos e aprendizado preditivo, gerando o código script_analise_ted_pix.py e o dataset limpo Meios_de_Pagamentos_Mensais_Tratado.csv para publicação no GitHub. 

Como limitação, cita-se o caráter nacional agregado dos dados do BCB. Sugere-se para trabalhos futuros a inclusão de modelos de decomposição sazonal e análises segmentadas por tipo de arranjo (P2P, P2B, B2B).
6. Links do Projeto
●	Canal da Apresentação no YouTube: https://www.youtube.com/@KellyRodrigues-r8s
●	Repositório de Código e Dados no GitHub: https://github.com/importanterodrigues-max
Referências
Brandt, C. A., Santos, E. M., e Silva, R. J. (2022). O impacto do Pix na concorrência bancária e na eficiência do Sistema Financeiro Nacional. Revista de Economia Bancária e Finanças, 24(2):89–108.
Duarte, A. J., Castro, P. H., e Lima, M. F. (2021). Arranjos de pagamentos instantâneos no Brasil: Uma análise da adoção e inclusão financeira impulsionada pelo Pix. Revista Brasileira de Finanças, 19(3):45–67.
McKinney, W. (2010). Data structures for statistical computing in Python. In Proceedings of the 9th Python in Science Conference, pages 51–56.
Pedregosa, F., Varoquaux, G., Gramfort, A., Michel, V., Thirion, B., Grisel, O., Blondel, M., Prettenhofer, P., Weiss, R., Dubourg, V., Vanderplas, J., Passos, A., Cournapeau, D., Brucher, M., Perrot, M., and Duchesnay, É. (2011). Scikit-learn: Machine learning in Python. Journal of Machine Learning Research, 12:2825–2830.
Silva, T. R. e Araujo, G. S. (2023). Previsão de demanda em meios de pagamentos eletrônicos utilizando aprendizado de máquina. Journal of Information and Data Management (JIDM), 14(1):115–130. SBC.

