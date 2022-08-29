Oi# Analise_Censo_Agropecuario_Base_dos_Dados
 Projeto de estudos de analise de dados usando uma base do Censo Agropecuário do Brasil

Nesse projeto eu realizei etapas como:

Importação das biliotecas e pacotes necessários

## Base escolhida

Usei a base Censo Agropecuário (br_ibge_censo_agropecuario) para realizar as análises e realizei um cruzamento com a base 
(br_bd_diretorios_brasil) para poder ter também os nomes dos municípios. Ambas as bases estão disponíveis no site da [Base dos Dados](https://basedosdados.org/dataset?order_by=score)

## Forma de download dos dados

Usei o read_sql para fazer o download da base

base_censo1 = bd.read_sql(
    '''
    SELECT censo.*, municipio.nome
        FROM basedosdados.br_ibge_censo_agropecuario.municipio AS censo 
        INNER JOIN basedosdados.br_bd_diretorios_brasil.municipio AS municipio
            ON censo.id_municipio = municipio.id_municipio
    ''',
    billing_project_id='teste1-360117'
)

## Tratamento e visualização

Realizei um tratamento para valores vazios encontrados na base e depois criei alguns dataframes auxiliares para facilitar a geração dos gráficos.
Depois usei o Plotly para poder gerar gráficos interativos e gerar um arquivo html para futuras visualizações

