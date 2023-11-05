Requisitos da análise:

Utilização de 20 questões realizadas na pesquisa

Caracterização dos sintomas clínicos da população

Características da população

Comportamento da população

Características econômicas da sociedade

Usando banco de dados em nuvem


Escolha dos dados:

Utilizado dados dos meses de Julho, Agosto e Setembro de 2020 , que são os meses com maior número de casos reportados, dentre as opções da pesquisa.

Como podemos usar apenas 20 questões das 150 disponíveis na pesquisa, seguimos o raciocínio abaixo na escolha das variáveis ​​mais relevantes:

Inicialmente descartamos variáveis ​​mais granulares e que tinham alto número de nulos, tais como informações específicas dos rendimentos da população (ex: somatório dos valores recebidos em auxílio emergencial, bolsa família, LOAS, retirava o recebimento em dinheiro, em alimentos, valores de obtenção, etc.).

Também descartamos variáveis ​​mais subjetivas e que não tinham tanta relação com os pedidos do hospital (gostaria de ter trabalho na semana passada, qual o motivo de não ter procurado trabalho, gostaria de ter trabalho mais horas, etc.).

Selecionamos as variáveis ​​que consideramos mais relevantes para a pesquisa inicialmente. Utilizamos o databricks/spark e SQL para analisar os dados e aproveitar a escolha.

Após a análise, optamos por fazer um ranking de sintomas e comorbidades mais frequentes para diminuir o número de variáveis ​​clínicas e escolhemos as variações que melhor representam o perfil socioeconômico da população.

Caminho dos dados
Extração das tabelas mensais do site do IBGE diretamente pelo Databricks. Salvamos as tabelas no driver e depois copiamos para o DBFS.
Unimos as tabelas dos 3 meses em um único conjunto de dados. Fizemos transformação e análise descritiva dos dados com python e SQL.
Fizemos a transferência dos dados para o GCS, salvando o arquivo em um bucket no formato parquet.
No Big Query criamos uma tabela externa apontando para os dados em parquet no GCS e uma view para permitir o acesso aos dados direto com o Power BI.
No PBI, importamos os dados para a criação dos gráficos e da apresentação.
Entregáveis
Nesse repositório encontro os seguintes arquivos:

Dicionário dos dados fornecidos pela PNAD;

Notebook com o processo de extração de dados nos formatos dbc e ipynb;

Caderno com análise descritiva inicial (somente para registro da exploração inicial) no formato dbc;

Notebook com a transformação dos dados escolhidos nos formatos dbc e ipynb;

Dashboard em PBI com análise final dos dados, respostas aos pedidos do hospital e conclusões.
