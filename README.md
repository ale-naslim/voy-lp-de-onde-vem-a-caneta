# Assets da LP "De onde vem a caneta"

Arquivos estáticos servidos por **jsDelivr** para a landing page
`lp.voysaude.com.br/de-onde-vem-a-caneta`, que é montada no Webflow.

```
https://cdn.jsdelivr.net/gh/ale-naslim/voy-lp-de-onde-vem-a-caneta@main/<caminho>
```

## O que tem aqui

| pasta | conteúdo |
|---|---|
| `js/script.js` | animações da página: frame-scrub do hero, abas de medicamento, menu, fade-ups |
| `frames/pens/` | 122 frames da faixa do hero — Wegovy, Mounjaro e Ozivy girando |
| `frames/caixa/` | 121 frames da faixa da caixa (não usada na versão atual da página) |
| `img/` | imagens de lote das canetas e do produto |
| `fonts/` | Season Mix e NB International Pro |
| `vid/` | depoimentos em vídeo |
| `brand/` | marca |

## Origem

Este repositório espelha `guilhermem-design/voy-de-onde-vem-a-caneta`, que
servia a página até aqui, e acrescenta a atualização de agosto de 2026:

- **`img/ozivy-codigo.jpg`** — imagem do lote do Ozivy, para a terceira aba;
- **`frames/pens/`** — a faixa passa a mostrar **três** canetas em vez de duas.
  Mesmo com uma caneta a mais ficou mais leve: 523 KB contra 901 KB em webp,
  porque o quadro foi reenquadrado justo no grupo e 88% dele é fundo chapado;
- **`js/script.js`** — o `mountScrub` desenha em `contain` (`Math.min`) em vez
  de `cover` (`Math.max`). Com três canetas o cover cortava as das pontas no
  celular: num viewport 375×812 só 26% da largura do quadro aparecia.
  O `mountContainScrub` não foi alterado.

## Cuidado ao atualizar

As URLs usam `@main`, e o jsDelivr guarda refs de branch por até **12 horas**.
Substituir um arquivo no mesmo caminho pode servir a versão antiga durante esse
período. Duas saídas:

- publicar em caminho novo (`frames/pens-v2/`, por exemplo); ou
- purgar o cache: `https://purge.jsdelivr.net/gh/ale-naslim/voy-lp-de-onde-vem-a-caneta@main/<caminho>`

O `script.js` é carregado com `?t=<timestamp>` pela página, então ele mesmo não
sofre com isso.
