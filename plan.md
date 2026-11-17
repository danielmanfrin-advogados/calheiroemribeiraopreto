# Plano de implementação — Calheiro em Ribeirão Preto

## Bloco do nicho

- Slug: `calheiroribeiraopreto`
- Portal: **Calheiro em Ribeirão Preto**
- Termo: calheiro em Ribeirão Preto, instalação e conserto de calhas
- Paleta: destaque `#1D4ED8`, escura `#15389C`, suave `#EDF1FC`, suave 2 `#D2DCF7`.
- Title inicial: **Calheiro em Ribeirão Preto | Instalação e Conserto**
- H1 inicial: **Calheiro em Ribeirão Preto para instalação e conserto de calhas**
- Subtítulo: Descreva o imóvel, o trecho e o que precisa ser feito. Envie os detalhes pelo WhatsApp para conversar com o prestador.
- Meta description inicial: Calheiro em Ribeirão Preto para instalação e conserto de calhas. Informe o bairro e a necessidade pelo WhatsApp para solicitar avaliação ao prestador.
- Para o atendimento: bairro, tipo de imóvel, trecho aproximado, material se souber, serviço pretendido e problema observado.
- Serviços: instalação de calhas (`instalacao-de-calhas`), conserto de calhas (`conserto-de-calhas`), limpeza e manutenção de calhas (`limpeza-e-manutencao-de-calhas`).
- Diferenciais editoriais: orçamento iniciado por mensagem com dados do imóvel; instalação/reparo sujeitos à avaliação; informações para imóveis residenciais e comerciais; orientação para descrever o problema e enviar foto se conveniente.
- FAQ: quando instalar calhas; sinais de problema sem subir ao telhado; reparo versus troca; atendimento residencial e comercial; como solicitar orçamento.
- Situações para páginas locais: instalação em reforma/construção; vazamento em emenda ou fixação; limpeza de folhas e resíduos. Não presumir fatos específicos de bairro.

## Implementação

Site estático em HTML, CSS e JavaScript nativos, com 13 páginas HTML reais em diretórios `index.html`. O texto completo ficará no HTML de cada rota. Não haverá framework, dependências, banco ou servidor de aplicação. `build.js` copiará os arquivos para `dist`, em conformidade com o pacote de implantação solicitado para Vercel.

Arquivos compartilhados: `style.css`, `config.js`, `tracker.js`. Os números provisórios e endpoint ficam centralizados em `config.js`. O tracker reproduz a lógica fornecida no anexo, inclusive formulário rápido, UTMs, gclid, sessão e envio GET no-cors. O Apps Script será extraído sem alterações do anexo do usuário.

Rotas: inicial; três páginas de serviço; seis páginas de bairros; Sobre; Perguntas frequentes; Política de privacidade. Cada página terá title, descrição, canonical, OG/Twitter, H1 único, navegação/CTAs funcionais, ligações internas, aviso legal e dados estruturados aplicáveis. Serão criados sitemap, robots, llms, manifesto de rotas e favicon.

## Design

- **Movimento:** landing page editorial orgânica, inspirada em serviços residenciais locais acolhedores.
- **Princípios:** clareza, confiança sem alegações não confirmadas, leitura móvel e orientação prática.
- **Cores:** fundo creme e azul profundo para unir confiança e contexto de manutenção residencial; verde reservado à ação WhatsApp.
- **Layout:** hero fotográfico largo com sobreposição escura, barra de navegação em pílula, formulário rápido sobreposto, alternância de seções creme/azul muito claro, blocos de conteúdo e CTA final arredondado.
- **Motivos:** cantos arredondados, selo discreto de atendimento local, ícones lineares simples.
- **Interação/animação:** alvos de toque grandes, foco visível, movimentos apenas discretos e desativados com `prefers-reduced-motion`.
- **Tipografia:** Fira Sans com fallback de sistema; títulos fortes e corpo legível.
- **Essência:** um ponto simples de contato para pessoas que precisam de serviço de calhas em Ribeirão Preto. Personalidade: claro, cuidadoso, direto.
- **Voz:** frases curtas e factuais; exemplos: “Conte onde está o imóvel e o que precisa ser feito.” / “A avaliação e os detalhes são informados pelo prestador.”
- **Marca:** wordmark textual com símbolo de linha de telhado/calha desenhado em SVG no favicon; azul `#1D4ED8` como assinatura.

## Estrutura do projeto

```text
index.html
servicos/<slug>/index.html
bairros/<slug>/index.html
sobre/index.html
perguntas-frequentes/index.html
politica-de-privacidade/index.html
img/{hero,sobre,<slug-de-servico>}.jpg
style.css, config.js, tracker.js
favicon.svg, sitemap.xml, robots.txt, llms.txt, manus-routes.json
package.json, build.js, vercel.json
apps-script/Code.gs, LEIA-ME.txt
```

Os textos de serviços serão únicos e terão ao menos 250 palavras por página; cada página de bairro terá ao menos 150 palavras originais sem afirmar características físicas não verificadas do local. Conteúdo técnico sobre trabalho em altura será cauteloso. A política de privacidade descreverá somente os registros de clique especificados e o tratamento posterior pelo prestador/WhatsApp.
