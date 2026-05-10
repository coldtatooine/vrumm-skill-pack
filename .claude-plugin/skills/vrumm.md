# /vrumm — Nova Branch de Trabalho

Criar nova branch a partir de upstream/staging ou upstream/main.
Argumento opcional: `$ARGUMENTS` = nome descritivo da branch (sem prefixo).

## Passo 1 — Tipo de mudança

Usar `AskUserQuestion` para perguntar o tipo:
- **fix** — correção de bug
- **feat** — nova funcionalidade

## Passo 2 — Nome da branch

Se `$ARGUMENTS` não estiver vazio, usar como nome descritivo.

Se vazio, usar `AskUserQuestion` para obter o nome descritivo (ex: `auth-bug`, `novo-widget`).

Montar nome final concatenando: `<tipo>-<nome-descritivo>`
Exemplos: `fix-auth-bug`, `feat-novo-widget`

Exibir o nome final para o usuário confirmar antes de continuar.

## Passo 3 — Base upstream

Usar `AskUserQuestion` com duas opções:
- **main** — código estável de produção
- **staging** — integração pré-release

## Passo 4 — Executar

```bash
git fetch upstream
git checkout -b <nome-final> upstream/<base-escolhida>
```

Confirmar com `git branch --show-current` e exibir resultado.
