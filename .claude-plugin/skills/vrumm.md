# /vrumm — Nova Branch de Trabalho

Criar nova branch a partir de upstream/staging ou upstream/main.
Argumento opcional: `$ARGUMENTS` = nome descritivo da branch (sem prefixo).

## Passo 0 — Banner de abertura

Antes de qualquer coisa, rodar este comando:

```bash
printf '\033[1;36m\n'
printf '  ==========================================\n'
printf '   \033[1;33m⚡ V R U M M ! \033[1;37m— nova branch saindo!\033[1;36m\n'
printf '  ==========================================\n'
printf '  \033[1;37m        |     |\n'
printf '         |     |\n'
printf '    _____|_____|_____\n'
printf '   /  \033[1;33m🏎️  VRUMM  🏎️\033[1;37m  \\  \n'
printf '  /___________________\\ \n'
printf '  \033[1;36m==========================================\033[0m\n\n'
```

## Passo 1 — Tipo de mudança

Usar `AskUserQuestion` para perguntar o tipo:
- **fix** — correção de bug 🐛
- **feat** — nova funcionalidade ✨

## Passo 2 — Nome da branch

Se `$ARGUMENTS` não estiver vazio, usar como nome descritivo.

Se vazio, usar `AskUserQuestion` para obter o nome descritivo (ex: `auth-bug`, `novo-widget`).

Montar nome final concatenando: `<tipo>-<nome-descritivo>`
Exemplos: `fix-auth-bug`, `feat-novo-widget`

Exibir o nome final e pedir confirmação:

```bash
printf '\033[1;35m  🏷️  Branch: \033[1;33m<nome-final>\033[1;35m — pode isso, Arnaldo?\033[0m\n'
```

## Passo 3 — Base upstream

Usar `AskUserQuestion` com duas opções:
- **main** — código estável de produção
- **staging** — integração pré-release

Após escolha, exibir:

```bash
printf '\033[1;34m  🌿 Base escolhida: upstream/<base-escolhida>\033[0m\n'
```

## Passo 4 — Executar

```bash
printf '\033[1;33m  🔄 Buscando upstream... segura o volante!\033[0m\n'
git fetch upstream
git checkout -b <nome-final> upstream/<base-escolhida>
```

Confirmar com `git branch --show-current`.

Se der certo, exibir banner de sucesso:

```bash
printf '\n\033[1;32m'
printf '  ╔══════════════════════════════════════════╗\n'
printf '  ║  🚦 BRANCH CRIADA! PODE ACELERAR! 🚦    ║\n'
printf '  ║                                          ║\n'
printf '  ║  \033[1;33m<nome-final>\033[1;32m                           ║\n'
printf '  ║                                          ║\n'
printf '  ║  💨 VRUMM VRUMM VRUMM! 🏎️              ║\n'
printf '  ╚══════════════════════════════════════════╝\033[0m\n\n'
printf '\033[1;37m  Agora é só codar! Use \033[1;36m/vrumm-go\033[1;37m quando terminar.\033[0m\n\n'
```
