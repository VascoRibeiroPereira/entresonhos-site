# Entre Sonhos — site pessoal

Versão estática e minimalista do site pessoal de Vasco Belo Pereira, inspirada visualmente no site do jogo **O Sonho**.

## Estrutura

- `index.html` — site completo numa página, com secções: Quem sou, O Sonho, Blog e Loja.
- `style.css` — identidade visual escura, glow esverdeado, núcleo animado e layout mobile-first.
- `script.js` — controlo de som, ano automático e preparação para link Etsy.
- `CNAME` — domínio personalizado `entre1000sonhos.pt`.
- `assets/favicon.svg` — ícone simples do núcleo Entre Sonhos.

## Publicação no GitHub Pages

1. Faz backup do repositório atual.
2. Apaga o conteúdo atual do repositório `entresonhos-site`.
3. Copia estes ficheiros para a raiz do repositório.
4. Faz commit e push para `main`.
5. Confirma em Settings → Pages que o GitHub Pages está a publicar a partir da branch `main`.

## Música

Por defeito, o site usa a música do jogo através deste URL:

`https://osonho.entre1000sonhos.pt/assets/audio/music.mp3`

O som não começa automaticamente. O visitante ativa/desativa através do botão "Som".

Se quiseres tornar o site independente do jogo, coloca o ficheiro `music.mp3` em `assets/audio/music.mp3` e altera em `index.html` para:

`data-audio-src="assets/audio/music.mp3"`

## Etsy

Quando a loja estiver pronta, abre `script.js` e substitui:

`const ETSY_URL = "";`

por:

`const ETSY_URL = "https://www.etsy.com/shop/NOME_DA_LOJA";`

O botão muda automaticamente de "Loja Etsy em breve" para "Abrir loja Etsy".
