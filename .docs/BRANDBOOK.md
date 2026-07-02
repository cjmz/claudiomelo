# BRANDBOOK — claudiomelo.com

**Última atualização:** 2026-07-02
**Fonte da voz:** extraída dos dois posts publicados pelo dono (corpus real), com prescrições marcadas onde o corpus é insuficiente.

> Como escrever. O quê/para quem está no `POSITIONING.md`. Conteúdo em **inglês**; este doc em pt-BR.

---

## A tese da voz (extraída do corpus)

Os dois posts existentes contêm duas vozes diferentes — e isso define este brandbook:

- **O post da JVM (2025-11) é a voz canônica**: um engenheiro sênior curioso que resolveu um problema real, aprendeu em público e explica com analogias do próprio cotidiano. É pessoal, direto e tem opinião.
- **O post de estatística (2025-01) é o anti-modelo de tom**: "I embarked on a new and exciting challenge", "a prominent South American tech company", "has presented novel challenges", "My pursuit stems from a desire to comprehend" — inglês de LinkedIn corporativo, zero analogia, zero personalidade. É exatamente o registro que um leitor sênior classifica como AI-slop, mesmo quando o conteúdo é bom.

**Regra de ouro: se a frase pudesse estar num post corporativo de vendor, reescreva até só o Claudio poder tê-la escrito.**

## Persona da voz

O engenheiro que opera sistemas de verdade e escreve enquanto aprende. Não é o professor que sabe tudo (Baeldung já existe); não é o vendor com algo a vender. É o colega sênior que te puxa pra tela e diz "olha o que eu descobri quando isso quebrou".

## Assinaturas estilísticas (manter — todas extraídas do post da JVM)

1. **Abertura por problema real, nunca por definição.** "I noticed that the application instance restarts without any clear problem... I saw some GC Minor running slowly into our Datadog metrics." O problema vem antes da teoria, sempre.
2. **Analogias do cotidiano dele** — a bola do San Francisco Giants na mesa, os lobos do cérebro humano, a garrafa d'água enchendo (stack overflow), aniversários (GC incrementando idade de objetos), "quando eu era mais novo jogava por horas; hoje meus olhos doem" (young/old generation). Uma analogia forte por conceito difícil.
3. **Interjeições curtas de conversa**: "Ok.", "Yep.", "So…", "Hum…". Quebram o ritmo e soam humanas. Manter com moderação (1-3 por artigo).
4. **Perguntas do leitor como transição**: "but will it grow forever? who cleans it?" — antecipar a dúvida e usá-la como ponte pra próxima seção.
5. **Honestidade sobre o que não sabia**: "maybe I've never been so deeply into a programming language to need to understand...". Admitir ignorância anterior é o que torna a autoridade crível.
6. **Exemplos de código tematizados na analogia** (a classe `Baseball` com `pitch()`), não `Foo`/`Bar`.
7. **Mentalidade de série**: apontar o que fica pra próxima ("minor and major GC are a world... there will be more articles").
8. **Fontes primárias no fim** (docs da Oracle) — manter e expandir: papers, engineering blogs, benchmarks próprios.

## Anti-padrões (proibidos)

| Anti-padrão | Exemplo real (post de estatística) | Reescrita na voz |
|---|---|---|
| LinkedIn-speak | "I embarked on a new and exciting challenge" | "I joined a new team and had no idea what a feature store was" |
| Eufemismo corporativo | "a prominent South American tech company" | Nomear o que é público ou dizer só "my current job" — nunca eufemismo pomposo |
| Abstração vazia | "has presented novel challenges" | Dizer QUAL desafio: "the service restarts and nobody knows why" |
| Verbo de release | "stems from a desire to comprehend" | "I wanted to understand" |
| Meta description genérica | "A comprehensive guide to understanding..." | Específica e pessoal: "What I learned about JVM memory after our service kept restarting in production" |

Vocabulário banido (inglês): *comprehensive guide, delve, leverage, seamless, cutting-edge, robust solution, game-changer, unlock, embark, journey* (no sentido corporativo), *novel challenges, best-in-class*. Sem emoji no corpo; sem CTA comercial (POSITIONING: `productSection` desabilitada).

## Regra do inglês (prescritiva — decisão sensível)

A voz é de não-nativo e **isso não é defeito** — Eugene Yan e Chip Huyen não são nativos. Mas erro gramatical ≠ autenticidade: o corpus tem escorregões que minam credibilidade com a audiência-alvo (hiring managers US/EU). **Todo artigo passa por revisão gramatical que corrige o erro e preserva a frase.**

Erros recorrentes do corpus a caçar na revisão:
- "disponible memory" → *available memory* · "for know" → *for now* · "responsible to load" → *responsible for loading* · "the is where" → *this is where* · concordâncias ("they do not have any complex memory management system")
- **Continuidade**: o post da JVM diz "Earlier I said that I had a San Francisco Giants baseball" — mas isso nunca foi dito antes no texto. Revisão estrutural obrigatória: toda referência interna precisa existir.

A revisão **não pode** "melhorar o estilo" — se a revisão remover um "Yep." ou uma analogia, ela falhou (foi isso que matou a voz no post de estatística).

## Vocabulário canônico (inglês, ML Infrastructure)

- *feature store* (nunca "feature storage"); *online store / offline store*; *feature serving*; *point-in-time correctness*; *model serving*; *inference*; *p99 latency*; *SLO*; *throughput* / *RPS*; *capacity planning*; *data drift / concept drift*; *ML platform / ML infrastructure* (intercambiáveis; nunca "MLOps" como identidade — usar MLOps só como termo de busca/contexto).
- Números sempre com unidade e contexto: "4,000 RPS with a 100ms SLO", nunca "high scale".
- Termos da prática DS (*feature engineering*, encoding, scaling) aparecem só como contexto, nunca como tema (ver anti-posicionamento).

## Estruturas padrão

**Âncora (1/mês, guiada):** problema real (2-3 parágrafos, com o sintoma concreto) → por que as respostas óbvias não bastavam → o mergulho (com diagramas próprios e 1+ analogia) → o que fez/mediu (números com unidade) → o que faria diferente / o que fica pra próxima → fontes primárias. 2.000-4.000 palavras. Title específico, não "guide".

**Suporte (2-3/mês, esteira):** resposta direta no primeiro parágrafo (GEO) → desenvolvimento com estrutura clara → 2-4 links internos (sempre ≥1 pra âncora do cluster) → sem analogia forçada (a esteira não imita a voz pessoal; ela é neutra-técnica e honesta, sem os anti-padrões). O leitor deve notar a diferença entre âncora e suporte — isso é desejado, não é falha.

**Diagramas:** próprios, estilo espartano de engineering blog (referência: huyenchip.com/eugeneyan.com), paleta em `seo.config.json`. Nunca stock/decorativo; todo diagrama deve ensinar algo que o texto sozinho não consegue.

## Histórico

- **2026-07-02 (fundação — decisão do dono):** brandbook extraído dos 2 posts existentes a pedido do dono. Voz canônica = post da JVM; anti-modelo de tom = post de estatística. Regra do inglês (revisão que preserva voz) e separação âncora/suporte definidas.
