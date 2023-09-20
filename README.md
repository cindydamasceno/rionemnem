# (Grupo 4 ) | Exploração da Base de Dados sobre multas por violação da Lei 8.213/91 (Lei das Cotas)
*Exercício final para disciplina de Fundamentos e Ética do Jornalismo de Dados, do Master em Jornalismo de Dados, Automação e Storytelling do Insper. As duas coletâneas de dados que serviram de base para esta análise foram obtidas pela equipe através de Lei de Acesso a Informação (LAI). Para manter o propósito da replicabilidade – e ampliar o terreno para análises posteriores – ambas foram adicionadas no formato bruto. **[(ver Problemas de Documentação)](https://github.com/cindydamasceno/rionemnem/tree/main#como-contornar-os-problemas-de-documenta%C3%A7%C3%A3o))***

<hr>

## **Bases de Dados utilizadas** 📝 <p>
+ [**Ver Bases Originais**](https://github.com/cindydamasceno/rionemnem/tree/main/Bases%20originais%20sem%20tratamento)
  +  Empresas Autuadas **(Tabela 1)**: relação de empresas autuadas por descumprirem a Lei 8.213/91 entre março de 2019 e março de 2023, obtida através de solicitação via LAI ao Ministerio do Trabalho e Emprego (MTE) [**(veja solicitação aqui)**](https://github.com/cindydamasceno/rionemnem/blob/main/DetalhesManifestacaoLai.pdf)  
  +  Empresas Multadas **(Tabela 2)**: relação de empresas multadas por descumprirem a Lei 8.213/91 entre março de 2019 e março de 2023 [**(veja solicitação aqui)**](https://github.com/cindydamasceno/rionemnem/blob/main/DetalhesManifestacaoLai.pdf)

## Escolha da base
A equipe utilizou dados solicitados via Lei de Acesso à Informação (LAI) ao Ministério do Trabalho e Emprego (MTE) para saber como, atualmente, as empresas se adaptaram à Lei de Cotas para Pessoas com Deficiência (8.213/91). A necessidade veio a partir de um projeto corporativo desenvolvido por uma das nossas integrantes. 

## Escolha da ferramenta
Apesar de volumosa, a base de dados cedida se mostrou simples o suficiente para ser tratada via Planilha Eletrônica. Para facilitar a troca assíncrona entre as integrantes, foi utiilizado a plataforma **Google Sheets** para análises. 

## Limpeza, padronização e documentação

### Cálculo por empresa
Para perceber a proporção entre autuações e multas, foi feito um cruzamento a partir do **número de CNPJ**, presente em ambas as tabelas, através do operador ``=PROCV``. Apesar da base original indicar uma possível presença de CPF (Cadastro de Pessoa Física) ou CEI (Cadastro Específico do INSS) como identificadores dos alvos das autuações, essas informações foram desconsideradas. Isso porque fugiram da proposta da análise (garantir que somente empresas entrassem na leitura da base de dados).  

O resultado foi uma nova tabela **[(Base Limpa)](https://github.com/cindydamasceno/rionemnem/blob/main/base_limpa_pcd.xlsx)**, que selecionou as empresas multadas **(Tabela 2)** entre as autuadas **(Tabela1)**. Este novo documento trouxe informações como ``Razão Social``, ``UF da empresa (SGUF)``, ``Data autuação``,	``Valor da Multa (vlmulta)``,	``Data e Valor Pago``. Como fugiam da proposta, outros valores foram desconsiderados após análise da equipe [**(ver colunas desconsideradas)**](https://github.com/cindydamasceno/rionemnem#colunas-desconsideradas). 

Com isso em mãos, iniciamos o cálculo da multa por empresa. Uma vez que um mesmo estabelecimento poderia ter sido multado mais de uma vez, utilizamos a **tabela dinâmica** para somar a coluna ``vlmulta``nos ``CNPJ`` iguais.  

### Cálculo por Unidade Federativa (UF)
Processo similar foi feito para cálculo do valor da multa por UF, mas com a soma de ``SGUF``para encontar o valor absoluto.  

### Cálculo do valor pago
Para separar a Data de Pagamento do Valor Pago (os dois estavam unidos na coluna ``Data e Valor Pago``), foi utilizado o operador ``=EXT.TEXTO``. Ele permite selecionar apenas uma porção de caracteres de uma célula específica. Neste caso, para selecionar a porção de informação apenas com os valores, foi utilizado a função a seguir: 

```
=EXT.TEXTO(A2;13;22)
```

### Cálculo por dias até o pagamento da multa
Uma vez que ADICIONAR DEPOIS DA THIELLEN

### Como contornar os problemas de documentação
Apesar da resposta chegar com celeridade, os documentos enviados pelo Ministério do Trabalho e Emprego (MTE) não foram disponibilizados com um Dicionário de Dados. Desta forma, a equipe optou por restringir a análise apenas aos dados identificáveis, como UF e Razão Social. Os valores desconsiderados, no entanto, foram avaliados antes da exclusão. Percebeu-se que eles não afetariam os cálculos principais. 

#### Colunas desconsideradas

+ Numero AI
+ Ultima Movimentacao: Ultima movimentação no processo (eu acho)
Data e Valor Pago: Valor pago na multa
+ Situacao Atual
+ dt decisao 1a 
+ decisao 1a 
+ dt recurso
+ dt decisao 2a 
+ Decisao 2a 
+ Decisao Definitiva
+ Processo Encerrado
+ Decisao de Procedência

## **Em caso de dúvidas, contate a equipe:**   
Christina Souza ()  
Cindy Damasceno (cindydjales@gmail.com)  
Thiellen Rodrigues ()  
Vanessa Loiola ()
