# Documentação — Anthropic, Claude e o modelo Claude Fable 5

**Data:** 9 de junho de 2026  
**Tema:** Lançamento do Claude Fable 5 e da classe de modelos Mythos  
**Fontes:** Anúncio oficial da Anthropic (anthropic.com/news/claude-fable-5-mythos-5) e cobertura de imprensa (CNBC, ITPro, Yahoo Finance, 9to5Mac) de 9 de junho de 2026

---

## 1. Contexto: a Anthropic e a família Claude

A Anthropic é uma empresa norte-americana de investigação e desenvolvimento em inteligência artificial, fundada em 2021, conhecida pela abordagem de "segurança em primeiro lugar" (safety-first) no desenvolvimento de modelos de linguagem de grande escala. O seu produto principal é a família de modelos **Claude**, disponibilizada através da aplicação Claude.ai (web, desktop e mobile), da API na Claude Platform, e de produtos agênticos como o **Claude Code** (programação via terminal/IDE) e o **Claude Cowork** (trabalho de conhecimento para não-programadores).

Antes de 9 de junho de 2026, a hierarquia de modelos da Anthropic organizava-se em três níveis de capacidade:

| Nível | Modelo mais recente | Posicionamento |
|---|---|---|
| Haiku | Claude Haiku 4.5 | Rápido e económico; tarefas simples e de alto volume |
| Sonnet | Claude Sonnet 4.6 | Equilíbrio capacidade/custo; uso geral e produção |
| Opus | Claude Opus 4.8 | Topo de gama; raciocínio complexo e tarefas exigentes |

## 2. A classe Mythos: antecedentes

Em **abril de 2026**, a Anthropic revelou o **Claude Mythos (Preview)**, um modelo que demonstrou capacidade invulgar para identificar vulnerabilidades de segurança em software — incluindo em todos os principais sistemas operativos e browsers — apesar de não ter sido concebido especificamente para cibersegurança.

Devido ao risco de uso indevido (por exemplo, ataques a infraestruturas críticas), a Anthropic optou por **não** disponibilizar o Mythos Preview publicamente. Em vez disso, criou o **Project Glasswing**: uma colaboração com organizações como Amazon Web Services, Apple, Google, Cisco, Microsoft e JPMorgan Chase, que receberam acesso antecipado para encontrar e corrigir vulnerabilidades no seu próprio software antes de atores maliciosos o poderem fazer.

## 3. Claude Fable 5 — o lançamento de 9 de junho de 2026

O **Claude Fable 5** é o primeiro modelo da família Claude 5 e o primeiro modelo da classe Mythos a ser disponibilizado ao público em geral. Pontos essenciais:

### 3.1. Posicionamento

- Inaugura um **novo nível acima do Opus** na hierarquia de modelos da Anthropic.
- **Fable 5 e Mythos 5 partilham o mesmo modelo subjacente.** A diferença está nas salvaguardas: o Fable 5 inclui restrições adicionais para capacidades de duplo uso (dual-use); o Mythos 5 é disponibilizado sem essas restrições, mas apenas a organizações aprovadas (parceiros do Project Glasswing, ciberdefensores, fornecedores de infraestrutura e investigadores selecionados em biologia).
- A Anthropic afirma que as capacidades do Fable 5 excedem as de qualquer modelo alguma vez disponibilizado publicamente pela empresa.

### 3.2. Capacidades e desempenho

- Estado da arte em quase todos os benchmarks testados, com destaque para **engenharia de software, trabalho de conhecimento (knowledge work), visão, investigação científica e tarefas de longo contexto**.
- Nalguns benchmarks, pontuou **mais de 10% acima do Claude Opus 4.8** (lançado apenas algumas semanas antes).
- Padrão relevante: **quanto mais longa e complexa a tarefa, maior a vantagem** do Fable 5 face aos modelos anteriores.
- Capacidade de **trabalho autónomo prolongado** superior a qualquer Claude anterior — relevante para fluxos agênticos (Claude Code, automações, pipelines longos).
- A Anthropic compara resultados favoráveis face ao Claude Opus 4.8 e ao GPT-5.5 (OpenAI).
- Exemplos reportados por terceiros: a Stripe afirmou que o modelo comprimiu meses de trabalho de engenharia em dias, incluindo uma migração de uma grande codebase Ruby que teria ocupado uma equipa durante mais de dois meses; a Hex reportou a primeira pontuação acima de 90% no seu benchmark de analytics.

### 3.3. Salvaguardas e mecanismo de fallback

O elemento mais distintivo do lançamento é a arquitetura de segurança que tornou possível a disponibilização pública de um modelo Mythos-class:

- **Bloqueio seletivo por domínio de risco:** pedidos em áreas de alto risco — cibersegurança ofensiva, biologia, química e destilação de modelos — não são respondidos pelo Fable 5.
- **Fallback automático para o Claude Opus 4.8:** quando uma salvaguarda é acionada, o sistema responde através do Opus 4.8 em vez de simplesmente recusar.
- **Frequência baixa:** segundo a Anthropic, as salvaguardas ativam-se em menos de 5% das sessões; em testes, 95% das sessões correram inteiramente com respostas do Fable 5.
- **Validação externa:** programa de bug bounty com mais de 1.000 horas de testes, durante o qual ninguém encontrou um jailbreak universal para o modelo.
- **Retenção de dados:** utilizadores empresariais de modelos Mythos-class estão sujeitos a retenção obrigatória de dados de 30 dias para monitorização de segurança.

### 3.4. Disponibilidade e preços

- **Disponibilidade imediata** (9 de junho de 2026) para subscritores pagos e clientes empresariais.
- Incluído nos planos **Pro, Max, Team e Enterprise até 22 de junho de 2026**; a partir de 23 de junho, poderão ser necessários créditos de uso adicionais até a capacidade de computação expandir (a Anthropic antecipa procura muito elevada e difícil de prever).
- **API:** $10 por milhão de tokens de input / $50 por milhão de tokens de output — menos de metade do preço do Mythos Preview, mas significativamente acima do Sonnet 4.6.
- String de modelo na API: `claude-fable-5`.
- O **Claude Mythos 5** mantém acesso restrito; os atuais utilizadores do Mythos Preview (ex.: parceiros do Project Glasswing) podem fazer upgrade, e a Anthropic planeia expandir o acesso através de um programa sistemático de "trusted access".

## 4. Hierarquia de modelos Anthropic após o lançamento

| Nível | Modelo | Acesso |
|---|---|---|
| **Mythos (novo)** | Claude Fable 5 | Público (com salvaguardas dual-use) |
| **Mythos (novo)** | Claude Mythos 5 | Restrito a organizações aprovadas (sem salvaguardas adicionais) |
| Opus | Claude Opus 4.8 | Público; serve de fallback ao Fable 5 |
| Sonnet | Claude Sonnet 4.6 | Público |
| Haiku | Claude Haiku 4.5 | Público |

## 5. Leitura estratégica

1. **Mudança de paradigma na disponibilização:** em vez do binário "lançar vs. reter" (como aconteceu com o Mythos Preview em abril), a Anthropic inaugurou um modelo de **disponibilização gradual com salvaguardas técnicas** — o mesmo modelo serve o público (Fable) e parceiros de confiança (Mythos), variando apenas o nível de restrição.
2. **Filosofia "race to the top":** segundo a Anthropic, o objetivo é disponibilizar a tecnologia de forma valiosa com os guardrails certos, para que produza "assimetricamente mais benefícios do que danos".
3. **Critério de escolha de modelo:** o salto de capacidade concentra-se em tarefas longas, complexas e autónomas. Para tarefas simples ou de alto volume, os modelos Sonnet e Haiku continuam a ser mais racionais em custo/benefício.
4. **Contexto empresarial:** o lançamento ocorre num momento de forte interesse de investidores na Anthropic, com um IPO potencialmente previsto ainda para 2026.

## 6. Questões em aberto (a acompanhar)

- Limites exatos de uso por plano após 22 de junho de 2026 e modelo de créditos.
- Especificações técnicas detalhadas (janela de contexto, limites de output) — verificar o system card publicado pela Anthropic.
- Evolução do programa de trusted access para o Mythos 5.
- Resultados independentes de benchmarks (os números citados são maioritariamente da própria Anthropic).

---

*Documentação compilada a 9 de junho de 2026, no dia do lançamento. Informação sujeita a atualização.*
