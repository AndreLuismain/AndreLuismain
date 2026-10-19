# André Luís da Silva Souza

**Sistemas de Informação (BSI) — ICMC · Universidade de São Paulo (USP)**  
**Pesquisador de Iniciação Científica (FAPESP) · Desenvolvimento Backend (Java & Spring Boot) · Arquitetura de Dados**

---

## Resumo Técnico

Graduando em Sistemas de Informação pelo Instituto de Ciências Matemáticas e de Computação da Universidade de São Paulo (ICMC-USP, São Carlos, conclusão prevista em 2029) e Técnico em Redes de Computadores formado pelo SENAI (Varginha-MG). Atua como pesquisador de Iniciação Científica com bolsa FAPESP sob orientação do Prof. Dr. Danilo Hernane Spatti, investigando arquiteturas de bancos de dados híbridos e persistência poliglota (`PostgreSQL` relacional combinado a `JSONB` e índices invertidos GIN) aplicadas ao setor elétrico e ao monitoramento regulatório da ANEEL (PRODIST Módulo 8).

Busca oportunidades de atuação como **Estagiário ou Desenvolvedor Júnior** em Engenharia de Software Backend, Arquitetura de Dados e Engenharia de Agentes de IA.

### Áreas de Atuação e Estudo

- **Desenvolvimento Backend:** Construção de APIs REST e serviços em Java 21 LTS e Spring Boot 3, controle transacional ACID, bloqueio pessimista (`SELECT FOR UPDATE`) com prevenção determinística de deadlocks, bloqueio otimista (`@Version`), padrões *Transactional Outbox* e *Append-Only Ledger*, e programação reativa não-bloqueante com Spring WebFlux e Project Reactor.
- **Arquitetura e Engenharia de Dados:** Modelagem relacional normalizada, bancos de dados multimodelo (`PostgreSQL` + `JSONB`), indexação B-Tree e GIN, migrações versionadas com Flyway e pipelines ETL em Python e Java.
- **Engenharia de Agentes de IA:** Integração estruturada com Large Language Models (LLMs), roteamento de requisições por complexidade de prompt, controle de taxa (*Token Bucket Rate Limiting*), sanitização de código e cache determinístico por hash `SHA-256`.
- **Fundamentos de Ciência da Computação e Infraestrutura:** Estruturas de dados e algoritmos em C e C++ (alocação de memória, ponteiros, registros e arquivos), programação em Assembly de 16 bits (Processador ICMC), administração de redes corporativas (Windows Server, Active Directory, GPO, PowerShell) e desenvolvimento de sistemas gráficos em Java (LibGDX) e C# (Unity).

---

## Tecnologias e Ferramentas

| Categoria | Tecnologias |
| :--- | :--- |
| **Linguagens** | Java 21 LTS, C (C11), C++17, SQL, Python, C#, PowerShell, Assembly (ICMC 16-bit) |
| **Backend e Frameworks** | Spring Boot 3, Spring Data JPA, Hibernate, Spring WebFlux, Project Reactor, Jakarta Bean Validation |
| **Bancos de Dados e Dados** | PostgreSQL (Relacional + JSONB / GIN), H2 Database, Flyway Migrations, Pipelines ETL |
| **Testes e Qualidade** | JUnit 5, Mockito, Spring Boot Test, MockMvc, Arquitetura em Camadas, Princípios SOLID |
| **Infraestrutura e Motores** | Docker, Maven, Gradle, Git, Linux, Windows Server, Active Directory (LDAP/GPO), Unity 3D, LibGDX |

---

## Vitrine de Repositórios e Projetos

### 1. Engenharia Backend, Sistemas Distribuídos e Agentes de IA

Repositório principal: **[`AndreLuismain/Java-Projects`](https://github.com/AndreLuismain/Java-Projects)**  
Monorepositório contendo 11 aplicações e microsserviços desenvolvidos em Java 21 e Spring Boot 3.

| Projeto | Escopo Técnico e Decisões de Arquitetura | Tecnologias |
| :--- | :--- | :--- |
| **[08 · Simulador de Transações Pix](https://github.com/AndreLuismain/Java-Projects/tree/main/08-simulador-transacoes-pix)** | Motor de transferências financeiras em centavos inteiros (`Long`). Implementa ordenação lexicográfica determinística de UUIDs antes de `SELECT FOR UPDATE` (prevenção de deadlocks), livro-razão imutável (*Append-Only Ledger*) de soma zero, *Transactional Outbox* para antifraude e idempotência via cabeçalho `Idempotency-Key`. | Java 21, Spring Boot 3, JPA, Flyway, H2/PostgreSQL |
| **[09 · API Gateway Reativo de Agentes](https://github.com/AndreLuismain/Java-Projects/tree/main/09-api-gateway-agentes)** | Gateway não-bloqueante construído sobre Spring WebFlux. Implementa *Rate Limiting* em memória pelo algoritmo *Token Bucket* (`ConcurrentHashMap` + `AtomicReference`) com resposta `HTTP 429` (`Retry-After`), classificador determinístico de complexidade de prompts (`FAST` vs. `ROBUST`) e propagação de `X-Correlation-Id`. | Java 21, Spring WebFlux, Project Reactor |
| **[10 · Agente Documentador de Código Legado](https://github.com/AndreLuismain/Java-Projects/tree/main/10-agente-documentador-legado)** | Serviço de análise estática e geração de documentação técnica para código legado (COBOL, Pascal, C, Java). Inclui defesa contra *path traversal*, sanitização de credenciais antes do envio ao provedor LLM e cache de inferência indexado por hash `SHA-256`. | Java 21, Spring Boot 3, SHA-256, REST |
| **[11 · Motor de Recomendação de Pesquisas IC](https://github.com/AndreLuismain/Java-Projects/tree/main/11-motor-recomendacao-pesquisas)** | Pipeline ETL com extração, normalização e deduplicação por hash `SHA-256`, combinado a um motor de ranqueamento híbrido (70% determinístico + 30% semântico via LLM) com *fallback* transparente. | Java 21, Spring Boot 3, JPA, H2/PostgreSQL |
| **[06 · API de Orquestração de Relatórios IC](https://github.com/AndreLuismain/Java-Projects/tree/main/06-api-orquestracao-relatorios-ic)** | Ingestão idempotente de apontamentos semanais de Iniciação Científica, classificação de esforço por categoria acadêmica via Agente LLM com *fallback* heurístico e compilação de relatórios em Markdown. | Java 21, Spring Boot 3, JPA, Flyway |
| **[07 · Agendamento de Laboratórios e Salas](https://github.com/AndreLuismain/Java-Projects/tree/main/07-agendamento-laboratorios-salas)** | Controle de concorrência pessimista (`LockModeType.PESSIMISTIC_WRITE`) contra *double-booking*, cálculo de interseção de intervalos temporais ($t_{\text{inícioA}} < t_{\text{fimB}} \land t_{\text{fimA}} > t_{\text{inícioB}}$) e exportação analítica em CSV. | Java 21, Spring Boot 3, JPA, Flyway |
| **[05 · Analisador de Editais de IC](https://github.com/AndreLuismain/Java-Projects/tree/main/analisador-editais-ic)** | Coleta automatizada com defesa anti-SSRF (bloqueio de IPs privados e *loopback*), *Rate Limiting* por domínio, processamento assíncrono (`@Async`) e extração estruturada via Google Gemini API. | Java 21, Spring Boot 3, WebFlux, Jsoup, PostgreSQL |

---

### 2. Pesquisa Científica (FAPESP) e Arquitetura de Dados

| Repositório / Projeto | Escopo Técnico e Arquitetura | Tecnologias |
| :--- | :--- | :--- |
| **[`ic-aneel-hybrid-database`](https://github.com/AndreLuismain/ic-aneel-hybrid-database)** | **Iniciação Científica FAPESP (ICMC-USP):** Arquitetura de dados híbrida no PostgreSQL 15+ que unifica tabelas relacionais contábeis (MCSE/MCPSE) com documentos geográficos semiestruturados (`BDGD` em `JSONB` indexado por GIN `jsonb_path_ops`) para auditoria de conformidade regulatória e Revisão Tarifária Periódica da ANEEL. Inclui pipeline ETL em Python (`ijson`/`pandas`) e API REST em Java 21 / Spring Boot 3. | PostgreSQL (`JSONB`/GIN), Python ETL, Java 21, Spring Boot 3 |
| **[03 · Analisador de Dados ANEEL](https://github.com/AndreLuismain/Java-Projects/tree/main/03%20Analisador%20Dados%20Aneel)** | Processador analítico em memória de arquivos CSV de indicadores regulatórios do setor elétrico utilizando Java Streams API e aritmética de precisão (`BigDecimal`). | Java 21, Streams API, CSV |
| **[04 · API de Gerenciamento de Obras Elétricas](https://github.com/AndreLuismain/Java-Projects/tree/main/04%20API%20Gerenciamento%20Obras)** | API RESTful em camadas para controle de cronograma e orçamento de obras de infraestrutura elétrica com persistência em PostgreSQL conteinerizado via Docker Compose. | Java 21, Spring Boot 3, PostgreSQL, Docker |

---

### 3. Infraestrutura como Código, Redes e Segurança Corporativa

| Repositório | Escopo Técnico | Tecnologias |
| :--- | :--- | :--- |
| **[`senai-security-active-directory`](https://github.com/AndreLuismain/senai-security-active-directory)** | Automação de provisionamento de Unidades Organizacionais (OUs), grupos de segurança e usuários em lote via CSV no Windows Server Active Directory utilizando scripts PowerShell, políticas de endurecimento (GPO) e módulo de consulta LDAP/JNDI em Java. | PowerShell, Windows Server, Active Directory, GPO, Java LDAP |

---

### 4. Fundamentos de Ciência da Computação, Arquitetura e Estruturas de Dados

| Repositório | Escopo Técnico | Tecnologias |
| :--- | :--- | :--- |
| **[`Simulador-de-Aula-do-Simoes`](https://github.com/AndreLuismain/Simulador-de-Aula-do-Simoes)** | Jogo interativo desenvolvido integralmente em Assembly de 16 bits para a arquitetura do Processador ICMC-USP, com escrita direta em memória de vídeo (`outchar`), tabelas de *sprites* e gerador pseudoaleatório por deslocamento de bits (LFSR/XOR), acompanhado do código-fonte em C do simulador da CPU/ULA e do montador (`montador`). | Assembly ICMC 16-bit, C (`gcc`), GTK+ 2.0 |
| **[`Studies-C`](https://github.com/AndreLuismain/Studies-C)** | Implementações de Algoritmos e Estruturas de Dados I (AEDS I) em C e C++: manipulação direta de cadeias de caracteres (`char[]` / ASCII), operações de conjuntos sobre vetores estáticos, sistemas CRUD com registros (`struct`) persistidos em disco (`BD_veiculos.txt`) e análise experimental de métodos de ordenação (*Bubble, Selection, Insertion Sort*). | C (C11), C++17, GCC/G++ |
| **[`Studies-Java`](https://github.com/AndreLuismain/Studies-Java)** | Laboratório estruturado em 12 módulos progressivos (`Easy`, `Medium`, `Hard`) em Java 21 LTS cobrindo POO, estruturas de dados e programação funcional: implementação de *LRU Cache* $O(1)$ (`HashMap` + lista duplamente encadeada), motor de *Autocomplete* com `TreeMap`, avaliador de AST com `sealed interface` e *Pattern Matching*, e padrões *Builder*, *Strategy*, *Template Method* e *Combinator*. | Java 21 LTS, Collections, Streams, Design Patterns |

---

### 5. Sistemas Gráficos e Desenvolvimento de Jogos

| Repositório | Escopo Técnico | Tecnologias |
| :--- | :--- | :--- |
| **[`JogoCerrado` (*EICerrado*)](https://github.com/AndreLuismain/JogoCerrado)** | Jogo educacional 3D sobre a fauna do bioma Cerrado desenvolvido em C# na Unity 6 (URP). Arquitetura modularizada em 13 namespaces independentes, com máquina de estados de IA via NavMesh, avaliação fotográfica por Raycasting e planos de Frustum da câmera, catálogo em ScriptableObjects e persistência em JSON. | C#, Unity 6 (URP), NavMesh AI, ScriptableObjects |
| **[`projeto-POO`](https://github.com/AndreLuismain/projeto-POO)** | Implementação orientada a objetos do jogo *Snake* em Java 21 e LibGDX (arquitetura multi-módulo Gradle `core` / `lwjgl3`). Utiliza fila duplamente terminada (`Deque<GridPosition>`) para movimentação em tempo constante $O(1)$, aritmética modular para *wrap-around* de bordas e testes unitários *headless* com JUnit 5. | Java 21, LibGDX, LWJGL 3, Gradle, JUnit 5 |

---

## Formação Acadêmica

- **Bacharelado em Sistemas de Informação (BSI)** *(2025 – 2029, em andamento)*  
  Instituto de Ciências Matemáticas e de Computação — Universidade de São Paulo (ICMC-USP, São Carlos)  
  Pesquisa de Iniciação Científica (Bolsista FAPESP): *Arquitetura de Dados Híbrida e Persistência Poliglota para Redes Elétricas*, orientação do Prof. Dr. Danilo Hernane Spatti.

- **Técnico em Redes de Computadores** *(Concluído)*  
  SENAI UI Aloysio Ribeiro de Almeida (Varginha-MG)  
  Infraestrutura física e lógica de redes, roteamento e *switching*, administração de servidores Linux e Windows Server, Active Directory e segurança de perímetro.
