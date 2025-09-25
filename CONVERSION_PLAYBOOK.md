## Playbook de Conversão (UI/CX)

Objetivo: aumentar cliques qualificados (WhatsApp/Ligar), reduzir atritos no mobile e reforçar confiança.

### 1) CTAs visíveis e repetidos
- Barra fixa no mobile (WhatsApp e Ligar) – sempre acessível.
- Botão flutuante (WhatsApp) e atalho para Instagram – presença social.
- CTA na hero com promessa clara: “Solicitar Orçamento – Resposta Rápida”.

### 2) Microcopy que remove fricção
- “Resposta rápida”, “Atendimento imediato”, “Garantia de 90 dias”.
- Transparência de horário e cobertura (já no rodapé e seções).

### 3) Velocidade e confiança
- Imagens lazy/async; CSS leve; animações respeitam `prefers-reduced-motion`.
- Foco visível e botões com boa área de toque.

### 4) Tracking e melhoria contínua
- Eventos: `whatsapp_*`, `call_mobile_bar`, `instagram_floating`, `page_view`, `visit`.
- Avalie: taxa de clique por seção, origem (UTM), horário/dia, mobile vs desktop.

### 5) Testes A/B sugeridos
- Texto do CTA (ex.: “Conversar Agora no WhatsApp” vs “Solicitar Orçamento”).
- Posição dos CTAs (hero, topo fixo vs flutuante).
- Cores de destaque (dourado atual vs verde WhatsApp dominante).

### 6) Próximos incrementos
- Inserir `schema.org/Service` para serviços principais.
- Formulário curto com envio por WhatsApp (pré-preenchido) como opção alternativa.
- FAQs colapsáveis com rich snippets (FAQPage) para SEO + objeções.


