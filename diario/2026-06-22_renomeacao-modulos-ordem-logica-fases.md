# Diário de Sessão — 2026-06-22 (2.ª sessão)

**Tema:** Renomeação de módulos de todas as fases com prefixo numérico de ordem lógica de execução

---

## Contexto de partida

Repositório sincronizado após sessão anterior (diário + commit + push do resumo de roadmap). O utilizador identificou uma inconsistência entre a Fase 0 (módulos já com prefixos numéricos: `01_`, `02_`, `03_`) e as Fases 1–5 (módulos sem qualquer ordenação numérica).

---

## Objectivo

1. Verificar o estado real do disco para todas as fases (revelou módulos não identificados na sessão anterior)
2. Propor a ordem lógica de execução de cada módulo em cada fase para aprovação
3. Renomear todos os módulos das Fases 1–5 com prefixo numérico
4. Actualizar o ficheiro `roadmap_devsecops.html` para reflectir as alterações
5. Commit e push — repositório remoto como espelho do local

---

## O que foi feito

### Descoberta de módulos não identificados previamente

A análise do disco revelou módulos que a primeira sessão tinha perdido devido a um bug no comando `find`:

**Fase 1:** `github-foundations` (GH-900) — não identificado antes
**Fase 2:** `aws-sysops`, `github-actions` — não identificados antes
**Fase 3:** `aws-developer`, `devsecops-foundation`, `github-advanced-security`, `seguranca-nse4` — não identificados antes
**Fase 4:** `openshift-acs-ex430`, `palo-alto-pcnsa` — não identificados antes
**Fase 5:** `aws-ai-ml`, `databricks`, `gcp-devops`, `github-copilot`, `nvidia-dli` — não identificados antes

### Também identificado: divergência Fase 0

O disco tem `01_claude-code`, `02_dat_ai_os`, `03_devsecops-knowledge-wiki`.
O git rastreava nomes diferentes (da iteração anterior). O HTML já usava os nomes correctos do disco — disco confirmado como fonte de verdade.

### Proposta de ordenação lógica — aprovada pelo utilizador

Critério: dependências de conhecimento — cada módulo prepara o seguinte.

| Fase | Ordem (resumo) |
|------|---------------|
| Fase 1 | linux → redes → python → aws-ccp → github-foundations → seguranca-nse |
| Fase 2 | docker → containers-ex188 → kubernetes-cka → terraform → ansible-rhce → github-actions → aws-sysops → supply-chain-security |
| Fase 3 | openshift-ex280 → ansible-aap-ex374 → aws-developer → security-ex415 → vault → owasp → seguranca-nse4 → devsecops-foundation → observabilidade → github-advanced-security |
| Fase 4 | kubernetes-cks → openshift-acs-ex430 → aws-security → aws-devops-pro → palo-alto-pcnsa → incident-response |
| Fase 5 | github-copilot → openshift-ai-ex267 → aws-ai-ml → nvidia-dli → databricks → gcp-devops → projectos |

### Renomeações efectuadas (git mv)

Todas as pastas de módulos das Fases 1–5 renomeadas com `git mv` — 131 ficheiros afectados, renomeações detectadas correctamente pelo git.

### HTML actualizado

`roadmap_devsecops.html` — actualizados os 2 paths de pastas explícitos na caixa de portfólio da Fase 1:
- `/fase-1-devsecops-foundations/linux-rhcsa/` → `/fase-1-devsecops-foundations/01_linux-rhcsa/`
- `/fase-1-devsecops-foundations/redes-ccna/` → `/fase-1-devsecops-foundations/02_redes-ccna/`

As restantes fases não tinham paths explícitos no HTML — sem alteração necessária.

---

## Decisões tomadas

- **Disco como fonte de verdade** para a Fase 0 — os nomes no disco prevalecem sobre o que o git rastreava.
- **Proposta apresentada antes de executar** — utilizador aprovou a ordenação antes de qualquer renomeação.
- **git mv em vez de rename manual** — garante que o git detecta as operações como renames e não como delete+create, preservando histórico.
- **HTML: alterações mínimas e correctas** — só os paths explicitamente referenciados foram actualizados; texto narrativo não foi alterado.

---

## Problemas encontrados

- Sessão anterior tinha perdido 13 módulos por bug no comando `find` (problema de precedência de operadores `-type f -o -type d` sem parênteses) — identificado e corrigido nesta sessão por leitura directa do disco.
- Divergência Fase 0: git vs. disco — resolvida confirmando o disco como correcto (o HTML já usava os nomes do disco).

---

## Código/Artefactos

| Acção | Detalhe |
|-------|---------|
| `git mv` × 37 operações | Todos os módulos Fases 1–5 renomeados com prefixo numérico |
| `roadmap_devsecops.html` | 2 paths actualizados na caixa de portfólio da Fase 1 |
| Commit `c291cb4` | 131 ficheiros, refactor de renomeação |
| Push para `origin/main` | Repositório remoto sincronizado |

---

## Estado actual

- Fases 0–5: todos os módulos com prefixo numérico de ordem lógica de execução
- Repositório local e remoto: sincronizados e espelhados
- HTML: consistente com a estrutura de pastas
- Fase 0: divergência git/disco pendente de resolução formal (baixa prioridade — conteúdo correcto no disco e no HTML)

---

## Próximos passos

- Iniciar RH124 (Linux RHCSA) — foco principal Jun–Set 2026
- Resolver formalmente a divergência Fase 0 entre git e disco (quando conveniente)
- Quando produzir o primeiro lab: usar template `docs/templates/lab-estudo.md` e commitar em `fase-1-devsecops-foundations/01_linux-rhcsa/labs/`

---

## Contexto crítico a preservar

- A estrutura de módulos está agora ordenada por dependências de conhecimento em todas as fases
- Fase 0 no disco: `01_claude-code`, `02_dat_ai_os`, `03_devsecops-knowledge-wiki` — estes são os nomes correctos
- `PORTFOLIO_TOKEN` expira Jun 2027 — renovar antes
- Nunca commitar directamente em `DigitALLtogether/portfolio-devsecops`
