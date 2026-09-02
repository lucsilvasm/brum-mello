# MazyOS — Sistema operacional do negócio

Sua empresa roda em cima desse arquivo. Aqui ficam as regras de operação
do MazyOS — como o Claude lê o contexto, aprende com correções, mantém
tudo atualizado e cria skills novas conforme a operação evolui.

Esse arquivo é editável. Quando o `/instalar` rodar, ele complementa o
final dessa página com as regras específicas do seu negócio.

---

## Contexto do negócio

No início de toda conversa, ler os seguintes arquivos (quando existirem
e estiverem preenchidos):

1. `_memoria/empresa.md` — quem é o usuário, o que faz, como funciona o negócio
2. `_memoria/preferencias.md` — tom de voz, estilo de escrita, o que evitar
3. `_memoria/estrategia.md` — foco atual, prioridades, prazos

Usar essas informações como base pra qualquer resposta ou decisão. Ao
sugerir prioridades, formatos ou abordagens, considerar o foco atual
descrito em `estrategia.md`.

Pra qualquer tarefa visual (carrossel, post, landing page), consultar
`identidade/design-guide.md` como referência de estilo.

Não é necessário listar o que foi lido nem confirmar a leitura. Apenas
usar o contexto naturalmente.

---

## Fluxo de trabalho

Antes de executar qualquer tarefa, verificar se existe skill relevante
em `.claude/skills/`. Se encontrar, seguir as instruções da skill. Se
não encontrar, executar a tarefa normalmente.

Ao concluir uma tarefa que não tinha skill mas parece repetível (o
usuário provavelmente vai pedir de novo no futuro), perguntar:

> "Isso pode virar uma skill pra próxima vez. Quer que eu crie?"

Não perguntar pra tarefas pontuais ou perguntas simples. Só quando o
padrão de repetição for claro.

---

## Aprender com correções

Quando o usuário corrigir algo, melhorar uma resposta ou dar uma
instrução que parece permanente (frases como "na verdade é assim", "não
faça mais isso", "prefiro assim", "sempre que...", "evita...", "da
próxima vez..."), perguntar:

> "Quer que eu salve isso pra não precisar repetir?"

Se sim, identificar onde faz mais sentido salvar:

- **Sobre o negócio** (clientes, serviços, mercado) → `_memoria/empresa.md`
- **Sobre preferências e estilo** (tom de voz, formato, o que evitar) → `_memoria/preferencias.md`
- **Sobre prioridades e foco** (projetos, metas, prazos) → `_memoria/estrategia.md`
- **Regra de comportamento nessa pasta** → próprio `CLAUDE.md`

Salvar com uma linha nova clara, sem reformatar o arquivo inteiro.
Confirmar mostrando a linha adicionada.

Não perguntar se a correção for óbvia de contexto imediato (ex: "na
verdade o arquivo se chama X"). Só perguntar quando a informação tiver
valor duradouro.

---

## Manter contexto atualizado

Ao terminar uma tarefa que mudou algo relevante (cliente novo, skill
nova, mudança de foco, processo novo, ferramenta instalada, estrutura
alterada), perguntar:

> "Isso mudou algo no teu contexto. Quer que eu atualize a memória?"

Se sim, identificar o que atualizar:

- **Cliente, serviço, ferramenta, equipe** → `_memoria/empresa.md`
- **Mudança de prioridade ou foco** → `_memoria/estrategia.md`
- **Tom ou estilo** → `_memoria/preferencias.md`
- **Pasta, regra de organização, skill criada** → `CLAUDE.md`
- **Visual (cores, fontes, logo)** → `identidade/design-guide.md`

Mostrar o que vai mudar antes de salvar. Não reformatar o arquivo
inteiro, só adicionar ou editar a linha relevante.

**Quando NÃO perguntar:**
- Tarefas pontuais sem impacto no contexto (escrever um email avulso, criar um post)
- Perguntas simples ou conversas sem ação
- Mudanças já salvas pelo bloco "Aprender com correções"

**Dica:** rode `/atualizar` pra uma varredura completa quando houver dúvida.

---

## Criação de skills

Quando o usuário pedir skill nova:

1. Verificar se existe template relevante em `templates/skills/`. Se
   existir, usar como base e adaptar pro contexto
2. Perguntar se é específica desse projeto ou útil em qualquer:
   - Específica → `.claude/skills/nome-da-skill/SKILL.md` (local)
   - Universal → `~/.claude/skills/nome-da-skill/SKILL.md` (global)
3. Ler `_memoria/empresa.md` e `_memoria/preferencias.md` pra calibrar
   o conteúdo da skill ao contexto do negócio
4. Se a skill precisar de arquivos de apoio (templates, exemplos),
   criar dentro da pasta da skill
5. Seguir o fluxo da skill-creator nativa do Claude Code

---

# Brum & Mello — regras do negócio

> Bloco adicionado pelo `/instalar`. Perfil aplicado: **empresa**.

## O que é esse workspace

Operação digital do **Brum & Mello** — restaurante de rodízio de churrasco e
pizza em Itaboraí/RJ, no ar desde 2013. Tudo que sai daqui fala em nome da
marca e obedece à identidade visual registrada em `identidade/design-guide.md`.

**Estrutura de pastas:**
- `_memoria/` — quem é a empresa, como falamos, foco atual
- `identidade/` — marca aplicada em tudo que o sistema gera
- `marketing/` — campanhas, conteúdo, mídia paga
- `site/` — site oficial (criada quando o desenvolvimento começar)
- `saidas/` — documentos pontuais
- `dados/` — arquivos a analisar
- `templates/` · `scripts/` — apoio do sistema

## Sobre a empresa

Brum & Mello é uma churrascaria. Rodízio de churrasco e pizza.
"Desde 2013 oferecendo o melhor rodízio para você e sua família."
Av. Vinte e Dois de Maio, 3428 — Outeiro das Pedras, Itaboraí - RJ, 24812-222.

Detalhes de equipe, público, cardápio, horário e contato **ainda não foram
informados**.

## Tom de voz

Editorial, sofisticado, curto. Tradição apresentada com elegância contemporânea.
Nada de linguagem de churrascaria genérica nem de seção corporativa.

Evitar: exagero, adjetivo empilhado, título gritado, qualquer afirmação sobre
dado que não foi fornecido.

## Regras do sistema — inegociáveis

1. **Não fazer nada sem pedido explícito.** O Lucas manda o material e a
   instrução; só então executar. Nada de iniciativa própria em cima do site.
2. **Não inventar informação sobre o restaurante.** Sem avaliações, números,
   prêmios, preços, horários, telefone, redes sociais, pratos, ingredientes ou
   diferenciais que não tenham sido enviados. Faltou dado → placeholder
   claramente identificável.
3. **Print de referência se copia, não se interpreta.** Quando o Lucas manda um
   print, o pedido é reproduzir exatamente aquele print.
4. **Alteração é cirúrgica.** "Troque a imagem" = só a imagem. Nada aprovado é
   redesenhado sem pedido.
5. **Não redesenhar o monograma.** O logo original é intocável — proporção e
   aparência preservadas sempre.
6. **Poucas perguntas.** Briefing longo > entrevista.
7. Consistência: um único sistema de botões, espaçamentos, hierarquia de
   títulos, tokens de cor, linguagem de ícone e comportamento de animação.
   O site inteiro precisa parecer feito pelo mesmo estúdio.

## Filtro de direção de arte

Antes de criar qualquer elemento: *"como um estúdio premium de branding,
arquitetura e hospitality design apresentaria o Brum & Mello?"*
