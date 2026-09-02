# Brum &amp; Mello — site oficial

Site institucional do **Brum &amp; Mello**, churrascaria de rodízio de churrasco e pizza
em Outeiro das Pedras, Itaboraí — RJ. No ar desde 2013.

## Stack

HTML, CSS e JavaScript puros. **Sem framework, sem build, sem dependências.**
O `index.html` é autocontido: todo o CSS e todo o JS moram dentro dele.
As únicas requisições externas são as fontes do Google Fonts.

Por isso não existe `package.json` nem etapa de compilação — o repositório
já é exatamente o que vai pro ar.

## Estrutura

```
index.html                 página inteira (CSS + JS embutidos)
vercel.json                cabeçalhos de cache e segurança
robots.txt
favicon-32.png             ícones gerados a partir do monograma
favicon-180.png
favicon-512.png
img/
  hero.jpg                 fotografia de fundo do hero
  monograma.jpg            logo da marca (header, marca d'água, footer)
  a-casa-por-dentro.jpg    tríptico da seção "A casa, por dentro"
  og.jpg                   preview de compartilhamento (1200x630)
  galeria/                 as 6 fotos da seção "Momentos que permanecem"
video/
  a-casa.mp4               vídeo ambiente da seção "A casa" (mudo, em loop)
```

## Rodar localmente

Qualquer servidor estático serve. Abrir o arquivo direto pelo `file://`
também funciona, com a ressalva de que alguns navegadores bloqueiam o
autoplay do vídeo nesse modo.

```bash
python -m http.server 5173
# depois: http://localhost:5173
```

## Deploy

Projeto estático. Na Vercel:

- **Framework Preset:** Other
- **Build Command:** (vazio)
- **Output Directory:** (vazio — a raiz do repositório)
- **Install Command:** (vazio)

O `vercel.json` já cuida do cache dos assets e dos cabeçalhos de segurança.

## Depois do primeiro deploy

No `<head>` do `index.html`, trocar por URLs absolutas:

- `og:image` → `https://SEU-DOMINIO/img/og.jpg`
- adicionar `og:url` → `https://SEU-DOMINIO/`

Sem isso o preview de link no WhatsApp e nas redes não carrega a imagem.

## Conteúdo ainda pendente

Estes pontos aparecem no site como placeholder identificado e esperam
material real do restaurante:

- **Cardápio** — as três categorias (carnes, pizzas, vinhos) estão com
  "Item a definir". A estrutura está pronta para receber os itens.
- **Localização** — o slot ao lado do endereço espera um mapa em estilo
  escuro ou uma foto da fachada.
- **Seção "A casa"** — a "história completa" está marcada como a fornecer.
- **Horário de funcionamento** — aparece como "a confirmar" em dois lugares.
- **Descrições das 4 experiências** — churrasco, pizza, vinhos e celebrações
  estão com "descrição a fornecer".

## Informações da marca

- Endereço: Av. Vinte e Dois de Maio, 3428 — Outeiro das Pedras, Itaboraí - RJ, 24812-222
- Reservas: WhatsApp `+55 21 97222-8399`
- Instagram: [@brumemello_](https://instagram.com/brumemello_)

## Identidade

| | |
|---|---|
| Grafite | `#0C1014` |
| Verde oliva | `#37442A` |
| Verde oliva secundário | `#506635` |
| Oliva de texto | `#9BAE83` |
| Off-white | `#E9E7DF` |
| Títulos | Cormorant Garamond |
| Textos e navegação | Jost |
