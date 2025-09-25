## Deploy na Vercel – Montagem Express

Este projeto é um site estático (HTML/CSS/JS). Você pode publicar com poucos cliques na Vercel.

### 1) Pré‑requisitos
- Conta na Vercel (`https://vercel.com`)
- (Opcional) Vercel CLI instalado globalmente
  - Windows: `npm i -g vercel`

Não há dependências de build. O site é servido diretamente do `index.html`.

### 2) Estrutura mínima
- `index.html`
- `imgs/` (opcional, suas imagens locais)
- `GOOGLE_ADS_TECHNICAL.md` e `GOOGLE_ADS_GUIDE.md` (documentação)

### 3) Deploy via Dashboard (recomendado)
1. Crie um repositório no GitHub com estes arquivos.
2. Na Vercel, clique em “Add New Project” → “Import Git Repository”.
3. Selecione o repositório e continue.
4. Em “Framework Preset”, deixe como “Other”.
5. “Root Directory”: mantenha a raiz (onde está o `index.html`).
6. Deploy. A Vercel publicará e informará a URL.

### 4) Deploy via Vercel CLI (opcional)
```bash
vercel login
vercel
# Siga as perguntas: projeto novo, escopo, diretório (raiz do projeto)
# Na pergunta "Link to existing project?" responda conforme desejar.
```

Se quiser um alias (URL amigável):
```bash
vercel alias set nome-projeto meu-dominio.vercel.app
```

### 5) Domínio customizado
1. Adicione seu domínio em “Settings” → “Domains”.
2. Siga as instruções de DNS (A/ALIAS/CNAME conforme a Vercel indicar).
3. A Vercel instala HTTPS automaticamente.

### 6) Variáveis/IDs do Google
Edite o `index.html` e substitua:
- `G-XXXXXXXXXX` pelo seu GA4 Measurement ID
- `AW-XXXXXXXXX` e `xxxxxxxxxxx` pelo seu Conversion ID/Label

### 7) Boas práticas de produção
- Otimize imagens na pasta `imgs/` e troque URLs externas por locais.
- Confira no “PageSpeed Insights” a performance (LCP, CLS, INP).
- Valide GA4 (DebugView) e conversões do Ads após o deploy.
- Ative o Consent Mode/banners se necessário.

### 8) Problemas comuns
- Página 404: confirme que o `index.html` está na raiz do projeto (não em subpasta).
- Tags duplicadas do Google: certifique-se de que está usando apenas gtag ou GTM, não ambos ao mesmo tempo (sem duplicar GA4/Ads).


