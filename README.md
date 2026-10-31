# YouTube Downloader (Tampermonkey)

Userscript para Google Chrome via Tampermonkey que adiciona um botão de download em qualquer página de vídeo do YouTube.

## Instalação

1. Instale a extensão **Tampermonkey** no Chrome.
2. Abra o painel do Tampermonkey → **Utilitários** → importe `youtube-downloader.user.js`, ou arraste o arquivo para uma aba do Chrome com o Tampermonkey ativo.
3. Abra qualquer vídeo em `https://www.youtube.com/watch?v=...`.

## Uso

- Clique no botão vermelho de download no canto inferior direito.
- **Vídeo (MP4)**: lista uma entrada por resolução disponível, da maior para a menor, com container, codec, tamanho e indicação de áudio.
- **Áudio (MP3)**: escolha 128, 192 ou 320 kbps e baixe o MP3 (decodificação + encode no próprio navegador). Também é possível baixar a faixa de áudio original (`.m4a`/`.webm`).

## Resoluções acima de 720p

O YouTube não oferece vídeo e áudio no mesmo arquivo acima de 720p. Nesses casos, o botão **MP4 com áudio** baixa a faixa de vídeo e a melhor faixa de áudio (AAC quando disponível) e as une em um único `.mp4` dentro do navegador, sem recodificar (mesma qualidade). O botão **só vídeo** baixa apenas a faixa de vídeo.

O muxing é feito com a biblioteca [mediabunny](https://mediabunny.dev), embutida no userscript. Vídeos 4K/8K longos podem usar bastante memória, pois o arquivo final é montado em memória antes do download.

## Limitações reais do YouTube

- Vídeos privados, com restrição de idade ou bloqueio regional podem não retornar formatos.
- O progresso e a conversão MP3 rodam em memória; vídeos muito longos exigem bastante RAM.

## Arquivos

- `youtube-downloader.user.js` — o userscript completo (com a biblioteca mediabunny embutida).
- `vendor/mediabunny.min.js` — cópia da biblioteca embutida no userscript (referência para atualização manual).
