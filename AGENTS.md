# AGENTS.md

## Projeto
Livvo

## Documentos-fonte
- PRD principal: [.catalog/PRD.md](.catalog/PRD.md)
- Convenções de acompanhamento do projeto: [.catalog/project-tracking.md](.catalog/project-tracking.md)

## Regra de idioma
- Toda a documentação do repositório, descrições de PR, issues e comentários de PR devem ser escritas em português brasileiro, com acentuação correta.

## Issues

- Abra a issue no repositório `thaifurforo/Livvo`. O quadro é o [projeto Livvo](https://github.com/users/thaifurforo/projects/3).
- Título curto, dizendo o que precisa ser feito.
- Corpo com o contexto, o resultado esperado e o que ainda está em aberto. Se já existir um documento no repositório que cubra o detalhe, enlace esse arquivo em vez de copiá-lo.
- Use uma label que descreva o tipo do trabalho. Se ela já existir no repositório, use essa. Se não existir, crie a label no repositório, com nome curto e uma descrição de uma linha, e aplique na issue.

## Pull requests

- Crie uma branch a partir de `main`. Não faça push direto em `main`.
- O pull request entrega uma issue. No corpo, inclua `Closes #N`, trocando `N` pelo número dessa issue.
- No merge, essa linha fecha a issue. A issue fechada vai para **Done** no projeto.
- Sem `Closes #N`, o merge não fecha a issue e o card não vai para Done.
- Não faça merge. Quem abre o pull request deixa o merge para uma pessoa.

Exemplo no corpo:

```
Closes #12
```
