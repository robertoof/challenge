# Challenge técnico Fullstack

## React/Next.js, C#/.NET e SQL Server

### Objetivo

Desenvolver uma aplicação web para registrar, acompanhar e concluir solicitações internas. O desafio busca avaliar domínio da stack, organização do código, modelagem de dados, decisões técnicas e capacidade de explicar a solução.

**Tempo sugerido:** 6 a 8 horas. Não esperamos uma aplicação com acabamento de produção. Caso o tempo termine, documente no README o que ficou pendente e como seria implementado.

## Cenário

Uma empresa precisa controlar solicitações internas de suporte. Cada solicitação deve possuir:

- título;
- descrição;
- solicitante;
- prioridade: baixa, média ou alta;
- status: aberta, em andamento ou concluída;
- data de criação;
- data de conclusão, quando aplicável.

## Requisitos obrigatórios

### Front-end

Utilize **React com Next.js e TypeScript**.

A aplicação deve permitir:

1. listar as solicitações;
2. cadastrar uma solicitação;
3. visualizar os detalhes;
4. alterar prioridade e status;
5. filtrar por status e prioridade;
6. pesquisar pelo título ou solicitante;
7. paginar os resultados;
8. apresentar estados de carregamento, lista vazia e erro;
9. validar o formulário e exibir mensagens compreensíveis ao usuário;
10. funcionar adequadamente em telas de computador e celular.

O candidato pode escolher App Router ou Pages Router, desde que explique a decisão.

### Back-end

Utilize **C# com ASP.NET Core Web API** e uma versão do .NET com suporte ativo.

A API deve oferecer operações para:

- cadastrar uma solicitação;
- consultar uma solicitação por identificador;
- listar solicitações com filtros, pesquisa e paginação;
- atualizar prioridade e status;
- excluir uma solicitação ainda aberta.

Implemente as seguintes regras:

1. título, descrição e solicitante são obrigatórios;
2. uma solicitação concluída deve receber a data de conclusão automaticamente;
3. uma solicitação concluída não pode voltar para aberta;
4. apenas solicitações abertas podem ser excluídas;
5. valores inválidos devem gerar resposta HTTP adequada e mensagem clara;
6. registros inexistentes devem retornar `404 Not Found`.

Organize as responsabilidades de modo que regras de negócio não fiquem concentradas nos controllers.

### Banco de dados

Utilize **Microsoft SQL Server**.

A solução deve incluir:

- modelo relacional coerente;
- chave primária e restrições necessárias;
- migrations ou script SQL versionado para criação do banco;
- persistência utilizando Entity Framework Core ou outra abordagem justificada;
- consultas parametrizadas;
- ordenação padrão pelas solicitações mais recentes;
- pelo menos um índice criado para apoiar os filtros ou a pesquisa implementada.

No README, explique a finalidade do índice escolhido e seu impacto esperado.

### Testes

Inclua testes automatizados relevantes. O mínimo esperado é:

- dois testes de regras de negócio no back-end;
- um teste de endpoint ou integração no back-end;
- um teste de componente ou fluxo principal no front-end.

Priorizamos a qualidade e a relevância dos cenários sobre a quantidade de testes.

## Diferenciais opcionais

Os itens abaixo não são obrigatórios e não devem comprometer os requisitos principais:

- autenticação e autorização;
- atualização otimista ou estratégia explícita de cache;
- Docker Compose para aplicação e SQL Server;
- documentação OpenAPI/Swagger aprimorada;
- acessibilidade demonstrável;
- observabilidade, logs estruturados ou correlação de requisições;
- pipeline de integração contínua;
- publicação em ambiente acessível.

## Entrega

Disponibilize o código em um repositório Git e inclua um `README.md` contendo:

1. instruções completas para executar a solução;
2. versões e dependências necessárias;
3. forma de criar e configurar o banco;
4. decisões técnicas e justificativas;
5. limitações conhecidas;
6. melhorias que faria com mais tempo;
7. tempo aproximado utilizado;
8. indicação de ferramentas de IA utilizadas e como foram usadas.

Não inclua senhas ou outros segredos no repositório. Forneça arquivos de exemplo para as configurações necessárias.

## Restrições

- Não é permitido substituir o SQL Server por banco em memória, SQLite ou outro banco na entrega principal.
- Bibliotecas de componentes e ferramentas auxiliares são permitidas, mas o candidato deve saber explicar sua utilização.
- Código produzido com auxílio de IA é permitido, desde que declarado. O candidato permanece responsável por entender e defender toda a solução.
- Commits progressivos são recomendados para permitir a compreensão da evolução do trabalho.

## Critérios de avaliação

| Área | Pontos | O que será observado |
|---|---:|---|
| Front-end React/Next.js | 20 | Componentização, estado, formulários, consumo da API, tratamento dos estados da interface, TypeScript e responsividade |
| Back-end C#/.NET | 25 | Design da API, regras de negócio, validação, erros, uso de HTTP, assincronismo e separação de responsabilidades |
| SQL Server e persistência | 20 | Modelagem, integridade, migrations/scripts, consultas, paginação, índices e prevenção de SQL injection |
| Arquitetura e integração | 15 | Limites entre camadas, contratos, integração front/back, configuração e manutenibilidade |
| Testes e qualidade | 10 | Relevância dos testes, legibilidade, tratamento de casos extremos e facilidade de manutenção |
| Documentação e apresentação | 10 | Execução reproduzível, justificativas, transparência, comunicação e domínio da própria solução |
| **Total** | **100** | |

### Faixas sugeridas

- **85 a 100:** forte aderência para nível sênior;
- **70 a 84:** boa aderência, com pontos específicos para aprofundar;
- **55 a 69:** aderência parcial; avaliar conforme o nível esperado;
- **abaixo de 55:** lacunas relevantes para a stack ou para a senioridade requerida.

Uma entrega que não executa pode ser avaliada, mas deve perder pontos nos itens afetados. A avaliação não deve premiar quantidade de funcionalidades em detrimento dos requisitos obrigatórios.

## Roteiro da apresentação técnica

Reserve entre 45 e 60 minutos:

1. **Demonstração — 10 minutos:** candidato executa o fluxo principal.
2. **Arquitetura — 10 minutos:** explica organização, contratos e decisões.
3. **Aprofundamento — 20 minutos:** perguntas técnicas sobre front-end, API e banco.
4. **Mudança ao vivo — 10 minutos:** pequena alteração para observar raciocínio e domínio do código.
5. **Discussão final — 10 minutos:** limitações, segurança, escala e próximos passos.

### Perguntas recomendadas

- Por que escolheu App Router ou Pages Router?
- O que é renderizado no servidor e no cliente? Por quê?
- Como evita estado duplicado ou dados desatualizados no front-end?
- Onde estão as regras de negócio e como garante que não sejam contornadas?
- Como a API diferencia erro de validação, conflito e registro inexistente?
- Como a paginação é executada no SQL Server?
- Qual consulta utiliza o índice criado? Como verificaria o plano de execução?
- O que aconteceria com duas atualizações simultâneas da mesma solicitação?
- Que mudanças seriam necessárias para suportar alto volume?
- Quais trechos foram auxiliados por IA e como foram validados?

### Sugestão de alteração ao vivo

Solicite uma única mudança pequena, dando ao candidato de 10 a 15 minutos. Exemplos:

- adicionar o status **cancelada** e definir uma transição permitida;
- incluir ordenação por prioridade;
- impedir conclusão quando a descrição tiver menos de determinado tamanho;
- exibir no front-end a duração de uma solicitação concluída.

Avalie a leitura do código, a identificação dos pontos afetados, a preservação das regras existentes e a explicação do raciocínio. A conclusão integral da alteração é menos importante que a qualidade da abordagem.

## Condições eliminatórias sugeridas

Use condições eliminatórias apenas quando forem essenciais para a vaga:

- solução principal sem React/Next.js, C#/.NET ou SQL Server;
- impossibilidade de explicar partes relevantes do próprio código;
- exposição de credenciais ou dados sensíveis no repositório;
- ausência completa de regras de negócio no servidor;
- entrega copiada sem atribuição ou declaração.

Não elimine automaticamente por problema de configuração local, escolha arquitetural diferente ou falta de um diferencial opcional. Primeiro avalie a justificativa e o domínio técnico demonstrado.
