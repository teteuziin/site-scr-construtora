# Site SCR Construtora — pacote de construção (FASE 2, nº10)

## ⚠️ NÃO PUBLICAR sem aprovação do usuário
Este pacote é uma prévia para aprovação. A publicação no GitHub Pages só acontece depois do "ok" do usuário, como em todas as empresas da fase 2.

## Declarações de design (Anti-Slop Website Builder v2, Seção 13)

- **Design Read (1 linha):** site institucional de construtora boutique de alto padrão para compradores e investidores do Caminho das Árvores (Salvador/BA), com linguagem editorial premium e tátil de canteiro — papel quente, tinta azul-marinho e o teal da marca.
- **Dials:** DESIGN_VARIANCE **7** / MOTION_INTENSITY **5** / VISUAL_DENSITY **4**.
  - Variance 7: seções numeradas em grid de 12 colunas com mídia assimétrica e blocos de empreendimento com arranjos variados (nada de grid de cards iguais).
  - Motion 5: o conteúdo já é vídeo; o motion é só de leitura — reveal de título por linha (line mask), número da seção com scale 0,9→1, recorte de mídia por clip-path — tudo scroll-driven em CSS (`animation-timeline: view()`), com fallback estático digno e `prefers-reduced-motion` respeitado. Sem fade-in-up, sem bounce, sem transition-all.
  - Density 4: premium respira; especificações em listas sóbrias, uma mensagem por seção.
- **Direção estética positiva:** Editorial + tactile realism (combinação declarada na skill). Editorial: serifada de display, numeração grande de seção, especificações em tabela limpa. Tactile: paleta de papel/tinta/teal amostrado da marca, mídia real emoldurada com sombra física, zero vidro/gradiente decorativo.
- **Tokens de tipo:** display **Fraunces** (560/640, opsz, tracking −0,02em, `text-wrap: balance` nos títulos grandes); corpo/UI **Archivo** (400/500/700/800, números tabulares). Nenhuma fonte da lista banida.
- **Tokens de cor:** papel `#F4F1EA`, papel alt `#ECE7DB`, superfície `#FBF9F4`, tinta `#0F1B2D`, tinta 2 `#22344E`, texto secundário `#44536A`, teal profundo `#1C5D6B` (texto/CTA — AA sobre o papel), teal vivo `#35919E` (só elemento gráfico), faixa escura `#0C1728`, foco visível `#B4552D` (laranja de obra, contraste alto em qualquer fundo). Sem `#000`/`#fff` puros. Teal e azul-marinho amostrados da logo dela (navy + teal).
- **Quebra de layout:** hero 50/50 (texto × vídeo vertical); seções numeradas 01–06 no grid do usuário (número+título col. 1–4, texto 5–7, mídia 8–12; mobile empilha número→título→texto→mídia); galeria do EGEU assimétrica (12 colunas, larguras variadas); blocos de empreendimento alternando arranjo de mídia; separação só por respiro vertical (4–6rem), nenhuma linha solta entre seções.

## Regras de conteúdo cumpridas
- **Preço: NENHUM.** `grep 'R$'` no HTML = 0. Valores de revenda de corretores (terceiros) ficaram fora, como manda o dossiê.
- **CTA único:** WhatsApp (71) 98340-5608 → `wa.me/5571983405608` (número da arte oficial dela). Telefone fixo (71) 3019-2394 **fora**.
- **Endereço do escritório FORA do site** (decisão registrada): a ficha do Google indica Ed. São Conrado Offices, R. Sd. Luiz Gonzaga das Virgens, 138, Caminho das Árvores — endereço só de ficha de terceiro, sem confirmação no material dela; seguindo a recomendação do dossiê ("na dúvida, fora"), o site usa só o bairro. O CNPJ 31.408.234/0001-04 (registro público da SCR - CONSTRUTORA LTDA) entra no rodapé, como é padrão em site de construtora.
- **Google sem nota** (rating nulo) — nenhuma avaliação impressa.
- **40 anos = trajetória do Sérgio; empresa desde 2018** — nunca misturados (hero diz "trajetória do fundador"; a seção 05 diz "nasceu em 2018, fundada por Sérgio Rego — que soma 40 anos").
- **Voz dela, 1ª pessoa:** "Sonhar, construir, realizar!", "Onde a família está, o futuro se constrói.", "Maestro, um projeto afinado com os seus sonhos", "A cada etapa, o projeto ganha forma.", "#gestãotransparente".
- **Domínio dela (scrconstrutora.com.br) NÃO abre** — verificado por três vias em 18/11/2026. Nada sobre isso aparece no site (regra do dossiê); é só o gancho da abordagem.
- **Depoimentos de destaques NÃO afirmados** (conteúdo dos destaques não é verificável sem login). Prova social = vídeos dela + empreendimentos entregues.
- **Renders legendados como projeto** nas legendas (torre do Maestro, Riserva pronto, living do decorado, piscina); fotos aéreas e de obra são reais e legendadas como foto.
- **Mapa do bairro usado como exceção consciente**: os rótulos dos empreendimentos na imagem SÃO o conteúdo.
- Pôsteres são frames dos próprios vídeos dela (com a grafia original dos vídeos) — não são fotos editadas pelo site.

## Mídias (media/) — 13 vídeos, todos com áudio (ffprobe)
Ver tabela completa no relatório de entrega e no catálogo do dossiê (`../scr-construtora-portfolio/README.md`).
Recompressões (áudio copiado sem recodificar, `-c:a copy`): egeu-tour 35,2→18,2 MB; licia-depoimento 29,7→23,6 MB; riserva-arquiteto e egeu-acabamentos e bairro-apresentadora idem (tamanhos no dossiê). Todos os arquivos < 25 MB.

## Interatividade útil
- Players próprios: botão de play centralizado (visível no mobile), vídeo pausa ao sair da tela (IntersectionObserver 0,25) e **não retoma sozinho**; hover do frame com scale 1,02 só em desktop.
- **Montador de contato** na seção 06: empreendimento + o que quer saber + nome opcional → abre `wa.me/5571983405608` com a mensagem montada, com prévia ao vivo da mensagem.

## Gate e pre-flight
- Gate manual: **24/24** (ver relatório de entrega).
- Tell Score estimado: **~12/100**.
- Testes 390/768/1440: layout verificado por construção (container 1400px, grid com empilhamento mobile, wrappers 9/16 máx. 350px, `overflow-x: hidden` + mídia `max-width: 100%`); a conferência visual fina no aparelho é do usuário, como no padrão da missão.
- Contraste: corpo `#0F1B2D` sobre `#F4F1EA` ≈ 15:1; secundário `#44536A` ≈ 7:1; teal de CTA `#1C5D6B` ≈ 6,3:1 (AA em texto normal e grande).

## Correção de espaçamento — 18/11/2026

Auditoria do usuário achou o micro-espaçamento "no olho", fora do sistema rígido de 8px. Correção aplicada **só em valores de padding/margin/gap** — conteúdo, textos, mídias, cores, fontes e layout intactos (diff do CSS mostra apenas valores de espaçamento; fora do `<style>`, só mudaram os `margin-top` inline das legendas `.figcap`, que também estavam fora da régua). Cada valor foi normalizado para o múltiplo de 0,5rem mais próximo; empates resolvidos pela função do elemento (`.skip`: link utilitário compacto → arredonda pra baixo; `.hero-stats`: blocos de dados distintos → 1,5rem, alinhado aos gaps de grupo do site). O teto do respiro das seções caiu de 6,5rem para **6rem**, como manda a especificação do usuário (4rem mobile / 6rem desktop).

**Verificação:** script sobre o CSS final (blocos `<style>` + estilos inline) — 83 valores de espaçamento, **100% múltiplos de 0,5rem**. Exceções ópticas intencionais, mantidas e declaradas: `.mask-line` (`padding-bottom:.08em` / `margin-bottom:-.08em` — compensação da máscara de linha do reveal de título) e `.playbtn .tri` (`margin-left:5px` — centralização óptica do triângulo de play).

| Seletor | Propriedade | De | Para |
|---|---|---|---|
| .skip | padding | .75rem 1.25rem | .5rem 1rem |
| .header-in | padding-block | .8rem | 1rem |
| nav.main a | padding | .35rem 0 | .5rem 0 |
| .btn | gap | .55rem | .5rem |
| .btn | padding | .85rem 1.6rem | 1rem 1.5rem |
| .btn.small | padding | .6rem 1.15rem | .5rem 1rem |
| .eyebrow | margin-bottom | 1.4rem | 1.5rem |
| .eyebrow | gap | .8rem | 1rem |
| .hero-sub | margin-top | 1.6rem | 1.5rem |
| .hero-ctas | margin-top | 2.2rem | 2rem |
| .hero-stats | gap | 1.25rem | 1.5rem |
| .stat span | margin-top | .35rem | .5rem |
| .hero-media | gap | .9rem | 1rem |
| section.sec | padding-block | clamp(4rem, 8vw, 6.5rem) | clamp(4rem, 8vw, 6rem) |
| .sec-text | padding-top | .4rem | .5rem |
| .sec-num | margin-bottom | 1.1rem | 1rem |
| .sec-text p + p | margin-top | 1.1rem | 1rem |
| .pull | margin-top | 1.6rem | 1.5rem |
| figure.shot figcaption | margin-top | .6rem | .5rem |
| .specs | margin-top | 1.6rem | 1.5rem |
| .specs li | padding | .65rem 0 | .5rem 0 |
| .dev-head | gap | .6rem 1.4rem | .5rem 1.5rem |
| .dev-head | margin-bottom | 1.2rem | 1rem |
| .tag | padding | .32rem .8rem | .5rem 1rem |
| .dev .media-row | margin-top | 1.8rem | 2rem |
| .steps li | gap | 1.1rem | 1rem |
| .steps li | padding | 1.05rem 0 | 1rem 0 |
| .builder | padding | 1.8rem | 2rem |
| .builder label | margin-bottom | .45rem | .5rem |
| .builder select, .builder input | padding | .85rem 1rem | 1rem 1rem |
| .builder select, .builder input | margin-bottom | 1.3rem | 1.5rem |
| .builder .preview | padding | 1rem 1.1rem | 1rem 1rem |
| .builder .preview | margin-bottom | 1.4rem | 1.5rem |
| .builder .preview b | margin-bottom | .4rem | .5rem |
| .contact .direct | margin-top | 1.6rem | 1.5rem |
| footer.site | padding-block | 2.6rem 3rem | 2.5rem 3rem |
| .footer-in | gap | 1.6rem 3rem | 1.5rem 3rem |
| footer.site .tagline | margin-top | .8rem | 1rem |
| .figcap (inline, 12×) | margin-top | .9rem | 1rem |
