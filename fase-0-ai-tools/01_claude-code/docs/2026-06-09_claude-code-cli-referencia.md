# Claude Code — Referência de Comandos CLI
> Atualizado para v2.1.x · Junho 2026  
> Fonte: documentação oficial Anthropic + claudeguide.io + blakecrosley.com

---

## Índice

1. [Instalação & Autenticação](#1-instalação--autenticação)
2. [Flags de Linha de Comando](#2-flags-de-linha-de-comando)
3. [Modo Não-Interativo (Pipe / Scripts)](#3-modo-não-interativo-pipe--scripts)
4. [Slash Commands (dentro de sessão)](#4-slash-commands-dentro-de-sessão)
5. [Atalhos de Teclado](#5-atalhos-de-teclado)
6. [Variáveis de Ambiente](#6-variáveis-de-ambiente)
7. [Formatos de Output (`--output-format`)](#7-formatos-de-output---output-format)
8. [Padrões de Uso Comuns](#8-padrões-de-uso-comuns)

---

## 1. Instalação & Autenticação

```bash
# Instalação recomendada (binário nativo, auto-update)
curl -fsSL https://claude.ai/install.sh | bash

# macOS via Homebrew
brew install --cask claude-code

# NPM — DEPRECATED desde v2.1.113, não usar em novos projetos
npm install -g @anthropic-ai/claude-code

# Verificar instalação
claude --version
claude doctor
```

### Autenticação

| Comando | Descrição |
|---|---|
| `claude auth login` | Fazer login ou trocar conta |
| `claude auth status` | Ver estado de autenticação atual |
| `claude auth logout` | Limpar credenciais guardadas |

---

## 2. Flags de Linha de Comando

Passadas ao executar `claude` no terminal, antes de entrar em sessão.

### Básicas

| Flag | Descrição | Exemplo |
|---|---|---|
| `--help`, `-h` | Mostrar ajuda | `claude --help` |
| `--version`, `-v` | Mostrar versão instalada | `claude --version` |
| `--debug` | Ativar logging detalhado para debug | `claude --debug` |
| `--init` | Inicializar projeto com ficheiro `CLAUDE.md` | `claude --init` |
| `--doctor` | Diagnóstico da instalação | `claude doctor` |

### Modelo e Configuração

| Flag | Descrição | Exemplo |
|---|---|---|
| `--model` | Substituir modelo para esta sessão | `claude --model claude-opus-4-7` |
| `--config` | Caminho para ficheiro de configuração custom | `claude --config ./team-settings.json` |
| `--system-prompt` | Injetar system prompt para a sessão | `claude --system-prompt "És um auditor de segurança"` |

### Contexto e Ferramentas

| Flag | Descrição | Exemplo |
|---|---|---|
| `--context` | Adicionar contexto extra de texto | `claude --context "$(cat NOTES.md)"` |
| `--allowedTools` | Restringir as ferramentas disponíveis | `claude --allowedTools "Read,Grep"` |
| `--disallowed-tools` | Bloquear ferramentas específicas | `claude --disallowed-tools "Bash,Write"` |

### Controlo de Sessão

| Flag | Descrição | Exemplo |
|---|---|---|
| `--continue`, `-c` | Continuar a sessão mais recente | `claude -c` |
| `--resume`, `-r` | Retomar sessão anterior por ID ou nome | `claude -r "auth-refactor"` |
| `--name`, `-n` | Definir nome de sessão ao arrancar | `claude -n "feature-x"` |
| `--max-turns` | Limitar número de turnos autónomos | `claude --max-turns 10` |
| `--fork-session` | Criar fork a partir de sessão retomada | `claude -r base --fork-session` |
| `-w`, `--worktree` | Iniciar em git worktree isolado | `claude -w` |
| `--from-pr` | Iniciar sessão ligada a uma PR (GitHub/GitLab/Bitbucket) | `claude --from-pr 123` |

### Permissões e Segurança

| Flag | Descrição | Risco |
|---|---|---|
| `--permission-mode` | Definir nível de permissões (`default`, `auto`, `bypassPermissions`) | Médio |
| `--enable-auto-mode` | Arrancar com Auto Mode ativo | Médio |
| `--dangerously-skip-permissions` | **YOLO mode** — ignora todos os prompts de confirmação | ⚠️ ALTO |

> **Aviso**: `--dangerously-skip-permissions` e `bypassPermissions` desativam todos os prompts de confirmação. Usar **apenas** em ambientes automatizados controlados e auditados previamente.

### Output e Scripting

| Flag | Descrição | Exemplo |
|---|---|---|
| `--print`, `-p` | Modo print — executa query e sai (não-interativo) | `claude -p "Explica este ficheiro"` |
| `--output-format` | Formato do output em modo `-p` (`text`, `json`, `stream-json`) | `claude -p "..." --output-format json` |
| `--bare` | Modo scripted — ignora hooks, LSP e plugins | `claude -p "conta ficheiros" --bare` |
| `--channels` | Redirecionar prompts de aprovação para Telegram/Discord | `claude --channels` |

### Plugins

| Flag | Descrição | Exemplo |
|---|---|---|
| `--plugin-url <url>` | Carregar plugin a partir de URL (`.zip`) para a sessão | `claude --plugin-url https://example.com/plugin.zip` |
| `--plugin-dir <path>` | Carregar plugin a partir de diretório ou `.zip` local | `claude --plugin-dir ./my-plugin.zip` |

---

## 3. Modo Não-Interativo (Pipe / Scripts)

O flag `-p` permite usar Claude Code em scripts e pipelines de CI/CD sem terminal interativo.

```bash
# Analisar um ficheiro
cat main.py | claude -p "O que faz este ficheiro? Lista as funções exportadas."

# Rever múltiplos ficheiros
cat src/auth.py src/middleware.py | claude -p "Encontra problemas de segurança."

# Guardar output numa variável
REVIEW=$(git diff HEAD~1 | claude -p "Revê este diff para bugs.")
echo "$REVIEW"

# Output JSON estruturado
git diff | claude -p "Lista breaking changes como JSON" --output-format json

# Integração CI/CD — rever PR
DIFF=$(git diff origin/main...HEAD)
REVIEW=$(echo "$DIFF" | claude -p "Revê este diff. Lista bugs como JSON." \
  --output-format json --dangerously-skip-permissions)
echo "$REVIEW" | jq '.result'

# Modo read-only (sem escrita, sem bash)
claude --allowedTools "Read,Grep,Glob" -p "Audita este código"
```

---

## 4. Slash Commands (dentro de sessão)

Digitados diretamente no input da conversa durante uma sessão ativa.

### Gestão de Sessão

| Comando | Descrição |
|---|---|
| `/help` | Mostrar ajuda e comandos disponíveis |
| `/quit`, `/exit` | Sair do Claude Code |
| `/clear` | Limpar histórico de conversa (novo contexto) |
| `/compact [foco]` | Compactar conversa para reduzir tokens. Ex: `/compact focus on tests` |
| `/context` | Ver utilização atual da janela de contexto com sugestões |
| `/status` | Mostrar estado da sessão: modelo, tokens, configurações |
| `/usage` | Ver tokens usados, custo e limites do plano |
| `/cost` | Atalho — abre tab de custo em `/usage` |
| `/resume [n/nome]` | Retomar sessão pelo número ou nome |
| `/rename [nome]` | Dar nome à sessão atual |

### Modelo

| Comando | Descrição |
|---|---|
| `/model <nome>` | Trocar modelo a meio de sessão |
| `/model claude-haiku-4-5` | Trocar para Haiku (rápido, económico) |
| `/model claude-sonnet-4-6` | Trocar para Sonnet (equilibrado) |
| `/model claude-opus-4-7` | Trocar para Opus (mais capaz) |

### Performance e Controlo

| Comando | Descrição |
|---|---|
| `/fast` | Ativar/desativar modo de output rápido |
| `/effort <low\|medium\|high>` | Definir nível de esforço do modelo |

### Permissões e Configuração

| Comando | Descrição |
|---|---|
| `/permissions` | Gerir permissões de ferramentas interativamente |
| `/config` | Abrir interface completa de configurações |
| `/hooks` | Ver configuração de hooks |

### Memória e Contexto

| Comando | Descrição |
|---|---|
| `/memory` | Ver e gerir ficheiros de memória (`CLAUDE.md`) |
| `/init` | Inicializar projeto com `CLAUDE.md` |

### MCP e Plugins

| Comando | Descrição |
|---|---|
| `/mcp` | Configurar servidores MCP |
| `/mcp enable` | Ativar servidor MCP |
| `/mcp disable` | Desativar servidor MCP |

### Utilitários

| Comando | Descrição |
|---|---|
| `/copy [N]` | Copiar blocos de código; `/copy 2` copia o 2.º mais recente |
| `/branch` | Criar branch git com nome sugerido pelo Claude |

### Comandos Personalizados (Skills)

Ficheiros `.md` em `.claude/commands/` (projeto) ou `~/.claude/commands/` (utilizador) ficam disponíveis como slash commands:

```
~/.claude/commands/deploy.md  →  /deploy
.claude/commands/qa.md        →  /qa
```

Argumentos passados via `$ARGUMENTS` no template do comando.

---

## 5. Atalhos de Teclado

| Atalho | Acção |
|---|---|
| `Enter` | Submeter mensagem |
| `Shift+Enter` | Nova linha sem submeter |
| `↑ / ↓` | Navegar no histórico de mensagens |
| `Tab` | Autocompletar slash commands e caminhos de ficheiros |
| `Ctrl+C` | Interromper execução de ferramenta atual |
| `Ctrl+C` (2×) | Sair do Claude Code |
| `Esc` (2×) | Abrir menu de rewind (reverter código e/ou conversa) |
| `Ctrl+R` | Pesquisar histórico de comandos |

---

## 6. Variáveis de Ambiente

| Variável | Descrição | Exemplo |
|---|---|---|
| `ANTHROPIC_API_KEY` | Chave de API (obrigatória para uso via API) | `export ANTHROPIC_API_KEY=sk-ant-...` |
| `CLAUDE_CODE_MODEL` | Modelo padrão | `export CLAUDE_CODE_MODEL=claude-sonnet-4-6` |
| `CLAUDE_CODE_SUBAGENT_MODEL` | Modelo para subagentes | `export CLAUDE_CODE_SUBAGENT_MODEL=claude-haiku-4-5` |
| `CLAUDE_CODE_MAX_OUTPUT_TOKENS` | Limite de tokens de output | `export CLAUDE_CODE_MAX_OUTPUT_TOKENS=4096` |
| `ANTHROPIC_BASE_URL` | Override do endpoint da API (proxies, LLMs locais) | `export ANTHROPIC_BASE_URL=http://localhost:8080` |
| `NO_COLOR` | Desativar cores no terminal | `export NO_COLOR=1` |
| `CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC` | Desativar telemetria e analytics | `export CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC=1` |

---

## 7. Formatos de Output (`--output-format`)

Usado em modo não-interativo com `-p`.

| Formato | Descrição |
|---|---|
| `text` | Texto simples (padrão) |
| `json` | Objeto JSON com `result`, `cost_usd`, `session_id`, `is_error` |
| `stream-json` | JSON Lines — stream de eventos à medida que chegam |

**Exemplo de output JSON:**
```json
{
  "result": "Encontrei 3 comentários TODO:\n1. Linha 42: TODO: handle edge case\n...",
  "cost_usd": 0.0023,
  "session_id": "abc123",
  "is_error": false
}
```

---

## 8. Padrões de Uso Comuns

```bash
# Arrancar numa pasta de projeto (lê CLAUDE.md automaticamente)
cd meu-projeto && claude

# Resumo dos últimos 10 commits como release notes
git log --oneline -10 | claude -p "Resume estes commits como release notes."

# Scan de vulnerabilidades (read-only)
claude -p "Procura SQL injection" --allowedTools "Read,Grep"

# Retomar sessão específica
claude --resume abc123def456

# Inicializar CLAUDE.md num novo projeto
claude --init

# Trocar modelo no meio de uma sessão longa
/model claude-opus-4-7   # dentro da sessão

# Ver custo acumulado
/usage
```

---

> **Nota sobre versões**: A partir de v2.1.113, o pacote npm `@anthropic-ai/claude-code` foi descontinuado em favor do binário nativo. Migrar com `claude install` se ainda estiveres no npm.
>
> Documentação oficial: https://docs.anthropic.com/claude-code/cli-reference
