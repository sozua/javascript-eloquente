{{meta {docid: values}}}

# Valores, Tipos e Operadores

{{quote {author: "Master Yuan-Ma", title: "O Livro da Programação", chapter: true}

Abaixo da superfície de uma máquina, o programa se move. Sem esforço, ele se expande e se contrai. Em grande harmonia, elétrons se espalham e se reagrupam. As formas no monitor são apenas ondulações na água. A essência permanece invisível por baixo.

quote}}

{{figure {url: "img/chapter_picture_1.jpg", alt: "Illustration of a sea of dark and bright dots (bits) with islands in it", chapter: framed}}}

No mundo do computador, só existe dados. Você pode ler dados, modificar dados, criar novos dados — mas aqui que não é dado não pode ser mencionado. Todos esses dados são armazenados como longas sequências de bits, e portanto, são fundamentalmente semelhantes.

_Bits_ são qualquer tipo de coisa com dois valores, geralmente descritos como zeros e uns. Dentro do computador, eles assumem formas como uma carga elétrica alta ou baixa, um sinal forte ou fraco, ou um ponto brilhante ou opaco na superfície de um CD. Qualquer pedaço de informação discreta pode ser reduzido a uma sequência de zeros e uns e, assim, representado em bits.

Por exemplo, podemos expressar o número 13 em bits. Isso funciona da mesma forma que um número decimal, mas em vez de 10 dígitos, temos apenas 2, e o peso de cada um aumenta por um fator de 2 da direita para a esquerda. Aqui estão os bits que compõem o número 13, com os pesos dos dígitos mostrados abaixo deles:

```{lang: null}
   0   0   0   0   1   1   0   1
 128  64  32  16   8   4   2   1
```

Esse é o número binário 00001101. Seus dígitos diferentes de zero representam 8, 4 e 1, que somam 13.

## Valores

Imagine um mar de bits - um oceano deles. Um típico computador moderno tem mais de 100 bilhões de bits em seu armazenamento volátil de dados (*working memory*). Já em seu armazenamento não volátil (o disco rígido ou equivalente), tende a ter algumas ordens de magnitude maior.

Para permitir trabalhar com essa quantidade de bits sem ficar perdido, nós separamos eles em partes que representam pedaços de informações. No ambiente Javascript, nós chamamos essas partes de *valores*. Apesar de todos os valores serem feito de bits, eles possuem diferentes papeis. Cada valor tem um *tipo* que determina seu papel. Alguns valores são números, outros são pedaços de texto, outro são funções, etc.

Para criar um valor, você deve simplesmente invocar seu nome. É conveniente, você não precisa juntar materiais para construir seus valores ou pagar por eles. Você só pede por um, e num passe de mágica, você o tem. Claro que valores não são criados do nada. Cada um deles precisam ser armazenados em algum lugar, e se você quer usar uma quantidade gigantesca deles ao mesmo tempo, você pode acabar com a memória do computador. Felizmente, este é um problema somente no caso onde você precisa usar eles ao mesmo tempo. Assim que você não precisa usar eles como valores, eles se dissiparão, deixando para trás bits a serem reciclados como matéria-prima para a próxima leva de bits.

O restante deste capítulo introduz os elementos atômicos de programas Javascript, isto é, os tipos de valores e operadores mais simples que podem ser atuar nestes valores.

## Números

Valores do tipo *número* são, sem novidades, valores numéricos. Em um programa Javascript, eles são escritos desta forma:

```
13
```

Usando isto em um programa irá fazer um padrão de bits para que o número 13 venha à existência dentro da memória do computador.

Javascript usa um valor fixo de número de bits (64) para armazenar um único valor numérico. Existe um número limitado de padrões que você consegue fazer com 64 bits, o que limita a quantidade de números que podem ser representados. Com *N* dígitos decimais, você consegue representar 10^N números. Similarmente, dados 64 números binários, você consegue representar 2^64 números, o que é em torno de 18 quintilhões (o número 18 seguido de 18 zeros). É muita coisa.

A memória de computador costumava ser muito menor e, por isso, as pessoas tendiam a usar grupos de 8 ou 16 bits para representar os números. Era fácil para extrapolar (*overflow*) acidentalmente estes pequenos números — isto é, acabar tendo um número que não cabe dentro desta quantidade de bits. Hoje mesmo os computadores que cabem em seu bolso tem bastante memória, então sinta-se livre para usar pedaços de 64 bits, pois você só irá ter que se preocupar com a extrapolação de memória quando estiver lidando com números astronomicamente grandes. 

Dito isto, nem todos os números menores do que 18 quintilhões podem ser representados precisamente como um número em JavaScript. Esses bits também armazenam números negativos, então um dos bits indicam o sinal do número. Um grande problema é representar fracionários. Para fazer isto, alguns dos bits são usados para armazenar a posição do ponto decimal. O máximo que um número pode ser realmente armazenado está na região dos 9 quadrilhões (15 zeros), que ainda assim é bem grande. 

Números fracionários são escritos utilizando um ponto:

```
9.81
```

Para números muito grandes ou muito pequenos, você pode utilizar notação científica adicionando um *e* (de "expoente") seguido pelo expoente do número

```
2.998e8
```

Isto resulta em 2.998 x 10^8 = 299,800,000

Calculos com números inteiros menores que os 9 quadrilhões mencionados possuem uma garantia que sempre serão precisos. Infelizmente, cálculos com números fracionários nem sempre serão precisos. Assim como π (pi) não pode ser precisamente expresso por um número finito de dígitos decimais, muitos números perdem alguma precisão quando apenas 64 bits estão disponíveis para armazená-los. É uma pena, mas isto causa problemas em apenas alguns casos específicos. O importante é ficar atento à isto e tratar dígitos fracionados como aproximações, não valores precisos.

### Cálculos aritméticos

A principal coisa que fazemos com números são cálculos aritméticos. Operações aritméticas como adição ou multiplicação levam 2 valores numéricos e produzem um novo número a partir deles. Aqui é como eles se parecem em Javascript:

```{meta: "expr"}
100 + 4 * 11
```

Os símbolos + e * são chamados de _operadores_. O primeiro representa adição enquanto o segundo representa multiplicação. Ao colocar um operador entre dois valores, ele irá aplicá-lo a estes valores e produzir um novo valor.

Este exemplo significa "Adiciona 4 e 100, e multiplica o resultado por 11", ou a multiplicação é feita antes da adição? Como você deve imaginar, a multiplicação acontece primeiro. Assim como na matemática, você pode alterar isto colocando a adição entre parênteses.

```{meta: "expr"}
(100 + 4) * 11
```

Para subtração, existe o operador -. Já a divisão pode ser feita com o operador /.

Quando o operador aparece em sequência e sem parênteses, a ordem que irá ser aplicada é determinada pela precedência dos operadores. O exemplo mostrou que a multiplicação vem antes que a adição. O operador / tem a mesma precedência que o *. De forma parecida, + e - tem a mesma precedência. Quando múltiplos operadores com a mesma precedência aparecem próximos um ao outro, como em 1 - 2 + 1, eles são aplicados da esquerda para a direita: (1 - 2) + 1.

Não se preocupe muito com essas regras de precedência. Na dúvida, só adicione parênteses.

Existe mais um operador aritmético, que talvez você possa não reconhecer de cara. O símbolo % é usado para representar o operador de _resto_. X % Y é o resto da divisão entre X e Y. Por exemplo, 314 % 100 produz 14, enquanto 144 % 12 produz 0. A precedência do operador de resto é a mesma que a multiplicação e divisão. Você também pode ver este operador sendo chamado de _módulo_.

### Números especiais 

Existem 3 valores especiais no Javascript que são considerados números mas não se comportam como números normais. Os primeiros 2 são Infinity e -Infinity, que representam infinito positivo e negativo. Infinity - 1 continua sendo Infinity, e assim por diante. Apesar de tudo, não coloque muita confiança em cálculos baseados no valor Infinity pois ele não é um valor matematicamente sólido, e logo levará para o próximo número especial: NaN.

NaN significa "not a number" ("não é um número", em português), apesar de ser um valor do tipo númerico. Você receberá ele quando, por exemplo, tentar calcular 0 / 0. Infinity - Infinity, ou a partir de qualquer operação númerica que não leva à um resultado significativo.

## Strings

O próximo tipo de dado é a _string_. Strings são usadas para representar textos. Elas são escritas delimitando seu conteúdo por aspas.
```
`Embaixo do oceano`
"Deitar no oceano"
'Flutuar no oceano'
```
Você pode utilizar aspas simples, aspas duplas, ou crase para delimitar strings, desde que as aspas no começo sejam as mesmas aspas do fim.

Você pode colocar quase qualquer coisa entre aspas para fazer o JavaScript criar um valor de string a partir disso, mas alguns caracteres são mais difíceis. Você pode imaginar que colocar aspas duplas dentro de aspas duplas pode ser um pouco complicado, já que as aspas podem parecer como se fosse o fim da string. Quebras de linhas (os caracteres que você recebe ao apertar enter{keyname}) só pode ser incluido quando a string é feita usando crases (`` ` ``)

Para fazer possível incluir tais caracteres em uma string, a notação a seguir é utilizada: a barra invertida (\) dentro do texto indica que o próximo caracter tem um significado especial, o que é chamado de _escapar_ o caracter. Uma aspa dupla que é precedida por uma barra invertida não irá finalizar a string mas ser parte dela. Quando um caractere n é precedido por uma barra invertida, ele interpretado como uma quebra de linha. De forma similar, um caractere t precedido por uma barra invertida, será interpretado como um caractere de tabulação. Veja a string a seguir:

```
"Esta é a primeira linha\nE esta a segunda"
```

This is the actual text in that string:
Isto é como está o texto dentro da string.

```{lang: null}
Esta é a primeira linha
E esta a segunda
```

Existem, com certeza, situações onde você quer que uma crase em uma string seja apenas uma crase, não um código especial. Se duas crases aparecerem em sequência uma da outra, elas serão recolhidas juntas, e apenas uma restará na string. É assim que a string "Um novo caractere de quebra de linha é escrito assim: "\n"." pode ser expresso:

```
"Um novo caractere de quebra de linha é escrito assim: \"\\n\"."
```
Strings, também, devem ser modeladas em uma sequência de bits para conseguirem existir dentro de um computador. A forma que o Javascript faz isso é baseado no padrão _((Unicode))_. Este padrão assinala um número para todos os caracteres que você pode precisar, incluindo caracteres gregos, arábicos, japoneses, armênicos, e assim por diante. É desta forma que o Javascript faz.

Apesar disso, existe uma complicação: Javascript usa uma representação de 16 bits por elemento da string, o que pode ser descrito por 2^16 caracteres diferentes. Entretanto, Unicode define mais caracteres que isto, o dobro hoje em dia para ser mais preciso. Então alguns caracteres, como muitos emojis, ocupam duas "posições de caracteres" em strings no Javascript. Iremos voltar a falar mais sobre isto no [Capítulo ? ](higher_order#code_units).

Strings não podem ser divididas, multiplicadas ou substraidas. Entretanto, o operador + _pode_ ser utilizado nelas, não para somar, mas para concatenar - isto é, juntar duas strings. A linhas a seguir irá produzir uma string "concatenar"
Strings cannot be divided, multiplied, or subtracted. The `+` operator _can_ be used on them, not to add, but to _concatenate_—to glue two strings together. The following line will produce the string `"concatenate"`:

```{meta: "expr"}
"con" + "ca" + "te" + "nar"
```

Valores do tipo string possuem um número de funções (_métodos_) associadas à elas que podem ser utilizadas para performar outros tipos de operações nelas. Falarei mais sobre isto no [Capítulo ?](data#methods).

Strings escritas com aspas simples ou aspas duplas se comportam de forma muito similar na maior parte do tempo - a única diferença está no tipo de aspas que você precisa escapar dentro delas. Strings criadas com crase, também chamadas de _((`template literal`))_, podem fazer algumas coisas extras. Além de permitirem pular linhas, elas também permitem incorporar outros valores.

```{meta: "expr"}
`metade de 100 é ${100 / 2}`
```

Quando você escreve alguma coisa dentro de %{} em um `template literal`, seu resultado será computado, convertido para string, e incluído naquela posição. Este exemplo produz "_metade de 100 é 50_".

## Operadores unários

Nem todos os operadores são símbolos. Alguns são escritos como palavras. Um exemplo é o operador `typeof`, que produz um valor do tipo string indicando o tipo do valor fornecido.

```
console.log(typeof 4.5)
// → number
console.log(typeof "x")
// → string
```

Usaremos `console.log` nos exemplos de código para indicar que queremos ver o resultado da avaliação de algo. (Mais sobre isso no próximo capítulo.)

Os outros operadores mostrados até agora neste capítulo operavam em dois valores, mas `typeof` recebe apenas um. Operadores que usam dois valores são chamados de operadores _binários_, enquanto aqueles que recebem um são chamados de operadores _unários_. O operador de subtração (`-`) pode ser usado tanto como operador binário quanto como unário.

```
console.log(- (10 - 2))
// → -8
```

## Valores booleanos

Muitas vezes é útil ter um valor que distingue entre apenas duas possibilidades, como "sim" e "não" ou "ligado" e "desligado". Para esse propósito, o JavaScript tem um tipo _Boolean_, que tem apenas dois valores, true e false, escritos como essas palavras.

### Comparação

Aqui está uma maneira de produzir valores booleanos:

```
console.log(3 > 2)
// → true
console.log(3 < 2)
// → false
```

Os sinais `>` e `<` são os símbolos tradicionais para "é maior que" e "é menor que", respectivamente. São operadores binários. Aplicá-los resulta em um valor booleano que indica se eles são verdadeiros neste caso.

Strings podem ser comparadas da mesma forma.

```
console.log("Aardvark" < "Zoroaster")
// → true
```

A forma como as strings são ordenadas é aproximadamente alfabética, mas não exatamente como você esperaria ver em um dicionário: letras maiúsculas são sempre "menores" que as minúsculas, então `"Z" < "a"`, e caracteres não alfabéticos (!, -, e assim por diante) também são incluídos na ordenação. Ao comparar strings, o JavaScript percorre os caracteres da esquerda para a direita, comparando os códigos Unicode um por um.

Outros operadores similares são `>=` (maior ou igual a), `<=` (menor ou igual a), `==` (igual a) e `!=` (diferente de).

```
console.log("Garnet" != "Ruby")
// → true
console.log("Pearl" == "Amethyst")
// → false
```

Existe apenas um valor em JavaScript que não é igual a si mesmo, e esse é `NaN` ("not a number").

```
console.log(NaN == NaN)
// → false
```

`NaN` supostamente denota o resultado de um cálculo sem sentido e, como tal, não é igual ao resultado de qualquer _outro_ cálculo sem sentido.

### Operadores lógicos

Existem também algumas operações que podem ser aplicadas aos próprios valores booleanos. JavaScript suporta três operadores lógicos: _and_, _or_ e _not_. Estes podem ser usados para "raciocinar" sobre booleanos.

O operador `&&` representa o _and_ lógico. É um operador binário, e seu resultado é verdadeiro apenas se ambos os valores fornecidos a ele forem verdadeiros.

```
console.log(true && false)
// → false
console.log(true && true)
// → true
```

O operador `||` denota o _or_ lógico. Ele produz true se qualquer um dos valores fornecidos a ele for true.

```
console.log(false || true)
// → true
console.log(false || false)
// → false
```

_Not_ é escrito como um ponto de exclamação (`!`). É um operador unário que inverte o valor dado a ele—`!true` produz `false` e `!false` dá `true`.

Ao misturar esses operadores booleanos com aritméticos e outros operadores, nem sempre é óbvio quando os parênteses são necessários. Na prática, você geralmente pode se virar sabendo que, dos operadores que vimos até agora, `||` tem a menor precedência, depois vem `&&`, então os operadores de comparação (`>`, `==`, e assim por diante), e depois o resto. Esta ordem foi escolhida de forma que, em expressões típicas como a seguinte, sejam necessários o mínimo de parênteses possível:

```
1 + 1 == 2 && 10 * 10 > 50
```

O último operador lógico que veremos não é unário, nem binário, mas _ternário_, operando em três valores. É escrito com um ponto de interrogação e dois pontos, assim:

```
console.log(true ? 1 : 2);
// → 1
console.log(false ? 1 : 2);
// → 2
```

Este é chamado de operador _condicional_ (ou às vezes apenas _o operador ternário_, já que é o único operador desse tipo na linguagem). O valor à esquerda do ponto de interrogação "escolhe" qual dos outros dois valores será retornado. Quando é true, ele escolhe o valor do meio, e quando é false, escolhe o valor da direita.

## Valores vazios

Existem dois valores especiais, escritos `null` e `undefined`, que são usados para denotar a ausência de um valor _significativo_. Eles são valores em si, mas não carregam informação.

Muitas operações na linguagem que não produzem um valor significativo retornam `undefined` simplesmente porque precisam retornar _algum_ valor.

A diferença de significado entre `undefined` e `null` é um acidente do design do JavaScript e não importa na maioria das vezes. Nos casos em que você realmente precisa se preocupar com esses valores, recomendo tratá-los como praticamente intercambiáveis.

## Conversão automática de tipo

Na introdução, mencionei que o JavaScript faz o possível para aceitar quase qualquer programa que você der a ele, mesmo programas que fazem coisas estranhas. Isso é bem demonstrado pelas seguintes expressões:

```
console.log(8 * null)
// → 0
console.log("5" - 1)
// → 4
console.log("5" + 1)
// → 51
console.log("five" * 2)
// → NaN
console.log(false == 0)
// → true
```

Quando um operador é aplicado ao tipo "errado" de valor, o JavaScript irá silenciosamente converter esse valor para o tipo que ele precisa, usando um conjunto de regras que frequentemente não são o que você quer ou espera. Isso é chamado de _coerção de tipo_. O `null` na primeira expressão se torna `0`, e o `"5"` na segunda expressão se torna `5` (de string para número). Já na terceira expressão, `+` tenta concatenação de string antes da adição numérica, então o `1` é convertido para `"1"` (de número para string).

Quando algo que não mapeia obviamente para um número (como `"five"` ou `undefined`) é convertido para um número, você obtém o valor `NaN`. Operações aritméticas subsequentes em `NaN` continuam produzindo `NaN`, então se você obtiver um desses em um lugar inesperado, procure por conversões de tipo acidentais.

Ao comparar valores do mesmo tipo usando `==`, o resultado é fácil de prever: você deve obter true quando ambos os valores são os mesmos, exceto no caso de `NaN`. Mas quando os tipos diferem, JavaScript usa um conjunto complicado e confuso de regras para determinar o que fazer. Na maioria dos casos, ele apenas tenta converter um dos valores para o tipo do outro valor. No entanto, quando `null` ou `undefined` ocorre em qualquer lado do operador, ele produz true apenas se ambos os lados forem `null` ou `undefined`.

```
console.log(null == undefined);
// → true
console.log(null == 0);
// → false
```

Esse comportamento é frequentemente útil. Quando você quer testar se um valor tem um valor real em vez de `null` ou `undefined`, você pode compará-lo a `null` com o operador `==` ou `!=`.

E se você quiser testar se algo se refere ao valor preciso `false`? Expressões como `0 == false` e `"" == false` também são verdadeiras por causa da conversão automática de tipo. Quando você _não_ quer que nenhuma conversão de tipo aconteça, existem dois operadores adicionais: `===` e `!==`. O primeiro testa se um valor é _precisamente_ igual ao outro, e o segundo testa se ele não é precisamente igual. Assim, `"" === false` é falso, como esperado.

Recomendo usar os operadores de comparação de três caracteres defensivamente para evitar que conversões de tipo inesperadas o atrapalhem. Mas quando você tem certeza de que os tipos em ambos os lados serão os mesmos, não há problema em usar os operadores mais curtos.

### Curto-circuito de operadores lógicos

Os operadores lógicos `&&` e `||` lidam com valores de diferentes tipos de uma maneira peculiar. Eles converterão o valor à sua esquerda para o tipo booleano para decidir o que fazer, mas dependendo do operador e do resultado dessa conversão, eles retornarão o valor _original_ à esquerda ou o valor à direita.

O operador `||`, por exemplo, retornará o valor à sua esquerda quando esse valor puder ser convertido para true e retornará o valor à sua direita caso contrário. Isso tem o efeito esperado quando os valores são booleanos e faz algo análogo para valores de outros tipos.

```
console.log(null || "user")
// → user
console.log("Agnes" || "user")
// → Agnes
```

Podemos usar essa funcionalidade como uma forma de recorrer a um valor padrão. Se você tiver um valor que pode estar vazio, você pode colocar `||` depois dele com um valor de substituição. Se o valor inicial puder ser convertido para false, você obterá a substituição. As regras para converter strings e números em valores booleanos afirmam que `0`, `NaN` e a string vazia (`""`) contam como false, enquanto todos os outros valores contam como true. Isso significa que `0 || -1` produz `-1`, e `"" || "!?"` produz `"!?"`.

O operador `??` se assemelha a `||`, mas retorna o valor à direita apenas se o da esquerda for `null` ou `undefined`, não se for algum outro valor que possa ser convertido para false. Frequentemente, isso é preferível ao comportamento de `||`.

```
console.log(0 || 100);
// → 100
console.log(0 ?? 100);
// → 0
console.log(null ?? 100);
// → 100
```

O operador `&&` funciona de forma semelhante, mas ao contrário. Quando o valor à sua esquerda é algo que se converte para false, ele retorna esse valor, e caso contrário, retorna o valor à sua direita.

Outra propriedade importante desses dois operadores é que a parte à sua direita é avaliada apenas quando necessária. No caso de `true || X`, não importa o que `X` seja—mesmo que seja um pedaço de programa que faça algo _terrível_—o resultado será true, e `X` nunca é avaliado. O mesmo vale para `false && X`, que é false e ignorará `X`. Isso é chamado de _avaliação de curto-circuito_.

O operador condicional funciona de maneira similar. Do segundo e terceiro valores, apenas o que é selecionado é avaliado.

## Resumo

Examinamos quatro tipos de valores JavaScript neste capítulo: números, strings, booleanos e valores indefinidos. Esses valores são criados digitando seu nome (`true`, `null`) ou valor (`13`, `"abc"`).

Você pode combinar e transformar valores com operadores. Vimos operadores binários para aritmética (`+`, `-`, `*`, `/` e `%`), concatenação de string (`+`), comparação (`==`, `!=`, `===`, `!==`, `<`, `>`, `<=`, `>=`) e lógica (`&&`, `||`, `??`), bem como vários operadores unários (`-` para negar um número, `!` para negar logicamente e `typeof` para encontrar o tipo de um valor) e um operador ternário (`?:`) para escolher um de dois valores com base em um terceiro valor.

Isso lhe dá informações suficientes para usar JavaScript como uma calculadora de bolso, mas não muito mais. O próximo capítulo começará a amarrar essas expressões em programas básicos.
