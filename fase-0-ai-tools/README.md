# Fase 0 — AI Tools & Claude Code Operating System

**Período:** Contínuo (transversal a todo o percurso)  
**Autoria dos cursos:** Nate Herk | AI Automation

> Fase transversal — Claude Code e Claude AI são os copilotos de todo este portfólio. Dominar estas ferramentas antes de começar as fases técnicas multiplica a capacidade de aprendizagem, documentação e automação ao longo de todo o percurso.

## Objectivo

Passar de utilizador casual do Claude a operador avançado do Claude Code: saber construir workflows, gerir contexto, integrar ferramentas via MCP, criar skills e subagentes, e configurar um AI Operating System pessoal que sirva de segundo cérebro durante o percurso DevSecOps.

## Módulos

| Pasta | Curso / Projecto | Duração | Descrição |
|-------|-----------------|---------|-----------|
| `01_build-sell-claude-code/` | Build & Sell with Claude Code | 10h+ | Fundamentos completos — de zero a operador avançado |
| `02_operating-systems/` | Build & Sell Claude Code Operating Systems | 2h+ | Arquitectura de um AI OS — frameworks 3 M's e 4 C's |
| `03_opus-ai-os/` | I Turned Claude Opus 4.8 Into My Entire AI Operating System | ~30min | Demonstração prática do setup em produção com Opus 4.8 |
| `04_devsecops-knowledge-wiki/` | DevSecOps Knowledge Wiki | contínuo | Sistema de conhecimento LLM Wiki (Karpathy) aplicado ao percurso DevSecOps |

## Transcrições de referência

Cada transcrição `.txt` está dentro do módulo correspondente, em `<módulo>/docs/`, junto das notas e labs. Recurso de referência directo durante o estudo de cada curso.

## Conteúdo por módulo

### 01 — Build & Sell with Claude Code (10h+)
24 capítulos, do contexto de mercado à monetização. Para este projecto, o foco está nos capítulos técnicos:
- Agentic AI landscape e porquê aprender Claude Code
- Setup, operações e modo de funcionamento
- Tokens, contexto e gestão de janela de contexto
- **CLAUDE.md** — o ficheiro de instruções do projecto (já em uso neste repo)
- **WAT Framework** — Workflows, Agents, Tools
- Deploy de automações (trigger.dev, modal)
- Arquitectura de projecto
- Built-in commands (`/` slash commands)
- RAG (Retrieval-Augmented Generation)
- APIs e MCPs (Model Context Protocol)
- **Skills e subagentes**
- **Agent teams**
- Browser automations
- Gestão de permissões
- **GitHub worktrees**
- Context management avançado

### 02 — Claude Code Operating Systems (2h+)
- **3 M's framework:** Mindset, Method, Machine
- **4 C's do AI OS:** Context, Connections, Capabilities, Cadence
- Arquitectura de um AI OS pessoal
- Mindset de automação: "default shift" — perguntar sempre "como pode AI fazer isto?"
- Function breakdown: decompor tarefas em blocos automatizáveis
- Curiosity rule: tratar AI como mentor, não como vending machine
- Abordagem tool-agnostic — a camada durável por baixo das ferramentas

### 03 — Opus 4.8 AI Operating System (~30min)
- Setup do "segundo cérebro" com Claude Opus 4.8
- Executive assistant pessoal
- Integração com contexto de negócio/estudo
- Optimização de tokens
- Evolução e manutenção do AI OS ao longo do tempo

## Estrutura de pastas

```
fase-0-ai-tools/
├── 01_build-sell-claude-code/
│   ├── docs/                     # Transcrição do curso (10h+)
│   ├── notas/                    # Resumos por capítulo
│   └── labs/                     # Exercícios práticos documentados
├── 02_operating-systems/
│   ├── docs/                     # Transcrição do curso (2h+)
│   ├── notas/                    # Resumos dos frameworks 3M e 4C
│   └── labs/                     # Setup e iteração do AI OS
├── 03_opus-ai-os/
│   ├── docs/                     # Transcrição do vídeo (~30min)
│   ├── notas/                    # Apontamentos da demonstração
│   └── labs/                     # Configuração prática do AI OS pessoal
└── 04_devsecops-knowledge-wiki/
    ├── docs/                     # Referências (transcript Karpathy, artigo original)
    ├── notas/                    # Arquitectura, decisões de design
    └── labs/                     # Setup e primeiras ingestões (raw/ + wiki/)
```
