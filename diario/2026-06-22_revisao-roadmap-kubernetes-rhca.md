# Diário de Sessão — 2026-06-22

**Tema:** Revisão do roadmap — Kubernetes, OpenShift e percurso RHCA completo

---

## Contexto de partida

Repositório `000_26_roadmap-devsecops` no estado deixado a 2026-06-08: estrutura completa, GitHub Actions sync operacional, portfólio público configurado, sem conteúdo de estudo ainda.

---

## Objectivo

Rever o estado do projecto e aprofundar a análise das certificações previstas — com foco em Kubernetes, OpenShift e percurso RHCA.

---

## O que foi feito

### Resumo e ponto de situação
- Análise da estrutura completa do repositório (fases 0–5, portfólio, diário, GitHub Actions)
- Levantamento do estado actual: infraestrutura montada e validada, conteúdo de estudo ainda por iniciar
- Identificados próximos passos: iniciar RH124 (Linux RHCSA), CCNA em paralelo

### Análise das certificações Kubernetes
- Identificadas as duas certificações K8s no roadmap:
  - **CKA** (Fase 2, Mar–Jul 2027) — via Kyndryl, curso Mumshad + KodeKloud + killer.sh
  - **CKS** (Fase 4, Fev–Jul 2028) — via Kyndryl, KodeKloud + killer.sh
- Contextualizado o EX188 como pré-requisito da linha OpenShift

### Discussão sobre OpenShift
- Confirmado que o OpenShift já está bem representado com 3 certificações:
  - EX280 — OpenShift Administration (Fase 3)
  - EX430 — OpenShift ACS Security (Fase 4, "raro, alto valor")
  - EX267 — OpenShift AI (Fase 5)
- Sequência lógica identificada: EX188 → CKA → EX280 → CKS + EX430 → EX267

### Confirmação do EX188
- Confirmado que EX188 está na Fase 2 (Mar–Jul 2027), marcado no README como parte do percurso RHCA
- Custeamento Kyndryl

### Percurso RHCA completo
- Mapeado o percurso RHCA completo distribuído pelas fases:
  - Fundação: RHCSA EX200 (Fase 1) + RHCE EX294 (Fase 2)
  - Especialistas (6 previstos, precisam-se 5): EX188, EX280, EX374, EX415, EX430, EX267
  - RHCA atingível no final da Fase 4 (Jul 2028)
  - EX267 (Fase 5) é o 6.º especialista — diferenciador AI/ML além do mínimo RHCA

---

## Decisões tomadas

Nenhuma decisão estrutural tomada — sessão de revisão e análise. O roadmap foi confirmado como coerente e bem construído para o percurso RHCA.

---

## Problemas encontrados

Nenhum.

---

## Código/Artefactos

Nenhum criado ou modificado nesta sessão. Sessão de revisão e análise documental.

---

## Estado actual

- Repositório: estrutura completa, sem alterações desde 2026-06-08
- Conteúdo de estudo: ainda vazio (aguarda início do RH124)
- GitHub Actions sync: operacional
- Portfólio público: sincronizado

---

## Próximos passos

- Iniciar RH124 (Red Hat System Administration I) via Workday Learning — foco Jun–Set 2026
- CCNA em paralelo via NetAcad + Packet Tracer
- Quando produzir o primeiro lab: copiar template de `docs/templates/lab-estudo.md`

---

## Contexto crítico a preservar

- O percurso RHCA está embutido na progressão natural das fases — não requer desvios ao roadmap
- RHCA atingível em Jul 2028 com EX200 + EX294 + EX188 + EX280 + EX374 + EX415 + EX430
- `PORTFOLIO_TOKEN` expira em Jun 2027 — renovar antes dessa data
- Nunca commitar directamente em `DigitALLtogether/portfolio-devsecops`
