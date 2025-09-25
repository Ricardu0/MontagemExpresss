## Guia de imagens do projeto

Esta pasta serve para armazenar as imagens do site. Abaixo, sugestões de arquivos e seus usos recomendados. Substitua as URLs externas do `index.html` por caminhos locais quando fizer o upload.

### Estrutura sugerida
- `hero.jpg` – imagem de destaque do topo (seção hero). Recomenda-se 1920x1080, JPG otimizado.
- `logo.png` – logotipo oficial com fundo transparente (preferência: 512x512, PNG). Use em `.logo-img` quando substituir o placeholder “ME”.
- `mapa-sp.jpg` – imagem ilustrativa da cobertura (seção "Atendemos Toda São Paulo"). 1000x700 aprox.
- `about-team.jpg` – imagem da equipe (página Quem Somos). 1000x700 aprox.
- `about-mission.jpg` – imagem para missão/visão (página Quem Somos). 1000x700 aprox.
- `services-residencial.jpg` – card de serviços residenciais. 800x600 aprox.
- `services-corporativo.jpg` – card de serviços corporativos. 800x600 aprox.
- `services-cozinha.jpg` – card de cozinhas planejadas. 800x600 aprox.
- `portfolio-*.jpg` – imagens de portfólio (use nomes descritivos: `portfolio-cozinha-pinheiros.jpg`, etc.). 1200x800 aprox.

### Boas práticas
- Otimize antes de enviar: use ferramentas como Squoosh, TinyPNG ou ImageOptim.
- Nomeie com palavras-chave: ajuda no SEO (ex.: `montagem-moveis-sala-santana.jpg`).
- Use `alt` descritivo em todas as imagens para acessibilidade e SEO.
- Prefira JPG para fotos e PNG/SVG para logotipos/ilustrações com transparência.

### Como trocar as URLs no index.html
1. Copie as imagens para esta pasta `imgs/`.
2. No `index.html`, substitua links externos como `https://images.unsplash.com/...` por `./imgs/nome-da-imagem.jpg`.
3. Mantenha os atributos `loading="lazy"` e `decoding="async"` para performance.

### Exemplo de uso do logotipo (opcional)
Você pode usar uma imagem real de logotipo no lugar do placeholder “ME”:

```html
<!-- Substitua o bloco .logo-placeholder por uma imagem -->
<img src="./imgs/logo.png" alt="Montagem Express" class="logo-img" width="50" height="50" />
```


