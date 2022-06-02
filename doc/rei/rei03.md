# C3 : Esquema conceptual

## Modelo E/A

ENTIDADES

* CAMIAO (matricula, capacidade, autonomia)
* VIAGEM (codigo, origem, destino, limiteCarga)
* SUBSIDIARIA (codigo, nome, telefone)
* ENCOMENDA (codigo, destino)
* GRUPO (armazem, condutores)
* FUNCIONARIO (nome, telefone, morada, cc, nfuncionario)
* CLIENTE (nome, codigo)

ASSOCIAÇÕES

* atribuidoA (CAMIAO, VIAGEM, FUNCIONARIO) M:N T/P
* dividoPor (FUNCIONARIO, GRUPO) 1:N T/P
* entrega (CAMIAO, CLIENTE, ENCOMENDA, SUBSIDIARIA) 1:1 P/T

 
![Diagrama](images/Diagrama_Atlas.jpeg) 

## Regras de negócio adicionais (Restrições)

Para ser selecionado para condutor da nossa empresa tem de ter a carta de condução de pesados.
Pode existir troca de turnos entre funcionários do mesmo grupo, nunca um funcionário de armazém pode trocar de turno com um condutor.

---
[< Previous](rei02.md) | [^ Main](https://github.com/SIBD08/SIBD08-Atlas/) |
:--- | :---: | 
