# C3 : Normalização

## Relações
_(Apresentar as relações obtidas da transformação direta a partir do modelo EA)_

## Normalização do Esquema Relacional
_(Apresentar o estudo da normalização das relações obtidas na secção anterior. Desnormalizar se necessário.)_

---

# C3 : Normalização

## Conversão do Modelo EA para Modelo Relacional

### Passo 1: Entidades e Atributos

Funcionario (_n.id, nome, morada, nic, telefone*)

Formacao (_tipoFormacao, nomeFormacao)

Turno (_parteDia, hora)

Horario (_diaSemana, horaFim, horaInicio)

Seccao (_gerencia, cosmético, fornecedor, reposição, caixa, perfumaria, limpeza, maquilhagem)

Fornecedor (_id, nome, tipoStock, telefone*)

Produto (_codigo, nome, tipoProduto, validade)

Entrega(_tipoProduto, validade, reserva, quantidade)

### Passo 2: Associações 1:1
Não existe associações de carnalidade 1:1

#### Passo 3: Associações 1:N

Funcionario (_n.id, nome, morada, nic, telefone*
#_parteDia -> Turno)

Formacao (_tipoFormacao, nomeFormacao)

Turno (_parteDia, hora
#_gerencia -> Turno, #_diaSemana -> Horario)

Horario (_diaSemana, horaFim, horaInicio)

Seccao (_gerencia, cosmético, fornecedor, reposição, caixa, perfumaria, limpeza, maquilhagem)

Fornecedor (_id, nome, tipoStock, telefone*)

Produto (_codigo, nome, tipoProduto, validade)

Entrega (_tipoProduto, validade, reserva, quantidade
#_id -> Fornecedor)

### Passo 4: Associações N:M

Funcionario (_n.id, nome, morada, nic, telefone*
#_parteDia -> Turno)

Formacao (_tipoFormacao, nomeFormacao)

Turno (_parteDia, hora
#_gerencia -> Turno, #_diaSemana -> Horario)

Horario (_diaSemana, horaFim, horaInicio)

Seccao (_gerencia, cosmético, fornecedor, reposição, caixa, perfumaria, limpeza, maquilhagem)

Fornecedor (_id, nome, tipoStock, telefone*)

Produto (_codigo, nome, tipoProduto, validade)

Entrega (_tipoProduto, validade, reserva, quantidade
#_id -> Fornecedor)

Precisade ( #_n.id -> Funcionario, #_tipoFormacao -> Formacao)

Envia (#_tipoProduto -> Entrega, #_codigo -> Produto)

### Passo 5: Atributo Multivalor

Funcionario (_n.id, nome, morada, nic, telefone*
#_parteDia -> Turno)

Formacao (_tipoFormacao, nomeFormacao)

Turno (_parteDia, hora
#_gerencia -> Turno, #_diaSemana -> Horario)

Horario (_diaSemana, horaFim, horaInicio)

Seccao (_gerencia, cosmético, fornecedor, reposição, caixa, perfumaria, limpeza, maquilhagem)

Fornecedor (_id, nome, tipoStock, telefone*)

Produto (_codigo, nome, tipoProduto, validade)

Entrega (_tipoProduto, validade, reserva, quantidade
#_id -> Fornecedor)

Precisade (#_n.id -> Funcionario, #_tipoFormacao -> Formacao)

Envia (#_tipoProduto -> Entrega, #_codigo -> Produto)

Contacto (#_n.id -> Funcionario, #_id -> Fornecedor, telefone)


### Passo 6: Associação ternária


Funcionario (_n.id, nome, morada, nic, telefone*
#_parteDia -> Turno)

Formacao (_tipoFormacao, nomeFormacao)

Turno (_parteDia, hora
#_gerencia -> Turno, #_diaSemana -> Horario)

Horario (_diaSemana, horaFim, horaInicio)

Seccao (_gerencia, cosmético, fornecedor, reposição, caixa, perfumaria, limpeza, maquilhagem)

Fornecedor (_id, nome, tipoStock, telefone*)

Produto (_codigo, nome, tipoProduto, validade)

Entrega (_tipoProduto, validade, reserva, quantidade
#_id -> Fornecedor)

Precisade (#_n.id -> Funcionario, #_tipoFormacao -> Formacao)

Envia (#_tipoProduto -> Entrega, #_codigo -> Produto)

Contacto (#_n.id -> Funcionario, #_id -> Fornecedor, telefone)

Tem ( #_id -> Fornecedor, #_gerencia -> Seccao, #_diaSemana ->Horario)


### Passo 7: Entidades Fracas

Não existe Entidades Fracas



## Relacoes 


|Funcionario|    |      |   |         |                   |
|-----------|----|------|---|---------|-------------------|
|_n.id      |nome|morada|nic|telefone*|#_parteDia -> Turno|

|Formacao     |            |    
|-------------|------------|
|_tipoFormacao|nomeFormacao|

|Turno    |    |                 |                    |
|---------|----|-----------------|--------------------|
|_parteDia|hora|#_gerencia->Turno|#_diaSemana->Horario|

|Horario   |       |          |      
|----------|-------|----------|
|_diaSemana|horaFim|horaInicio|

|Seccao   |         |          |         |                        |           |
|---------|---------|----------|---------|------------------------|-----------|
|_gerencia|cosmetico|fornecedor|reposicao|caixa|perfumaria|limpeza|maquilhagem|

|Fornecedor|    |         |         |
|----------|----|---------|---------|
|_id       |nome|tipoStock|telefone*|


|Produto|    |           |        |
|-------|----|-----------|--------|
|_codigo|nome|tipoProduto|validade|

|Entrega     |        |       |          |                |
|------------|--------|-------|----------|----------------|
|_tipoProduto|validade|reserva|quantidade|#_id->Fornecedor|


|PrecisaDe          |                        |
|-------------------|------------------------|
|#_n.id->Funcionario|#_tipoFormacao->Formacao|

|Envia                 |                 |        
|----------------------|-----------------|
|#_tipoProduto->Entrega|#_codigo->Produto|

|Contacto           |                 |        |
|-------------------|-----------------|--------|
|#_n.id->Funcionario|#_codigo->Produto|telefone|

|Tem             |                  |                     |             
|----------------|------------------|---------------------|
|#_id->Fornecedor|#_gerencia->Seccao|#p_diaSemana->Horario|


## Normalização do Esquema Relacional

# 1ª Forma Normal (1NF)

Funcionario (_n.id, #nome, morada, nic
#_parteDia -> Turno)

  Telefonefuncionario (_nome, telefone)

Formacao (_tipoFormacao, nomeFormacao)

Turno (_parteDia, hora
#_gerencia -> Turno, #_diaSemana -> Horario)

Horario (_diaSemana, horaFim, horaInicio)

Seccao (_gerencia, cosmético, fornecedor, reposição, caixa, perfumaria, limpeza, maquilhagem)

Fornecedor (_id, #nome, tipoStock)
  
  Telefonefornecedor (_nome, telefone)

Produto (_codigo, nome, tipoProduto, validade)

Entrega (_tipoProduto, validade, reserva, quantidade
#_id -> Fornecedor)

Precisade (#_n.id -> Funcionario, #_tipoFormacao -> Formacao)

Envia (#_tipoProduto -> Entrega, #_codigo -> Produto)

Contacto (#_n.id -> Funcionario, #_id -> Fornecedor, telefone)

Tem ( #_id -> Fornecedor, #_gerencia -> Seccao, #_diaSemana ->Horario)


# 2ª Forma Normal (2NF)

Funcionario (_n.id, #nome, morada, nic
#_parteDia -> Turno)

  Telefonefuncionario (_nome, telefone)

Formacao (_tipoFormacao, nomeFormacao)

Turno (_parteDia, hora
#_gerencia -> Turno, #_diaSemana -> Horario)

Horario (_diaSemana, horaFim, horaInicio)

Seccao (_gerencia, cosmético, fornecedor, reposição, caixa, perfumaria, limpeza, maquilhagem)

Fornecedor (_id, #nome, tipoStock)
  
  Telefonefornecedor (_nome, telefone)

Produto (_codigo, nome, tipoProduto, validade)

Entrega (_tipoProduto, validade, reserva, quantidade
#_id -> Fornecedor)

Precisade (#_n.id -> Funcionario, #_tipoFormacao -> Formacao)

Envia (#_tipoProduto -> Entrega, #_codigo -> Produto)

Contacto (#_n.id -> Funcionario, #_id -> Fornecedor, telefone)

Tem ( #_id -> Fornecedor, #_gerencia -> Seccao, #_diaSemana ->Horario)


# 3ª Forma Normal (3NF)

Funcionario (_n.id, #nome, morada, nic
#_parteDia -> Turno)

  Telefonefuncionario (_nome, telefone)

Formacao (_tipoFormacao, nomeFormacao)

Turno (_parteDia, hora
#_gerencia -> Turno, #_diaSemana -> Horario)

Horario (_diaSemana, horaFim, horaInicio)

Seccao (_gerencia, cosmético, fornecedor, reposição, caixa, perfumaria, limpeza, maquilhagem)

Fornecedor (_id, #nome, tipoStock)
  
  Telefonefornecedor (_nome, telefone)

Produto (_codigo, nome, tipoProduto, validade)

Entrega (_tipoProduto, validade, reserva, quantidade
#_id -> Fornecedor)

Precisade (#_n.id -> Funcionario, #_tipoFormacao -> Formacao)

Envia (#_tipoProduto -> Entrega, #_codigo -> Produto)

Contacto (#_n.id -> Funcionario, #_id -> Fornecedor, telefone)

Tem ( #_id -> Fornecedor, #_gerencia -> Seccao, #_diaSemana ->Horario)


# Forma Normal de Boyce-Codd (BCNF)

Funcionario (_n.id, #nome, morada, nic
#_parteDia -> Turno)

  TELEFONEFUNCIONARIO (_nome, telefone)

Formacao (_tipoFormacao, nomeFormacao)

Turno (_parteDia, hora
#_gerencia -> Turno, #_diaSemana -> Horario)

Horario (_diaSemana, horaFim, horaInicio)

Seccao (_gerencia, cosmético, fornecedor, reposição, caixa, perfumaria, limpeza, maquilhagem)

Fornecedor (_id, #nome, tipoStock)
  
  TELEFONEFORNECEDOR (_nome, telefone)

Produto (_codigo, nome, tipoProduto, validade)

Entrega (_tipoProduto, validade, reserva, quantidade
#_id -> Fornecedor)

Precisade (#_n.id -> Funcionario, #_tipoFormacao -> Formacao)

Envia (#_tipoProduto -> Entrega, #_codigo -> Produto)

Contacto (#_n.id -> Funcionario, #_id -> Fornecedor, telefone)

Tem ( #_id -> Fornecedor, #_gerencia -> Seccao, #_diaSemana ->Horario)

# 4ª Forma Normal (4NF)

Funcionario (_n.id, #nome
#_parteDia -> Turno)

  Localidade (_nome, morada)
  
  Identificacao (_nome, nic)

  Telefonefuncionario (_nome, telefone)

Formacao (_tipoFormacao, nomeFormacao)

Turno (_parteDia, hora
#_gerencia -> Turno, #_diaSemana -> Horario)

Horario (_diaSemana, horaFim, horaInicio)

Seccao (_gerencia, cosmético, fornecedor, reposição, caixa, perfumaria, limpeza, maquilhagem)

Fornecedor (_id, #nome, tipoStock)
  
  Telefonefornecedor (_nome, telefone)

Produto (_codigo, nome, tipoProduto, validade)

Entrega (_tipoProduto, validade, #reserva
#_id -> Fornecedor)

  Reservaquantidade (_reserva, quantidade)

Precisade (#_n.id -> Funcionario, #_tipoFormacao -> Formacao)

Envia (#_tipoProduto -> Entrega, #_codigo -> Produto)

Contacto (#_n.id -> Funcionario, #_id -> Fornecedor, telefone)

Tem ( #_id -> Fornecedor, #_gerencia -> Seccao, #_diaSemana ->Horario)
[< Previous](rebd02.md) | [^ Main](https://github.com/SIBD08/SIBD08-Atlas/) | [Next >](rebd04.md)
:--- | :---: | ---: 
