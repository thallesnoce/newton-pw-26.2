# PERÍCIA COMPARATIVA DE FRAMEWORKS CSS

*Não "qual é o melhor?", mas "o que eu ganho e o que eu perco?"*

**Programação Web — Aula 9 de 20 · Bibliotecas CSS e Entrega da Fase 1**

## 🎯 MISSÃO

Três arquivos constroem o MESMO componente: com CSS próprio, com Bootstrap 5 e com Tailwind. Sua missão é medir os trade-offs com números e sair desta aula com um critério próprio de escolha — que você vai usar hoje mesmo, na entrega da Fase 1.

- Abra os três: comparativo-css-proprio.html, comparativo-bootstrap.html e comparativo-tailwind.html.
- Os arquivos de Bootstrap e Tailwind precisam de internet (CDN). Sem rede, compare pelo código.
- Ferramentas: aba Network, painel Coverage (Ctrl+Shift+P → "Coverage"), Lighthouse e o código-fonte.
- Não existe resposta certa nesta ficha. Existe justificativa boa ou fraca.

**⏱️ Tempo:** 40 minutos     **👥 Formato:** individual, conferindo cada rodada com o colega ao lado

> **Nome:** ____________________   **Turma:** ____________________   **Data:** ___ / ___ / ______

## RODADA 01 — Onde mora a decisão visual?

> `Abrir o código-fonte dos três arquivos (Ctrl+U) e localizar UM card em cada`

O card é branco, com borda cinza e canto arredondado nos três. Descubra onde essa informação está escrita em cada versão:

```text
                        linhas de CSS   "branco + borda + canto"
                        proprio         esta escrito em...
                        -------------   ------------------------
CSS proprio             ____ linhas     ( )CSS  ( )HTML
Bootstrap               ____ linhas     ( )CSS  ( )HTML
Tailwind                ____ linhas     ( )CSS  ( )HTML

tamanho do HTML de UM card (conte os caracteres da linha do <article>):
  css proprio: ____   bootstrap: ____   tailwind: ____
```

**Sua análise:**

1. Em qual versão o HTML é mais fácil de LER? E de ESCREVER?

2. Se a decisão visual está no HTML, o que acontece quando o site tem 40 páginas?

3. Em qual versão você conseguiria mudar o estilo de todos os cards editando um único lugar?

## RODADA 02 — O cliente quer trocar de azul para verde

> `Nos três arquivos, tentar mudar a cor primária pelo DevTools`

É o pedido mais comum do mundo real. Meça o custo dessa mudança em cada versão:

```text
                        quantos lugares   voce conseguiu
                        precisam mudar?   fazer no DevTools?
                        ---------------   ------------------
CSS proprio             ______            ( )sim ( )nao
Bootstrap               ______            ( )sim ( )nao
Tailwind                ______            ( )sim ( )nao

no CSS proprio, o que exatamente voce mudou?
  ______________________________________________________
```

**Sua análise:**

1. Qual recurso da aula 5 fez essa mudança ser trivial no CSS próprio?

2. No Bootstrap, por que mudar a cor primária de verdade não é tão simples quanto parece?

3. No Tailwind, o que você teria que fazer em cada card? Existe forma de centralizar isso?

## RODADA 03 — Quanto o usuário baixa — e quanto se usa

> `Aba Network (marcar Disable cache, recarregar) e painel Coverage (Ctrl+Shift+P → "Show Coverage")`

Todo CSS que chega ao navegador foi baixado pelo usuário, usado ou não. Meça:

```text
                        CSS baixado   % realmente usado
                        -----------   -----------------
CSS proprio             ______ kB     ______ %
Bootstrap               ______ kB     ______ %
Tailwind (Play CDN)     ______ kB     ______ %

obs: o Play CDN do Tailwind NAO representa producao — instalado via npm,
     ele gera um CSS so com as classes usadas. Anote o valor mesmo assim.
```

**Sua análise:**

1. Qual versão desperdiça mais bytes do usuário? Em uma conexão 4G lenta, isso importa?

2. Por que o CSS próprio tem aproveitamento tão alto?

3. O que o Bootstrap traz que esta página não usa? Cite dois componentes.

## RODADA 04 — Vocabulário novo ou CSS que você já sabe?

> `Listar classes reais dos dois arquivos de framework e classificar cada uma`

Frameworks cobram um preço de aprendizado. Descubra qual é o preço de cada um:

```text
BOOTSTRAP — 5 classes que voce encontrou:
  1. ______________  descreve: ( )componente ( )propriedade CSS
  2. ______________  descreve: ( )componente ( )propriedade CSS
  3. ______________  descreve: ( )componente ( )propriedade CSS
  4. ______________  descreve: ( )componente ( )propriedade CSS
  5. ______________  descreve: ( )componente ( )propriedade CSS

TAILWIND — 5 classes que voce encontrou:
  1. ______________  descreve: ( )componente ( )propriedade CSS
  2. ______________  descreve: ( )componente ( )propriedade CSS
  3. ______________  descreve: ( )componente ( )propriedade CSS
  4. ______________  descreve: ( )componente ( )propriedade CSS
  5. ______________  descreve: ( )componente ( )propriedade CSS
```

**Sua análise:**

1. Qual dos dois exige decorar nomes que só existem naquele framework?

2. Quantas das classes do Tailwind você conseguiu entender só com o CSS das aulas 4 a 8?

3. Se você trocar de framework no próximo projeto, qual dos dois aprendizados você leva com você?

## RODADA 05 — Framework resolve acessibilidade?

> `Rodar o Lighthouse (só Accessibility) nos três arquivos`

É a crença mais comum sobre frameworks. Teste antes de acreditar:

```text
                        nota   primeiro problema apontado
                        ----   ---------------------------------
CSS proprio             ____   _________________________________
Bootstrap               ____   _________________________________
Tailwind                ____   _________________________________

algum framework resolveu, sozinho:
  alt das imagens?          ( )sim ( )nao
  contraste do texto?       ( )sim ( )nao
  foco visivel no teclado?  ( )sim ( )nao
```

**Sua análise:**

1. Usar framework melhorou, piorou ou não alterou a nota? Por quê?

2. O que um framework PODE ajudar em acessibilidade, e o que continua sendo seu trabalho?

3. Depois destas 5 rodadas: qual você vai usar na Fase 1? Escreva a justificativa em uma frase.

## 🏆 DESAFIO BÔNUS

Terminou antes do tempo? Escolha um destes:

- No arquivo do Bootstrap, remova a linha do `<link>` do CDN e recarregue. O que sobra? O que isso diz sobre dependência externa?
- Procure na documentação do Bootstrap 5 o que mudou em relação ao 4. Encontre a menção ao jQuery.
- No Tailwind, tente descobrir a que valor em px corresponde a classe px-4. Onde essa escala está definida?
