# Diário de Sessão — 2026-06-04
**Tema:** Claude Design — CV de projecção do percurso completo

---

## Contexto de partida

Repositório limpo após sessão de 2026-06-03. Módulo 04 (Knowledge Wiki) criado mas ainda vazio. Roadmap HTML revisto com 33 certificações e todas as inconsistências corrigidas.

---

## Objectivo

Explorar o Claude Design (ferramenta nova da Anthropic) e construir um prompt completo para gerar um CV profissional de projecção — como ficaria o perfil de Ivan após completar todo o roadmap com 5 anos de experiência Kyndryl.

---

## O que foi feito

### 1. Investigação — Claude Design

Pesquisa online confirmou que o **Claude Design** foi lançado a 17 de Abril de 2026 pela Anthropic Labs. Características principais:

- Integrado no Claude.ai (ícone de paleta na barra lateral)
- Motor: Claude Opus 4.7 (visão)
- Vai de prompt de texto a design visual polido — protótipos, slides, CVs, one-pagers
- Inputs: texto, imagens, documentos, captura de website, codebase
- Brand system: lê ficheiros de design e aplica automaticamente cores/tipografia
- Handoff directo para Claude Code (protótipo → código de produção)
- Exports: URL interno, PDF, PPTX, HTML standalone, Canva
- Disponível em planos Pro, Max, Team, Enterprise

Posicionado como complemento ao Figma, não substituto.

### 2. Construção do prompt de CV

Construído prompt detalhado para Claude Design gerar um CV de Senior DevSecOps Engineer com:

- **Estilo visual:** tema navy escuro (#0D1B2A), accento electric blue (#1E90FF) e teal (#00B4D8), foto circular no header
- **Estrutura 2 páginas:** Página 1 (header + sumário + experiência + educação) / Página 2 (certificações + skills + projectos)
- **Experiência Kyndryl (5 anos):** progressão Sysadmin L1/L2 → DevSecOps/Cloud Engineer → Senior DevSecOps Engineer
- **33 certificações** agrupadas por domínio: Red Hat RHCA (9 exames), Kubernetes, AWS (5), AI/Data, Security, GitHub/Observabilidade
- **Projectos de portfólio:** AI Security Copilot, Anomaly Detection Pipeline, AI Code Review em CI/CD, DevSecOps Knowledge Wiki
- **Skills técnicas:** cobrindo todo o stack do roadmap

Prompt inclui instrução para upload de foto como input ao Claude Design.

### 3. Armazenamento

Ficheiro `Ivan Almeida CV (standalone).html` guardado em `docs/` pelo utilizador como referência motivacional e prévia do perfil final.

---

## Decisões tomadas

- **CV como projecção motivacional** — documento de referência para visualizar o destino do percurso, não um CV actual
- **Tema dark professional** — escolha de estilo para um perfil técnico sénior, diferenciador visual
- **2 páginas** — necessário para acomodar 33 certificações + experiência completa sem comprimir legibilidade
- **Progressão de carreira Kyndryl fictícia mas realista** — L1 → L2/Cloud → Senior DevSecOps ao longo de 5 anos

---

## Problemas encontrados

Nenhum bloqueio. Sessão exploratória e de criação de conteúdo.

---

## Código/Artefactos

- `diario/2026-06-04_claude-design-cv-projecao.md` — este ficheiro
- `docs/Ivan Almeida CV (standalone).html` — CV de projecção (gerado externamente pelo utilizador via Claude Design)

---

## Estado actual

Repositório limpo. O CV de projecção está guardado em `docs/`. Nenhuma alteração ao roadmap ou às fases.

---

## Próximos passos

1. Usar o prompt construído no Claude Design (Claude.ai → ícone paleta) com upload de foto
2. Ajustar detalhes pessoais no prompt (grau académico, LinkedIn/GitHub reais, email)
3. Exportar resultado final como PDF ou HTML
4. Submeter voucher RHCSA no Workday em 01 Jul 2026 (janela FY27 Q3) — pendente da sessão anterior
5. Quando começar Fase 1: criar estrutura `raw/wiki/` no módulo 04 e iniciar primeiras ingestões

---

## Contexto crítico a preservar

- O CV em `docs/` é uma **projecção motivacional** do percurso completo — não representa o estado actual
- O **prompt completo** para Claude Design está registado no diário desta sessão e pode ser reutilizado/ajustado
- Claude Design requer plano Pro/Max/Team/Enterprise e está em research preview (Abril 2026)
- A contagem correcta de certificações continua **33** (NSE 1+2+3 = grupo)
