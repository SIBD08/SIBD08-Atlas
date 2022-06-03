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

Cliente (_codigo, nome)

Encomenda (_codigo, #_codigo->Cliente)

Subsidiaria (_codigo, nome, #_codigo->Viagem)

ContactoSubsidiaria (_nome, contacto)

Viagem (_codigo)

Camiao (_matricula, autonomia, capacidadeCarga)

Funcionario (_numFuncionario, nome, morada, cc, #_matricula->camião, #armazem ->Funcao, #condutor->Funcao)

TelemovelFuncionario (_nome, telemovel)

Funcao (armazém,condutor)

Destino (#_codigo->Encomenda, #_codigo->Subsidiaria, #_codigo-> Viagem)

LimiteCarga (#_codigo-> Encomenda, #_codigo-> Viagem, #_matricula->Camiao)

# 2ª Forma Normal (2NF)

Cliente (_codigo, nome)

Encomenda (_codigo, #_codigo->Cliente)

Subsidiaria (_codigo, nome, #_codigo->Viagem)

ContactoSubsidiaria (_nome, contacto)

Viagem (_codigo)

Camiao (_matricula, autonomia, capacidadeCarga)

Funcionario (_numFuncionario, nome, morada, cc, #_matricula->camião, #armazem ->Funcao, #condutor->Funcao)

TelemovelFuncionario (_nome, telemovel)

Funcao (armazém,condutor)

Destino (#_codigo->Encomenda, #_codigo->Subsidiaria, #_codigo-> Viagem)

LimiteCarga (#_codigo-> Encomenda, #_codigo-> Viagem, #_matricula->Camiao)

# 3ª Forma Normal (3NF)

Cliente (_codigo, nome)

Encomenda (_codigo, #_codigo->Cliente)

Subsidiaria (_codigo, nome, #_codigo->Viagem)

ContactoSubsidiaria (_nome, contacto)

Viagem (_codigo)

Camiao (_matricula, autonomia, capacidadeCarga)

Funcionario (_numFuncionario, nome, morada, cc, #_matricula->camião, #armazem ->Funcao, #condutor->Funcao)

TelemovelFuncionario (_nome, telemovel)

Funcao (armazém,condutor)

Destino (#_codigo->Encomenda, #_codigo->Subsidiaria, #_codigo-> Viagem)

LimiteCarga (#_codigo-> Encomenda, #_codigo-> Viagem, #_matricula->Camiao)


# Forma Normal de Boyce-Codd (BCNF)

Cliente (_codigo, nome)

Encomenda (_codigo, #_codigo->Cliente)

Subsidiaria (_codigo, nome, #_codigo->Viagem)

ContactoSubsidiaria (_nome, contacto)

Viagem (_codigo)

Camiao (_matricula, autonomia, capacidadeCarga)

Funcionario (_numFuncionario, nome, morada, cc, #_matricula->camião, #armazem ->Funcao, #condutor->Funcao)

TelemovelFuncionario (_nome, telemovel)

Funcao (armazém,condutor)

Destino (#_codigo->Encomenda, #_codigo->Subsidiaria, #_codigo-> Viagem)

LimiteCarga (#_codigo-> Encomenda, #_codigo-> Viagem, #_matricula->Camiao)


# 4ª Forma Normal (4NF)

Cliente (_codigo, nome)

Encomenda (_codigo, #_codigo->Cliente)

Subsidiaria (_codigo, nome, #_codigo->Viagem)

ContactoSubsidiaria (_nome, contacto)

Viagem (_codigo)

Camiao (_matricula, autonomia, capacidadeCarga)

Funcionario (_numFuncionario, nome, #_matricula->camião, #armazem ->Funcao, #condutor->Funcao)

LocalidadeFuncionario (_nome, morada)

IdentificacaoFuncionario (_nome, cc)

TelemovelFuncionario (_nome, telemovel)

Funcao (armazém,condutor)

Destino (#_codigo->Encomenda, #_codigo->Subsidiaria, #_codigo-> Viagem)

LimiteCarga (#_codigo-> Encomenda, #_codigo-> Viagem, #_matricula->Camiao)

[< Previous](rebd02.md) | [^ Main](https://github.com/SIBD08/SIBD08-Atlas/) | [Next >](rebd04.md)
:--- | :---: | ---: 
