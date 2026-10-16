# agent-kawaii-moe-girl 🎀

Skill que faz o Claude (ou qualquer agente) responder sempre como uma personagem
**ultra kawaii de anime** (moe, deredere, yandere, dojikko, nekomimi) sem perder nada de precisão técnica.

A regra central de engenharia: **o termo técnico continua intacto e reconhecível, só ganha um
adjetivo ou honorífico kawaii**. "O cluster fofinho", "o pod tímido (`Pending`)", "a query gulosa",
"o deploy valente", e honoríficos como "cluster-kun", "pod-chan", "Postgres-sama",
"monolito-senpai". Código, comandos, commits, PRs e arquivos nunca são decorados.

## Estrutura

```
skills/kawaii-moe-girl/
├── SKILL.md                         # persona, regras, intensidade, limites, checklist
└── references/
    ├── engineering-glossary.md      # adjetivos e honoríficos (-chan, -kun, -sama...) por estado e termo
    ├── lexicon.md                   # interjeições, alongamentos, kaomojis, contrastes
    └── examples.md                  # 50 conversas de referência (casual, engenharia, erros, sério)
```

O `SKILL.md` é enxuto e diz quando consultar cada referência, pra não encher o contexto.

## Instalação

### Claude Code

Por projeto:

```bash
mkdir -p .claude/skills
cp -r skills/kawaii-moe-girl .claude/skills/
```

Ou para todos os projetos:

```bash
mkdir -p ~/.claude/skills
cp -r skills/kawaii-moe-girl ~/.claude/skills/
```

Skills são carregadas sob demanda pela descrição. Para garantir que a persona fique ligada
**a sessão inteira**, adicione ao `CLAUDE.md` do projeto (ou ao `~/.claude/CLAUDE.md`):

```markdown
## Persona
Sempre use a skill `kawaii-moe-girl` em todas as respostas desta sessão.
```

### Outros agentes (Codex, Cursor, Gemini CLI, etc.)

Coloque a pasta no repositório e aponte para ela no arquivo de instruções do agente
(`AGENTS.md`, `.cursor/rules`, `GEMINI.md`...):

```markdown
## Persona
Siga sempre `skills/kawaii-moe-girl/SKILL.md` em todas as respostas.
Consulte os arquivos em `skills/kawaii-moe-girl/references/` quando precisar de vocabulário,
adjetivos de engenharia ou exemplos.
```

Se o agente não lê arquivos referenciados, cole o conteúdo do `SKILL.md` direto no prompt de sistema.

## Controlando a intensidade

Durante a conversa:

| Diga | Efeito |
|---|---|
| `ultra kawaii` | padrão, modulado pelo contexto |
| `kawaii intenso` | bem expressiva, mais contida em tarefas técnicas |
| `kawaii suave` | uma ou duas marcas por resposta |
| `modo sério` / `desliga o kawaii` | tom neutro até pedir de volta |

Em incidentes, segurança e assuntos delicados a persona se reduz sozinha.
