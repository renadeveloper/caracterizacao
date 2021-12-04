# Javascript


## Contexto Histórico


JavaScript é uma linguagem de programação, criada por Brendan Eich, a pedido da empresa Netscape, em meados de 1995. No início, o JavaScript foi batizado com outro nome: LiveScript. A empresa SUN Microsystems se interessou pela linguagem e participou do seu desenvolvimento. Com o sucesso inicial do JavaScript, a mudança do nome de LiveScript para JavaScript foi inevitável, e, com certeza, veio por influência da própria SUN, que mantinha a linguagem de programação Java. É bom salientar que Java e JavaScript são parecidas somente no nome já que se diferem no conceito e no uso.

Uma curiosidade sobre JavaScript é que, a princípio, a linguagem foi criada com o objetivo de validar formulários HTML e, na verdade, o JavaScript foi concebido para rodar no servidor. No entanto, com o passar do tempo isso foi modificado e, hoje, é uma linguagem Client-side.

O JavaScript na verdade se chama ECMAScript, o nome porém, foi mantido pela popularidade que já havia sido adquirida. Desde 2012, todos os navegadores modernos possuem suporte total ao ECMAScript 5.1. Navegadores mais antigos suportam pelo menos ECMAScript 3. Em 17 de Junho de 2015, a ECMA International publicou a sexta versão do ECMAScript, que é oficialmente chamado de ECMAScript 2015, e foi inicialmente conhecido como ECMAScript 6 ou ES6. Desde então, as especificações do ECMAScript são lançadas anualmente. Essa documentação faz referência à última versão de referência, que atualmente é a ECMAScript 2018. Com o advento do ES6 e com o advento de frameworks como ReactJS e VueJs, JavaScript se tornou uma das linguagens mais utilizadas no mundo todo [segundo a pesquisa de Popularidade do GitHub, realizada em 2021](https://pypl.github.io/PYPL.html).

Nesse guia serão abordados aspectos da versão ES6 da linguagem como base de referência.


## Principais Características


JavaScript não é uma linguagem fortemente tipada, ou seja, as variáveis declaradas podem intercambiar seus tipos a qualquer momento e assim receber valores de tipos de dados diferentes e fazer operações entre eles sem a necessidade de um conversão (casting) explícita do tipo. Exemplo:

```js
const doisBinario = '10';
const numeroDez = 10;
console.log(doisBinario + numeroDez);  // o resultado será a string 1010

```

JavaScript também é dinamicamente tipada, ou seja, é uma linguagem em que o tipo de uma variável pode ser alterado durante a execução do código.

JavaScript é uma linguagem interpretada. O navegador recebe o código JavaScript em sua forma de texto original e executa o script a partir dele. Do ponto de vista técnico, a maioria dos intérpretes modernos de JavaScript realmente usa uma técnica chamada compilação just-in-time para melhorar o desempenho; o código-fonte JavaScript é compilado em um formato binário mais rápido enquanto o script está sendo usado, para que possa ser executado o mais rápido possível. No entanto, o JavaScript ainda é considerado uma linguagem interpretada, pois a compilação é manipulada em tempo de execução, e não antes.

Java Script é uma linguagem orientada a objetos com funções de primeira classe, conhecida como a linguagem de scripting para páginas Web, mas também utilizada em muitos ambientes fora dos navegadores. Ela é uma linguagem de scripting baseada em protótipos.

JavaScript também é uma linguagem multiparadigma, suportando os estilos orientado a objetos, imperativo e funcional.


## Variáveis


JavaScript é uma linguagem case-sensitive, ou seja, sensível às letras maíusculas e minúsculas - na qual se você cria uma variável com nome `sobreNome`  esta é diferente de outra variável chamada `sobrenome` .

Não há limite para o comprimento do nome da variável em JavaScript.

As variáveis em JavaScript devem ser iniciadas com uma letra, um sublinhado (_) ou um cifrão. ser palavra-chave ou palavra reservada da linguagem e não podem conter espaços.

Palavras-chave reservadas do JavaScript não podem ser usadas como nome de variável (Exemplo: if, else, switch, while, for, etc.)


## Tipos de Dados


Os tipos de dados de uma variável Javascript podem ser:

- String: quase qualquer valor entre aspas simples ou aspas duplas;
- Numérico: números, com ou sem pontos flutuantes;
- Booleano: true (verdadeiro) ou false (falso);
- Null e undefined: representando variáveis que não têm um valor ou estão incompletas; 
- Objeto: um valor de referência, ou seja, aponta para algum lugar específico na memória;
- Symbol: novo em ECMAScript 6, tipo de dado cuja as instâncias são únicas e imutáveis.

É possível verificar o tipo das variáveis com o operador unário `typeof`:

```js
var cliente = "Renata";
typeof cliente // será impresso string

```


## Escopo


Em JavaScript, toda variável é “elevada/içada” (hoisting) até o topo do seu contexto de execução. Esse mecanismo move as variáveis para o topo do seu escopo antes da execução do código.

No nosso exemplo acima, como a variável mensagemDentroDoIf está dentro de uma function, a declaração da mesma é elevada (hoisting) para o topo do seu contexto, ou seja, para o topo da function.

É por esse mesmo motivo que “é possível usar uma variável antes dela ter sido declarada”: em tempo de execução a variável será elevada (hoisting) e tudo funcionará corretamente.

Exemplo:

```js
var hello = function() { 
    mensagem = 'Oi, Renata'; 
    console.log(mensagem); 
    var mensagem;
}

hello();
```

É possível declarar variáveis em JavaScript utilizando as palavras reservadas de declaração `var` e `let`. No caso da palavra-chave `var`, além da variável ser içada (hoisting) ela é automaticamente inicializada com o valor undefined (caso não seja atribuído nenhum outro valor). No caso do `var` há a necessidade de ter que lidar com o escopo de função das variáveis declaradas (escopo abrangente) o que pode acarrentar em confusões no desenvolvimento. 

Pensando em trazer o escopo de bloco para o JavaScript, o ECMAScript 6 trouxe a palavra-chave `let`. Através da palavra-chave `let` podemos declarar variáveis com escopo de bloco. Quando tentamos acessar uma variável que foi declarada através da palavra-chave `let` fora do seu escopo, o erro Uncaught ReferenceError: escopoBloco is not defined foi apresentado.

Ainda é possível atribuir um valor à palavra-chave `const`, que não pode ser alterado por se tratar de uma palavra-chave para declaração de constantes. Apesar de o conceito de constantes e variáveis serem opostos, por definição, é possível utilizar constantes para ter um comportamento mais previsível de tipo no JavaScript já que o valor atribuído não será modificado. 

Resumindo:

- `const` possui escopo de função e escopo de bloco; `let` possui escopo de função, escopo de bloco mas pode ser iniciada como undefined; e `var` possui escopo de função e escopo global mas também pode ser inicializada como undefined;
- Variáveis declaradas com a palavra-chave `var` podem ser utilizadas mesmo antes de sua declaração;
- Variáveis criadas com `let` só podem ser utilizadas após sua declaração, pois, apesar de serem elevadas, elas não são inicializadas;
- É possível utilizar constantes por meio da palavra-chave `const` ou utilizar variáveis com escopo de bloco através da `let`.


## Vinculação


Javascript é uma linguagem de vinculação dinâmica: em tempo de execução a tipagem de uma variável na linguagem será definida com base no valor o qual foi utilizado. 
Exemplo:

```js

nome = "Renata"
console.log(nome) //será printado "Renata"
profissao = ", estudante de computação"
console.log(nome + profissao)  //será printado "Renata, estudante de computação"
profissao = 20
console.log(profissao) //será printado 20, o novo valor da variável profissao
profissao = 20
console.log(nome + profissao) //será printado "Renata20"

```


## Tempo de Vida


Quando o código JavaScript é executado, o processo de realmente fazer o código ser executado é gerenciado pelo ambiente de tempo de execução. No navegador Google Chrome ou Node.js, por exemplo, esse mecanismo é o V8 do Chrome. Como o V8 compila o código JavaScript em código de máquina, ele executa otimizações no código e considera a alocação de memória. Ele também gerencia separadamente a desalocação de memória, por meio de um processo automatizado conhecido como `coleta de lixo`.

JavaScript aloca memória automaticamente quando os valores são declarados inicialmente. O `coletor de lixo` monitora a alocação de memória e determina se as variáveis ​​ainda são necessárias, caso contrário, libera esse pedaço de memória. Não existe um algoritmo ou combinação de algoritmos que possa prever com total precisão quais variáveis ​​estão prontas para a coleta de lixo e, como tal, a questão de quando liberar memória é considerada um problema `indecidível`, ou seja, não pode ser resolvido por uma máquina de Turing.

Como não existe um método infalível para determinar quando a memória deve ser liberada, ocorre de variáveis ​​que não são mais necessárias para um programa não serem detectadas pelos algoritmos de coleta de lixo e permanecem na memória, processo chamado de `vazamentos de memória`, que é quando uma variável não é mais necessária em seu programa, mas ainda está presente na memória). Com vazamentos de memória suficientes, um programa poderia, em teoria, exceder a memória disponível e travar. Em linguagens de baixo nível, por exemplo, é possível gerenciar sua própria memória e o vazamento de memória também pode correr quando o/a programador/a esquece de liberar a memória.


## Para saber mais


O objetivo desse tutorial é elucidar alguns conceitos sobre linguagens no geral como Tempo de Vida, Vinculação, etc. voltado para a linguagem JavaScript. Assim, foram ocultados outros aspectos mais comuns das linguagens de propósito geral como estruturas de controle e repetição, operadores aritméticos e lógicos, etc. Esses conceitos apesar de importantes não se diferenciam tanto de uma linguagem de alto nível e propósito geral para outra. Para saber mais sobre esses conceitos, [clique aqui](https://devdocs.io/javascript/) ou [aqui](http://www.ecmascript.org/).

## Referências 

+ [Entenda a diferença entre var, let e const no JavaScript](https://www.alura.com.br/artigos/entenda-diferenca-entre-var-let-e-const-no-javascript?gclid=Cj0KCQiAnaeNBhCUARIsABEee8UIsmy39fYMcjhKhobZZHWQX6ijAokxw-JzzavJL-8hoKlS0xLlkv8aAqKAEALw_wcB )

+ [JavaScript, um breve histórico](https://www.cpt.com.br/cursos-informatica-desenvolvimentodesoftwares/artigos/linguagem-de-programacao-javascript-um-breve-historico)

+ [Aprenda JavaScript](https://developer.mozilla.org/pt-BR/docs/Learn/JavaScript)

+ [Operadpres em JavaScript](https://www.todoespacoonline.com/w/2014/04/operadores-em-javascript/)

+ [Ciclo de Vida da Memória em JavaScript](https://ichi.pro/pt/o-ciclo-de-vida-da-memoria-em-javascript-100450691317580)

