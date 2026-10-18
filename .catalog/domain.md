# Domínio — Livvo V0

**Data:** 2026-10-17
**Status:** Decidido
**PRD:** [PRD.md](PRD.md)
**Arquitetura:** [architecture.md](architecture.md)

Status, tag e estante são três classificações independentes. Trocar uma não altera as outras nem as estatísticas.

O exemplar é o vínculo entre uma conta e uma edição. É o livro dessa pessoa na estante. Não é a obra nem a edição do catálogo compartilhado. Duas contas com a mesma edição têm exemplares diferentes.

## Conta

E-mail, nome e senha ficam no ASP.NET Core Identity. Na mesma conta:

| Atributo | Valores | Default | Validade |
| --- | --- | --- | --- |
| Perfil | `Publico`, `Privado` | `Publico` | Não existe vazio. Cadastro sem o campo grava `Publico`. A pessoa pode enviar `Privado` no cadastro e trocar depois. |
| Leitor | verdadeiro ou falso | verdadeiro | Nasce leitora. Leitor e autor ambos falsos é estado inválido. |
| Autor | verdadeiro ou falso | falso | Opcional na mesma conta. Não cria outra conta. |
| Tema | `Claro`, `Escuro` | `Claro` | A escolha permanece na conta. O navegador também guarda a preferência local até a conta existir. |

Perfil `Privado` na V0 só é visível para a própria conta. Seguidores autorizados chegam na V1.

## Estante

Toda conta nasce com uma estante chamada `Padrão`, na mesma transação da conta. Um exemplar fica em uma estante só. Sem outra estante escolhida, o exemplar fica na `Padrão`. A pessoa pode criar estante ao adicionar ou editar o exemplar.

Visibilidade da estante: `Publico`, `SeguidoresAutorizados` ou `SomenteEu`. Sem visibilidade no pedido, perfil `Publico` gera estante `Publico` e perfil `Privado` gera estante `SeguidoresAutorizados`. `SomenteEu` só é gravado quando o pedido traz esse valor.

Mudar a visibilidade da estante reescreve a visibilidade de todos os exemplares dela. Mudar o perfil da conta não reescreve estantes nem exemplares.

## Obra

A página pública do catálogo é da obra. As edições aparecem dentro dela.

| Atributo | Valores | Default | Validade |
| --- | --- | --- | --- |
| Título | texto | obrigatório | Entra na comparação de duplicata de obra. |
| Autores | nomes ordenados | obrigatório ao menos um | Entram na comparação de duplicata de obra. |
| Tipo | `Livro`, `Quadrinho`, `Revista` | `Livro` | Não existe nulo. Omissão no cadastro grava `Livro`, e esse valor é válido. O pedido pode enviar `Quadrinho` ou `Revista`. O filtro por tipo é da V1. |

Colunas já criadas para a V1, sem tela e sem filtro na V0, para a RNF-02 não reescrever a obra quando os filtros do RF-10 chegarem:

| Atributo | Default | Significado do vazio |
| --- | --- | --- |
| Gênero | nulo | Não informado. |
| Nacionalidade | nulo | Não informado. |

Nulo nesses campos é estado válido. Não significa `Livro` nem um valor sentinela.

## Edição

Pertence a uma obra. Status, tags, estante e progresso da pessoa grudam na edição que ela tem, por meio do exemplar e do histórico.

| Atributo | Default | Significado do vazio |
| --- | --- | --- |
| Ano | nulo | Desconhecido. Não é ano zero. Nulo não conta como igual na duplicata. |
| Número da edição | nulo | Desconhecido. Zero não é número válido. Nulo não conta como igual na duplicata. |
| Quantidade de páginas | nulo | Desconhecida. Histórico em porcentagem soma zero página e ainda conta o dia. |
| ISBN | nulo | Futuro do scanner (V1). A coluna existe para não reescrever a edição. |
| Capa | nula | Edição válida. A resposta traz `capaUrl` nulo. |
| Hash da capa | nulo | Só existe quando há capa reduzida. 64 bits. |

A capa guardada é WebP com o lado maior em 1200 px. O original não fica no disco. O arquivo é dado do catálogo compartilhado: quem pode abrir a obra pode ver a imagem, mesmo que o exemplar de alguém esteja privado.

## Exemplar

Uma conta e uma edição, no máximo um par.

| Atributo | Default | Validade |
| --- | --- | --- |
| Estante | `Padrão`, se nenhuma for escolhida | Uma estante só. |
| Status | `QueroLer` | `Lido`, `Lendo`, `Relendo`, `QueroLer`, `Abandonei`. `QueroLer` é válido ao adicionar. Não existe status vazio. |
| Tags | conjunto vazio | Vazio é válido. Pode haver várias entre `Tenho`, `QueroTer`, `Emprestei` e `Favorito`. |
| Visibilidade | a do perfil, pela regra da estante | `Publico`, `SeguidoresAutorizados` ou `SomenteEu`. |

`SomenteEu` só entra se o pedido pedir. Nenhum nível de perfil preenche `SomenteEu` sozinho.

Na V0, item `SeguidoresAutorizados` ou `SomenteEu` só a própria conta vê. O valor `SeguidoresAutorizados` já fica gravado para a V1 autorizar seguidores sem reclassificar a estante.

## Histórico

Checkpoint da edição na conta, não um incremento solto. Cada envio guarda página ou porcentagem. O horário de início é opcional. O registro existe com e sem esse campo.

Páginas do mês e do ano são a soma dos avanços positivos entre checkpoints daquela edição. Recuo não soma página. Porcentagem vira página só quando a edição tem quantidade de páginas. Sem quantidade, o dia entra na divisão e soma zero página. Dia sem envio fica fora da média. Mudar visibilidade de perfil, estante, exemplar ou publicação não altera esses números.

A média da meta de dias seguidos, da V1, não entra nesta conta.

## O que não vira tabela na V0

Anotação, fila de votação de duplicata, seguidor, publicação, feed, comunidade, clube, insígnia, meta e conquista. Perfil comercial de editora também fica na V2.

## Duplicata

Dois avisos, os dois antes de gravar, os dois confirmáveis pela pessoa na V0. A fila de cinco aprovações é da V1.

**Obra.** Título e autor ambos com similaridade `pg_trgm` maior ou igual a 0,35. Os dois sinais precisam passar. A pessoa inclui o exemplar como outra edição da obra encontrada, ou confirma que é outra obra.

**Edição.** Avisa quando a capa tem distância de Hamming menor ou igual a 8 e o ano ou o número coincidem, ou quando ano e número coincidem mesmo sem capa. Capa sozinha, ano sozinho ou número sozinho não avisam. A pessoa confirma que é outra edição, ou escolhe a edição já cadastrada.

Os limiares ficam em configuração do servidor.
