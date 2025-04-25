# Modelo de Banco de Dados

## Descrição
Banco de dados desenvolvido para gerenciar informações de acompanhamento do cultivo de lavouras através de sensores de umidade, PH, fósforo e potássio.

## Estrutura das Tabelas

### Tabela: SENSOR
| Coluna                | Tipo de Dados | Chave Primária | Chave Estrangeira |
|-----------------------|---------------|----------------|-------------------|
| id_sensor             | VARCHAR(255)  | Sim            | Não               |
| data_hora_medicao     | TIMESTAMP     | Não            | Não               |
| localizacao_latitude  | DECIMAL       | Não            | Não               |
| localizacao_longitude | DECIMAL       | Não            | Não               |
| valor medição         | DECIMAL       | Não            | Não               |


### Tabela: MEDICAO
| Coluna                | Tipo de Dados | Chave Primária | Chave Estrangeira |
|-----------------------|---------------|----------------|-------------------|
| data_hora_medicao     | TIMESTAMP     | Sim            | Não               |
| id_sensor             | VARCHAR(255)  | Não            | Sim               |
| tipo medição          | VARCHAR(255)  | Não            | Não               |
| valor medição         | DECIMAL       | Não            | Não               |


### Tabela: IRRIGACAO
| Coluna                 | Tipo de Dados | Chave Primária | Chave Estrangeira |
|------------------------|---------------|----------------|-------------------|
| data_hora_irrigacao    | TIMESTAMP     | Sim            | Não               |
| id_torneira            | VARCHAR(255)  | Não            | Não               |
| agua_despejada         | VARCHAR(255)  | Não            | Não               |
| corretivo_ph_despejado | DECIMAL       | Não            | Não               |
| fosforo_despejado      | DECIMAL       | Não            | Não               |
| potassio_despejado     | DECIMAL       | Não            | Não               |


### Tabela: TORNEIRA
| Coluna                 | Tipo de Dados | Chave Primária | Chave Estrangeira |
|------------------------|---------------|----------------|-------------------|
| id_torneira            | VARCHAR(255)  | Sim            | Não               |
| data_hora_irrigacao    | TIMESTAMP     | Não            | Sim               |
| area_coberta_latitude  | DECIMAL       | Não            | Não               |
| area_coberta_longitude | DECIMAL       | Não            | Não               |
| agua_despejada         | VARCHAR(255)  | Não            | Não               |
| corretivo_ph_despejado | DECIMAL       | Não            | Não               |
| fosforo_despejado      | DECIMAL       | Não            | Não               |
| potassio_despejado     | DECIMAL       | Não            | Não               |


## Relacionamentos

- Entre as tabelas SENSOR e MEDICAO há um relacionamento 1:1, dado que cada sensor apresentará uma medicação somente, 
a cada dia e hora, e que cada medição será realizada por um sensor apenas.

- Entre as tabelas IRRIGACAO e TORNEIRA há um relacionamento 1:N, dado que para cada horário de irrigação uma ou mais 
torneiras podem ser acionadas.