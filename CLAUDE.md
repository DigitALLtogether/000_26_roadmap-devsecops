# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## O que é este repositório

Não é um projecto de software com build/test — é um repositório documental e técnico em crescimento.

## Estrutura de fases

| Pasta | Período | Foco |
|-------|---------|------|
| `fase-0-fundacoes/` | Jun 2026 – Fev 2027 | Linux, Redes, Python, AWS CCP, Segurança básica |
| `fase-1-containers-iac/` | Mar – Jul 2027 | Docker, Kubernetes, Terraform, Ansible, Supply Chain |
| `fase-2-devsecops-core/` | Ago 2027 – Jan 2028 | OpenShift, Vault, OWASP, Observabilidade |
| `fase-3-pro-security/` | Fev – Jul 2028 | AWS Pro/Security, CKS, OpenShift ACS, Palo Alto |
| `fase-4-ia-aplicada/` | 2029+ | AI/ML aplicado a DevSecOps, projectos de portfólio |
| `diario/` | Contínuo | Registo semanal de progresso |

## Convenções de nomes e conteúdo

**Diário semanal** (`diario/`): ficheiros com formato `AAAA-WNN-tema.md`  
Exemplo: `2026-W23-inicio-percurso.md`

**Dentro de cada módulo** (ex: `fase-0-fundacoes/linux-rhcsa/`):
- `notas/` — resumos e apontamentos teóricos
- `labs/` — relatórios e ficheiros produzidos em ambiente prático
- `scripts/` ou `manifests/` ou `playbooks/` ou `configs/` — artefactos executáveis, conforme o módulo

**READMEs:** cada fase e cada módulo tem o seu próprio README com contexto, certificações-alvo e descrição das subpastas.

## Regras de segurança (.gitignore)

Nunca commitar:
- Credenciais: `*.pem`, `*.key`, `*.env`, `.env*`, `secrets/`, `credentials/`
- Estado do Terraform: `*.tfstate`, `*.tfstate.backup`, `.terraform/`

## Fluxo de trabalho editorial

Ao adicionar conteúdo novo:
1. Colocar na subpasta correcta dentro da fase/módulo correspondente.
2. Se for um lab ou script novo, verificar se o módulo já tem README — actualizar se necessário.
3. Registar progresso no diário semanal (`diario/AAAA-WNN-tema.md`), incluindo horas, o que foi feito e o que ficou pendente.
4. Commits em português, com mensagem descritiva do artefacto adicionado.
