# Project Tracking — Livvo

## Ferramenta Atual

**Ferramenta:** GitHub Issues e GitHub Projects v2. Este repositório não tem workflow de release.

**Base de rastreio:** GitHub Issues + GitHub Projects v2

**Repositório:** `thaifurforo/Livvo`
**Project:** [Livvo](https://github.com/users/thaifurforo/projects/3)

O tracking permanente do projeto fica no GitHub:

- **GitHub Issues:** fonte de verdade do trabalho.
- **GitHub Project v2:** quadro operacional. A issue fechada por um pull request com `Closes #N` vai para **Done**.

Milestones e GitHub Releases não fazem parte do acompanhamento atual.

## Estrutura

### Issues

O procedimento de abertura está em [AGENTS.md](../AGENTS.md).

- Abra a issue no repositório `thaifurforo/Livvo`. O quadro é o [projeto Livvo](https://github.com/users/thaifurforo/projects/3).
- Título curto, dizendo o que precisa ser feito.
- Corpo com o contexto, o resultado esperado e o que ainda está em aberto. Se já existir um documento no repositório que cubra o detalhe, enlace esse arquivo em vez de copiá-lo.
- Use uma label que descreva o tipo do trabalho. Se ela já existir no repositório, use essa. Se não existir, crie a label no repositório, com nome curto e uma descrição de uma linha, e aplique na issue.

### Pull requests

O procedimento está em [AGENTS.md](../AGENTS.md).

- Crie uma branch a partir de `main`. Não faça push direto em `main`.
- O pull request entrega uma issue. No corpo, inclua `Closes #N`, trocando `N` pelo número dessa issue.
- No merge, essa linha fecha a issue. A issue fechada vai para **Done** no projeto.
- Sem `Closes #N`, o merge não fecha a issue e o card não vai para Done.
- Não faça merge. Quem abre o pull request deixa o merge para uma pessoa.

### Project

O Project [Livvo](https://github.com/users/thaifurforo/projects/3) é o quadro operacional.

O status registrado neste repositório é **Done**: a issue fechada por um pull request com `Closes #N` vai para essa coluna. Os demais campos do quadro não estão documentados aqui.

## Versionamento e Releases

Não há automação de release nem milestones neste repositório. Não existe workflow em `.github/` e não existem labels `release:*`.

## Convenções

Labels presentes no repositório:

- `accessibility`
- `bug`
- `documentation`
- `duplicate`
- `enhancement`
- `good first issue`
- `help wanted`
- `invalid`
- `prd`
- `question`
- `wontfix`

Pull requests para `main` saem de uma branch criada a partir de `main`, usam `Closes #N` para fechar a issue entregue, e quem abre o pull request não faz o merge.

## Fontes Ativas

- Progresso é acompanhado em GitHub Issues + Project v2.
- O PRD está em [.catalog/PRD.md](PRD.md).
- Milestones e changelog versionado não fazem parte do acompanhamento atual.
