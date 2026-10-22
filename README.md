# Awesome-Graphql-Frameworks

## Top GraphQL Frameworks Ecosystem



**Curated List of SaaS Products & Open-Source GitHub Projects**  

*Focused on Schema-First Servers, Code-First Modules & Self-Hosted Federation Platforms*  

**Last updated: October 2026**



This repository tracks notable **SaaS platforms** and **open-source projects** for **GraphQL Frameworks**. These tools provide the server-side infrastructure for building GraphQL APIs—handling schema definition, resolvers, federation, and execution—so teams can expose data graphs without writing protocol-level code from scratch.



**Examples** include Apollo Server, Hasura, GraphQL Hive, WunderGraph Cosmo, NestJS GraphQL, Prisma, and Supabase (the category leaders).



**Open-source emphasis**: This section is heavily expanded with every major active project for self-hosting, federation governance, and transparent schema management—ideal for teams that need data sovereignty, avoid per-request SaaS pricing, and require auditable GraphQL infrastructure. The open-source landscape is anchored by **Apollo Server** (the spec-compliant JavaScript standard), **Hasura** (instant GraphQL over databases), and **GraphQL Hive** (MIT-licensed federation platform), with **NestJS GraphQL** offering code-first TypeScript integration, **Prisma** serving as the ORM layer inside resolvers, and **Supabase** providing Postgres-native GraphQL via `pg_graphql`.



Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.



## Table of Contents

- [SaaS/Hosted Platforms](#saas-hosted-platforms)

- [Open-Source GitHub Projects](#open-source-github-projects)

- [How to Contribute](#how-to-contribute)

- [Disclaimer](#disclaimer)



## SaaS/Hosted Platforms



- **[Apollo GraphOS (Studio)](https://studio.apollographql.com/)**  

  Apollo's commercial platform for schema registry, federation management, and usage reporting. The open-source Apollo Server integrates with GraphOS for schema checks and metrics, but the platform itself is proprietary. Enterprise-tier pricing for teams needing federation governance and schema delivery.



- **[Hasura Cloud (DDN)](https://hasura.io/)**  

  Managed tier of Hasura's Data Delivery Network. **Important licensing nuance**: Hasura V3 core engine and data connectors are Apache 2.0, but the **DDN CLI, web console, and LSP are proprietary**—building metadata requires the cloud control plane . The managed offering provides instant GraphQL over Postgres, MongoDB, ClickHouse, and SQL Server without self-hosting.



- **[AWS AppSync](https://aws.amazon.com/appsync/)**  

  AWS's managed GraphQL service with real-time subscriptions, offline support, and built-in authorization. Integrates with DynamoDB, Lambda, and other AWS services. Consumption-based pricing. Proprietary, best for AWS-native architectures.



- **[StepZen (IBM)](https://stepzen.com/)**  

  GraphQL-as-a-service platform for composing graphs from REST, SOAP, SQL, and other GraphQL sources. Acquired by IBM and integrated into their API Connect portfolio. Declarative configuration via `stepzen` CLI. Proprietary with free tier.



## Open-Source GitHub Projects



- **[Apollo Server](https://github.com/apollographql/apollo-server)**  

  The spec-compliant, production-ready JavaScript GraphQL server. **Apollo Server 5** is a small upgrade from v4 focused on dependency version adjustments, typically taking minutes to migrate . Compatible with any GraphQL client, runs on Express, Fastify, AWS Lambda, Azure Functions, Cloudflare Workers, and more . **Schema-first** orientation with straightforward setup and universal data source compatibility . **Status note**: the OpenSSF scorecard shows maintenance activity has slowed (2/10 maintained score), though v5 remains current . MIT licensed. Best for Node.js teams that want a standard, well-documented server without framework lock-in.



- **[Hasura GraphQL Engine](https://github.com/hasura/graphql-engine)**  

  The instant GraphQL standard over databases. **V2** (stable) provides real-time GraphQL over Postgres with row-level permissions, event triggers, and actions. **V3** (DDN) adds support for MongoDB, ClickHouse, and SQL Server via data connectors . **Licensing**: V3 core engine and all connectors are Apache 2.0; V2 core engine is Apache 2.0, with CLI/console under MIT . **Critical caveat**: Hasura's own team confirms that while the engine is open-source, the **DDN CLI, web console, and LSP are proprietary**, and building metadata for V3 requires the cloud control plane . Best for teams that want instant GraphQL over existing databases and can work within the V2 self-hosted model or accept the DDN cloud dependency for V3.



- **[GraphQL Hive](https://github.com/graphql-hive)**  

  A **fully open-source (MIT) schema registry, analytics, and gateway** for GraphQL federation and monolithic APIs . **Components**: Hive Console (schema registry), Hive Gateway (JS-based federation/proxy gateway), and **Hive Router** (high-performance Rust federation router) . Supports Federation v1 and v2, subscriptions, and self-hosting via Docker . The Hive Gateway can act as a Federation gateway, subgraph, or proxy for any GraphQL API . **Ecosystem**: The Guild also maintains `graphql-yoga` (spec-compliant server), `graphql-modules`, and `graphql-eslint` within the same organization . Best for teams that want Apollo Federation compatibility with MIT licensing and self-hosting as a first-class option.



- **[WunderGraph Cosmo](https://github.com/wundergraph/cosmo)**  

  Full-lifecycle GraphQL federation management platform. **Stack**: CLI (`wgc`), Control Plane (Platform API + Node API), Router (federation-aware), and Studio (web interface) . Supports Federation v1 and v2, including subscriptions. **Deployment**: runs locally, on-premises, or as managed service . **Positioning**: enterprise-ready for scaling from a few subgraphs to thousands of operations, with composition checks, analytics, and distributed tracing . **Governance**: open-source router with self-host or managed options, no usage penalties . Best for teams that need federation governance with a path from self-hosted to managed without lock-in.



- **[NestJS GraphQL (`@nestjs/graphql`)](https://github.com/nestjs/graphql)**  

  The GraphQL module for the NestJS framework. **Two approaches**: **code-first** (TypeScript decorators generate schema) or **schema-first** (SDL files generate TypeScript types) . Supports Apollo and Mercurius drivers, real-time subscriptions via WebSocket, federation, and a plugin system . **GraphiQL** is the default IDE since v14 (GraphQL Playground was removed) . **Maintenance**: 2k stars, active with 30 commits in 90 days . MIT licensed. Best for NestJS teams that want first-class GraphQL integration with TypeScript end-to-end type safety.



- **[Prisma](https://github.com/prisma/prisma)**  

  The TypeScript ORM that serves as the **database layer inside GraphQL resolvers**—not a GraphQL framework itself. Prisma Client provides type-safe database queries, and its schema syntax is heavily inspired by GraphQL SDL . Works with Apollo Server, GraphQL Yoga, NestJS, Pothos, Nexus, and TypeGraphQL . **Note**: Prisma is migrating to a **Prisma Next** TypeScript rewrite (v7 branch), designed to be extensible and AI-agent friendly . Best for teams that want an ORM with end-to-end type safety from database to GraphQL resolver, reducing N+1 boilerplate via built-in dataloader patterns .



- **[Supabase (pg_graphql)](https://github.com/supabase/supabase)**  

  Supabase is a Postgres development platform; its GraphQL capability comes from the **`pg_graphql`** extension, which reflects a GraphQL schema from existing SQL tables and exposes it via `graphql.resolve()` . **No additional server required**—any language that connects to Postgres can query via GraphQL . Integrates with PostgREST for HTTP exposure . **Status**: introspection is **disabled by default** since `pg_graphql` 1.6.0 and must be enabled per schema . Best for teams already using Supabase or Postgres that want GraphQL without a separate server layer, accepting the trade-off of schema reflection rather than hand-crafted resolvers.



### Additional Strong Open-Source Options



- **GraphQL Yoga** — Spec-compliant, Fetch API-based GraphQL server from The Guild. Runs on any JS environment (Node, Deno, Bun, Cloudflare Workers). Best for teams that want a lightweight alternative to Apollo Server with modern runtime support .

- **Pothos** — Code-first schema builder for TypeScript with a plugin system. Pairs well with Prisma for type-safe resolvers. Best for teams that prefer code-first without NestJS's framework overhead.

- **Mercurius** — Fastify-based GraphQL server with JIT compilation. Best for Fastify users seeking performance.

- **Frameworks for building custom systems**: Use **Apollo Server** or **GraphQL Yoga** as the execution layer, **Prisma** inside resolvers for database access, and **GraphQL Hive** or **WunderGraph Cosmo** for federation governance if the graph spans multiple services. For NestJS teams, use **`@nestjs/graphql`** with **Prisma** for a cohesive TypeScript stack. For instant GraphQL over Postgres without resolvers, use **Hasura V2** (self-hosted) or **Supabase `pg_graphql`**.



## How to Contribute



1. Fork the repo.

2. Add/edit entries in `README.md` (follow existing format).

3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.

4. Submit PR with a short explanation.



Star the repo if you find it useful!



## Disclaimer



- This is a **community-curated** list — not exhaustive and not an endorsement.

- **"Open-source" claims vary significantly**: Apollo Server and GraphQL Hive are fully MIT/Apache licensed. Hasura V3's engine is Apache 2.0, but its DDN CLI and console are proprietary, and V3 metadata creation requires the cloud control plane—self-hosting V3 is not fully open-source . Verify licensing before committing to a self-hosted deployment.

- **Prisma is an ORM, not a GraphQL framework**: it handles database access inside resolvers, not schema definition or execution. It's included because it's a common companion to GraphQL servers, not a replacement for them .

- **Apollo Server's maintenance activity has slowed** according to OpenSSF metrics; evaluate GraphQL Yoga as a lighter, actively maintained alternative if you don't need Apollo Studio integration .



---



**Made for backend engineers, full-stack developers, and platform teams building GraphQL APIs with control over their data layer.**  

Let's make GraphQL frameworks more open, understandable, and appropriately licensed.
