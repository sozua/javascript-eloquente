# Introdução

{{quote {author: "Ellen Ullman", title: "Close to the Machine: Technophilia and Its Discontents", chapter: true}

Acreditamos que estamos criando o sistema para nossos próprios propósitos. Acreditamos que o estamos fazendo à nossa própria imagem... Mas o computador não é realmente como nós. É uma projeção de uma parte muito estreita de nós mesmos: aquela porção dedicada à lógica, ordem, regra e clareza.

quote}}

{{figure {url: "img/chapter_picture_00.jpg", alt: "Ilustração de uma chave de fenda ao lado de uma placa de circuito de aproximadamente o mesmo tamanho", chapter: "framed"}}}

Este é um livro sobre como instruir computadores. Atualmente, os computadores são tão comuns quanto chaves de fenda, mas são bem mais complexos, e fazer com que eles façam exatamente o que você quer nem sempre é fácil.

Se a tarefa que você tem para o seu computador é comum e bem compreendida, como mostrar seu e-mail ou funcionar como uma calculadora, você pode simplesmente abrir o aplicativo apropriado e começar a trabalhar. Mas para tarefas únicas ou de escopo aberto, muitas vezes não há um aplicativo adequado.

É aí que a programação pode entrar. Programação é o ato de construir um programa - um conjunto de instruções precisas que dizem ao computador o que fazer. Como os computadores são bestas estúpidas e pedantes, programar é fundamentalmente tedioso e frustrante.

Felizmente, se você conseguir superar esse fato - e talvez até gostar do rigor de pensar em termos que máquinas estúpidas possam lidar - programar pode ser recompensador. Permite que você faça coisas em segundos que levariam uma eternidade manualmente. É uma forma de fazer sua ferramenta de computador fazer coisas que não podia fazer antes. E proporciona um maravilhoso exercício de resolução de problemas e pensamento abstrato.

A maior parte da programação é feita com linguagens de programação. Uma linguagem de programação é uma linguagem construída artificialmente usada para instruir computadores. É interessante que a maneira mais eficaz que encontramos para nos comunicar com um computador se baseia tanto na forma como nos comunicamos uns com os outros. Como as linguagens humanas, as linguagens de computador permitem que palavras e frases sejam combinadas de novas maneiras, tornando possível expressar conceitos sempre novos.

Em certo ponto, interfaces baseadas em linguagem, como os prompts BASIC e DOS dos anos 1980 e 1990, eram o principal método de interação com computadores. Elas foram amplamente substituídas por interfaces visuais, que são mais fáceis de aprender, mas oferecem menos liberdade. Mas as linguagens ainda estão lá, se você souber onde procurar. Uma delas, JavaScript, está embutida em todo navegador web moderno - e, portanto, está disponível em quase todos os dispositivos.

Este livro tentará familiarizá-lo o suficiente com esta linguagem para fazer coisas úteis e divertidas com ela.

## Sobre programação

Além de explicar JavaScript, vou introduzir os princípios básicos de programação. Programar, como se constata, é difícil. As regras fundamentais são simples e claras, mas programas construídos sobre essas regras tendem a se tornar complexos o suficiente para introduzir suas próprias regras e complexidade. Você está, de certa forma, construindo seu próprio labirinto, e pode facilmente se perder nele.

Haverá momentos em que ler este livro será bem frustrante. Se você é novo em programação, haverá muito conteúdo novo para aprender. Muito desse conteúdo será então combinado de maneiras que exigem que você faça novas conexões e compreenda novos conceitos.

Cabe a você fazer o esforço necessário. Quando estiver lutando para seguir o livro, não tire conclusões precipitadas sobre suas próprias capacidades. Você está bem - você só precisa continuar. Faça uma pausa, releia algum material e certifique-se de ler e entender os programas e exercícios de exemplo. Aprender é um trabalho árduo, mas tudo o que você aprende é seu e tornará o aprendizado posterior mais fácil.


{{quote {author: "Ursula K. Le Guin", title: "A Mão Esquerda da Escuridão"}

Quando a ação se torna não lucrativa, reúna informações; quando a informação se torna não lucrativa, durma.

quote}}

Um programa é muitas coisas. É um pedaço de texto digitado por um programador, é a força diretiva que faz o computador fazer o que faz, são dados na memória do computador, mas ao mesmo tempo controla as ações realizadas nessa memória. Analogias que tentam comparar programas a objetos familiares tendem a falhar. Uma superficialmente adequada é comparar um programa a uma máquina - muitas partes separadas tendem a estar envolvidas, e para fazer o todo funcionar, precisamos considerar as maneiras pelas quais essas partes se interconectam e contribuem para a operação do todo.

Um computador é uma máquina física que atua como hospedeira para essas máquinas imateriais. Os computadores em si só podem fazer coisas objetivas. A razão pela qual são tão úteis é que fazem essas coisas a uma velocidade incrivelmente alta. Um programa pode combinar engenhosamente um enorme número dessas ações simples para fazer coisas muito complicadas.

Um programa é uma construção do pensamento. É gratuito para construir, é sem peso, e cresce facilmente sob nossas mãos digitadoras. Mas à medida que um programa evolui, também cresce sua complexidade. A habilidade de programar é a habilidade de construir programas que não confundam o programador. Os melhores programas são aqueles que conseguem fazer algo interessante enquanto ainda são fáceis de entender.

Alguns programadores acreditam que essa complexidade é melhor gerenciada usando apenas um pequeno conjunto de técnicas bem compreendidas em seus programas. Eles compuseram regras estritas ("melhores práticas") prescrevendo a forma que os programas devem ter e cuidadosamente permanecem dentro de sua pequena zona segura.

Isso não é apenas chato - é ineficaz. Novos problemas muitas vezes requerem novas soluções. O campo da programação é jovem e ainda está se desenvolvendo rapidamente, e é variado o suficiente para ter espaço para abordagens muito diferentes. Há muitos erros terríveis a serem cometidos no design de programas, e você deve ir em frente e cometê-los pelo menos uma vez para que os entenda. Um senso do que um bom programa parece é desenvolvido com a prática, não aprendido de uma lista de regras.

## Por que a linguagem importa

No início, no nascimento da computação, não havia linguagens de programação. Os programas pareciam algo assim:

```{lang: null}
00110001 00000000 00000000
00110001 00000001 00000001
00110011 00000001 00000010
01010001 00001011 00000010
00100010 00000010 00001000
01000011 00000001 00000000
01000001 00000001 00000001
00010000 00000010 00000000
01100010 00000000 00000000
```

Este é um programa para somar os números de 1 a 10 e imprimir o resultado: `1 + 2 + ... + 10 = 55`. Ele poderia rodar em uma máquina hipotética simples. Para programar os primeiros computadores, era necessário configurar grandes conjuntos de interruptores na posição correta ou perfurar buracos em tiras de cartões e alimentá-las ao computador. Você pode imaginar como esse procedimento era tedioso e propenso a erros. Mesmo escrever programas simples exigia muita inteligência e disciplina. Os complexos eram quase inconcebíveis.

Claro, inserir manualmente esses padrões arcanos de bits (os uns e zeros) dava ao programador uma profunda sensação de ser um poderoso mago. E isso deve valer algo em termos de satisfação no trabalho.

Cada linha do programa anterior contém uma única instrução. Poderia ser escrito em inglês assim:

1. Armazene o número 0 na posição de memória 0.
2. Armazene o número 1 na posição de memória 1.
3. Armazene o valor da posição de memória 1 na posição de memória 2.
4. Subtraia o número 11 do valor na posição de memória 2.
5. Se o valor na posição de memória 2 for o número 0, continue com a instrução 9.
6. Adicione o valor da posição de memória 1 à posição de memória 0.
7. Adicione o número 1 ao valor da posição de memória 1.
8. Continue com a instrução 3.
9. Imprima o valor da posição de memória 0.

Embora isso já seja mais legível do que a sopa de bits, ainda é bastante obscuro. Usar nomes em vez de números para as instruções e locais de memória ajuda.

```
  Defina "total" como 0.
  Defina "contador" como 1.
[loop]
  Defina "comparar" como "contador".
  Subtraia 11 de "comparar".
  Se "comparar" for 0, continue em [fim].
  Adicione "contador" a "total".
  Adicione 1 a "contador".
  Continue em [loop].
[fim]
  Imprima "total".
```

Você consegue ver como o programa funciona neste ponto? As duas primeiras linhas dão a duas posições de memória seus valores iniciais: `total` será usado para construir o resultado do cálculo, e `contador` manterá o controle do número que estamos olhando atualmente. As linhas usando `comparar` são provavelmente as mais confusas. O programa quer ver se `contador` é igual a 11 para decidir se pode parar de rodar. Como nossa máquina hipotética é bastante primitiva, ela só pode testar se um número é zero e tomar uma decisão com base nisso. Portanto, usa a posição de memória rotulada `comparar` para calcular o valor de `contador - 11` e toma uma decisão com base nesse valor. As próximas duas linhas adicionam o valor de `contador` ao resultado e incrementam `contador` em 1 toda vez que o programa decide que `contador` ainda não é 11.

Aqui está o mesmo programa em JavaScript:

```javascript
let total = 0, contador = 1;
while (contador <= 10) {
  total += contador;
  contador += 1;
}
console.log(total);
// → 55
```

Esta versão nos dá algumas melhorias a mais. Mais importante, não há necessidade de especificar a maneira como queremos que o programa salte para frente e para trás - a construção `while` cuida disso. Ela continua executando o bloco (envolvido em chaves) abaixo dela enquanto a condição que lhe foi dada se mantiver. Essa condição é `contador <= 10`, que significa "contador é menor ou igual a 10". Não precisamos mais criar um valor temporário e compará-lo com zero, o que era apenas um detalhe desinteressante. Parte do poder das linguagens de programação é que elas podem cuidar de detalhes desinteressantes para nós.

No final do programa, após a construção `while` ter terminado, a operação `console.log` é usada para escrever o resultado.

Finalmente, aqui está como o programa poderia parecer se tivéssemos as convenientes operações `range` e `sum` disponíveis, que respectivamente criam uma coleção de números dentro de um intervalo e calculam a soma de uma coleção de números:

```javascript
console.log(sum(range(1, 10)));
// → 55
```

A moral desta história é que o mesmo programa pode ser expresso de formas longas e curtas, ilegíveis e legíveis. A primeira versão do programa era extremamente obscura, enquanto esta última é quase inglês: `log` (registre) a `sum` (soma) do `range` (intervalo) de números de 1 a 10. (Veremos em capítulos posteriores como definir operações como `sum` e `range`.)

Uma boa linguagem de programação ajuda o programador permitindo que ele fale sobre as ações que o computador deve realizar em um nível mais alto. Ela ajuda a omitir detalhes, fornece blocos de construção convenientes (como `while` e `console.log`), permite que você defina seus próprios blocos de construção (como `sum` e `range`), e torna esses blocos fáceis de compor.

## O que é JavaScript?

JavaScript foi introduzido em 1995 como uma forma de adicionar programas a páginas da web no navegador Netscape Navigator. A linguagem desde então foi adotada por todos os outros principais navegadores gráficos. Ela tornou possíveis as aplicações web modernas - ou seja, aplicações com as quais você pode interagir diretamente sem fazer um recarregamento de página para cada ação. JavaScript também é usado em sites mais tradicionais para fornecer várias formas de interatividade e inteligência.

É importante notar que JavaScript quase não tem nada a ver com a linguagem de programação chamada Java. O nome similar foi inspirado por considerações de marketing ao invés de bom julgamento. Quando JavaScript estava sendo introduzido, a linguagem Java estava sendo fortemente comercializada e ganhando popularidade. Alguém pensou que seria uma boa ideia tentar aproveitar esse sucesso. Agora estamos presos ao nome.

Após sua adoção fora da Netscape, um documento padrão foi escrito para descrever como a linguagem JavaScript deveria funcionar para que as várias peças de software que afirmavam suportar JavaScript pudessem ter certeza de que realmente forneciam a mesma linguagem. Isso é chamado de padrão ECMAScript, em homenagem à organização Ecma International que conduziu a padronização. Na prática, os termos ECMAScript e JavaScript podem ser usados de forma intercambiável - são dois nomes para a mesma linguagem.

Há aqueles que dirão coisas terríveis sobre JavaScript. Muitas dessas coisas são verdadeiras. Quando fui obrigado a escrever algo em JavaScript pela primeira vez, rapidamente comecei a desprezá-lo. Ele aceitava quase tudo que eu digitava, mas interpretava de uma maneira completamente diferente do que eu queria dizer. Isso tinha muito a ver com o fato de que eu não tinha a menor ideia do que estava fazendo, é claro, mas há um problema real aqui: JavaScript é ridiculamente liberal no que permite. A ideia por trás desse design era que tornaria a programação em JavaScript mais fácil para iniciantes. Na realidade, isso principalmente torna mais difícil encontrar problemas em seus programas, porque o sistema não os apontará para você.

Essa flexibilidade também tem suas vantagens, no entanto. Ela deixa espaço para técnicas que são impossíveis em linguagens mais rígidas e, como você verá (por exemplo no Capítulo 10), pode ser usada para superar algumas das deficiências do JavaScript. Após aprender a linguagem adequadamente e trabalhar com ela por um tempo, aprendi a realmente gostar do JavaScript.

Houve várias versões de JavaScript. ECMAScript versão 3 foi a versão amplamente suportada durante a ascensão do JavaScript à dominância, aproximadamente entre 2000 e 2010. Durante esse tempo, estava em andamento o trabalho em uma versão 4 ambiciosa, que planejava uma série de melhorias e extensões radicais à linguagem. Mudar uma linguagem viva e amplamente usada de maneira tão radical provou ser politicamente difícil, e o trabalho na versão 4 foi abandonado em 2008. Uma versão 5 muito menos ambiciosa, que fez apenas algumas melhorias não controversas, saiu em 2009. Em 2015, saiu a versão 6, uma grande atualização que incluía algumas das ideias planejadas para a versão 4. Desde então, temos tido novas atualizações pequenas todos os anos.

O fato de que o JavaScript está evoluindo significa que os navegadores têm que se manter constantemente atualizados. Se você estiver usando um navegador mais antigo, ele pode não suportar todos os recursos. Os designers da linguagem são cuidadosos para não fazer mudanças que possam quebrar programas existentes, então novos navegadores ainda podem executar programas antigos. Neste livro, estou usando a versão 2023 do JavaScript.

Navegadores web não são as únicas plataformas nas quais JavaScript é usado. Alguns bancos de dados, como MongoDB e CouchDB, usam JavaScript como sua linguagem de script e consulta. Várias plataformas para programação desktop e de servidor, mais notavelmente o projeto Node.js (o assunto do [Capítulo ?](node)), fornecem um ambiente para programar JavaScript fora do navegador.

## Código, e o que fazer com ele

Código é o texto que compõe programas. A maioria dos capítulos deste livro contém bastante código. Acredito que ler código e escrever código são partes indispensáveis do aprendizado da programação. Tente não apenas passar os olhos pelos exemplos - leia-os atentamente e entenda-os. Isso pode ser lento e confuso no início, mas prometo que você pegará o jeito rapidamente. O mesmo vale para os exercícios. Não assuma que os entende até ter realmente escrito uma solução funcional.

Recomendo que você tente suas soluções para exercícios em um interpretador JavaScript real. Dessa forma, você obterá feedback imediato sobre se o que está fazendo está funcionando, e, espero, será tentado a experimentar e ir além dos exercícios.

Ao ler este livro em seu navegador, você pode editar (e executar) todos os programas de exemplo clicando neles.

<!-- TODO: Traduzir estas páginas -->
A maneira mais fácil de executar o código de exemplo do livro - e experimentar com ele - é procurá-lo na versão online do livro em https://eloquentjavascript.net. Lá, você pode clicar em qualquer exemplo de código para editá-lo e executá-lo e ver a saída que ele produz. Para trabalhar nos exercícios, vá para https://eloquentjavascript.net/code, que fornece código inicial para cada exercício de codificação e permite que você veja as soluções.

Executar os programas definidos neste livro fora do site do livro requer algum cuidado. Muitos exemplos são independentes e devem funcionar em qualquer ambiente JavaScript. Mas o código em capítulos posteriores é frequentemente escrito para um ambiente específico (o navegador ou Node.js) e só pode ser executado lá. Além disso, muitos capítulos definem programas maiores, e as partes de código que aparecem neles dependem umas das outras ou de arquivos externos. O sandbox no site fornece links para arquivos ZIP contendo todos os scripts e arquivos de dados necessários para executar o código de um determinado capítulo.

## Visão geral deste livro

Este livro contém aproximadamente três partes. Os primeiros 12 capítulos discutem a linguagem JavaScript. Os próximos sete capítulos são sobre navegadores web e a maneira como o JavaScript é usado para programá-los. Finalmente, dois capítulos são dedicados ao Node.js, outro ambiente para programar JavaScript. Há cinco capítulos de projeto no livro que descrevem programas de exemplo maiores para lhe dar uma ideia da programação real.

A parte da linguagem do livro começa com quatro capítulos que introduzem a estrutura básica da linguagem JavaScript. Eles discutem estruturas de controle (como a palavra `while` que você viu nesta introdução), funções (escrever seus próprios blocos de construção) e estruturas de dados. Após estes, você será capaz de escrever programas básicos. Em seguida, os Capítulos [?](higher_order) e [?](object) introduzem técnicas para usar funções e objetos para escrever código mais abstrato e manter a complexidade sob controle.

Após um primeiro capítulo de projeto que constrói um robô de entrega rudimentar, a parte da linguagem do livro continua com capítulos sobre manipulação de erros e correção de bugs, expressões regulares (uma importante ferramenta para trabalhar com texto), modularidade (outra defesa contra a complexidade) e programação assíncrona (lidando com eventos que levam tempo). O segundo capítulo de projeto, onde implementamos uma linguagem de programação, conclui a primeira parte do livro.

A segunda parte do livro, Capítulos [?](browser) a [?](paint), descreve as ferramentas às quais o JavaScript do navegador tem acesso. Você aprenderá a exibir coisas na tela (Capítulos [?](dom) e [?](canvas)), responder à entrada do usuário (Capítulo [?](event)) e se comunicar pela rede (Capítulo [?](http)). Há novamente dois capítulos de projeto nesta parte: construindo um jogo de plataforma e um programa de pintura de pixels.

O Capítulo [?](node) descreve o Node.js, e o Capítulo [?](skillsharing) constrói um pequeno site usando essa ferramenta.

## Convenções tipográficas

Neste livro, texto escrito em fonte `monoespaçada` representará elementos de programas. Às vezes, estes são fragmentos autossuficientes, e às vezes eles apenas se referem a parte de um programa próximo. Os programas (dos quais você já viu alguns) são escritos da seguinte forma:

```javascript
function fatorial(n) {
  if (n == 0) {
    return 1;
  } else {
    return fatorial(n - 1) * n;
  }
}
```

Às vezes, para mostrar a saída que um programa produz, a saída esperada é escrita após ele, com duas barras e uma seta na frente.

```javascript
console.log(fatorial(8));
// → 40320
```

Boa sorte!
