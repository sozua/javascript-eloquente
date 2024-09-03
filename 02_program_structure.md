# Estrutura do programa

{{quote {author: "_why", title: "Why's (Poignant) Guide to Ruby", chapter: true}

E meu coração brilha vermelho vivo sob minha pele fina e translúcida e eles têm que administrar 10cc de JavaScript para me trazer de volta. (Eu respondo bem a toxinas no sangue.) Cara, essa coisa vai tirar qualquer brilho que você tenha!

quote}}

{{figure {url: "img/chapter_picture_2.jpg", alt: "Ilustração exibindo um número de tentáculos segurando peças de xadrez", chapter: framed}}}

Neste capítulo, começaremos a fazer coisas que podem realmente ser chamadas de _programação_. Vamos expandir nosso domínio da linguagem JavaScript além dos substantivos e fragmentos de frases que vimos até agora, chegando ao ponto em que podemos expressar prosa significativa.

## Expressões e declarações

No [Capítulo ?](values), criamos valores e aplicamos operadores a eles para obter novos valores. Criar valores dessa forma é a principal substância de qualquer programa JavaScript. Mas essa substância precisa ser enquadrada em uma estrutura maior para ser útil. É isso que vamos abordar neste capítulo.

Um fragmento de código que produz um valor é chamado de _expressão_. Todo valor que é escrito literalmente (como `22` ou `"psicanálise"`) é uma expressão. Uma expressão entre parênteses também é uma expressão, assim como um operador binário aplicado a duas expressões ou um operador unário aplicado a uma.

Isso mostra parte da beleza de uma interface baseada em linguagem. As expressões podem conter outras expressões de uma maneira semelhante a como subfrases em linguagens humanas são aninhadas - uma subfrase pode conter suas próprias subfrases, e assim por diante. Isso nos permite construir expressões que descrevem computações arbitrariamente complexas.

Se uma expressão corresponde a um fragmento de frase, uma _declaração_ JavaScript corresponde a uma frase completa. Um programa é uma lista de declarações.

O tipo mais simples de declaração é uma expressão com um ponto e vírgula depois dela. Este é um programa:

```
1;
!false;
```

Um programa inútil, no entanto. Uma expressão pode servir apenas para produzir um valor, que pode então ser usado pelo código que a envolve. No entanto, uma declaração pode existir por si só, então se ela não afetar nada, é inútil. Ela pode exibir algo na tela ou pode mudar o estado interno da máquina de uma maneira que afetará as declarações que vêm depois dela. Essas mudanças são chamadas de _efeitos colaterais_. As declarações no exemplo anterior apenas produzem os valores `1` e `true` e então os descartam imediatamente. Isso não afeta nenhuma outra declaração. Quando você executa este programa, nada observável acontece.

Em alguns casos, o JavaScript permite que você omita o ponto e vírgula no final de uma declaração. Em outros casos, ele deve estar lá, ou a próxima linha será tratada como parte da mesma declaração. As regras para quando ele pode ser omitido com segurança são um tanto complexas e propensas a erros. Então neste livro, toda declaração que precisa de um ponto e vírgula sempre terá um. Eu recomendo que você faça o mesmo, pelo menos até que tenha aprendido mais sobre as sutilezas de ponto e vírgulas ausentes.

## Variáveis

Como um programa mantém um estado interno? Como ele se lembra das coisas? Vimos como produzir novos valores a partir de valores antigos, mas isso não altera os valores antigos, e o novo valor deve ser usado imediatamente ou se dissipará novamente. Para capturar e manter valores, o JavaScript fornece algo chamado _variável_.

```
let capturado = 5 * 5;
```

Isso nos dá um segundo tipo de declaração. A palavra especial (palavra-chave) `let` indica que esta frase vai definir uma variável. É seguida pelo nome da variável e, se quisermos dar-lhe imediatamente um valor, por um operador `=` e uma expressão.

A declaração acima cria uma variável chamada `capturado` e a usa para capturar o número que é produzido multiplicando 5 por 5.

Depois que uma variável foi definida, seu nome pode ser usado como uma expressão. O valor de tal expressão é o valor que a variável mantém atualmente. Aqui está um exemplo:

```
let dez = 10;
console.log(dez * dez);
// → 100
```

Quando uma variável aponta para um valor, isso não significa que está ligada a esse valor para sempre. O operador `=` pode ser usado a qualquer momento em variáveis existentes para desconectá-las de seu valor atual e fazê-las apontar para um novo:

```
let tema = "claro";
console.log(tema);
// → claro
tema = "escuro";
console.log(tema);
// → escuro
```

Você deve imaginar as variáveis como tentáculos, em vez de caixas. Elas não _contêm_ valores; elas os _capturam_ - duas variáveis podem se referir ao mesmo valor. Um programa pode acessar apenas os valores aos quais ainda tem uma referência. Quando você precisa lembrar de algo, você cria um tentáculo para segurá-lo ou reconecta um de seus tentáculos existentes a ele.

Vamos olhar outro exemplo. Para lembrar o número de dólares que Luigi ainda lhe deve, você cria uma variável. Quando ele paga $35, você dá a essa variável um novo valor.

```
let dividaDeLuigi = 140;
dividaDeLuigi = dividaDeLuigi - 35;
console.log(dividaDeLuigi);
// → 105
```

Quando você define uma variável sem dar a ela um valor, o tentáculo não tem nada para agarrar, então termina no ar vazio. Se você pedir o valor de uma variável vazia, você obterá o valor `undefined`.

Uma única declaração `let` pode definir múltiplas variáveis. As definições devem ser separadas por vírgulas:

```
let um = 1, dois = 2;
console.log(um + dois);
// → 3
```

As palavras `var` e `const` também podem ser usadas para criar variáveis, de maneira similar a `let`.

```
var nome = "Ayda";
const saudacao = "Olá ";
console.log(saudacao + nome);
// → Hello Ayda
```

A primeira delas, `var` (abreviação de "variável"), era a forma como as variáveis eram declaradas no JavaScript pré-2015, quando `let` ainda não existia. Voltarei à maneira precisa como ela difere de `let` no [próximo capítulo](functions). Por enquanto, lembre-se de que ela faz basicamente a mesma coisa, mas raramente a usaremos neste livro porque se comporta de maneira estranha em algumas situações.

A palavra `const` significa _constante_. Ela define uma variável constante, que aponta para o mesmo valor enquanto existir. Isso é útil para variáveis que dão um nome a um valor para que você possa se referir a ele facilmente mais tarde.

## Nomes de variáveis

Os nomes de variáveis podem ser qualquer palavra. Dígitos podem fazer parte de nomes de variáveis - `captura22` é um nome válido, por exemplo - mas o nome não deve começar com um dígito. Um nome de variável pode incluir cifrões (`$`) ou sublinhados (`_`) mas nenhuma outra pontuação ou caracteres especiais.

Palavras com um significado especial, como `let`, são _palavras-chave_, e não podem ser usadas como nomes de variáveis. Há também uma série de palavras que são "reservadas para uso" em versões futuras do JavaScript, que também não podem ser usadas como nomes de variáveis. A lista completa de palavras-chave e palavras reservadas é bastante longa:

```{lang: "null"}
break case catch class const continue debugger default
delete do else enum export extends false finally for
function if implements import interface in instanceof let
new package private protected public return static super
switch this throw true try typeof var void while with yield
```

Não se preocupe em memorizar esta lista. Quando a criação de uma variável produzir um erro de sintaxe inesperado, verifique se você está tentando definir uma palavra reservada.

## O ambiente

A coleção de variáveis e seus valores que existem em um dado momento é chamada de _ambiente_. Quando um programa inicia, este ambiente não está vazio. Ele sempre contém variáveis que fazem parte do padrão da linguagem, e na maioria das vezes, também tem variáveis que fornecem maneiras de interagir com o sistema ao redor. Por exemplo, em um navegador, existem funções para interagir com o site atualmente carregado e para ler entradas do mouse e do teclado.

## Funções

Muitos dos valores fornecidos no ambiente padrão são do tipo _função_. Uma função é um pedaço de programa envolvido em um valor. Tais valores podem ser _aplicados_ para executar o programa envolvido. Por exemplo, em um ambiente de navegador, a variável `prompt` contém uma função que mostra uma pequena caixa de diálogo pedindo uma entrada do usuário. Ela é usada assim:

```
prompt("Enter passcode");
```

{{figure {url: "img/prompt.png", alt: "Uma caixa de diálogo com a mensagem 'enter passcode'", width: "8cm"}}}

Executar uma função é chamado de _invocar_, _chamar_ ou _aplicar_ ela. Você pode chamar uma função colocando parênteses após uma expressão que produza um valor de função. Geralmente você usará diretamente o nome da variável que contém a função. Os valores entre parênteses são dados ao programa dentro da função. No exemplo, a função `prompt` usa a string que fornecemos como o texto a ser mostrado na caixa de diálogo. Valores dados a funções são chamados de _argumentos_. Diferentes funções podem precisar de um número diferente ou de tipos diferentes de argumentos.

A função `prompt` não é muito usada na programação web moderna, principalmente porque você não tem controle sobre a aparência da caixa de diálogo resultante, mas pode ser útil em programas e experimentos simples.

## A função console.log

Nos exemplos, usei `console.log` para exibir valores. A maioria dos sistemas JavaScript (incluindo todos os navegadores modernos e Node.js) fornecem uma função `console.log` que escreve seus argumentos em _algum_ dispositivo de saída de texto. Nos navegadores, a saída vai para o console JavaScript. Esta parte da interface do navegador está oculta por padrão, mas a maioria dos navegadores a abre quando você pressiona F12 ou, em um Mac, [command]{keyname}-[option]{keyname}-I. Se isso não funcionar, procure através dos menus por um item chamado Developer Tools ou similar.

{{if interactive

Ao executar os exemplos (ou seu próprio código) nas páginas deste livro, a saída de `console.log` será mostrada após o exemplo, em vez de no console JavaScript do navegador.

```
let x = 30;
console.log("o valor de x é", x);
// → o valor de x é 30
```

if}}

Embora os nomes de variáveis não possam conter pontos, `console.log` tem um. Isso porque `console.log` não é uma simples variável, mas na verdade uma expressão que recupera a propriedade `log` do valor mantido pela variável `console`. Descobriremos exatamente o que isso significa no [Capítulo ?](data#properties).

## Valores de retorno

Mostrar uma caixa de diálogo ou escrever texto na tela é um _efeito colateral_. Muitas funções são úteis por causa dos efeitos colaterais que produzem. As funções também podem produzir valores, nesse caso, elas não precisam ter um efeito colateral para serem úteis. Por exemplo, a função `Math.max` recebe qualquer quantidade de argumentos numéricos e retorna o maior.

```
console.log(Math.max(2, 4));
// → 4
```

Quando uma função produz um valor, diz-se que ela _retorna_ esse valor. Qualquer coisa que produza um valor é uma expressão em JavaScript, o que significa que chamadas de função podem ser usadas dentro de expressões maiores. No código a seguir, uma chamada para `Math.min`, que é o oposto de `Math.max`, é usada como parte de uma expressão de adição:

```
console.log(Math.min(2, 4) + 100);
// → 102
```

O [Capítulo ?](functions) explicará como escrever suas próprias funções.

## Fluxo de controle

Quando seu programa contém mais de uma declaração, as declarações são executadas como se fossem uma história, de cima para baixo. Este programa de exemplo tem duas declarações. A primeira pergunta ao usuário por um número, e a segunda, que é executada depois da primeira, mostra o quadrado desse número:

```
let oNumero = Number(prompt("Escolha um número"));
console.log("Seu número ao quadrado é " +
            oNumero * oNumero);
```

A função `Number` converte um valor para um número. Precisamos dessa conversão porque o resultado de `prompt` é um valor de string, e queremos um número. Existem funções similares chamadas `String` e `Boolean` que convertem valores para esses tipos.

Aqui está a representação esquemática bastante trivial do fluxo de controle em linha reta:

{{figure {url: "img/controlflow-straight.svg", alt: "Diagrama mostrando uma seta reta", width: "4cm"}}}

## Execução condicional

Nem todos os programas são estradas retas. Podemos, por exemplo, querer criar um caminho ramificado, onde o programa toma o ramo adequado com base na situação em questão. Isso é chamado de _execução condicional_.

{{figure {url: "img/controlflow-if.svg", alt: "Diagrama mostrando uma seta que se divide em duas e depois se junta novamente",width: "4cm"}}}

A execução condicional é criada em JavaScript com a palavra-chave `if`. No caso mais simples, queremos que algum código seja executado se, e somente se, uma certa condição for verdadeira. Podemos, por exemplo, querer mostrar o quadrado da entrada apenas se ela for realmente um número:

```{test: wrap}
let oNumero = Number(prompt("Escolha um número"));
if (!Number.isNaN(oNumero)) {
  console.log("O quadrado do seu número é: " +
              theNumber * theNumber);
}
```

Com essa modificação, se você inserir "papagaio", nenhuma saída será mostrada.

A palavra-chave `if` executa ou pula uma declaração dependendo do valor de uma expressão booleana. A expressão decisiva é escrita após a palavra-chave, entre parênteses, seguida pela declaração a ser executada.

A função `Number.isNaN` é uma função padrão do JavaScript que retorna `true` apenas se o argumento que lhe é dado for `NaN`. A função `Number` retorna `NaN` quando você lhe dá uma string que não representa um número válido. Assim, a condição se traduz para "a menos que `oNumero` não seja um número, faça isto".

A declaração após o `if` está envolvida em chaves (`{` e `}`) neste exemplo. As chaves podem ser usadas para agrupar qualquer número de declarações em uma única declaração, chamada de _bloco_. Você também poderia tê-las omitido neste caso, já que elas contêm apenas uma única declaração, mas para evitar ter que pensar sobre quando elas são necessárias, a maioria dos programadores JavaScript as usa em toda declaração envolvida como esta. Seguiremos principalmente essa convenção neste livro, exceto por algumas linhas de código curtas.

```
if (1 + 1 == 2) console.log("É verdade");
// → É verdade
```

Muitas vezes você não terá apenas código que executa quando uma condição é verdadeira, mas também código que lida com o outro caso. Este caminho alternativo é representado pela segunda seta no diagrama. Você pode usar a palavra-chave `else`, junto com `if`, para criar dois caminhos de execução separados e alternativos:

```{test: wrap}
let oNumero = Number(prompt("Escolha um número"));
if (!Number.isNaN(oNumero)) {
  console.log("O quadrado do seu número é: " +
              oNumero * oNumero);
} else {
  console.log("Ei. Por que você não me deu um número?");
}
```

Se você tiver mais de dois caminhos para escolher, você pode "encadear" múltiplos pares `if`/`else` juntos. Aqui está um exemplo:

```
let num = Number(prompt("Escolha um número"));

if (num < 10) {
  console.log("Pequeno");
} else if (num < 100) {
  console.log("Médio");
} else {
  console.log("Grande");
}
```

O programa primeiro verificará se `num` é menor que 10. Se for, ele escolhe esse ramo, mostra "Pequeno" e termina. Se não for, ele toma o ramo `else`, que contém um segundo `if`. Se a segunda condição (< 100) for verdadeira, significa que o número está entre 10 e 100, e "Médio" é mostrado. Se não for, o segundo e último ramo `else` é escolhido.

O esquema para este programa se parece com algo assim:

{{figure {url: "img/controlflow-nested-if.svg", alt: "Diagrama mostrando uma seta que se divide em duas, com um dos ramos se dividindo novamente, antes de todos os ramos se juntarem novamente", width: "4cm"}}}

## Loops while e do

Considere um programa que imprime todos os números pares de 0 a 12. Uma maneira de escrever isso é assim:

```
console.log(0);
console.log(2);
console.log(4);
console.log(6);
console.log(8);
console.log(10);
console.log(12);
```

Isso funciona, mas a ideia de escrever um programa é fazer algo _menos_ trabalhoso, não mais. Se precisássemos de todos os números pares menores que 1.000, essa abordagem seria inviável. O que precisamos é de uma maneira de executar um pedaço de código várias vezes. Essa forma de fluxo de controle é chamada de _loop_.

{{figure {url: "img/controlflow-loop.svg", alt: "Diagrama mostrando uma seta para um ponto que tem uma seta cíclica voltando para si mesmo e outra seta indo adiante", width: "4cm"}}}

O fluxo de controle em loop nos permite voltar a algum ponto no programa onde estávamos antes e repeti-lo com nosso estado de programa atual. Se combinarmos isso com uma variável que conta números, podemos fazer algo assim:

```
let numero = 0;
while (numero <= 12) {
  console.log(numero);
  numero = numero + 2;
}
// → 0
// → 2
//   … etcetera
```

Uma declaração começando com a palavra-chave `while` cria um loop. A palavra `while` é seguida por uma expressão entre parênteses e então uma declaração, muito parecido com `if`. O loop continua entrando nessa declaração enquanto a expressão produzir um valor que dê `true` quando convertido para booleano.

A variável `numero` demonstra a maneira como uma variável pode acompanhar o progresso de um programa. Cada vez que o loop se repete, `numero` recebe um valor que é 2 a mais que seu valor anterior. No início de cada repetição, ele é comparado com o número 12 para decidir se o trabalho do programa está terminado.

Como um exemplo que realmente faz algo útil, podemos agora escrever um programa que calcula e mostra o valor de 2^10^ (2 elevado à 10ª potência). Usamos duas variáveis: uma para manter o controle de nosso resultado e uma para contar quantas vezes multiplicamos este resultado por 2. O loop testa se a segunda variável já chegou a 10 e, se não, atualiza ambas as variáveis.

```
let resultado = 1;
let contador = 0;
while (contador < 10) {
  resultado = resultado * 2;
  contador = contador + 1;
}
console.log(resultado);
// → 1024
```

O contador poderia também ter começado em `1` e verificado por `<= 10`, mas por razões que se tornarão aparentes no [Capítulo ?](data#array_indexing), é uma boa ideia se acostumar a contar a partir de 0.

Note que o JavaScript também tem um operador para exponenciação (`2 ** 10`), que você usaria para calcular isso em código real — mas isso teria arruinado o exemplo.

Um loop `do` é uma estrutura de controle similar a um loop `while`. Ele difere apenas em um ponto: um loop `do` sempre executa seu corpo pelo menos uma vez, e começa a testar se deve parar apenas após essa primeira execução. Para refletir isso, o teste aparece após o corpo do loop:

```
let seuNome;
do {
  seuNome = prompt("Quem é você?");
} while (!seuNome);
console.log("Olá " + seuNome);
```

Este programa forçará você a inserir um nome. Ele perguntará repetidamente até obter algo que não seja uma string vazia. Aplicar o operador `!` converterá um valor para o tipo booleano antes de negá-lo, e todas as strings exceto `""` convertem para `true`. Isso significa que o loop continua girando até que você forneça um nome não vazio.

## Indentando Código

Nos exemplos, tenho adicionado espaços antes das declarações que fazem parte de alguma declaração maior. Esses espaços não são necessários — o computador aceitará o programa muito bem sem eles. De fato, até mesmo as quebras de linha nos programas são opcionais. Você poderia escrever um programa como uma única linha longa se quisesse.

O papel desta indentação dentro dos blocos é fazer com que a estrutura do código se destaque para leitores humanos. Em código onde novos blocos são abertos dentro de outros blocos, pode se tornar difícil ver onde um bloco termina e outro começa. Com a indentação adequada, a forma visual de um programa corresponde à forma dos blocos dentro dele. Eu gosto de usar dois espaços para cada bloco aberto, mas os gostos diferem — algumas pessoas usam quatro espaços, e algumas pessoas usam caracteres de tabulação. O importante é que cada novo bloco adicione a mesma quantidade de espaço.

```
if (false != true) {
  console.log("Isso faz sentido.");
  if (1 < 2) {
    console.log("Nenhuma surpresa aqui.");
  }
}
```

A maioria dos programas editores de código (incluindo o deste livro) ajudará indentando automaticamente as novas linhas na quantidade apropriada.

## Loops for

Muitos loops seguem o padrão mostrado nos exemplos `while`. Primeiro uma variável "contadora" é criada para acompanhar o progresso do loop. Então vem um loop `while`, geralmente com uma expressão de teste que verifica se o contador atingiu seu valor final. No final do corpo do loop, o contador é atualizado para acompanhar o progresso.

Como esse padrão é tão comum, JavaScript e linguagens similares fornecem uma forma um pouco mais curta e mais abrangente, o loop `for`:
```
for (let numero = 0; numero <= 12; numero = numero + 2) {
  console.log(numero);
}
// → 0
// → 2
//   … etcetera
```

Este programa é exatamente equivalente ao exemplo [anterior](program_structure#loops) de impressão de números pares. A única mudança é que todas as declarações que estão relacionadas ao "estado" do loop estão agrupadas depois de `for`.

Os parênteses após uma palavra-chave `for` devem conter dois pontos e vírgulas. A parte antes do primeiro ponto e vírgula _inicializa_ o loop, geralmente definindo uma variável. A segunda parte é a expressão que _verifica_ se o loop deve continuar. A parte final _atualiza_ o estado do loop após cada iteração. Na maioria dos casos, isso é mais curto e mais claro do que uma construção `while`.

Este é o código que calcula 2^10^ usando `for` em vez de `while`:

```{test: wrap}
let resultado = 1;
for (let contador = 0; contador < 10; contador = contador + 1) {
  resultado = resultado * 2;
}
console.log(resultado);
// → 1024
```

## Saindo de um Loop

Ter a condição do loop produzir `false` não é a única maneira de um loop terminar. Existe uma declaração especial chamada `break` que tem o efeito de imediatamente pular para fora do loop envolvente.

Este programa ilustra o uso da declaração `break`. Ele encontra o primeiro número que é tanto maior ou igual a 20 quanto divisível por 7.

```
for (let atual = 20; ; atual = atual + 1) {
  if (atual % 7 == 0) {
    console.log(atual);
    break;
  }
}
// → 21
```

Usar o operador resto (`%`) é uma maneira fácil de testar se um número é divisível por outro número. Se for, o resto da divisão deles é zero.

A construção `for` neste exemplo não tem uma parte que verifica o fim do loop. Isso significa que o loop nunca parará a menos que a declaração `break` dentro dele seja executada.

Se você remover essa declaração `break` ou acidentalmente escrever uma condição que sempre produza `true`, seu programa ficará preso em um _loop infinito_. Um programa preso em um loop infinito nunca terminará de rodar, o que geralmente é uma coisa ruim.

{{if interactive

Se você criar um loop infinito em um dos exemplos nestas páginas, geralmente será perguntado se você quer parar o script após alguns segundos. Se isso falhar, você terá que fechar a aba em questão para recuperar.

if}}

A palavra-chave `continue` é similar ao `break`, no sentido de que influencia o progresso de um loop. Quando `continue` é encontrado no corpo de um loop, o controle pula para fora do corpo e continua com a próxima iteração do loop.

## Atualizando variáveis sucintamente

Especialmente ao fazer loops, um programa frequentemente precisa "atualizar" uma variável para manter um valor baseado no valor anterior dessa variável.

```{test: no}
contador = contador + 1;
```

JavaScript fornece um atalho para isso:

```{test: no}
contador += 1;
```

Atalhos similares funcionam para muitos outros operadores, como `resultado *= 2` para dobrar `resultado` ou `contador -= 1` para contar para trás.

Isso nos permite encurtar nosso exemplo de contagem um pouco mais:

```
for (let numero = 0; numero <= 12; numero += 2) {
  console.log(numero);
}
```

Para `contador += 1` e `contador -= 1`, existem equivalentes ainda mais curtos: `contador++` e `contador--`.

## Desencadeando com base em um valor usando `switch`

Não é incomum que o código se pareça com isto:

```{test: no}
if (x == "valor1") acao1();
else if (x == "valor2") acao2();
else if (x == "valor3") acao3();
else acaoPadrao();
```

Existe uma construção chamada `switch` que é destinada a expressar tal "desencadeamento" de uma maneira mais direta. Infelizmente, a sintaxe que JavaScript usa para isso (que herdou da linha de linguagens de programação C/Java) é um pouco estranha — uma cadeia de declarações `if` pode parecer melhor. Aqui está um exemplo:

```
switch (prompt("Como está o tempo?")) {
  case "chuvoso":
    console.log("Lembre-se de levar um guarda-chuva.");
    break;
  case "ensolarado":
    console.log("Vista-se com roupas leves.");
  case "nublado":
    console.log("Vai dar um passeio.");
    break;
  default:
    console.log("Tipo de tempo desconhecido!");
    break;
}
```

Você pode colocar qualquer número de rótulos `case` dentro do bloco aberto por `switch`. O programa começará a ser executado a partir do rótulo que corresponde ao valor fornecido ao `switch`, ou em `default` se nenhum valor correspondente for encontrado. Ele continuará executando, mesmo através de outros rótulos, até encontrar uma declaração `break`. Em alguns casos, como no caso `"ensolarado"` no exemplo, isso pode ser usado para compartilhar algum código entre casos (ele recomenda ir lá fora tanto para tempo ensolarado quanto nublado). Mas cuidado — é fácil esquecer tal `break`, o que fará com que o programa execute código que você não quer que seja executado.

## Capitalização

Nomes de variáveis não podem conter espaços, mas muitas vezes é útil usar várias palavras para descrever claramente o que a variável representa. Estas são basicamente suas escolhas para escrever um nome de variável com várias palavras nele:

```{lang: null}
tartarugapeluda
tartaruga_peluda
TartarugaPeluda
tartarugaPeluda
fuzzylittleturtle
fuzzy_little_turtle
FuzzyLittleTurtle
fuzzyLittleTurtle
```

O primeiro estilo pode ser difícil de ler. Eu gosto bastante da aparência dos sublinhados, embora esse estilo seja um pouco doloroso de digitar. As funções padrão do JavaScript, e a maioria dos programadores JavaScript, seguem o último estilo — eles capitalizam toda palavra, exceto a primeira. Não é difícil se acostumar com pequenas coisas como essa, e código com estilos de nomenclatura mistos pode ser irritante de ler, então seguimos esta convenção.

Em alguns casos, como na função `Number`, a primeira letra de uma variável também é capitalizada. Isso foi feito para marcar esta função como um construtor. O que é um construtor ficará claro no [Capítulo ?](object#constructors). Por enquanto, o importante é não se incomodar com esta - aparente - falta de consistência.

## Comentários

Frequentemente, o código bruto não transmite todas as informações que você quer que um programa transmita aos leitores humanos, ou ele transmite de uma maneira tão confusa que as pessoas podem não entender. Em outros momentos, você pode simplesmente querer incluir alguns pensamentos relacionados como parte do seu programa. É para isso que servem os _comentários_.

Um comentário é um pedaço de texto que faz parte de um programa, mas é completamente ignorado pelo computador. JavaScript tem duas maneiras de escrever comentários. Para escrever um comentário de uma linha, você pode usar dois caracteres de barra (`//`) e então o texto do comentário após ele:

```{test: no}
let saldoDaConta = calcularSaldo(conta);
// É um vale verde onde um rio canta
saldoDaConta.ajustar();
// Pegando loucamente farrapos brancos na grama.
let relatorio = new Relatorio();
// Onde o sol no orgulhoso monte ressoa:
adicionarAoRelatorio(saldoDaConta, relatorio);
// É um pequeno vale, espumando como luz em um copo.
```

Um comentário `//` vai apenas até o final da linha. Uma seção de texto entre `/*` e `*/` será ignorada inteiramente, independentemente de conter quebras de linha. Isso é útil para adicionar blocos de informação sobre um arquivo ou um pedaço de programa:

```
/*
  Eu encontrei este número pela primeira vez rabiscado no verso de um
  caderno velho. Desde então, ele tem aparecido frequentemente, surgindo
  em números de telefone e números de série de produtos que comprei.
  Obviamente ele gosta de mim, então decidi mantê-lo.
*/
const meuNumero = 11213;
```

## Resumo
Agora você sabe que um programa é construído a partir de declarações, que às vezes contêm mais declarações. Declarações tendem a conter expressões, que por sua vez podem ser construídas a partir de expressões menores.

Colocar declarações uma após a outra dá a você um programa que é executado de cima para baixo. Você pode introduzir perturbações no fluxo de controle usando declarações condicionais (`if`, `else` e `switch`) e loops (`while`, `do` e `for`).

variáveis podem ser usadas para arquivar pedaços de dados sob um nome, e são úteis para rastrear o estado em seu programa. O ambiente é o conjunto de variáveis que são definidas. Os sistemas JavaScript sempre colocam um número de variáveis padrão úteis em seu ambiente.

Funções são valores especiais que encapsulam um pedaço de programa. Você pode invocá-las escrevendo `nomeDaFuncao(argumento1, argumento2)`. Tal chamada de função é uma expressão e pode produzir um valor.

## Exercícios

Se você não tem certeza de como testar suas soluções para os exercícios, consulte a introdução.

Cada exercício começa com uma descrição do problema. Leia esta descrição e tente resolver o exercício. Se você encontrar problemas, considere ler as dicas após o exercício. Você pode encontrar soluções completas para os exercícios online em https://eloquentjavascript.net/code#2. Se você quer aprender algo com os exercícios, recomendo olhar as soluções somente depois de ter resolvido o exercício, ou pelo menos depois de ter trabalhado nele por tempo suficiente para ter uma leve dor de cabeça.

### Fazendo um triângulo com loop

Escreva um loop que faça sete chamadas a `console.log` para gerar o seguinte triângulo:

```{lang: null}
#
##
###
####
#####
######
#######
```

Uma maneira interessante para saber o comprimento de uma string é escrevendo .length após ela.

```
let abc = "abc";
console.log(abc.length);
// → 3
```

{{if interactive

A maioria dos exercícios contém um pedaço de código que pode ser utilizada para alterar e resolver o exercício. Lembre-se que você pode clicar em um bloco de código para editá-lo.

```
// Seu código aqui.
```
if}}

{{hint

Você pode começar com um programa que simplesmente imprime os números de 1 a 7, na qual você pode derivar algumas modificações no [exemplo de impressão de números dado no início do capítulo aqui](program_structure#loops), onde o loop `for` foi introduzido.

Agora, considere a equivalência entre números e cadeias em um hash de caracteres. Você pode ir de 1 para 2 adicionando 1 (+ = 1). Você pode ir de "#" para "##", adicionando um caractere (+ = "#"). Assim, a solução pode acompanhar de perto o número, de impressão do programa.

hint}}

### FizzBuzz

Escreva um programa que imprima usando `console.log()` todos os números de 1 a 100 com duas exceções. Para números divisíveis por 3, imprima `Fizz` ao invés do número, e para números divisíveis por 5 (e não 3), imprima `Buzz`.

Quando o programa estiver funcionando, modifique-o para imprimir `FizzBuzz` para números que são divisíveis ambos por 3 e 5 (e continue imprimindo `Fizz` e `Buzz` para números divisíveis por apenas um deles).

(Isto é na verdade uma pergunta de entrevista usada para eliminar uma porcentagem significativa de candidatos programadores. Então se você resolvê-la, você está autorizado de se sentir bem consigo mesmo).

{{if interactive
```
// Seu código aqui
```
if}}

{{hint

Interar sobre os números é trabalho claro de um loop, e selecionar o que imprimir é uma questão de execução condicional. Lembre-se do truque de usar o operador restante (%) para verificar se um número é divisível por outro número (terá zero de resto).

Na primeira versão, existem três resultados possíveis para cada número, então você irá criar uma cadeia de `if`/`else if`/`else`.

Na segunda versão o programa tem uma solução simples e uma inteligente. A maneira mais simples é adicionar um outro "ramo" para um teste preciso da condição dada. Para o método inteligente é construir uma sequência de caracteres contendo palavra ou palavras para a saída, que imprima a palavra ou o número, caso não haja palavra, fazendo o uso do operador elegante `||`.

hint}}

### Tabuleiro de xadrez

Escreva um programa que cria uma string que representa uma grade 8x8, usando novas linhas para separar os caracteres. A cada posição da grade existe um espaço ou um caractere "#". Esses caracteres formam um tabuleiro de xadrez.

Passando esta string para o console.log deve mostrar algo como isto:

```{lang: null}
 # # # #
# # # # 
 # # # #
# # # # 
 # # # #
# # # # 
 # # # #
# # # # 
```

Quando você tiver o programa que gere este padrão, defina a variável `tamanho = 8` e altere programa para que ele funcione para qualquer `tamanho`, a saída da grade de largura e altura.

{{if interactive
```
// Seu código aqui
```
if}}

{{hint

A sequência pode ser construída iniciando vazia (`""`) e repetidamente adicionando caracateres. O caracter para uma nova linha é escrito assim `\n`.

Utilize console.log para visualizar a saída do seu programa.

Para trabalhar com duas dimensões, você irá precisar de um loop dentro de outro loop. Coloque entre chaves os "corpos" dos loops para se tornar mais fácil de visualizar quando inicia e quando termina. Tente recuar adequadamente esses "corpos". A ordem dos loops deve seguir a ordem que usamos para construir a string (linha por linha, esquerda para direita, cima para baixo). Então o loop mais externo manipula as linhas e o loop interno manipula os caracteres por linha.

Você vai precisar de duas variáveis para acompanhar seu progresso. Para saber se coloca um espaço ou um `"#"` em uma determinada posição, você pode testar se a soma dos dois contadores ainda é divisível por (`% 2`).

Encerrando uma linha com um caracter de nova linha acontece após a linha de cima ser construída, faça isso após o loop interno, mas dentro do loop externo.

hint}}
