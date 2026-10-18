# Stack — Livvo V0

**Data:** 2026-10-17
**Status:** Decidida
**PRD:** [PRD.md](PRD.md)

A V0 roda inteira no servidor dedicado já contratado na Hostinger. O único custo novo de infraestrutura é o domínio. Não entra banco gerenciado, serviço de identidade, APM nem fila paga.

No dedicado dá para instalar PostgreSQL e MySQL/MariaDB. A hospedagem compartilhada da Hostinger só oferece MariaDB. O PRD fixa servidor dedicado, então os dois bancos cabem sem serviço pago novo. A escolha é PostgreSQL, pela extensão `pg_trgm`, que segura o teto de 1 s da RNF-09 na comparação de título e autor.

| Camada | Tecnologia | Justificativa | RNF |
| --- | --- | --- | --- |
| API | ASP.NET Core no .NET 10 (LTS), Kestrel | Monólito tipado, cookie do Identity na mesma origem, hospedável em Linux | RNF-01, RNF-02, RNF-04, RNF-09 |
| Proxy | Nginx e systemd | TLS no domínio, encaminha para o Kestrel, sobe o processo com a máquina | RNF-01, RNF-03 |
| Web | React, TypeScript, Vite (`react-ts`), React Router | Web responsiva em português, computador e celular, modo claro e escuro | RNF-03, RNF-07, RNF-08, RNF-10 |
| Banco | PostgreSQL no mesmo servidor, EF Core com Npgsql | Sem serviço pago. `pg_trgm` e índice GIN para duplicata de obra. A base não troca na V1 | RNF-01, RNF-02, RNF-09 |
| Capa | SkiaSharp | Recusa arquivo grande e grava só WebP reduzido. Licença compatível com uso comercial futuro | RNF-01, RNF-09 |
| Contrato | `Microsoft.AspNetCore.OpenApi` e `Microsoft.Extensions.ApiDescription.Server` | Documento OpenAPI gerado no build. Swagger UI não entra | RNF-02 |
| Teste de API | `WebApplicationFactory` | Contrato, autorização e regras de domínio contra o OpenAPI | RNF-04, RNF-06 |
| Teste de componente | Vitest em modo browser, `vitest-browser-react`, provider Playwright | Componentes da jornada por papel acessível | RNF-07, RNF-08 |
| QA | Playwright e `@axe-core/playwright` | Jornada da Marina no computador e no celular, teclado e contraste | RNF-07, RNF-08, RNF-10 |
| Backup | `pg_dump` cifrado e cópia do diretório de capas | Fora do disco principal. O destino não pode ser um serviço de infraestrutura novo e pago | RNF-01, R-04 |
| Observabilidade | Log estruturado e endpoint de saúde | Sem APM pago | RNF-01 |

Documentação conferida antes de fechar a stack: ASP.NET Core (`/dotnet/aspnetcore.docs`) para proxy reverso, cookie e OpenAPI nativo desde o .NET 9; Npgsql EF Core (`/npgsql/efcore.pg`) para `pg_trgm`; React (`/websites/react_dev`) para Vite e tema; Vitest (`/vitest-dev/vitest`) para teste de componente no browser; Playwright (`/microsoft/playwright`) para jornada, viewports e axe; SkiaSharp (`/mono/skiasharp`) para decodificar JPEG, PNG e WebP e gravar WebP.

Tipografia, cor, componentes visuais e logo não fazem parte desta stack. Entram na etapa de design, depois desta arquitetura e antes das tasks.

O cliente nativo, em Kotlin Multiplatform, não entra na V0. Quando existir, consome esta mesma API. A porta de bearer fica descrita na arquitetura e não é implementada agora.
