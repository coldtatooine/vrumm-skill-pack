# /vrumm-go — Commit › Push › PR

Automatizar fluxo final: commit, push e abertura de PR para a base escolhida.

## Passo 1 — Verificar estado

Rodar `git status` e `git diff --stat` para mostrar ao usuário o que será commitado.

Se não houver mudanças staged nem unstaged, informar e encerrar.

## Passo 2 — Staging

Usar `AskUserQuestion` para perguntar o que adicionar:
- **Tudo** — `git add .`
- **Apenas tracked** — `git add -u`
- **Manual** — usuário informa os paths (pedir via `AskUserQuestion`)

## Passo 3 — Mensagem de commit

Se `$ARGUMENTS` não estiver vazio, usar como mensagem de commit.

Se vazio, usar `AskUserQuestion` para obter a mensagem.

Prefixar automaticamente com o tipo da branch atual:
- Branch começa com `fix-` → prefixo `fix:`
- Branch começa com `feat-` → prefixo `feat:`
- Outro → sem prefixo automático

Exemplo final: `fix: corrige validação de token expirado`

## Passo 4 — Commit

```bash
git commit -m "<mensagem-final>"
```

## Passo 5 — Push

```bash
git push -u origin HEAD
```

O `-u` define o tracking para `origin/<branch>`, necessário para `gh pr create` resolver o head corretamente.

## Passo 6 — Base do PR

Usar `AskUserQuestion` para perguntar o destino do PR:
- **main** — código estável de produção
- **staging** — integração pré-release

## Passo 7 — Abrir PR

```bash
gh pr create --base <base-escolhida> --title "<mensagem-do-commit>" --body ""
```

Exibir URL do PR criado ao usuário.
