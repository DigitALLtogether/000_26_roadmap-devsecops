# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## O que é este repositório

Não é um projecto de software com build/test — é um repositório documental e técnico em crescimento.

## Estrutura de fases

| Pasta | Período | Foco |
|-------|---------|------|
| `fase-0-ai-tools/` | Contínuo | Claude Code, AI Operating System, automação com IA |
| `fase-1-devsecops-foundations/` | Jun 2026 – Fev 2027 | Linux, Redes, Python, AWS CCP, Segurança básica |
| `fase-2-devsecops-fundamentals/` | Mar – Jul 2027 | Docker, Kubernetes, Terraform, Ansible, Supply Chain |
| `fase-3-devsecops-core/` | Ago 2027 – Jan 2028 | OpenShift, Vault, OWASP, Observabilidade |
| `fase-4-devsecops-pro-security/` | Fev – Jul 2028 | AWS Pro/Security, CKS, OpenShift ACS, Palo Alto |
| `fase-5-advanced-ai-applications/` | 2029+ | AI/ML aplicado a DevSecOps, projectos de portfólio |
| `diario/` | Contínuo | Diário de sessões de trabalho |

## Convenções de nomes e conteúdo

**Diário de sessão** (`diario/`): ficheiros com formato `AAAA-MM-DD_tema.md`  
Exemplo: `2026-06-01_inicio-percurso.md`

**Dentro de cada módulo** (ex: `fase-1-devsecops-foundations/linux-rhcsa/`):
- `notas/` — resumos e apontamentos teóricos
- `labs/` — relatórios e ficheiros produzidos em ambiente prático
- `scripts/` ou `manifests/` ou `playbooks/` ou `configs/` — artefactos executáveis, conforme o módulo

**READMEs:** cada fase e cada módulo tem o seu próprio README com contexto, certificações-alvo e descrição das subpastas.

## Regras de segurança (.gitignore)

Nunca commitar:
- Credenciais: `*.pem`, `*.key`, `*.env`, `.env*`, `secrets/`, `credentials/`
- Estado do Terraform: `*.tfstate`, `*.tfstate.backup`, `.terraform/`

## Fluxo de trabalho editorial

**Início de cada sessão:** correr `git pull` para garantir que o repositório local está sincronizado com o GitHub antes de editar qualquer ficheiro.

Ao adicionar conteúdo novo:
1. Colocar na subpasta correcta dentro da fase/módulo correspondente.
2. Se for um lab ou script novo, verificar se o módulo já tem README — actualizar se necessário.
3. Commits em português, com mensagem descritiva do artefacto adicionado.
4. Gerar o diário de sessão ao encerrar com `"Kody, encerra sessão."`.

## Instruções de fluxo de trabalho

### Encerramento de sessão

Gatilho: `"Kody, encerra sessão."` ou variação equivalente (ex: "fecha sessão", "termina sessão", "encerra a conversa").

Acção: gerar e guardar automaticamente um ficheiro em `diario/` com o formato `AAAA-MM-DD_tema.md`, onde o tema descreve o foco da sessão.

Secções obrigatórias:
- **Contexto de partida** — estado do projecto no início da sessão
- **Objectivo** — o que se pretendia fazer
- **O que foi feito** — resumo do trabalho realizado
- **Decisões tomadas** — escolhas relevantes e razões
- **Problemas encontrados** — bloqueios ou imprevistos
- **Código/Artefactos** — ficheiros criados ou modificados
- **Estado actual** — onde ficou o projecto
- **Próximos passos** — o que fazer na próxima sessão
- **Contexto crítico a preservar** — informação importante para continuidade

### Resumo de sessão

Gatilho: `"Kody, resume sessão."` ou variação equivalente (ex: "resume sessão", "resume a conversa").

Acção: resumir o estado actual completo do projecto — fases, conteúdo existente, pendentes e próximos passos. Usado tipicamente no início de cada sessão para reestabelecer contexto.

### Artefactos visuais

HTMLs e artefactos visuais nunca são gerados automaticamente nem por iniciativa própria. São gerados apenas quando o utilizador pede explicitamente.

Kody deve sugerir proactivamente quando faria sentido gerar um artefacto, indicando o tipo e o conteúdo que incluiria (ex: "Neste ponto faria sentido gerar um HTML com X e Y — queres que avance?"). O utilizador decide sempre se e quando gerar.
