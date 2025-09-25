## Google Ads e GA4 – Guia Técnico de Implementação e Boas Práticas

Este documento descreve, de forma técnica, como instrumentar Google Analytics 4 (GA4), Google Ads (conversões) e tags relacionadas neste site, além de cobrir otimizações que impactam performance, SEO e qualidade do tráfego pago.

### 1) Identificadores necessários
- GA4 Measurement ID: substitua `G-XXXXXXXXXX`
- Google Ads Conversion ID (account): `AW-XXXXXXXXX`
- Google Ads Conversion Label (por evento): `xxxxxxxxxxx`

Armazene estes valores em local seguro. No código, substitua os placeholders.

### 2) Instalação do gtag.js (GA4 + Ads)
Coloque no `<head>` do site, o mais acima possível:

```html
<!-- GA4 + Google Ads (gtag.js) -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);} // eslint-disable-line
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');      // GA4
  gtag('config', 'AW-XXXXXXXXX');      // Google Ads (remarketing / conv. global)
</script>
```

Observação: se você optar por Google Tag Manager (GTM), evite duplicar gtag.js. Centralize no contêiner do GTM.

### 3) Eventos e conversões
O site dispara eventos de:
- `visit` (visita inicial – sessão);
- `page_view` (ao alternar “páginas” SPA/anchors);
- Eventos de clique (links com `data-event`), ex.: `whatsapp_nav`, `whatsapp_special`, `whatsapp_portfolio`.

Exemplo de envio manual de evento:
```js
gtag('event', 'whatsapp_nav', { link_url: 'https://wa.me/...' });
```

#### 3.1) Conversões do Google Ads
Para marcar um evento como conversão, use:
```js
gtag('event', 'conversion', {
  send_to: 'AW-XXXXXXXXX/xxxxxxxxxxx'
});
```
Recomendações:
- Crie “Conversões” no Google Ads e copie o `Conversion ID` e `Label`.
- Dispare a conversão no momento mais fiel ao objetivo (ex.: clique no WhatsApp, envio de formulário, telefone clicado, etc.).
- Evite duplicidade (não dispare a mesma conversão múltiplas vezes por sessão sem critério).

### 4) Consent Mode v2 (opcional e recomendado)
Para conformidade (LGPD/GDPR), adicione o Consent Mode antes de qualquer `config`:
```html
<script>
  gtag('consent', 'default', {
    'ad_user_data': 'denied',
    'ad_personalization': 'denied',
    'ad_storage': 'denied',
    'analytics_storage': 'denied'
  });
  // Após obter consentimento do usuário:
  // gtag('consent', 'update', { ad_storage: 'granted', analytics_storage: 'granted', ... });
</script>
```

### 5) UTM e atribuição
- Use parâmetros UTM nas campanhas (`utm_source`, `utm_medium`, `utm_campaign`, `utm_content`).
- No WhatsApp e CTAs, preserve parâmetros quando possível (ex.: criar links dinâmicos que concatenam querystring atual).

### 6) Depuração e validação
- Extensões: “Tag Assistant Companion”, “GA4 DebugView”.
- Console: o site loga `Visit`, `View` e `Click` com contexto.
- Tempo real do GA4: confira eventos entrando e parâmetros (DebugView).
- Google Ads: “Conversões” → Status “Recebendo dados” e “Verificada recentemente”.

### 7) Boas práticas de qualidade de tráfego e Landing Page Experience
- Velocidade: Core Web Vitals (LCP, CLS, INP). Minimizar scripts, lazy-loading de imagens, `decoding="async"`.
- Relevância: título, `meta description`, headings coerentes com o anúncio.
- Confiança: informações de contato, garantia, políticas claras.
- Responsividade: UX mobile impecável, botões acessíveis.
- Acessibilidade: foco visível, `prefers-reduced-motion` respeitado.

### 8) SEO técnico que também impacta Ads
- `canonical` correto (evita duplicidade)
- Open Graph / Twitter Card (melhora compartilhamento social)
- JSON-LD `LocalBusiness` (elegível a rich results)
- Sitemap.xml e robots.txt apropriados
- Imagens otimizadas e com `alt` descritivo

### 9) Estrutura atual no projeto (resumo)
- gtag está no `<head>` do `index.html` com IDs de placeholder.
- Eventos automáticos: `visit`, `page_view`, cliques com `data-event`.
- Conversão exemplo no clique de WhatsApp (substituir `send_to`).

### 10) Migrar para GTM (opcional)
- Benefícios: governança de tags, versionamento, triggers/variáveis avançadas.
- Passos: inserir contêiner do GTM no `<head>` e `<body>`, mover gtag/GA4/Ads para tags do GTM e remover gtag direto do código.

### 11) Checklist de publicação
- [ ] Substituiu `G-XXXXXXXXXX` e `AW-XXXXXXXXX/xxxxxxxxxxx` pelos reais
- [ ] Validou conversões no Google Ads
- [ ] Conferiu eventos no GA4 DebugView
- [ ] Verificou páginas com PageSpeed Insights / Lighthouse
- [ ] Conferiu console para logs de visita/cliques
- [ ] Implementou Consent Mode (se aplicável)

### 12) Solução de problemas
- Conversão não aparece no Ads: verifique bloqueadores, `send_to`, consentimento, e se evento realmente dispara.
- GA4 sem dados: checar ID, duplicidade de scripts, consentimento negado.
- Tráfego pago com alta taxa de rejeição: revisar correspondência de copy, velocidade e UX.


