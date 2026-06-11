# Módulo 03 — DevSecOps Knowledge Wiki

**Tipo:** Projecto de portfólio contínuo  
**Fase:** 0 (arranque) → transversal a todo o percurso  
**Tecnologia:** Claude Code + Markdown + Obsidian (opcional)

---

## O que é

Sistema de conhecimento pessoal construído ao longo de todo o percurso DevSecOps, baseado no conceito **LLM Wiki** de Andrej Karpathy.

Toda a documentação recolhida e estudada durante o percurso — notas de cursos, relatórios de labs, documentação oficial, artigos técnicos — é ingerida pelo Claude Code e organizada automaticamente numa wiki de ficheiros markdown, com relações entre conceitos, ferramentas e domínios.

## Arquitectura

```
wiki/
├── raw/                  ← material bruto a ingerir
│   ├── linux/            # notas, man pages, docs Red Hat
│   ├── redes/            # CCNA, RFCs, Packet Tracer labs
│   ├── containers/       # Docker, K8s, Podman, OCI specs
│   ├── iac/              # Terraform, Ansible, GitOps
│   ├── seguranca/        # OWASP, CVEs, hardening guides
│   └── cloud/            # AWS, GCP, OpenShift docs
├── wiki/                 ← conhecimento organizado pelo Claude Code
│   ├── index.md          # índice global de conceitos e relações
│   ├── log.md            # histórico de ingestões
│   └── [páginas geradas] # artigos, conceitos, ferramentas, técnicas
└── CLAUDE.md             ← instruções do agente de ingestão
```

## Fluxo de trabalho

1. **Ingestão:** colocar material em `raw/` (nota de estudo, artigo, secção de documentação)
2. **Processamento:** dizer ao Claude Code "ingere o material novo na wiki"
3. **Organização automática:** o Claude lê, cria páginas `.md` com relações, actualiza o `index.md` e o `log.md`
4. **Consulta:** perguntar directamente ao Claude "explica-me SELinux com base nas minhas notas" ou navegar no Obsidian

## Por que não RAG nem vector databases

Karpathy documentou que a 100–500 artigos / ~500k palavras, o LLM consegue manter índices e sumários automáticos e navegar as relações com eficiência suficiente. Zero infra, zero custos adicionais — apenas uma pasta de markdown.

## Valor durante o percurso

| Situação | Benefício |
|----------|-----------|
| Preparação para exame | "Resume SELinux com base nas minhas notas de labs" |
| Estudo de novo tema | "Que conceitos de Linux se relacionam com K8s network policies?" |
| Identificar lacunas | "Que tópicos do RHCSA estão pouco documentados na wiki?" |
| Revisão cruzada | "Como o Vault se integra com o que aprendi em Terraform?" |

## Valor no portfólio

- Base de conhecimento construída ao longo de 3+ anos com histórico documentado
- Demonstra capacidade de gerir conhecimento técnico complexo com IA
- Cobrindo 6+ domínios com relações explícitas entre eles
- Diferenciador real em entrevistas: não são apenas certificações, é sistema

## Estado

- [ ] Setup inicial da estrutura e CLAUDE.md do wiki agent
- [ ] Primeiras ingestões — notas RH124/RH134 (Fase 1)
- [ ] Wiki em crescimento contínuo com cada fase

## Referências

- Andrej Karpathy — post original sobre LLM knowledge bases (X / GitHub Gist)
- Secção em `../02_dat_ai_os/docs/transcript_Build & Sell Claude Code Operating Systems (2+ Hour Course).txt` → 2:05:13–2:16:xx
