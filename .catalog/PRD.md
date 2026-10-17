# PRD: Livvo

**Data:** 2026-10-17
**Status:** Aprovado
**Issue:** https://github.com/thaifurforo/Livvo/issues/1


## Visão Geral

Leitores no Brasil acompanham o que leram, estão lendo, querem ler, têm ou querem ter em ferramentas separadas. O Livvo (nome temporário; app e web, em português) reúne estantes, progresso, feed e comunidade, com uma página por obra e edições dentro dela.

A estatística de ritmo conta só os dias em que a pessoa enviou histórico. A média de páginas no mês ou no ano é a soma das páginas lidas dividida pelos dias com envio, para não tratar ausência de registro como falha.

O produto é gratuito para quem usa no início. A operação nasce na hospedagem que já existe, um servidor dedicado na Hostinger, para poucos usuários, em peças que possam crescer quando houver mais gente e receita. O custo novo no início é o domínio. Uso comercial futuro faz parte da visão: catálogo, APIs e qualquer coleta de dados de terceiros só entram se o uso lucrativo for permitido, ou se der para trocar a fonte sem prender o produto.

Quem fica sem isso é o leitor que quer o registro da leitura sem punição por dias sem página, e o grupo que hoje separa estante, clube e conversa.

**Decisões desta seção**

- Nome temporário: Livvo
- Público inicial: Brasil, português apenas
- Hospedagem inicial: servidor dedicado já contratado na Hostinger. O custo novo no início é o domínio. O desenho segue preparado para mais usuários depois
- Fins lucrativos: entram na visão; não entram no custo de agora

## Escopo

### Dentro da V0

- Web responsiva em português, para computador e celular, com modo claro e modo escuro. App nativo fica para quando houver usuários.
- Conta e perfil básico, com opção de perfil público ou privado. No privado, só pessoas autorizadas visualizam, no modelo de um perfil fechado.
- A conta pessoal pode ser Leitor, Autor, ou os dois ao mesmo tempo.
- Status de leitura: Lido, Lendo, Relendo, Quero Ler, Abandonei.
- Tags: Tenho, Quero ter, Emprestei, Favorito.
- Uma estante chamada Padrão em toda conta. A pessoa cria outras estantes como preferir (por categoria, gênero ou outro critério), inclusive ao adicionar ou editar um livro. Sem estante escolhida, o livro fica na Padrão. Cada livro fica em uma estante só.
- Visibilidade de estantes e livros: o padrão segue o perfil. Cada item pode ser público, privado (somente seguidores autorizados) ou somente eu. Ao mudar a visibilidade de uma estante, todos os livros dela passam para a mesma visibilidade. Isso não altera as estatísticas.
- Página da obra com edições dentro dela.
- Quem adiciona um livro vê aviso de possível duplicata por título e autor próximos, e pode incluir o exemplar como outra edição.
- Histórico de leitura por página ou por porcentagem, com horário de início opcional.
- Páginas lidas no mês e no ano, e média só dos dias em que houve histórico enviado.

### Fora da V0, dentro da V1

- Anotações no livro, visíveis só para quem escreveu. Servem, por exemplo, para registrar para quem emprestou o livro ou para anotar a leitura e os personagens.
- Filtros por metadados do livro, entre eles tipo (livro, quadrinho, revista), autor, gênero e nacionalidade.
- Insígnias, metas, conquistas e seguidores. No perfil, a pessoa escolhe 5 insígnias principais para exibir; as demais aparecem em "Ver mais". Conquistas ficam em uma aba própria do perfil, separadas por categorias. Metas podem ser de páginas, de um livro específico, de quantidade de livros ou de dias seguidos com histórico enviado. Quando a insígnia depende de conquistas, a regra é todas as listadas ou pelo menos N de um conjunto.
- Feed com três recortes: geral (padrão), seguindo e o próprio. Ordenação por mais recente (padrão) ou em alta.
- Citações, posts, resenhas, enquetes e histórico de leitura. Qualquer publicação pode ser marcada como spoiler, esteja ou não ligada a um histórico de leitura. O histórico no feed pode levar uma mensagem, com opção de spoiler, e/ou uma reação. Outras pessoas podem comentar e curtir essas publicações.
- As mesmas visibilidades da V0 (público, privado para seguidores autorizados, somente eu) valem para as publicações. O padrão segue o perfil e não altera as estatísticas.
- Scanner de ISBN-10 e ISBN-13.
- Votação da comunidade para confirmar um livro que a pessoa afirma não ser duplicata (limiar padrão de 5 aprovações, configurável no admin). Com poucos usuários no início, essa fila não fecha.
- Bate-papo em grupo, clube do livro e comunidades públicas e privadas. O clube pode existir dentro de uma comunidade ou sozinho.
- Metas em grupo e competições dentro da comunidade. Quem cria escolhe os critérios: objetivo colaborativo ou disputa por páginas em um período, de forma contínua, por quantidade de livros ou outro critério definido na criação.

### V2

- Perfil comercial de Editora, separado do perfil pessoal. Um ou mais perfis pessoais gerenciam esse perfil, no modelo de páginas. A V2 pode incluir outros tipos de perfil comercial além de Editora.
- Estudo de integração de progresso com Kindle, Google Books e equivalentes, por atualização automática ou botão de atualizar.

### Fora do produto, como trabalho de suporte

- Pesquisa da base inicial (Pagy, Skoob, Google Books, Amazon Books, ISBN Database nas versões gratuitas) e da permissão de uso comercial. Nada disso entra no catálogo antes dessa checagem.

## Personas

### Marina — leitora em rajadas (principal, V0)

29 anos, lê no ônibus e some por semanas. Marca página ou porcentagem quando volta, vê o mês sem sentir que falhou nos dias em branco, e marca status (por exemplo Quero Ler ou Lendo) e tags (por exemplo Quero ter) sem planilha. Usa o celular. A V0 precisa atendê-la primeiro.

### Caio — estante em casa (V0 no catálogo, V1 no scanner)

34 anos, compra edição específica e se irrita quando o app junta traduções diferentes. Quer achar a edição certa, marcar a tag Emprestei, organizar estantes por gênero ou categoria, e mais tarde escanear o ISBN. Entra na V0 pela página da obra; o scanner fica na V1.

### Helena — conduz um clube (V1)

41 anos. O grupo conversa no WhatsApp e a lista de leitura fica em outro app. Quer um clube sozinho, ou dentro de uma comunidade, com resenhas e enquetes, sem obrigar todo mundo a ter os dois.

**Decisões desta seção**

- Marina é a persona principal dos requisitos e do fluxo da V0.
- Caio entra nos requisitos de obra, edição, tag e estante personalizada.
- Helena entra nos requisitos de comunidade, clube e feed da V1.
- Status de leitura, tag e estante são três classificações independentes.


## Requisitos Funcionais

O histórico na V0 fica no perfil e na obra. Ele só aparece no feed na V1. Status, tag e estante mudam um sem alterar os outros.

### V0

#### RF-01 — Conta e perfil básico

**Critérios de aceite:**

- [ ] CA-01: Uma pessoa cria conta, entra e sai, e vê o próprio perfil em português no celular.
- [ ] CA-02: O perfil mostra o nome, o status, as tags e as estantes dessa conta.
- [ ] CA-03: O perfil é público ou privado. No privado, só pessoas autorizadas por essa conta visualizam o perfil.
- [ ] CA-04: A conta pessoal pode ser Leitor, Autor, ou os dois ao mesmo tempo, sem criar outra conta.

#### RF-02 — Status de leitura

**Critérios de aceite:**

- [ ] CA-01: Cada livro na conta tem um status entre Lido, Lendo, Relendo, Quero Ler e Abandonei.
- [ ] CA-02: Trocar o status mantém as tags e a estante do livro.

#### RF-03 — Tags

**Critérios de aceite:**

- [ ] CA-01: Cada livro pode receber Tenho, Quero ter, Emprestei e Favorito, inclusive mais de uma ao mesmo tempo.
- [ ] CA-02: Colocar ou tirar uma tag mantém o status e a estante do livro.

#### RF-04 — Estantes

**Critérios de aceite:**

- [ ] CA-01: Toda conta nasce com uma estante chamada Padrão. Um livro sem outra estante escolhida fica nela.
- [ ] CA-02: Ao adicionar ou editar um livro, a pessoa cria uma estante nova sem abrir a página de estantes, e o livro passa a ficar nela.
- [ ] CA-03: Cada livro fica em uma estante só.

#### RF-05 — Página da obra e edições

**Critérios de aceite:**

- [ ] CA-01: Cada obra tem uma página, e as edições aparecem dentro dela.
- [ ] CA-02: Status, tags, estante e progresso ficam ligados à edição que a pessoa tem, e a página da obra mostra as edições juntas.

#### RF-06 — Aviso de duplicata

**Critérios de aceite:**

- [ ] CA-01: Ao salvar um livro novo, o sistema compara proximidade de título e de autor com obras já existentes.
- [ ] CA-02: Se houver correspondência, a pessoa vê a obra existente e pode incluir o exemplar como outra edição.

#### RF-07 — Histórico de leitura

**Critérios de aceite:**

- [ ] CA-01: A pessoa registra progresso por número de página ou por porcentagem.
- [ ] CA-02: O horário de início é opcional; o registro salva com e sem esse campo.

#### RF-08 — Estatísticas do período

**Critérios de aceite:**

- [ ] CA-01: O perfil mostra a soma de páginas lidas no mês e no ano.
- [ ] CA-02: A média do período é essa soma dividida pela quantidade de dias em que houve envio de histórico. Dia sem envio fica de fora da divisão.
- [ ] CA-03: Mudar a visibilidade do perfil, da estante, do livro ou de uma publicação não altera esses números.

### V1

#### RF-09 — Anotações privadas no livro

**Critérios de aceite:**

- [ ] CA-01: Na edição que está na conta, a pessoa cria, edita e apaga anotações de texto livre, como para quem emprestou o livro ou notas de leitura e de personagens.
- [ ] CA-02: A anotação fica restrita à conta que a escreveu.

#### RF-10 — Filtros por metadados

**Critérios de aceite:**

- [ ] CA-01: A pessoa filtra os livros por metadados, entre eles tipo (livro, quadrinho ou revista), autor, gênero e nacionalidade.
- [ ] CA-02: O tipo é um metadado como os demais, e o filtro mostra só os itens que combinam com os valores escolhidos.

#### RF-11 — Insígnias

**Critérios de aceite:**

- [ ] CA-01: O perfil exibe até 5 insígnias principais, escolhidas pela própria conta.
- [ ] CA-02: Quem vê o perfil abre o conjunto completo por uma ação do tipo "Ver mais".
- [ ] CA-03: A regra pode ser todas as conquistas listadas. Para a insígnia X que exige A, B e C, ter só A e B deixa a insígnia de fora.
- [ ] CA-04: A regra pode ser pelo menos N conquistas de um conjunto. Para uma insígnia que exige pelo menos 2 de A, B e C, ter A e B concede a insígnia, e ter B e C também.

#### RF-12 — Metas

**Critérios de aceite:**

- [ ] CA-01: A pessoa cria uma meta de páginas, de conclusão de um livro específico, de quantidade de livros ou de dias seguidos com histórico enviado.
- [ ] CA-02: O progresso da meta usa o histórico já registrado. Dias seguidos contam só dias com envio, e essa conta existe só dentro da meta, sem entrar na média da RF-08.

#### RF-13 — Conquistas

**Critérios de aceite:**

- [ ] CA-01: As conquistas ficam em uma aba própria do perfil, separadas por categorias.
- [ ] CA-02: Uma conquista pode existir sem insígnia.
- [ ] CA-03: A regra pode ser todas as conquistas listadas. Para a insígnia X que exige A, B e C, ter só A e B deixa a insígnia de fora.
- [ ] CA-04: A regra pode ser pelo menos N conquistas de um conjunto. Para uma insígnia que exige pelo menos 2 de A, B e C, ter A e B concede a insígnia, e ter B e C também.

#### RF-14 — Seguidores

**Critérios de aceite:**

- [ ] CA-01: Uma pessoa segue e deixa de seguir outra conta.
- [ ] CA-02: O perfil mostra as contagens de seguidores e de seguindo.
- [ ] CA-03: Em perfil privado, o acesso de seguidor passa a valer depois que a conta autoriza.

#### RF-15 — Citações, posts, resenhas e enquetes

**Critérios de aceite:**

- [ ] CA-01: A pessoa publica citação, post, resenha e enquete, e esses itens aparecem no feed de quem segue.
- [ ] CA-02: Uma enquete recebe votos e mostra o resultado a quem pode ver o post.
- [ ] CA-03: Quem publica pode marcar a publicação como spoiler. O conteúdo marcado só aparece depois que quem lê escolhe revelar.
- [ ] CA-04: Outras pessoas podem comentar e curtir a publicação.

#### RF-16 — Histórico no feed

**Critérios de aceite:**

- [ ] CA-01: Um histórico enviado também gera um item no feed.
- [ ] CA-02: O item mostra página ou porcentagem, e o horário de início só quando foi informado.
- [ ] CA-03: Quem publica pode acrescentar uma mensagem, uma reação, ou as duas. A mensagem pode ser marcada como spoiler e só aparece depois que quem lê escolhe revelar.
- [ ] CA-04: Outras pessoas podem comentar e curtir o item de histórico, do mesmo modo que nas publicações da RF-15.

#### RF-17 — Scanner de ISBN

**Critérios de aceite:**

- [ ] CA-01: A câmera lê ISBN-10 e ISBN-13.
- [ ] CA-02: O código encontrado abre a edição correspondente ou o fluxo de cadastro com o ISBN preenchido.

#### RF-18 — Votação de duplicata

**Critérios de aceite:**

- [ ] CA-01: Se a pessoa recusar o aviso de duplicata, o livro entra numa fila até o número de aprovações configurado no admin. O padrão é 5.
- [ ] CA-02: Com as aprovações atingidas, o livro passa a existir como obra separada. Abaixo disso, permanece pendente.

#### RF-19 — Comunidades e clube do livro

**Critérios de aceite:**

- [ ] CA-01: Existe comunidade pública e comunidade privada, com bate-papo em grupo.
- [ ] CA-02: Um clube do livro pode ser criado dentro de uma comunidade ou sozinho, e os dois casos funcionam sem exigir o outro.
- [ ] CA-03: Quem cria uma meta em grupo ou uma competição escolhe os critérios: objetivo colaborativo, ou disputa por páginas num período, de forma contínua, por quantidade de livros, ou outro critério definido na criação. Na meta colaborativa, os participantes somam para o mesmo objetivo.

#### RF-21 — Recortes do feed

**Critérios de aceite:**

- [ ] CA-01: O feed abre no recorte geral. A pessoa pode mudar para seguindo ou para o próprio.
- [ ] CA-02: A ordenação abre em mais recente. A pessoa pode mudar para em alta, ordenado pelo engajamento recente (reações, comentários e votos).

#### RF-22 — Visibilidade de estantes, livros e publicações

Estantes e livros na V0. Publicações na V1.

**Critérios de aceite:**

- [ ] CA-01: Cada estante, livro e publicação tem visibilidade pública, privada (somente seguidores autorizados) ou somente eu. O padrão segue a visibilidade do perfil.
- [ ] CA-02: Ao mudar a visibilidade de uma estante, todos os livros dela passam para a mesma visibilidade.
- [ ] CA-03: Essa mudança não altera as estatísticas da conta.

### V2

#### RF-20 — Progresso vindo de outro app de leitura

**Critérios de aceite:**

- [ ] CA-01: O estudo de viabilidade registra, por fonte (Kindle, Google Books e equivalentes), se a atualização automática ou o botão de atualizar é permitido e tecnicamente possível.
- [ ] CA-02: Só entra no produto a fonte cujo uso comercial e o acesso ao progresso tenham sido aprovados nesse estudo.

#### RF-23 — Perfis comerciais

**Critérios de aceite:**

- [ ] CA-01: Editora é um perfil separado da conta pessoal. Leitor e Autor continuam na conta pessoal.
- [ ] CA-02: Um ou mais perfis pessoais gerenciam o mesmo perfil comercial, no modelo de páginas.
- [ ] CA-03: O mesmo mecanismo aceita outros tipos de perfil comercial além de Editora, cada um também separado da conta pessoal.


## Requisitos Não Funcionais

### RNF-01 — Hospedagem e domínio

A V0 roda no servidor dedicado já contratado na Hostinger. O custo novo para colocar o produto no ar é o domínio. Nenhum outro serviço de infraestrutura pago entra nessa fase.

### RNF-02 — Crescimento

O desenho da V0 atende o grupo inicial e aceita mais usuários e os recursos da V1 sem trocar a base de dados nem reescrever conta, livro e histórico.

### RNF-03 — Idioma e tela

A interface da V0 está em português e os fluxos de conta, estante, obra e histórico funcionam no navegador, em tela de computador e de celular.

### RNF-04 — Reserva de acesso

Perfil privado, item "somente eu" e anotação da RF-09 só saem do servidor para quem a regra autoriza. Esconder o conteúdo na tela não cumpre esta regra. Texto de spoiler fica de fora: quem já pode ver a publicação pode receber esse texto, e a interface o esconde até a pessoa escolher revelar.

### RNF-05 — Configuração do limiar

O número de aprovações da RF-18 muda no admin. O valor inicial é 5, e a mudança vale para as filas seguintes sem publicar código novo.

### RNF-06 — Privacidade no Brasil

A conta pode ser encerrada pela própria pessoa, e as anotações privadas e o histórico dessa conta saem junto. O tratamento dos dados pessoais cabe na LGPD.

### RNF-07 — Acessibilidade da V0

Os fluxos de entrar, colocar um livro na estante e registrar histórico são utilizáveis por teclado e têm contraste e rótulos suficientes para leitor de tela, no nível AA das WCAG 2.2.

### RNF-08 — Modo escuro

A pessoa alterna entre modo claro e modo escuro na V0. A escolha permanece quando ela volta. Os dois modos mantêm o contraste exigido na RNF-07.

### RNF-09 — Latência no servidor (V0)

No servidor dedicado da Hostinger, o percentil 95 fica dentro destes tetos, medido na aplicação, sem contar a rede do celular:

- Salvar histórico, mudar status, tag ou estante: até 500 ms.
- Abrir os dados de estante, obra e perfil: até 800 ms.
- Aviso de duplicata ao salvar um livro: até 1 s.

### RNF-10 — Latência percebida no celular (V0)

Em conexão móvel comum no Brasil, o percentil 95 para a estante e para o registro de histórico ficarem utilizáveis é de até 2 s.

### RNF-11 — Latência do feed (V1)

Abrir o feed no recorte e na ordenação padrão fica utilizável em até 2 s no percentil 95, na mesma conexão. Publicar, curtir e comentar confirmam em até 500 ms no percentil 95 no servidor.


## Fluxo de Usuário

Jornada principal da V0, com a Marina.

1. Marina abre o Livvo no navegador, no computador ou no celular, cria a conta como Leitora e escolhe perfil público ou privado. Se quiser, marca Autor na mesma conta.
2. Ela escolhe modo claro ou escuro. A estante Padrão aparece vazia.
3. Ela busca o livro. Se a obra e a edição que ela quer já existem, ela adiciona essa edição à estante e segue para o passo 5.
4. Ela só cadastra algo novo em dois casos: a obra não aparece na busca, ou a obra aparece e a edição que ela quer não. Ao salvar uma obra nova, se título e autor se aproximam de uma obra já existente, o Livvo mostra essa obra e ela pode incluir o exemplar como outra edição.
5. Sem escolher outra estante, o livro fica na Padrão. No mesmo passo ela pode criar uma estante e deixar o livro nela, e marcar status e tags. O status inicial sugerido é Quero Ler. Lendo é a segunda opção no mesmo controle.
6. Ela abre a edição e registra o progresso por página ou por porcentagem. O horário de início fica em branco, ou ela informa.
7. No perfil, ela vê as páginas do mês e do ano e a média só dos dias em que enviou histórico.

O feed, as anotações privadas, as metas e o restante da V1 começam depois desse ciclo, a partir do perfil e da edição que ela já tem.


## Métricas de Sucesso

A base de todas é zero, porque a V0 ainda não está no ar. A janela é de 8 semanas depois do lançamento.

### M-01 — Jornada concluída

Conta com pelo menos uma edição na estante e um histórico enviado. Meta: 30 contas.

### M-02 — Retorno sem leitura diária

Entre as contas da M-01, 40% enviam histórico em dois dias diferentes dentro de 30 dias após o primeiro registro. A média da RF-08 continua sem contar dia sem envio. Esta meta observa se a pessoa volta em outro dia.

### M-03 — Primeiro histórico

Entre quem conclui a jornada, a mediana do tempo entre criar a conta e enviar o primeiro histórico fica em até 10 minutos.

A taxa de edições encontradas na busca fica fora desta janela. Com o catálogo ainda curto, o cadastro de obra ou edição é o caminho esperado.


## Riscos e Dependências

### R-01 — Catálogo de terceiros

Importar de Pagy, Skoob, Google Books, Amazon Books ou ISBN Database, inclusive por coleta de páginas, pode ser incompatível com uso comercial. Enquanto a checagem não terminar, a V0 vive do que as pessoas buscam e cadastram.

### R-02 — Catálogo curto no lançamento

A M-01 depende de achar ou cadastrar uma edição. Se o cadastro da obra e da edição falhar, as 30 jornadas não acontecem.

### R-03 — Aviso de duplicata

Título e autor parecidos podem apontar para outra obra. A pessoa consegue seguir ao incluir como edição ou, na V0, ao confirmar que é outra obra. Na V1, a fila de 5 aprovações pode deixar livro parado enquanto houver pouca gente.

### R-04 — Um servidor

A V0 inteira fica no dedicado da Hostinger. Indisponibilidade ou limite dessa máquina para o serviço e tira as metas de latência da RNF-09 e da RNF-10. O histórico e as estantes precisam de cópia de segurança fora desse disco.

### R-05 — Domínio

Sem o domínio pago, o endereço público não existe. A hospedagem já está contratada.

### R-06 — Nome Livvo

O nome é temporário e ainda não houve consulta de marca nem de domínio.

### R-07 — Progresso de outros apps

Kindle, Google Books e equivalentes podem não entregar o progresso para um terceiro, ou podem vetar uso comercial. A RF-20 só entra depois do estudo por fonte.

### Dependências para a V0 entrar no ar

Acesso ao servidor da Hostinger, backup desse servidor, registro do domínio, e o fluxo de busca mais cadastro de obra e edição funcionando sem base importada.


## Anexos / Decisões adiadas

### D-01 — Nome

Livvo segue temporário. A consulta de marca e a escolha do domínio ficam para antes do anúncio público.

### D-02 — App nativo

A V0 é a web responsiva no computador e no celular. O aplicativo nativo entra quando houver usuários.

### D-03 — Base inicial

A pesquisa em Pagy, Skoob, Google Books, Amazon Books e ISBN Database, nas versões gratuitas, e a permissão de uso comercial, acontecem antes de qualquer importação. A V0 não espera essa base.

### D-04 — Progresso externo

Quais fontes da RF-20 entram, e se a atualização é automática ou por botão, dependem do estudo de viabilidade.

### D-05 — Outros perfis comerciais

Na V2, Editora é o primeiro tipo. Novos tipos usam o mesmo mecanismo de perfil separado, gerido por um ou mais perfis pessoais. A lista desses tipos fica aberta.

### D-06 — Forma do backup

A cópia de segurança fora do disco da Hostinger é dependência da V0. A ferramenta, a frequência e o local da cópia ficam para a arquitetura.

Algoritmo de proximidade de título e autor, e o detalhe do que conta como engajamento em "em alta", ficam para a arquitetura. O PRD já define que a ordenação em alta usa reações, comentários e votos.
