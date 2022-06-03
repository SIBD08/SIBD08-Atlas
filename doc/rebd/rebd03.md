# C3 : Normalização

## Conversão do Modelo EA para Modelo Relacional

### Passo 1: Entidade Tipo

Cliente (_codigo, nome)

Encomenda (_codigo)

Subsidiaria (_codigo, nome, contacto)

Viagem (_codigo)

Camiao (_matricula, autonomia, capacidadeCarga)

Funcionario (_numFuncionario, nome, telemóvel, morada, cc)

Funcao (armazém,condutor)

### Passo 2: Associações 1:1

Cliente (_codigo, nome)

Encomenda (_codigo)

Subsidiaria (_codigo, nome, contacto)

Viagem (_codigo)

Camiao (_matricula, autonomia, capacidadeCarga)

Funcionario (_numFuncionario, nome, telemóvel, morada, cc
#_matricula->camiao)

Funcao (armazém,condutor)

### Passo 3: Associações 1:N

Cliente (_codigo, nome)

Encomenda (_codigo,
#_codigo->Cliente)

Subsidiaria (_codigo, nome, contacto,
#_codigo->Viagem)

Viagem (_codigo)

Camiao (_matricula, autonomia, capacidadeCarga)

Funcionario (_numFuncionario, nome, telemóvel, morada, cc,
#_matricula->camião, #armazem ->Funcao, #condutor->Funcao)

Funcao (armazém,condutor)

### Parte 4: Associações N:M

Não existem associações com cardinalidade N:M

### Parte 5: Atributo Multivalor 

Não existem Atributos Multivalor

### Parte 6: Associações ternárias 

Cliente (_codigo, nome)

Encomenda (_codigo,
#_codigo->Cliente)

Subsidiaria (_codigo, nome, contacto,
#_codigo->Viagem)

Viagem (_codigo)

Camiao (_matricula, autonomia, capacidadeCarga)

Funcionario (_numFuncionario, nome, telemóvel, morada, cc,
#_matricula->camião, #armazem ->Funcao, #condutor->Funcao)

Funcao (armazém,condutor)

Destino (#_codigo->Encomenda, #_codigo->Subsidiaria, #_codigo-> Viagem)

LimiteCarga (#_codigo-> Encomenda, #_codigo-> Viagem, #_matricula->Camiao)

### Passo 7: Entidades Fracas

Não existem Entidades Fracas



## Relacoes 


|Cliente |    | 
|--------|----|
|_codigo  |nome|

|Encomenda    |              |    
|-------------|--------------|
|_codigo | #_codigo->Cliente|

|Subsidiario    |    |                 |                    |
|---------|----|-----------------|--------------------|
|_codigo|nome|contacto|#_codigo->Viagem|

|Viagem   |     
|----------|
|_codigo|

|Camiao  |         |          |
|---------|---------|----------|
|_matricula|autonomia|capacidadeCarga|

|Funcionario|    |         |         |       |                        |                   |                  |
|-----------|----|---------|---------|-------|------------------------|-------------------|-----------------|
|_numFuncionario | nome | telemovel | morada | cc | #_matricula->camiao | #armazem->funcao | #condutor->funcao |


|Funcao|    |
|-------|----|
|armazem|condutor|

|Destino   |        |       |
|------------|--------|-------|
|#_codigo->Encomenda|#_codigo->Subsidiario|#_codigo->Viagem |


|LimiteCarga         |                        |                |
|-------------------|------------------------|--------------|
|#_codigo->Encomenda|#_codigo->viagem|#_matricula->Camiao



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
