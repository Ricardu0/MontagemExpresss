## Guia simples: Ativar Google e anúncios no seu site

Este guia explica, de forma fácil, como ligar o Google Analytics 4 (GA4) e as conversões do Google Ads no seu site, além de dar dicas rápidas para melhorar seus anúncios e atrair mais clientes.

### 1) O que você precisa
- Um ID do GA4 (começa com `G-...`)
- Um ID de conversão do Google Ads (ex.: `AW-123456789`)
- Um “Label” de conversão (ex.: `AbCdEfGhIjk`)

Se não tiver, peça ao seu gestor de tráfego ou crie no Google Analytics/Ads.

### 2) Onde colocar no site
Já deixamos o código preparado no `index.html`. Você só precisa trocar os IDs de exemplo pelos seus reais.

### 3) Como medir resultados
- Visitas: o site registra quando alguém entra.
- Páginas: quando a pessoa navega pelas seções.
- WhatsApp: quando alguém clica nos botões (navbar, seções e portfólio), o sistema envia um evento para o Google.

Isso ajuda você a entender o que atrai mais conversas e pedidos de orçamento.

### 4) Como contar “conversões” no Google Ads
Conversão é a ação importante (ex.: clique no WhatsApp, envio de formulário). No nosso site, o clique no WhatsApp já está pronto para marcar conversão. No Google Ads, crie a conversão e copie o `Conversion ID` e o `Label`. Depois substitua no código (já indicado).

### 5) Dicas rápidas para ter mais resultados
- Títulos e descrições claros: mostre o que você faz e para quem.
- Chamada para ação forte: “Solicitar orçamento agora no WhatsApp”.
- Velocidade: imagens leves (já usamos carregamento “lazy”).
- Mobile: teste no celular; botões grandes e fáceis de clicar.
- Prova social e confiança: mostre portfólio, garantia e áreas atendidas.

### 6) Como saber se está funcionando
- No Google Analytics 4, veja os relatórios em Tempo Real e o “DebugView”.
- No Google Ads, acompanhe em “Conversões” se está recebendo dados.
- No navegador, abra o console (F12) e veja mensagens como “Visit”, “View” e “Click”.

### 7) Privacidade (opcional, recomendado)
Se quiser pedir consentimento para cookies, ative o “Consent Mode”. Um profissional pode configurar um banner e ligar isso ao Google.

### 8) Quando usar o Google Tag Manager (GTM)
Se você pretende testar muitas tags diferentes (Meta, TikTok, Hotjar etc.), o GTM facilita sem precisar mexer no código toda hora. Caso contrário, a configuração atual com gtag já funciona muito bem.

### 9) Próximos passos
- Trocar os IDs de exemplo pelos seus.
- Criar a conversão de WhatsApp no Google Ads e validar.
- Rodar campanhas com bons termos (ex.: “montagem de móveis em São Paulo”, “montador de móveis SP”).
- Acompanhar os resultados por alguns dias e otimizar.

Se quiser, posso substituir os IDs no código e validar tudo com você.


