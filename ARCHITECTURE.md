## Arquitetura do Projeto

Este documento descreve a organização do código, responsabilidades e princípios adotados (incluindo SOLID), além de pontos de extensão.

### Visão Geral
- Tipo: Site estático (HTML/CSS/JS) – sem build.
- Entrada principal: `index.html`.
- Documentos de apoio: `GOOGLE_ADS_TECHNICAL.md`, `GOOGLE_ADS_GUIDE.md`, `README_VERCEL.md`, `imgs/IMAGES_GUIDE.md`.

### Estrutura Lógica no `index.html`
- CSS no `<style>`: estilos base, navegação, hero, seções (serviços, sobre, portfólio), responsividade e componentes (cards, botões, floating actions).
- JavaScript no `<script>`: módulo `App` responsável por navegação, tracking, efeitos e integrações.

### Módulo JavaScript: `App`
- `init()`: ponto de entrada. Configura tracking, listeners, animações e ações flutuantes (WhatsApp/Instagram).
- `navigateTo(pageId, evt)`: roteamento simples entre seções (SPA-like) e tracking de `page_view`.
- `toggleMenu()`: abre/fecha o menu mobile.
- `trackVisit()`: registra visita com `sessionId` e evento GA4 `visit`.
- `bindAnalyticsClicks()`: captura cliques de links com `data-event` e envia para GA4/Ads (cliques WhatsApp/Instagram).
- `setupSmoothScroll()`: rolagem suave para âncoras internas.
- `setupScrollNavbar()`: troca estilo da navbar conforme scroll (listener passivo).
- `setupAnimations()`: anima entrada de cards via `IntersectionObserver` (lazy animation).
- `setupOutsideClickClose()`: fecha menu ao clicar fora.
- `addFloatingWhatsApp()`/`addFloatingInstagram()`: criam botões flutuantes no mobile.
- `ensureFloatingStack()`: garante um container único para ações flutuantes (pilha).

Para compatibilidade com o HTML existente, as funções globais são mantidas:
- `window.showPage(pageId)` → `App.navigateTo(pageId, event)`
- `window.toggleMenu()` → `App.toggleMenu()`

### Princípios Aplicados (SOLID)
- S – Single Responsibility: cada método do `App` foca em uma responsabilidade (navegação, tracking, UI, etc.).
- O – Open/Closed: o `App` é extensível por novos métodos (ex.: outro botão flutuante) sem alterar os existentes.
- L – Liskov Substitution: funções mantêm contratos simples (DOM in/out, sem tipos exóticos), suportando substituições e mocks.
- I – Interface Segregation: listeners e utilitários são pequenos e independentes (ex.: scroll, animações, tracking).
- D – Dependency Inversion: dependências externas (GA4/Ads) são chamadas por boundary (`gtag`), checadas via `typeof` para evitar acoplamento rígido.

### Performance e Acessibilidade
- Imagens com `loading="lazy"`, `decoding="async"`, `alt`, dimensões recomendadas em `imgs/IMAGES_GUIDE.md`.
- Listeners com `{ passive: true }` quando apropriado.
- `will-change` e transições leves nos botões flutuantes.
- `prefers-reduced-motion` honrado no CSS.
- Foco visível (`:focus-visible`) e cores com bom contraste.

### Tracking e Ads
- GA4/Ads via `gtag` no `<head>` (IDs placeholders a substituir).
- Eventos: `visit`, `page_view`, cliques com `data-event` (ex.: `whatsapp_floating`, `whatsapp_hero`, `instagram_floating`).
- Conversões de exemplo com `send_to: 'AW-XXXXXXXXX/xxxxxxxxxxx'` (substituir pelos reais).

### Extensão e Customização
- Novas seções: adicioná-las como `.page` e chamar `App.navigateTo('id')`.
- Novos CTAs: usar atributo `data-event="nome_do_evento"` para tracking automático.
- Novos ícones flutuantes: criar método similar a `addFloatingInstagram()` e anexar no `ensureFloatingStack()`.
- Migrar para GTM: mover tags para o contêiner e remover `gtag` direto (ver `GOOGLE_ADS_TECHNICAL.md`).

### Boas Práticas de Manutenção
- Manter funções curtas, com nomes claros.
- Evitar lógica inline no HTML; preferir utilitários no `App`.
- Não duplicar tags do Google; validar no DebugView (GA4) e em Conversões (Ads).


