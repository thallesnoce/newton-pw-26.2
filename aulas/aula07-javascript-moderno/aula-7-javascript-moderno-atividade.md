# LABORATÓRIO DE JAVASCRIPT MODERNO

*Prever, executar, explicar: descobrir a linguagem pelo console*

**Programação Web — Aula 11 de 20 · JavaScript Moderno**

## 🎯 MISSÃO

Você vai descobrir as regras do JavaScript por experimento, e não por lista de sintaxe. A ordem importa: escreva a PREVISÃO antes de apertar Enter. Quem só lê o resultado aprende a reconhecer a saída; quem prevê aprende a raciocinar sobre o código.

- Abra laboratorio-js.html e o console do navegador (F12 → Console).
- A página já define a constante PRODUTOS com 10 itens: você não precisa digitar dados.
- Em cada rodada: escreva a previsão, execute, anote a saída real e explique a diferença.
- Previsão errada não é erro — é o momento em que você aprende algo. Registre-a mesmo assim.

**⏱️ Tempo:** 40 minutos     **👥 Formato:** individual, conferindo cada rodada com o colega ao lado

> **Nome:** ____________________   **Turma:** ____________________   **Data:** ___ / ___ / ______

## RODADA 01 — const, let e var

> `Console → executar linha por linha, na ordem`

Três formas de declarar, três comportamentos diferentes. Descubra a regra de cada um testando o que dá erro e o que não dá:

```text
const a = 1;  a = 2;              // previsao: __________________
let   b = 1;  b = 2;              // previsao: __________________
const t = [1, 2];  t.push(3);  t; // previsao: __________________

{ var x = 'dentro'; }  x;         // previsao: __________________
{ let y = 'dentro'; }  y;         // previsao: __________________
```

**Sua análise:**

1. A linha 3 deu erro? Escreva com suas palavras o que const realmente impede.

2. Comparando as duas últimas linhas: qual declaração respeita as chaves { } e qual ignora?

3. Qual das três você vai usar por padrão no seu projeto, e em que situação vai trocar?

## RODADA 02 — Tipos e comparação

> `Console → um por vez, prevendo antes`

JavaScript converte tipos sozinho quando você usa ==. Descubra a regra e por que ela causa bugs difíceis de achar:

```text
typeof 42          // ______________
typeof '42'        // ______________
typeof true        // ______________
typeof PRODUTOS    // ______________  (surpresa?)
typeof undefined   // ______________

'10' ==  10        // ______________
'10' === 10        // ______________
0    ==  false     // ______________
0    === false     // ______________
```

**Sua análise:**

1. O que == faz antes de comparar, e que === não faz?

2. typeof de um array surpreendeu você? Como descobrir se um valor é array? (dica: Array.isArray)

3. Um formulário devolve sempre texto. Se você comparar a idade digitada com == 18, que bug pode aparecer?

## RODADA 03 — map — transformar

> `Console → usar a constante PRODUTOS já definida pela página`

map percorre a lista e devolve uma NOVA lista com o resultado da função aplicada a cada item. Teste e compare os tamanhos:

```text
PRODUTOS.length                        // ______

PRODUTOS.map(p => p.nome)              // previsao do tamanho: ______

PRODUTOS.map(p => `${p.nome}: R$ ${p.preco}`)
  // escreva as 2 primeiras linhas da saida:
  // ______________________________________________
  // ______________________________________________

PRODUTOS.map(p => { p.nome })          // previsao: __________________
```

**Sua análise:**

1. O array de saída do map tem sempre o mesmo tamanho do de entrada? Por quê?

2. A última linha devolveu uma lista de undefined. O que faltou dentro das chaves?

3. PRODUTOS mudou depois dos três map? Confira digitando PRODUTOS. O que isso diz sobre o método?

## RODADA 04 — filter e find — selecionar

> `Console → prever o TIPO da resposta antes de executar`

Os dois recebem uma função que devolve verdadeiro ou falso. A diferença está no que cada um entrega de volta:

```text
PRODUTOS.filter(p => p.categoria === 'perifericos')
  // previsao: quantos itens? ______  e o TIPO da resposta: ______________

PRODUTOS.filter(p => p.preco < 100)
  // previsao: quantos itens? ______

PRODUTOS.find(p => p.id === 3)
  // previsao: o TIPO da resposta: ______________

PRODUTOS.find(p => p.id === 999)      // previsao: __________________
PRODUTOS.filter(p => p.id === 999)    // previsao: __________________
```

**Sua análise:**

1. filter devolve array; find devolve um item. E quando nada é encontrado, cada um devolve o quê?

2. Você quer saber só SE existe algum produto em falta, sem precisar dele. Que método usaria? (dica: some)

3. Escreva a expressão que devolve os produtos de 'perifericos' com preço abaixo de 100 — em uma única linha.

## RODADA 05 — reduce — colapsar em um valor

> `Console → primeiro com laço, depois com reduce, comparando os números`

reduce percorre a lista carregando um acumulador. É o método que assusta, e a melhor forma de entendê-lo é chegar ao mesmo número por dois caminhos:

```text
// caminho 1 — com laco:
let soma = 0;
for (const p of PRODUTOS) { soma += p.preco * p.quantidade; }
soma;                                  // resultado: ______________

// caminho 2 — com reduce:
PRODUTOS.reduce((acc, p) => acc + p.preco * p.quantidade, 0)
                                       // resultado: ______________

// e se o zero do final for esquecido?
PRODUTOS.reduce((acc, p) => acc + p.preco)  // previsao: ______________
```

**Sua análise:**

1. Os dois caminhos deram o mesmo número? Qual dos dois você entende melhor hoje?

2. Para que serve o 0 no final do reduce? O que aconteceu quando você o omitiu?

3. reduce pode devolver um array ou um objeto, não só um número. Onde isso seria útil no seu projeto?

## RODADA 06 — Destructuring, spread e a armadilha da cópia

> `Console → executar na ordem e observar o ORIGINAL depois de cada passo`

Extrair campos e copiar objetos são operações do dia a dia — e a cópia esconde a armadilha mais cara da aula:

```text
const item = PRODUTOS[0];
const { nome, preco } = item;
nome; preco;                      // previsao: __________________

const [primeiro, segundo] = PRODUTOS;
primeiro.nome;                    // previsao: __________________

const promo = { ...item, preco: item.preco / 2 };
promo.preco;                      // previsao: ______
item.preco;                       // previsao: ______  <- ATENCAO

const lista2 = PRODUTOS;
lista2.pop();
PRODUTOS.length;                  // previsao: ______  <- ATENCAO
```

**Sua análise:**

1. Alterar promo mudou item? E alterar lista2 mudou PRODUTOS? Explique a diferença entre os dois casos.

2. Escreva a linha que copia PRODUTOS de verdade, de forma que pop() na cópia não afete o original.

3. Como você garantiria que uma função nunca altera o array que recebeu? Escreva a regra em uma frase.

## 🏆 DESAFIO BÔNUS

Terminou antes do tempo? Escolha um destes:

- Encadeie três métodos em uma linha: filtre os disponíveis, ordene por preço e devolva só os nomes dos 3 primeiros.
- Descubra por experimento o que .sort() faz com \[10, 9, 100, 1\] e por que o resultado parece errado. (dica: o padrão compara como texto)
- Teste const frete = 0; frete || 10 e depois frete ?? 10. Explique a diferença e diga em que situação ela viraria um bug de cobrança.
- Escreva uma função que recebe qualquer número de argumentos (rest) e devolve a média deles. Teste com zero argumentos.
