# Diário de Sessão — 2026-06-08

**Tema:** Portfolio sync via GitHub Actions + rename do repositório principal

---

## Contexto de partida

Repositório local sincronizado com o GitHub (`git pull` — já actualizado).
Foram encontradas 5 pastas locais não rastreadas (`fase-0-claude/`, `fase-1-fundacoes/`, etc.) — restos de um refactor de nomenclatura anterior, completamente vazias. Removidas.

---

## Objectivo

1. Discutir e definir a estrutura de labs (estudo vs. portfólio)
2. Implementar a separação repositório de trabalho / portfólio público com sync automático via GitHub Actions
3. Criar templates reutilizáveis para labs de estudo e de portfólio
4. Renomear o repositório principal para reflectir a sua função real

---

## O que foi feito

### Limpeza inicial
- Removidas 5 pastas vazias legadas do refactor anterior (`fase-0-claude/`, `fase-1-fundacoes/`, `fase-2-containers-iac/`, `fase-4-ia-aplicada/`, `fase-5-pro-security/`)

### Discussão e definição de frameworks
- Definidos os dois perfis de lab:
  - **Lab de estudo** — rápido, no calor do momento, para aprendizagem
  - **Lab de portfólio** — curado com distância crítica, demonstra competência a visitantes externos
- Estabelecido que o processo É importante num lab de portfólio — mas narrado retrospectivamente, não em bruto
- Criados frameworks concretos para cada tipo

### Implementação da estrutura de portfólio
- Criada pasta `portfolio/` na raiz com estrutura espelhando as fases (fase-0 a fase-5)
- Fase 1 espelha os módulos activos (linux-rhcsa, redes-ccna, seguranca-nse, python, aws-ccp)
- Fases 2–5 com `.gitkeep` para rastreamento futuro
- `portfolio/README.md` — carta de apresentação autónoma para visitantes externos

### Templates de labs
- `docs/templates/lab-estudo.md` — framework leve: Objectivo, Ambiente, O que fiz, O que correu mal, Takeaways, Estado
- `docs/templates/lab-portfolio.md` — framework completo: Contexto, Abordagem, Implementação, Obstáculos, Validação, Reflexão

### GitHub Actions — sync automático
- Criado `DigitALLtogether/portfolio-devsecops` (repo público)
- Criado Personal Access Token (fine-grained, scope Contents read/write, repo portfolio-devsecops)
- Secret `PORTFOLIO_TOKEN` adicionado ao repo principal
- Criado `.github/workflows/sync-portfolio.yml`:
  - Dispara em push para `main` quando há alterações em `portfolio/**`
  - Dispara também manualmente via `workflow_dispatch`
  - Usa `cpina/github-action-push-to-another-repository@v1.7.2`
  - Sincroniza o conteúdo de `portfolio/` para `DigitALLtogether/portfolio-devsecops`
- Workflow testado e validado com sucesso — portfólio público actualizado automaticamente

### Rename do repositório principal
- GitHub repo renomeado: `000_26_portfolio-devsecops` → `000_26_roadmap-devsecops`
- Remote URL local actualizado
- Descrição do repo no GitHub actualizada
- Todos os ficheiros com referências ao nome antigo actualizados

### Documentação actualizada
- `CLAUDE.md` — adicionadas `portfolio/` e `docs/templates/` na tabela de estrutura; convenções de uso dos templates; regras do portfólio público
- `README.md` — título e descrição actualizados para reflectir função de roadmap; link para portfólio público
- `portfolio/README.md` — link para repositório principal actualizado
- `diario/2026-05-30_inicio-percurso.md` — referências ao nome antigo actualizadas

---

## Decisões tomadas

- **Separação roadmap/portfólio:** repositório principal é o espaço de trabalho; `portfolio-devsecops` é o showcase público. Nunca commitar directamente no repo de portfólio — o fluxo é sempre pelo repo principal.
- **Sync automático via GitHub Actions** em vez de `git subtree push` manual — mais robusto e sem fricção.
- **`workflow_dispatch`** adicionado ao workflow para permitir sincronização manual quando necessário.
- **Nome `000_26_roadmap-devsecops`** reflecte a função real do repositório — roadmap de aprendizagem, não portfólio. O portfólio público tem o seu próprio repo.
- **Diários históricos actualizados** para consistência — não para revisionar história, mas para evitar confusão com o novo repo `portfolio-devsecops`.

---

## Problemas encontrados

- Primeiro run do GitHub Action falhou: repo `portfolio-devsecops` criado vazio (sem branch `main`). Resolvido adicionando `create-target-branch-if-needed: true` ao workflow.
- O workflow não dispara quando só se alteram ficheiros em `.github/` — necessário usar `workflow_dispatch` para o primeiro teste.

---

## Código/Artefactos

| Ficheiro | Acção |
|----------|-------|
| `.github/workflows/sync-portfolio.yml` | Criado |
| `docs/templates/lab-estudo.md` | Criado |
| `docs/templates/lab-portfolio.md` | Criado |
| `portfolio/README.md` | Criado |
| `portfolio/fase-*/` (subpastas) | Criadas com `.gitkeep` |
| `CLAUDE.md` | Actualizado |
| `README.md` | Actualizado |
| `portfolio/README.md` | Actualizado (link repo principal) |
| `diario/2026-05-30_inicio-percurso.md` | Actualizado (nome repo) |

---

## Estado actual

- Repositório principal: `DigitALLtogether/000_26_roadmap-devsecops` (público, branch `main`)
- Portfólio público: `DigitALLtogether/portfolio-devsecops` (público, sincronizado)
- GitHub Actions: operacional e validado
- Templates de labs: prontos a usar
- Pasta `portfolio/` estruturada e aguarda conteúdo real com o avanço do estudo

---

## Próximos passos

- Iniciar RH124 via Workday Learning (foco principal Jun–Set 2026)
- Estudo gradual do CCNA em paralelo via NetAcad + Packet Tracer
- Quando produzir o primeiro lab real: copiar template adequado, preencher e commitar
- Labs de portfólio: copiar para `portfolio/fase-1-devsecops-foundations/modulo/` e o sync trata do resto
- Renomear a pasta local `000_26_portfolio-devsecops` para `000_26_roadmap-devsecops` no Windows Explorer (opcional mas recomendado para consistência)

---

## Contexto crítico a preservar

- O fluxo de portfólio é: trabalhar sempre em `portfolio/` deste repo → push → GitHub Action sincroniza automaticamente
- **Nunca commitar directamente em `DigitALLtogether/portfolio-devsecops`** — isso quebra o sync
- Secret `PORTFOLIO_TOKEN` expira em Jun 2027 — renovar antes dessa data
- A pasta local no disco ainda se chama `000_26_portfolio-devsecops` — renomear manualmente quando conveniente
