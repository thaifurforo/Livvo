# Instruções para agentes

O produto está descrito em [docs/prd.md](docs/prd.md). Issues não copiam o PRD inteiro.

## Issues

- Abra a issue no repositório `thaifurforo/Livvo`. O projeto do GitHub é o [Livvo](https://github.com/users/thaifurforo/projects/3).
- Título curto, no que a entrega faz.
- Corpo com o contexto e o que falta decidir. O requisito detalhado continua no PRD, com link para `docs/prd.md`.
- Use as labels que já existem quando couberem (`documentation`, `prd`, `enhancement`, `bug`).

## Pull requests

- Uma branch a partir de `main`. Não faça push direto em `main`.
- O corpo do pull request inclui `Closes #N`, com o número da issue que a entrega fecha.
- O merge leva o card dessa issue para **Done** no projeto: o pull request mergeado fecha a issue, e a issue fechada vai para Done.
- Sem `Closes #N`, o merge não move a issue.

Exemplo no corpo:

```
Closes #12
```

- Não faça merge. Quem abre o pull request deixa o merge para uma pessoa.
