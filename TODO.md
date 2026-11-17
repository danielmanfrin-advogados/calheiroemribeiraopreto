# Entregáveis e critérios

## 1. Conteúdo estático e navegação — concluído
- Marca e slug correspondem ao nicho informado: “Calheiro em Ribeirão Preto” e `calheiroribeiraopreto`.
- O projeto deve ter 13 páginas: `index.html`; três páginas em `servicos/<slug>/index.html`; seis páginas em `bairros/<slug>/index.html`; `sobre/index.html`; `perguntas-frequentes/index.html`; `politica-de-privacidade/index.html`.
- Cada rota contém texto já no HTML, um H1, breadcrumb nas páginas internas, links internos funcionais, botões WhatsApp e telefone no topo, no corpo e na faixa final, e aviso legal obrigatório idêntico.
- Home apresenta hero, selo regional, H1/subtítulo, CTAs, pedido rápido com localização e serviço, seção de boas-vindas e três passos, três cards de serviço, quatro diferenciais, seis bairros, cinco FAQs e CTA final.
- Serviços: instalação de calhas, conserto de calhas, limpeza e manutenção de calhas; cada página contém ao menos 250 palavras únicas, quando indicado, o que informar, como pedir, 2–3 dúvidas próprias, bairros atendidos e ligações para outros serviços.
- Cada página de bairro contém ao menos 150 palavras originais, alterna exemplos e ordem dos blocos sem inventar ruas, prédios, estabelecimentos ou tempos de deslocamento, e liga a serviços e outros bairros.
- Sobre, FAQ completa e Política de privacidade estão presentes. FAQ inicial e FAQ completa reproduzem exatamente as mesmas cinco perguntas e respostas.

## 2. Identidade visual, acessibilidade e imagens — concluído
- Visual mobile-first, fonte Fira Sans com fallback, paleta `#1D4ED8`, `#15389C`, `#EDF1FC`, `#D2DCF7`, fundo creme e botões WhatsApp/telefone da referência.
- Navegação em pílula, hero fotográfico com contraste, pedido rápido sobreposto, cartões arredondados, seções alternadas, faixa CTA e barra fixa inferior no celular.
- Foco visível, contraste mínimo AA, alvos de toque de pelo menos 44 px, `prefers-reduced-motion`, sem rolagem horizontal em 360 px.
- Criar `img/hero.jpg` (horizontal 1600×900), `img/sobre.jpg` e uma imagem 4:3 por serviço. As imagens são ilustrativas, neutras, sem textos, marcas, placas legíveis ou rostos em destaque; usar alt neutro, width/height e lazy loading fora da primeira dobra. Compactar imagens para aproximadamente 150 KB ou menos. Se geração/armazenamento falhar, caixas neutras e `img/PROMPTS.txt`.

## 3. Chamadas e registro de cliques — concluído
- `config.js` guarda site, nicho, WhatsApp, telefone, mensagem padrão, cidade e endpoint `https://script.google.com/macros/s/AKfycbzNOf1W0H8qo7UEY0AGEyLIF3ksLYgj2YELKy9OytgORZ_3Zs6PmRGl_a2p9w-myqdnlg/exec`, com comentários para trocar números.
- Todos os links de WhatsApp usam `data-acao="whatsapp"`, `data-local` apropriado e `data-msg`; telefone usa `data-acao="ligar"` e `data-local`. Hrefs iniciais usam o telefone provisório `5516900000000` e o tracker substitui os números pelo config.
- Copiar a lógica de tracker.js do anexo sem alterações: GET no-cors com keepalive e fallback Image; envia site, nicho, ação, local, página, título, origem, UTM, gclid apenas como “sim” quando presente, dispositivo, tela, idioma, detalhe e sessão. O pedido rápido combina serviço, bairro e região.
- Não coletar nome, e-mail, CPF ou outro dado pessoal; não usar cookies de publicidade.
- `apps-script/Code.gs` é transcrito sem alterações do anexo.

## 4. SEO, GEO e metadados — concluído
- Cada página: title até 60 caracteres, description de 120–155, canonical absoluto, Open Graph, Twitter Card, robots index/follow, `lang="pt-BR"`, viewport, theme-color, favicon, hierarquia H2/H3.
- `sitemap.xml` lista as 13 URLs no domínio `https://calheiroribeiraopreto.vercel.app`, lastmod `2026-11-17`, prioridades 1.0 inicial, 0.8 serviços e 0.6 demais. `robots.txt` libera rastreamento e aponta para sitemap. Links começam por `/`.
- JSON-LD: WebSite e FAQPage na inicial; Service nas páginas de serviço e bairros com provider Organization (portal), areaServed City Ribeirão Preto e estado de São Paulo; FAQPage na FAQ; BreadcrumbList em páginas internas. Dados FAQ devem ser idênticos ao conteúdo visível.
- `llms.txt` em Markdown inclui resumo, os três serviços, seis bairros, links institucionais e perguntas/respostas completas.
- Sem LocalBusiness com endereço inventado. Palavras-chave naturais e respostas diretas no início das seções.

## 5. Privacidade e conteúdo responsável — concluído
- Linguagem em português do Brasil, simples, direta, sem propaganda exagerada, sem travessão, sem promessas de preço, desconto, prazo, chegada, 24h, garantia, certificações ou avaliações não confirmadas; sem endereço, CNPJ ou nome de empresa inventados.
- Terceira pessoa (“o prestador”, “o atendente”). Conteúdo legal/técnico cauteloso, sem inventar leis; orientar a confirmar detalhes com o prestador ou órgão competente quando aplicável.
- Rodapé de todas as páginas: “Este site é um portal de contato e não presta o serviço diretamente. O atendimento é feito por prestadores parceiros da região. Valores, prazos e formas de pagamento são informados pelo prestador no atendimento.”
- Política explica os campos registrados ao clicar, finalidade, ausência de dados diretos e cookies publicitários, conversa tratada pelo prestador e WhatsApp, direitos conforme Lei 13.709/2018 solicitados pelo WhatsApp e data de atualização.

## 6. Build, Vercel e instruções — concluído
- HTML/CSS/JS puros. `package.json` sem dependências (somente nome, private, version, type module e script build), sem package-lock. Criar `build.js` com cópia nativa do Node para `dist`, ignorando arquivos de projeto conforme anexo.
- `vercel.json` exatamente com buildCommand `npm run build`, outputDirectory `dist`, `cleanUrls:true`, `trailingSlash:true`.
- Estrutura e assets na raiz, não em src/public. Build deixa `dist/index.html`.
- `LEIA-ME.txt` explica config dos números, atualização do Code.gs e implantação existente com Nova versão e acesso “Qualquer pessoa”, execução de setup(), tabela dinâmica de relatório por Site e contagem de Botão (campo de ação), Search Console/sitemap, Perfil da Empresa no Google apenas para prestador com endereço real, substituição de imagens mantendo nomes e implantação Vercel.
- `manus-routes.json` lista as rotas do site sem endpoints/ativos.

## 7. Verificação de entrega — concluído
- Executar `npm install` e `npm run build`; conferir que o build gera `dist/index.html` sem dependências do projeto.
- Verificar os 13 arquivos/rotas, titles, descrições e canonical, links internos, sitemap, mensagens e metadados dos botões, JSON-LD/FAQ, política, aviso legal, paleta e layout responsivo.
