# NEXOR Player para Vercel

Player estático pronto para publicar na Vercel. A regra em `vercel.json` envia qualquer rota `/player/...` para o player.

## Como montar o link

Codifique a URL da mídia antes de adicioná-la ao caminho. Por exemplo, para a mídia abaixo:

```
https://cdn.exemplo.com/canal/playlist.m3u8?token=abc
```

o endereço do player será:

```
https://SEU-DOMINIO.vercel.app/player/https%3A%2F%2Fcdn.exemplo.com%2Fcanal%2Fplaylist.m3u8%3Ftoken%3Dabc
```

No navegador, isso equivale a usar `encodeURIComponent(urlDaMidia)`. O player também aceita a URL antiga via `?url=...` e o formato Base64 URL-safe no caminho.

## Publicação

1. Crie um repositório no GitHub e envie os arquivos desta pasta para a raiz dele.
2. Na Vercel, escolha **Add New → Project**, importe o repositório e confirme a publicação. Não há etapa de build: é um site estático.
3. Depois de publicado, use o domínio fornecido pela Vercel ou conecte seu domínio próprio nas configurações do projeto.

## Observações

- A origem da mídia precisa aceitar reprodução no navegador (CORS, quando aplicável) e entregar um formato compatível, como HLS (`.m3u8`), MP4 ou WebM.
- URLs de mídia colocadas no caminho ficam visíveis no histórico e nos registros de acesso. Para links que contenham segredos, prefira URLs temporárias e não use credenciais permanentes.
