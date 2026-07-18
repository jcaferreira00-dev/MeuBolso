# Bolsos — controle por envelopes

App de controle financeiro por envelopes/orçamento por categoria. PWA em HTML/CSS/JS puro, sem build step, sem Firebase — todos os dados ficam em `localStorage` no aparelho do usuário.

## Conceito

Cada categoria de gasto vira um "envelope" com um limite mensal. Ao lançar uma despesa, o valor sai do envelope daquela categoria. O selo circular no topo de cada envelope mostra visualmente quanto já foi usado (verde = tranquilo, dourado = atenção, vermelho = estourou).

## Estrutura de arquivos

```
bolsos-app/
├── index.html        # estrutura das telas
├── style.css          # design tokens e layout
├── app.js              # toda a lógica (localStorage, cálculos, render)
├── manifest.json    # manifesto PWA
├── sw.js                # service worker (cache offline)
├── privacy.html      # política de privacidade (exigida pela Play Store)
└── icons/               # ícones do app (192, 512, maskable, favicon)
```

Este código é independente do site principal (`jcaferreira00-dev.github.io`) — pode ser hospedado em qualquer subpasta ou repositório próprio.

## Rodando localmente

Basta servir a pasta com qualquer servidor estático (não abre direto com `file://` por causa do service worker):

```bash
npx serve .
# ou
python3 -m http.server 8080
```

## Publicar no GitHub Pages

1. Suba a pasta `bolsos-app/` para um repositório (ou subpasta do site atual).
2. Em Settings → Pages, aponte para a branch/pasta correspondente.
3. Acesse `https://jcaferreira00-dev.github.io/bolsos-app/` (ajuste o caminho conforme onde publicar).

## Publicar na Play Store (mesmo fluxo já usado nos outros apps)

1. **PWABuilder** (gratuito) — [pwabuilder.com](https://www.pwabuilder.com): informe a URL publicada no GitHub Pages, gere o pacote Android (`.aab`) e o APK de teste.
2. **Google Play Console** — taxa única de US$ 25.
3. Preencha a ficha da loja (nome, descrição, capturas de tela, ícone) e aponte a política de privacidade para a URL de `privacy.html` publicada.
4. Contas novas exigem teste fechado com 12+ testadores reais em aparelhos físicos por 14 dias consecutivos antes de liberar produção.

## Backup dos dados

Como não há nuvem, o app tem exportação/importação manual de backup (JSON) na aba Ajustes — vale lembrar o usuário disso na descrição da loja.
