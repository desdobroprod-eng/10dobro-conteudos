# Hotsite 10Dobro • Conteúdos

Portal estático unificado dos canais (Bom dia com Jesus + Pra Ouvir no Trânsito).
Atualiza sozinho: a cada vídeo postado, o pipeline grava no `data/feed.json` e
re-renderiza `index.html` + uma página por vídeo em `posts/`.

## Como funciona
- `site_publisher.publish_to_site(...)` é chamado pelo pipeline ao postar (jornada do cliente).
- `python -m canal_youtube.site_publisher backfill` importa os vídeos já publicados.
- `python -m canal_youtube.site_publisher` só re-renderiza a partir do feed.

## AdSense
Defina no `.env`: `ADSENSE_CLIENT=ca-pub-XXXXXXXXXXXXXXXX`. Sem isso, os slots ficam
como placeholder "Espaço publicitário". Com a key, o script do AdSense é injetado e
os `<ins class="adsbygoogle">` ativam (após aprovação do site no AdSense).

## Deploy (grátis)
- **Vercel:** `cd canal_youtube/site && vercel --prod` (ou arraste a pasta em vercel.com).
- **Netlify:** arraste `canal_youtube/site/` em app.netlify.com/drop.
- **GitHub Pages:** publique o conteúdo de `site/` numa branch `gh-pages`.

Os embeds do YouTube só funcionam em domínio http(s) real (não via `file://`).
