# Escopo, Profundidade e Objetos de Avaliação

## Introdução

Nesta seção definimos o que será avaliado no **No Fluxo UnB**, até que nível de detalhe pretendemos ir e o que fica de fora neste momento. A ideia é deixar claro o recorte da avaliação para que os resultados façam sentido dentro das nossas limitações de tempo e acesso.

As decisões aqui tomadas se baseiam na [priorização de características](proposito-da-avaliacao.md#14-classificação-e-ênfase-das-características-de-qualidade) feita anteriormente, no [mapeamento de partes interessadas](partes-interessadas.md) e nas [características do produto](caracteristicas-produto.md).

---

## 1. O que será avaliado (Dentro do Escopo)

A tabela abaixo lista os componentes do No Fluxo UnB que serão avaliados e o motivo de cada um ter sido incluído.

<div align="center">
    <p><strong>Tabela 1 – Objetos incluídos na avaliação</strong></p>
</div>

| Objeto de Avaliação | Descrição | Por que está no escopo? |
| :--- | :--- | :--- |
| **Backend da API** (Node.js / Express / TypeScript) | Servidor que processa requisições e se comunica com o banco de dados via Supabase. | É o coração do sistema — se o backend falha, nada funciona. Impacta diretamente confiabilidade e manutenibilidade. |
| **Frontend Web** (SvelteKit 2 / Svelte 5) | Interface onde o aluno interage com o fluxograma, faz upload do histórico e visualiza estatísticas. | Erros no frontend podem causar problemas como dados não salvos ou telas travadas. Além disso, a organização dos componentes afeta a manutenibilidade. |
| **Processamento de PDF** (Python / PyMuPDF + OCR) | Serviço que lê o histórico escolar em PDF e extrai as disciplinas cursadas. | Funcionalidade central do sistema. Se a leitura do PDF falha ou extrai dados errados, todo o fluxograma fica comprometido. |
| **Repositório e documentação** | Estrutura de pastas, README, Docker, CI/CD, guias de contribuição. | Como o projeto troca de equipe a cada semestre, a documentação é o que garante que alguém novo consiga contribuir. |
| **Banco de dados** (PostgreSQL / Supabase) | Esquema de tabelas, migrações e persistência dos dados acadêmicos. | Perder dados do histórico ou do fluxograma é a pior coisa que pode acontecer para o usuário. A integridade dos dados é essencial. |

<p align="center"><b>Fonte:</b> Autores, 2026.</p>

---

## 2. O que NÃO será avaliado (Fora do Escopo)

Alguns componentes ficaram de fora nesta fase. A tabela abaixo explica o motivo de cada exclusão.

<div align="center">
    <p><strong>Tabela 2 – Objetos excluídos da avaliação</strong></p>
</div>

| Objeto Excluído | Por que ficou de fora? |
| :--- | :--- |
| **Módulo de IA / RAGFlow** | Ainda está em desenvolvimento e não tem uma versão estável. Avaliar IA exigiria métricas próprias (precisão, relevância) que não fazem parte do nosso foco atual. Pretendemos incluir em fases futuras. |
| **Infraestrutura de produção** | Não temos acesso ao servidor de produção, então não dá pra avaliar configurações de rede, balanceamento de carga, etc. Vamos nos limitar ao que está no código-fonte. |
| **Integrações externas** (Google OAuth, Supabase Auth) | São serviços de terceiros que a gente não controla. Vamos avaliar como o sistema *trata* falhas dessas integrações, mas não os serviços em si. |
| **Usabilidade / UX** | Na [priorização](proposito-da-avaliacao.md#14-classificação-e-ênfase-das-características-de-qualidade) essa característica ficou como "não se enquadra". Decidimos focar em qualidade interna primeiro. |
| **Segurança** | Avaliar segurança de verdade exige ferramentas e conhecimento que a equipe ainda não tem (pentesting, SAST, DAST). Pode entrar em fases futuras. |

<p align="center"><b>Fonte:</b> Autores, 2026.</p>

---

## 3. Profundidade da Avaliação

Nem todos os objetos serão analisados com o mesmo nível de detalhe. Definimos três níveis de profundidade:

<div align="center">
    <p><strong>Tabela 3 – Níveis de profundidade</strong></p>
</div>

| Nível | O que significa | Exemplo |
| :---: | :--- | :--- |
| **P1 – Superficial** | Verificação básica: o artefato existe e está minimamente organizado. | Checar se tem README, se o CI roda. |
| **P2 – Intermediário** | Análise com ferramentas automatizadas e revisão do código. | Rodar linter, verificar cobertura de testes, revisar estrutura de pastas. |
| **P3 – Aprofundado** | Testes manuais, simulação de cenários e análise detalhada de fluxos críticos. | Testar com PDFs mal formatados, simular picos de acesso, analisar tratamento de exceções. |

<p align="center"><b>Fonte:</b> Autores, 2026.</p>

A tabela a seguir cruza cada objeto com as duas características avaliadas e o nível que pretendemos atingir:

<div align="center">
    <p><strong>Tabela 4 – Profundidade por objeto</strong></p>
</div>

| Objeto | Confiabilidade | Manutenibilidade | Por quê? |
| :--- | :---: | :---: | :--- |
| Backend API | P3 | P3 | É o componente mais crítico. Precisa de análise completa nas duas frentes. |
| Frontend Web | P2 | P2 | Importante, mas falhas tendem a ser mais localizadas que no backend. |
| Processamento PDF | P3 | P2 | A confiabilidade aqui é crucial (PDFs vêm em formatos variados). O módulo é isolado, então a manutenibilidade é mais simples de analisar. |
| Repositório e Docs | P1 | P3 | Não afeta diretamente a confiabilidade do sistema em si, mas é vital pra manutenibilidade. |
| Banco de Dados | P3 | P1 | Integridade dos dados é prioridade máxima. O esquema é gerenciado pelo Supabase, então a manutenibilidade é menor preocupação. |

<p align="center"><b>Fonte:</b> Autores, 2026.</p>

---

## 4. Relação com Avaliações Anteriores/Futuras

Este documento faz parte da primeira fase do processo de avaliação. As fases previstas são:

- **Fase 1 (Atual):** Definição do Escopo, Propósito e Seleção de Características ISO 25010.
- **Fase 2 (Próxima):** Elaboração das Questões GQM e seleção de Métricas Quantitativas.
- **Fase 3:** Coleta de dados (testes laboratoriais e auditorias automáticas).
- **Fase 4:** Interpretação dos resultados e proposição de melhorias de software.

Conforme o processo avançar, pretendemos expandir o escopo gradualmente:

<div align="center">
    <p><strong>Tabela 5 – Cobertura progressiva planejada</strong></p>
</div>

| Fase | Período | O que entra |
| :---: | :--- | :--- |
| Fase 1 | Maio/2026 | Confiabilidade e Manutenibilidade nos 5 objetos definidos acima. |
| Fase 2 | Junho/2026 | Eficiência de Desempenho no backend e no processamento de PDF. |
| Fase 3 | Julho/2026 | Módulo de IA (se estiver estável) e Adequação Funcional. |
| Fase 4 | Agosto/2026 | Segurança com ferramentas especializadas e reavaliação geral. |

<p align="center"><b>Fonte:</b> Autores, 2026.</p>

---

## 5. Limitações e Restrições

- **Ambiente:** A avaliação será feita em ambiente de desenvolvimento/staging, o que pode diferir do comportamento em produção (Vercel/Docker).

- **Dados:** Os dados de teste dependem do que já está populado no banco. Pode não representar bem o volume real de uso.

- **Ferramental:** Vamos usar ferramentas gratuitas (ESLint, SonarQube Community) e emuladores de navegador pra testes mobile, já que não temos dispositivos físicos.

- **Versão:** A análise será sobre a versão **2.3.0** do No Fluxo UnB. Versões futuras podem ter mudanças que invalidem parte dos resultados.

- **Acesso:** Não temos acesso a logs de produção nem métricas de uptime, então a avaliação de confiabilidade vai se basear no código e em testes simulados.

---

## Referências Bibliográficas

> ASSOCIAÇÃO BRASILEIRA DE NORMAS TÉCNICAS. *ABNT NBR ISO/IEC 25010:2011 — Modelos de qualidade de sistema e software*. Rio de Janeiro: ABNT, 2011.

> ASSOCIAÇÃO BRASILEIRA DE NORMAS TÉCNICAS. *ABNT NBR ISO/IEC 25040:2011 — Processo de avaliação*. Rio de Janeiro: ABNT, 2011.

> NO FLUXO UNB. **Repositório oficial do projeto**. Disponível em: <https://github.com/unb-mds/2025-1-NoFluxoUNB>. Acesso em: 13 maio 2026.

---

## Histórico de Versões

| Versão | Descrição | Autor(es) | Data de Produção | Revisor(es) | Data de Revisão |
| :----: | :--- | :--- | :---: | :--- | :---: |
| 1.0 | Criação do documento de escopo, profundidade e objetos de avaliação | `Ingrid Alves` | `13/05/2026` | | |
