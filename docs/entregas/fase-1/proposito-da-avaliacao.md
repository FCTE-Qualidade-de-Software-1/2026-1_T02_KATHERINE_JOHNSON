# 1. Propósito da Avaliação

Conforme sugere o Processo de Avaliação de Produto, a Fase 1 visa, dentre outros levantamentos, definir o propósito da avaliação. Esta seção tem como função esclarecer o contexto, a motivação e os objetivos específicos para a realização da avaliação do produto em questão, o sistema **No Fluxo UnB**. Diante disso, tomando como base a norma SQuaRE, neste processo serão avaliadas duas características de qualidade de produto: Manutenibilidade e Confiabilidade. A seguir, serão detalhados os aspectos relacionados a cada uma dessas características, bem como a forma como os resultados da avaliação serão utilizados para aprimorar o produto e orientar futuras decisões de desenvolvimento.

## 1.1 Contexto e Motivação

Este processo se encaixa no contexto acadêmico da disciplina de Qualidade de Software, ministrada no curso de Engenharia de Software da Universidade de Brasília (UnB). Diante dos novos conceitos abordados na disciplina, foi requisitado que fosse realizada uma avaliação de produto, a fim de aplicar na prática os tópicos levantados nesta área da engenharia. 

A motivação da avaliação do software se dá pelo crescente uso do sistema nos últimos semestres letivos, visto que a aplicação trouxe benefícios consideráveis para a comunidade de estudantes da UnB. Diante disso, um processo de avaliação rigoroso e sistemático é capaz de levantar sugestões de melhorias, bem como identificar pontos fortes do sistema, contribuindo para a evolução contínua do **No Fluxo UnB** e para a satisfação dos usuários.

## 1.2 Declaração do Propósito

Este propósito reforça o objetivo de realizar uma análise técnica e sistemática da qualidade do **No Fluxo UnB**, identificando seus pontos fortes e suas principais fragilidades em ambiente de uso. Como o sistema auxilia diretamente no planejamento acadêmico dos estudantes, incluindo funcionalidades como upload de histórico, visualização de pré-requisitos e cálculo de carga horária, a avaliação busca verificar o nível de maturidade do produto diante de sua crescente utilização pela comunidade universitária.

O principal objetivo é fornecer um diagnóstico fundamentado que auxilie a equipe responsável pelo desenvolvimento e manutenção do projeto na identificação de melhorias e na definição de estratégias de evolução. Dessa forma, a análise concentra-se em garantir que o software apresente estabilidade e preserve corretamente o progresso acadêmico do estudante (Confiabilidade), além de possíveis atualizações constantes afim de manter a atualização e correção de bugs (Manutenibilidade).

## 1.3 Utilização dos Resultados da Avaliação

Os resultados obtidos por meio desta avaliação têm como finalidade orientar os esforços técnicos e gerenciais relacionados ao **No Fluxo UnB**. Para assegurar que a análise permaneça alinhada à realidade do produto, a utilização dos resultados considera o seguinte cenário de aplicação:

**Cenário de Aplicação:**  
*Durante as semanas que antecedem o período de matrícula no SIGAA, ocorre um pico de acessos simultâneos no No Fluxo UnB. Estudantes de diversos cursos acessam a plataforma para fazer upload de seus históricos em PDF, visualizar a cadeia de pré e co-requisitos e testar simulações de grade. Qualquer instabilidade do servidor, falha de salvamento do fluxo em formato de texto/json ou lentidão excessiva no banco de dados compromete o planejamento acadêmico, gerando frustração direta no usuário.*

| Característica | Análise a ser conduzida | Decisão a ser apoiada | Quem tomará a decisão? |
| :--- | :--- | :--- | :--- |
| **Confiabilidade** | Testes de carga e análise de tratamento de exceções no backend (Java) durante requisições pesadas (ex: leitura de histórico e mesclagem de fluxogramas de cursos diferentes). | Priorização do backlog técnico para correção de gargalos de infraestrutura e implementação de tratativas de erro que evitem a queda do sistema durante os picos de acesso. | Desenvolvedores e Mantenedores do NoFluxo UnB |
| **Manutenibilidade** | Análise estática da base de código (frontend em React e backend em Java) utilizando ferramentas automatizadas e métricas da ISO/IEC 25023 para identificar dívida técnica e nível de complexidade. | Determinar quais módulos são sujeitas a refatoração e atualização de documentação para viabilizar a entrada de novos alunos contribuidores, reduzindo o esforço e o custo de evolução do sistema. | Desenvolvedores e Mantenedores do NoFluxo UnB |



# 1.4 Seleção e Priorização das Características de Qualidade

Com o objetivo de definir o escopo da avaliação do No Fluxo UnB, foi realizada uma análise de todas as oito características de qualidade propostas pelo modelo ISO/IEC 25010 (SQuaRE). Em seguida, a equipe realizou uma votação interna para debater as principais características e priorizar os esforços da avaliação.

Para isso, utilizou-se o método de priorização MoSCoW, conforme exigido pelo Processo de Avaliação da disciplina. A equipe decidiu elencar as três características principais para compor o escopo (Confiabilidade, Manutenibilidade e Segurança). As demais características foram categorizadas como *Could* ou *Won't*, uma decisão justificada para evitar a diluição do esforço técnico em pontos menos críticos no momento atual da aplicação.

A classificação apresentada a seguir considera o contexto de utilização do sistema durante os períodos de matrícula, bem como as particularidades relacionadas à sua manutenção acadêmica:

| Característica de Qualidade (ISO 25010) | Resultado MoSCoW | Justificativa |
| :--- | :---: | :--- |
| **Confiabilidade** | Must | **Foco principal.** Falhas críticas, travamentos ou perda de dados do histórico processado frustram o planejamento do aluno e quebram a confiança no sistema durante o período de matrículas. |
| **Manutenibilidade** | Must | **Foco principal.** O projeto é rotativo entre alunos e apresenta indícios de códigos de infraestrutura gerados por IA. Garantir a legibilidade e evitar dívidas técnicas é vital para a sobrevivência do produto. |
| Segurança | Should | **Foco secundário.** O sistema lida com o planejamento de disciplinas e upload de arquivos. Como não possui processamento de alto risco, a análise de vulnerabilidades atua como apoio à estabilidade geral do sistema. |
| Adequação Funcional | Could | A aplicação já atende adequadamente às suas funcionalidades principais, como leitura de histórico e montagem de grade. Assim, o foco atual está mais relacionado à estabilidade do sistema do que à validação de requisitos. |
| Eficiência de Desempenho | Could | Importante para manter um tempo de resposta adequado no processamento de históricos e pré-requisitos, embora tenha menor prioridade em relação à prevenção de falhas estruturais do sistema. |
| Compatibilidade | Won't | Fora do escopo. O sistema é uma aplicação web autossuficiente e não tem como foco atual a troca contínua de informações ou a interoperabilidade com outros softwares de terceiros. |
| Portabilidade | Won't | Fora do escopo. O No Fluxo UnB já roda nos navegadores web previstos; a transferência ou adaptação do software para novos hardwares ou sistemas operacionais não é uma prioridade. |
| Usabilidade | Não se enquadra / Won't | Característica excluída do escopo de avaliação pelas regras iniciais do projeto da disciplina. |

## 1.5 Síntese do Propósito de Avaliação

Em síntese, o objeto de estudo deste planejamento é o sistema **No Fluxo UnB**, considerando sua **versão atual** disponibilizada no repositório oficial da comunidade universitária. A plataforma pertence ao **contexto acadêmico e educacional**, funcionando como uma aplicação web voltada ao apoio no planejamento de disciplinas e na organização da grade curricular dos estudantes da Universidade de Brasília.

Quanto aos objetivos desta avaliação, o propósito central é produzir um **diagnóstico técnico** sobre a qualidade do software em seu estado atual, **identificando aspectos que podem ser aprimorados**. Dessa forma, os resultados obtidos poderão auxiliar a equipe responsável pelo projeto na evolução contínua do sistema e na **adequação do produto às boas práticas de Engenharia de Software**.

## Referências Bibliográficas

1. NOFLUXO UNB. *Documentação oficial do projeto*. Disponível em: <https://mdsreq-fga-unb.github.io/2023.1-UnBnoFluxo/>. Acesso em: 12 maio 2026.

2. ASSOCIAÇÃO BRASILEIRA DE NORMAS TÉCNICAS. *ABNT NBR ISO/IEC 25010:2011: Engenharia de software e sistemas — Requisitos e avaliação da qualidade de produto de software (SQuaRE) — Modelos de qualidade de sistema e software*. Rio de Janeiro: ABNT, 2011.

3. UNBNOFLUXO. *Visão geral do produto e backlog*. Plataforma web interativa para estudantes da Universidade de Brasília. Disponível em: <https://github.com/unb-mds/2025-1-NoFluxoUNB>. Acesso em: 12 maio 2026.

---

## Histórico de Versões

| Versão | Descrição | Autor(es) | Data de Produção |
| :---: | :--- | :--- | :---: |
| 1.0 | Elaboração do Propósito da Avaliação, Contexto e Motivação. | `Caio Lamego` | `12/05/2026` |
| 1.1 | Detalhamento da Declaração do Propósito e Utilização dos Resultados. | `Caio Lamego` | `14/05/2026` |
