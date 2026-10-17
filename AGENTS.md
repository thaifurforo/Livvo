# Instruções para agentes

Estas regras valem para qualquer issue e qualquer pull request deste repositório.

## Issues

- Abra a issue no repositório `thaifurforo/Livvo`. O quadro é o [projeto Livvo](https://github.com/users/thaifurforo/projects/3).
- Título curto, dizendo o que precisa ser feito.
- Corpo com o contexto, o resultado esperado e o que ainda está em aberto. Se já existir um documento no repositório que cubra o detalhe, enlace esse arquivo em vez de copiá-lo.
- Use uma label que já exista e que descreva o tipo do trabalho.

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
