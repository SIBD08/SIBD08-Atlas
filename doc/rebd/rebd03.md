# C3 : Normalização

## Conversão do Modelo EA para Modelo Relacional

### Passo 1: Entidade Tipo

Cliente (_codigo, nome)

Encomenda (_codigo,peso,dataEntrega)

Subsidiaria (_codigo, nome, {contacto})

Viagem (_codigo, nEncomendas)

Camiao (_matricula, autonomia, capacidadeCarga)

Funcionario (_numFuncionario, nome, {telem贸vel}, morada, cc)

Funcao (id, nome)

### Passo 2: Associações 1:1

Cliente (_codigo, nome)

Encomenda (_codigo,peso,dataEntrega)

Subsidiaria (_codigo, nome, {contacto})

Viagem (_codigo, nEncomendas)

Camiao (_matricula, autonomia, capacidadeCarga, 
        #funcionarioNFuncionario -> Funcionario)
        
Funcionario (_numFuncionario, nome, {telem贸vel}, morada, cc)
Funcao (id, nome)



### Passo 3: Associações 1:N

Cliente (_codigo, nome)

Encomenda (_codigo,peso,dataEntrega
           #codigoCliente -> Cliente, #codigoViagem -> Viagem, #codigoSubsidiaria -> Subsidiaria)
           
Subsidiaria (_codigo, nome, {contacto})

Viagem (_codigo, nEncomendas, 
        #codigoSubsidiaria -> Subsidiaria, #matriculaCamiao -> Camiao)
        
Camiao (_matricula, autonomia, capacidadeCarga, 
        #funcionarioNFuncionario -> Funcionario)
        
Funcionario (_numFuncionario, nome, {telem贸vel}, morada, cc
             #idFuncao -> Funcao)
             
Funcao (id, nome)

### Parte 4: Associações N:M

Não existem associações com cardinalidade N:M

### Parte 5: Atributo Multivalor 

Cliente (_codigo, nome)

Encomenda (_codigo,peso,dataEntrega
           #_codigoCliente -> Cliente, #_codigoViagem -> Viagem, #_codigoSubsidiaria -> Subsidiaria)
           
Subsidiaria (_codigo, nome, {contacto})

Viagem (_codigo, nEncomendas, 
        #_codigoSubsidiaria -> Subsidiaria, #_matriculaCamiao -> Camiao)
        
Camiao (_matricula, autonomia, capacidadeCarga, 
        #_funcionarioNFuncionario -> Funcionario)
        
Funcionario (_numFuncionario, nome, {telem贸vel}, morada, cc
             #_idFuncao -> Funcao)
             
Funcao (id, nome)

ContactoSub (#_codigo -> Subsidiaria, {contacto})

ContactoFun (#_numFuncionario -> Funcionario, {telemovel})

### Parte 6: Associações ternárias 

Não existem associações ternárias

### Passo 7: Entidades Fracas

Não existem Entidades Fracas



## Relacoes 


|Cliente |    | 
|--------|----|
|_codigo  |nome|

|Encomenda    |              |               |               |              |             |
|-------------|--------------|---------------|--------------|--------------|-------------|
|_codigo | peso | dataEntrega | #_codigo->Cliente| #_codigo->Viagem | #_codigo->Subsidiaria 

|Subsidiario    |    |           |
|---------|----|-----------------|
|_codigo|nome|contacto|

|Viagem   |           |             |                |
|----------|-----------|------------|---------------|
|_codigo| nEncomendas | #_codigo->Subsidiaria | #_matricula->Camiao

|Camiao  |         |          |                |
|---------|---------|----------|--------------|
|_matricula|autonomia|capacidadeCarga| #_nFuncionario->Funcionario

|Funcionario|    |         |         |       |                        |
|-----------|----|---------|---------|-------|------------------------|
|_numFuncionario | nome | telemovel | morada | cc | #_id->Funcao 


|Funcao|    |
|-------|----|
|_id| nome |

|ContactoSub   |        |
|------------|--------|
| #_codigo->Subsidiaria | contacto |


|ContactoFun        |                        |
|-------------------|------------------------|
| #_numFuncionario->Funcionario | telemovel



## Normalização do Esquema Relacional

# 1ª Forma Normal (1NF)

Cliente (_codigo, nome)

Encomenda (_codigo,peso,dataEntrega,
           #_codigoCliente -> Cliente, #_codigoViagem -> Viagem, #_codigoSubsidiaria -> Subsidiaria)
           
Subsidiaria (_codigo, nome)

-> ContactoSubsidiaria (_nome, {contacto})

Viagem (_codigo, nEncomendas, 
        #_codigoSubsidiaria 
-> Subsidiaria, #_matriculaCamiao -> Camiao)
        
Camiao (_matricula, autonomia, capacidadeCarga, 
        #_funcionarioNFuncionario -> Funcionario)
        
Funcionario (_numFuncionario, nome, morada, cc,
             #_idFuncao -> Funcao)
             
-> TelemovelFuncionario (_nome, {telemóvel})

Funcao (id, nome)

# 2ª Forma Normal (2NF)

Cliente (_codigo, nome)

Encomenda (_codigo,peso,dataEntrega,
           #_codigoCliente -> Cliente, #_codigoViagem -> Viagem, #_codigoSubsidiaria -> Subsidiaria)
           
Subsidiaria (_codigo, nome)

ContactoSubsidiaria (_nome, {contacto})

Viagem (_codigo, nEncomendas, 
        #_codigoSubsidiaria -> Subsidiaria, #_matriculaCamiao -> Camiao)
        
Camiao (_matricula, autonomia, capacidadeCarga, 
        #_funcionarioNFuncionario -> Funcionario)
        
Funcionario (_numFuncionario, nome,
             #_idFuncao -> Funcao)
             
-> DadosFuncionario (_nome, morada, cc)

TelemovelFuncionario (_nome, {telemóvel})

Funcao (id, nome)

# 3ª Forma Normal (3NF)

Cliente (_codigo, nome)

Encomenda (_codigo, peso, dataEntrega,
           #_codigoCliente -> Cliente)
           
-> CodigosEncomenda (#_codigoCliente -> Cliente, #_codigoViagem -> Viagem, #_codigoSubsidiaria -> Subsidiaria) 

Subsidiaria (_codigo, nome)

ContactoSubsidiaria (_nome, {contacto})

Viagem (_codigo, nEncomendas, 
        #_codigoSubsidiaria -> Subsidiaria, #_matriculaCamiao -> Camiao)
        
Camiao (_matricula, autonomia, capacidadeCarga, 
        #_funcionarioNFuncionario -> Funcionario)
        
Funcionario (_numFuncionario, nome,
             #_idFuncao -> Funcao)
             
DadosFuncionario (_nome, morada, cc)

TelemovelFuncionario (_nome, {telemóvel})

Funcao (id, nome)


# Forma Normal de Boyce-Codd (BCNF)

Não muda.


# 4ª Forma Normal (4NF)

Não muda

[< Previous](rebd02.md) | [^ Main](https://github.com/SIBD08/SIBD08-Atlas/) | [Next >](rebd04.md)
:--- | :---: | ---: 
