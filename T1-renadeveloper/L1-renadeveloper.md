# Python


## Contexto Histórico


A linguagem Python foi criada por Guido Van Rossum em 1989 quando este trabalhava no Centrum Voor Wiskunde en Informatica no início dos anos 1980, e seu trabalho era implementar a linguagem de programação conhecida como ABC. Durante o final dos anos 1980, ele começou a procurar por uma linguagem de script que tivesse sintaxe semelhante ao ABC, mas que tivesse acesso às chamadas de sistema do Amoeba. Após procurar e não encontrar nenhuma linguagem que atendesse às suas necessidades, Rossum decidiu projetar uma linguagem de script simples que pudesse superar as inadequações do ABC. No final da década de 1980, Rossum começou a desenvolver o novo script, e em 1991, lançou a versão de abertura da linguagem de programação.

Se engana porém quem pensa que o nome Python vem como referência às cobras. A inspiração vem, na verdade de um programa da BBC famoso Na década de 1970, do qual van Rossum era um grande fã, chamado Fly Circus de Monty Python, ou apenas Monty Python. 

Em maio de 2000, Guido e o time principal de Python se mudaram para a BeOpen.com para formar o time BeOpen PythonLabs. Em outubro do mesmo ano, o time da PythonLabs se moveu para a Digital Creations. Em 2001, a Python Software Foundation, uma organização sem fins lucrativos, foi formada especialmente para manter a linguagem e hoje possui sua propriedade intelectual.

Python é uma das linguagens mais utilizadas no mundo todo e a que mais cresceu (15,2%) nos últimos cinco anos [segundo a pesquisa de Popularidade do GitHub, realizada em 2021](https://pypl.github.io/PYPL.html).

Nesse guia serão abordados aspectos da versão 3.10.0 da linguagem como base de referência.


## Principais Características

Python é uma linguagem fortemente tipada, ou seja, é uma linguagem em que se deve fazer operações com a necessidade da realização de cast. Exemplo:

```py

doisBinario = '10'
numeroDez = 10
print(doisBinario + numeroDez);  // o interpretador/compilador dirá que não é possível somar strings e inteiros

```

e também dinamicamente tipada, ou seja, é uma linguagem em que o tipo de uma variável pode ser alterado durante a execução do código.

Python é tanto uma linguagem interpretada quanto uma linguagem compilada. Um compilador traduz linguagem Python em linguagem de máquina - código Python é traduzido em um código intermediário que deve ser executado por uma máquina virtual conhecida como PVM (Python Virtual Machine). Assim, Python é uma linguagem interpretada - principalmente por essa compilação ocorrer em tempo de execução (compilação just-in-time).

Python é uma linguagem de propósito geral podendo ser uma linguagem também de script, modo pelo qual foi muito conhecida. 

Python é uma linguagem multiparadigma, suportando os paradigmas orientado a objetos, imperativo, funcional e procedural.


## Variáveis

Python é uma linguagem case-sensitive, ou seja, sensível às letras maíusculas e minúsculas - na qual se você cria uma variável com nome `linguagem` esta é diferente de outra variável chamada `Linguagem`.

As variáveis em Python possuem sequência de tamanho ilimitado, podem conter caracteres alfanuméricos (A-z 0-9), podem conter sublinhados, podem iniciar com letra (A-z) e podem iniciar com sublinhado - apesar de não ser indicado.

As variáveis em Python não podem conter pontos, espaços em branco, não podem ser iniciadas com números ou ser palavra-chave ou palavra reservada da linguagem.


## Tipos de Dados

Os tipos de dados de uma variável Python podem ser:

- Inteiro: representado por int;
- Ponto Flutuante ou Decimal: representado por float;
- Tipo Complexo: representado por complex;
- String: representado por str;
- Boolean: podendo ser true ou false e sendo representado por bool;
- Lista: representado por list;
- Tuplas: representado por tuple
- Dicionário: representado por dict.


É possível verificar o tipo das variáveis com o operador unário `typeof`:

```py
cliente = "Renata"
print(type(cliente)) # será impresso string
```

É possível fazer o casting (mudança de tipos de variáveis) utilizando funções nativas do Python. Exemplo:

```py
cliente = "1"
numero_cliente = int(cliente)
print(type(numero_cliente)) # será printado o tipo int

```


### Escopo


Em Python existem dois tipos de escopos para variáveis: `escopo global` e `escopo local`. No escopo local, uma variável local (criada dentro de uma função) existe apenas dentro da função onde foi declarada. Assim, as variáveis locais são inicializadas a cada nova chamada à função e não é possível acessar seu valor fora da função onde ela foi declarada. Para que possamos interagir com variáveis locais, passamos parâmetros e retornamos valores nas funções. No escopo global, uma variável global é declarada fora das funções e pode ser acessada por todas as funções presentes no módulo onde é definida e também podem ser acessadas por outros módulos, caso eles importem o módulo onde a variável foi definida. Exemplo:

```py
variavel_global = "Eu sou Variavel Global"
def escreve():
    variavel_local = "Eu sou Variavel Local"
    print(variavel_global)
    print(variavel_local)

print("Executando a função escreve texto:") 

escreve()

print("Tentando acessar as variáveis diretamente:")
print(variavel_global)
print(variavel_local)

```

```

------------------ OUTPUT ------------------


Executando a função escreve texto:
Eu sou Variavel Global
Eu sou Variavel Local
Tentando acessar as variáveis diretamente:
Eu sou Variavel Global
Traceback (most recent call last):
  File "main.py", line 13, in <module>
    print(variavel_local)
NameError: name 'variavel_local' is not defined

```

Outra característica interessante de escopo sobre Python é a possibilidade de alterar as variáveis globais. Se tentarmos alterar o valor de uma variável global dentro de uma função, será criada na verdade uma nova variável local com o mesmo nome da global definida fora da função. Exemplo:

```py
variavel_global = "Eu sou Variavel Global"
def escreve():
    variavel_local = "Eu sou Variavel Local"
    variavel_global = "Eu sou uma alteração na Variavel Global"
    print(variavel_global)
    print(variavel_local)

print("Executando a função escreve texto:") 

escreve()

print("Tentando acessar as variáveis diretamente:")
print(variavel_global)
print(variavel_local)

```

```

------------------ OUTPUT ------------------

Executando a função escreve texto:
Eu sou uma alteração na Variavel Global
Eu sou Variavel Local
Tentando acessar as variáveis diretamente:
Eu sou Variavel Global
Traceback (most recent call last):
  File "main.py", line 14, in <module>
    print(variavel_local)
NameError: name 'variavel_local' is not defined

```

Para de fato fazer uma alteração no valor de uma variável global é preciso fazer uma declaração global ao declarar a variável e fazer isso antes de incializar ela. Exemplo:

```py
def escreve():
	global variavel_global
	variavel_local = "Eu sou Variavel Local"
	variavel_global = "Eu sou uma alteração na Variavel Global"
	print(variavel_global)
	print(variavel_local)

print("Executando a função escreve texto:") 

escreve()

print("Tentando acessar as variáveis diretamente:")
print(variavel_global)

```

```

------------------ OUTPUT ------------------

Executando a função escreve texto:
Eu sou uma alteração na Variavel Global
Eu sou Variavel Local
Tentando acessar as variáveis diretamente:
Eu sou uma alteração na Variavel Global

```


### Vinculação

Python é uma linguagem de vinculação dinâmica: em tempo de execução a tipagem de uma variável na linguagem será definida com base no valor o qual foi utilizado. 
Exemplo:

```py

nome = "Renata"
print(nome) #será printado "Renata"
profissao = ", estudante de computação"
print(nome + profissao)  #será printado "Renata, estudante de computação"
print(type(profissao)) #será printado que o tipo da variável profissão é str (string)
profissao = 20
print(type(profissao)) #será printado que o tipo da variável profissão é int (inteiro)

```

## Tempo de Vida


Python usa duas estratégias para alocação de memória: `contagem de referência` e `coleta de lixo`.

Antes do Python versão 2.0, o interpretador Python usava apenas contagem de referência para gerenciamento de memória. A contagem de referência funciona contando o número de vezes que um objeto é referenciado por outros objetos no sistema. Quando as referências a um objeto são removidas, a contagem de referência para um objeto é diminuída. Quando a contagem de referência torna-se zero, o objeto é desalocado.

O problema é que contagens de referência exigem trabalho computacional para serem descobertos e a coleta de lixo deve ser uma atividade planejada. O Python programa a coleta de lixo com base em um limite de alocações e desalocações de objetos. Quando o número de alocações menos o número de desalocações é maior que o número limite, o coletor de lixo é executado. Geralmente o número limite padrão é de 700 alocações. É possível inspecionar o limite de novos objetos (objetos em Python conhecidos como objetos da geração 0) importando o módulo gc e solicitando os limites de coleta de lixo:

```py

import gc 
print("Limite de coleta de lixo: ", gc.get_threshold()) 

```

Também é possível chamar o coletor de lixo manualmente durante a execução de um programa. Existem duas maneiras de realizar a coleta de lixo manual: coleta de lixo baseada em tempo e baseada em eventos. Na coleta de lixo baseada em tempo, o coletor é chamado após um intervalo de tempo fixo e a coleta de lixo baseada em eventos chama o coletor de lixo na ocorrência do evento.

## Para saber mais


O objetivo desse tutorial é elucidar alguns conceitos sobre linguagens no geral como Tempo de Vida, Vinculação, etc. voltado para a linguagem Python. Assim, foram ocultados outros aspectos mais comuns das linguagens de propósito geral como estruturas de controle e repetição, operadores aritméticos e lógicos, etc. Esses conceitos apesar de importantes não se diferenciam tanto de uma linguagem de alto nível e propósito geral para outra. Para saber mais sobre esses conceitos, [clique aqui](https://devdocs.io/python~3.10/) ou [aqui](https://docs.python.org/3.10/reference/index.html#reference-index).


## Referências 

+ [Python e R: variáveis e tipos das linguagens](https://blog.grancursosonline.com.br/python-e-r-variaveis-e-tipos-das-linguagens/)

+ [O que é Python e o que pode dar errado](https://www.caelum.com.br/apostila-python-orientacao-a-objetos/o-que-e-python#o-que-pode-dar-errado)

+ [Tipos de Variáveis no Python](https://pythonacademy.com.br/blog/tipos-de-variaveis-no-python)

+ [Funções em Python: escopo de variáveis](http://www.bosontreinamentos.com.br/programacao-em-python/funcoes-em-python-escopos-de-variaveis/)

+ [Coleta de Lixo em Python](https://acervolima.com/coleta-de-lixo-em-python/)