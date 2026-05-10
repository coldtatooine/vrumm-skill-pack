# /vrumm-go — Commit › Push › PR

Automatizar fluxo final: commit, push e abertura de PR para a base escolhida.

## Passo 0 — Banner de abertura

Antes de qualquer coisa, rodar este comando para exibir o banner animado:

```bash
printf '\033[1;33m\n'
printf '  🏎️  \033[1;31mV R U M M  G O !\033[0m\n'
printf '\033[1;33m'
printf '  ==========================================\n'
printf '        ______\n'
printf '       /|_||_\`.__    \033[1;37m commit › push › PR \033[1;33m\n'
printf '      (   _    _ _\  \n'
printf '      =`-(_)--(_)-'"'"'  \033[0m\n'
printf '\033[1;33m  ==========================================\033[0m\n\n'
```

## Passo 1 — Verificar estado

Rodar `git status` e `git diff --stat` para mostrar ao usuário o que será commitado.

Se não houver mudanças staged nem unstaged, exibir mensagem e encerrar:

```bash
printf '\033[1;36m  🏁 Nada pra commitar. Tudo limpo, piloto!\033[0m\n'
```

## Passo 2 — Staging

Usar `AskUserQuestion` para perguntar o que adicionar:
- **Tudo** — `git add .`
- **Apenas tracked** — `git add -u` *(recomendado)*
- **Manual** — usuário informa os paths

Após staging, exibir:

```bash
printf '\033[1;32m  📦 Arquivos no baú... prontos pro pit stop!\033[0m\n'
```

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

Após commit bem-sucedido:

```bash
printf '\033[1;35m  ✅ COMMIT feito! Carimbo no passaporte!\033[0m\n'
```

## Passo 5 — Push

```bash
printf '\033[1;34m  🚀 Acelerando pro origin...\033[0m\n'
git push -u origin HEAD
```

O `-u` define o tracking para `origin/<branch>`, necessário para `gh pr create` resolver o head corretamente.

Após push bem-sucedido:

```bash
printf '\033[1;32m  ☁️  No ar! Branch chegou no servidor!\033[0m\n'
```

## Passo 6 — Base do PR

Usar `AskUserQuestion` para perguntar o destino do PR:
- **main** — código estável de produção
- **staging** — integração pré-release

## Passo 7 — Abrir PR

```bash
printf '\033[1;33m  🔧 Abrindo PR... não esquece de revisar!\033[0m\n'
gh pr create --base <base-escolhida> --title "<mensagem-do-commit>" --body ""
```

Após criar PR com sucesso, exibir a URL e o banner final:

```bash
printf '\n\033[1;32m'
printf '  ╔══════════════════════════════════════╗\n'
printf '  ║  🏆  PR ABERTO! MISSÃO CUMPRIDA!  🏆  ║\n'
printf '  ║                                      ║\n'
printf '  ║   VRUMM VRUMM! 🏎️  💨               ║\n'
printf '  ╚══════════════════════════════════════╝\033[0m\n\n'
```

Exibir a URL do PR criado ao usuário em destaque:

```bash
printf '\033[1;36m  🔗 PR: <url-do-pr>\033[0m\n\n'
```
