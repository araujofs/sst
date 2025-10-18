# Visão do produto

## Sistema de simulação tributária (SST)

<small>Versão 0.4</small>

---

## Histórico de revisões
| Data       | Versão | Descrição                      | Autor            |
|------------|--------|--------------------------------|------------------|
| 15/10/2025 | 0.1    | Versão inicial do documento                                                      | Arthur Araújo |
| 16/10/2025 | 0.2    | Adicionado novos stakeholders e Descrição de ambiente de uso                     | Davi Leite   |
| 17/10/2025 | 0.3    | Inclusão do diagrama do sistema e características principais                     | Gabriel Carvalho |
| 18/10/2025 | 0.4    | Adicionado tabela de principais necessidades do sistema e de usuários e atores.  | Davi Leite   |
---

## Sumário
- [Introdução](#introdução)
  - [Propósito](#propósito)
  - [Definições e abreviações](#definições-e-abreviações)
    - [Abreviações](#abreviações)
    - [Definições](#definições)
  - [Escopo do produto](#escopo-do-produto)
- [Posicionamento](#posicionamento)
  - [Oportunidade de negócios](#oportunidade-de-negócios)
  - [Descrição dos benefícios para os clientes e dos problemas resolvidos](#descrição-dos-benefícios-para-os-clientes-e-dos-problemas-resolvidos)
- [Descrição dos stakeholders e dos usuários](#descrição-dos-stakeholders-e-dos-usuários)
  - [Stakeholders](#stakeholders)
  - [Usuários e atores](#usuários-e-atores)
- [Descrição do ambiente de uso](#descrição-do-ambiente-de-uso)
  - [Ambiente de uso](#ambiente-de-uso)
  - [Necessidades principais quanto ao ambiente](#necessidades-principais-do-ambiente)
- [Visão geral do produto](#visão-geral)
  - [Visão geral](#visão-geral)
  - [Custo e venda](#custo-e-venda)
  - [Licenciamento e instalação](#licenciamento-e-instalação)
  - [Características e funcionalidades de alto nível](#características-e-funcionalidades-de-alto-nível)
  - [Restrições](#restrições) 

---

# Introdução

Esse documento de visão do produto (DVP) visa apresentar a visão geral do sistema de simulação tributária, detalhando o propósito, escopo, stakeholders, ambiente de uso e características principais do produto.

## Propósito

O propósito do DVP é fornecer uma visão clara e concisa do sistema de simulação tributária, que auxiliará empresas e profissionais a calcular e simular impostos de maneira eficiente e precisa. 

O documento destina-se a desenvolvedores, gerentes de projeto, stakeholders e qualquer pessoa envolvida no desenvolvimento e implementação do sistema, garantindo que todos tenham uma compreensão comum dos objetivos e funcionalidades do produto e sejam alinhados quanto às expectativas.

## Definições e abreviações
### Abreviações
| Abreviação | Descrição                                                                  |
| ---------- | -------------------------------------------------------------------------- |
| DVP        | Documento de Visão do Produto                                              |
| API        | Application Programming Interface (Interface de Programação de Aplicações) |
| UI         | User Interface (Interface do Usuário)                                      |
| UX         | User Experience (Experiência do Usuário)                                   |
| SST        | Sistema de Simulação Tributária                                            |
| MVP        | Minimum Viable Product (Produto Mínimo Viável)                             |

### Definições
| Termo            | Descrição                                                                                     |
| ---------------- | --------------------------------------------------------------------------------------------  |
| Simulação        | Processo de modelar o comportamento de um sistema real através de um modelo computacional.    |
| Alíquota         | Percentual aplicado sobre uma base de cálculo para determinar o valor do imposto devido.      |
| Base de cálculo  | Valor sobre o qual a alíquota é aplicada para calcular o imposto.                             |
| Tributação       | Sistema de arrecadação de impostos por parte do governo.                                      |
| Imposto          | Contribuição financeira obrigatória imposta pelo governo sobre renda, propriedade ou consumo. |
| Compliance       | Conformidade com leis, regulamentos e normas aplicáveis.                                      |
| Relatório        | Documento que apresenta informações detalhadas sobre um determinado assunto.                  |
| Simples nacional | Regime tributário simplificado para micro e pequenas empresas no Brasil.                      |
| Lucro presumido  | Regime tributário baseado em uma presunção de lucro para cálculo de impostos.                 |
| Lucro real       | Regime tributário onde os impostos são calculados com base no lucro efetivo da empresa.       |
| Web              | Tecnologia que permite o acesso a informações e serviços através da internet.                 |

## Escopo do produto 

O **SST** é um sistema web que tem por objetivo principal facilitar os processos de simulação e cálculos de tributação para profissionais da contabilidade. Será utilizado por contadores, consultores fiscais e gestores financeiros que necessitam de uma ferramenta eficiente para calcular impostos, gerar relatórios e garantir conformidade com as regulamentações fiscais vigentes.

# Posicionamento
## Oportunidade de negócios

Algumas oportunidades de negócios do SST são as seguintes:

- **Uso do sistema por assinatura**: Permite que o sistema seja usado por diversos clientes diferentes da área de contabilidade, mediante pagamento mensal, anual ou qualquer outro pacote disponível, oferecendo também planos diferentes de funcionalidades e preços, de maneira que seja acessível. 
- **Venda da licença do sistema junto com serviços de suporte e manutenção**: Oferece o sistema para empresas da área de contabilidade com pagamento único pela licença para o uso, mas pagamento contínuo por serviços relacionados a suporte e manutenção do mesmo (sem entrega do código-fonte).
- **Criação de ecossistema auxiliar**: Disponibilizar aos clientes um ecossistema de serviços e produtos relacionados ao sistema, como outras ferramentas de gestão, consultoria, etc. de maneira que o usuário do sistema não precise recorrer a ferramentas completamente diferentes da que está habituado a usar.

## Descrição dos benefícios para os clientes e dos problemas resolvidos
| Benefícios                                                        | Problemas resolvidos                           | Afetados                                              |
| ----------------------------------------------------------------- | ---------------------------------------------- | ----------------------------------------------------- |
| Cálculo automático de impostos                                    | Erros manuais no cálculo de impostos           | Contadores, consultores fiscais, gestores financeiros |
| Simulação de diferentes cenários tributários                      | Dificuldade em prever impactos fiscais         | Contadores, consultores fiscais, gestores financeiros |
| Geração de relatórios detalhados                                  | Falta de documentação adequada para auditorias | Contadores, gestores financeiros                      |
| Notificação automática sobre mudanças na legislação tributária    | Desatualização sobre leis fiscais              | Contadores, consultores fiscais                       |
| Possibilidade de atualização manual de alíquotas e regras fiscais | Desatualização de alíquotas e regras fiscais   | Contadores, consultores fiscais                       |

# Descrição dos stakeholders e dos usuários
## Stakeholders

| Stakeholder | Descrição | Papel |
| ----------- | --------- | ----- |
| Clientes | Empresas e profissionais da contabilidade que vão utilizar o sistema para prestar serviços relacionados à simulação e cálculo de tributos. | Usuários finais do sistema |
| Especialistas em legislação tributária | Profissionais com profundo conhecimento das leis fiscais e tributárias, responsáveis por garantir que o sistema esteja atualizado e em conformidade com as regulamentações vigentes. | Consultores fiscais, advogados especializados em direito tributário |
| Equipe de Banco de dados | Profissionais responsáveis por projetar, implementar e manter o banco de dados do sistema, garantindo a integridade, segurança e desempenho dos dados. | Administradores de banco de dados, engenheiros de dados |
| Gerente de projeto | Profissional responsável por coordenar as equipes de desenvolvimento, infraestrutura e suporte, garantindo que o projeto seja concluído dentro do prazo e orçamento estabelecidos. | Gerenciamento do projeto |
| Equipe de infraestrutura | Profissionais responsáveis por garantir que o sistema esteja hospedado, seguro e disponível para os usuários. | Administradores de sistemas, especialistas em segurança |
| Equipe de desenvolvimento | Profissionais responsáveis por desenvolver e fazer a manutenção do sistema | Engenheiros de software, designers |
| Equipe de suporte | Profissionais responsáveis por oferecer assistência técnica aos usuários do sistema | Suporte técnico |
| Equipe de marketing e vendas | Profissionais responsáveis por promover e vender o sistema | Marketing, vendas |

## Usuários e atores

| Usuário/Atores         | Descrição                                                                 | Responsabilidades                                              | Stakeholders Relacionados                  |
|------------------------|---------------------------------------------------------------------------|---------------------------------------------------------------|--------------------------------------------|
| Contadores             | Profissionais de contabilidade que utilizam o sistema para cálculos e simulações tributárias | Realizar simulações, calcular impostos, gerar relatórios      | Clientes                                   |
| Consultores fiscais    | Especialistas em legislação tributária que apoiam empresas e clientes      | Analisar cenários fiscais, propor estratégias tributárias      | Especialistas em legislação tributária      |
| Gestores financeiros   | Responsáveis pelo planejamento financeiro das empresas                     | Avaliar impactos fiscais, tomar decisões estratégicas          | Clientes                                   |
| Administradores do sistema | Usuários com permissões para gerenciar configurações e usuários         | Gerenciar acessos, configurar regras e parâmetros do sistema   | Equipe de desenvolvimento, suporte         |
| Suporte técnico        | Profissionais que auxiliam usuários em dúvidas e problemas técnicos        | Prestar suporte, solucionar problemas e registrar feedback     | Equipe de suporte                          |

# Descrição do ambiente de uso

## Ambiente de uso

### TO-DO



### Necessidades principais do ambiente

| Necessidade    | Prioridade | Interesse dos Clientes | Solução Atual | Soluções Propostas |
|----------------|------------|-----------------------|---------------|--------------------|
| Qualidade      | Alta       | Garantia de cálculos precisos e confiáveis | Processos manuais ou sistemas genéricos | Implementação de validação automática e auditoria de dados |
| Desempenho     | Alta       | Rapidez nas simulações e geração de relatórios | Sistemas lentos ou sobrecarregados | Otimização do backend e uso de servidores escaláveis |
| Segurança      | Alta       | Proteção de dados fiscais e pessoais | Armazenamento local sem criptografia | Criptografia de dados, autenticação forte e conformidade LGPD |
| Usabilidade    | Média      | Facilidade de uso para profissionais não técnicos | Interfaces complexas ou pouco intuitivas | Interface web responsiva e intuitiva, treinamento e suporte |
| Confidencialidade | Alta    | Garantia de privacidade das informações | Compartilhamento informal de dados | Controle de acesso, registro de operações e políticas de privacidade |

# Visão geral do produto
## Visão geral

O Sistema de Simulação Tributária SST é uma aplicação web voltada para facilitar cálculo e a simulação de impostos, permitindo que profissionais da área da contabilidade e financeira realizem análises fiscais com maior precisão agilidade e confiabilidade. O sistema irá possibilitar a simulação de diferentes  tipos de cenários tributários, geração de relatórios detalhados e atualização manual das regras fiscais conforme as legislações, o qual vai garantir a conformidade com as normas legais vigentes.

Por ser um sistema web, o SST funciona totalmente online, utilizando uma infraestrutura de TI composta por servidores, banco de dados e mecanismos de segurança. Ele não exige nenhum hardware específico, sendo acessível em navegadores modernos, tanto em computadores quanto em tablets e smartphones.

Dessa forma, os usuários que são os contadores, consultores fiscais e gestores financeiros, eles poderão acessar o sistema através de computadores, tablets e smartphones, o que permite o uso tanto em escritórios quanto remotamente.

A comunicação entre os dispositivos que os usuários irão utilizar e o servidor ocorre por meio de protocolos de comunicação HTTP e HTTPS, o qual vai garantir troca segura de informações, especialmente durante a realização de cálculos e simulações.

Além disso, o  nosso sistema SST pode se integrar a serviços externos, como APIs de legislação e bancos de dados fiscais, possibilitando a atualização automática de alíquotas e normas tributárias.

A estrutura operacional do sistema é apresentada na Figura 1.


![Arquitetura geral do Sistema sst](../../assets/image/image.png)

**Figura 1** - Arquitetura geral do sistema SST



# Características e funcionalidades de alto nível

Esta seção define e descreve as características do SST. Trata-se dos requisitos de alto nível do sistema que são necessários para propiciar benefícios aos usuários.

1. O sistema deve permitir o cálculo automático de impostos, considerando diferentes tributos e parâmetros definidos pelo usuário
1. O sistema deve possibilitar a simulação de diversos tipos de cenários tributários, permitindo ao usuário comparar resultados e tomar decisões estratégicas com base em dados reais
1. O sistema deve gerar relatórios detalhados com informações sobre tributos, valores calculados, simulações feitas e resultados de comparação
1. O sistema deve emitir notificações sobre mudanças na legislação, alertando o usuário sobre atualizações que possam impactar seus cálculos ou planejamentos fiscais
1. O sistema deve permitir a atualização manual de alíquotas e regras fiscais, para que o usuário possa ajustar o sistema conforme novas normas legais
1. O sistema deve garantir conformidade com a Lei Geral de Proteção de Dados (LGPD), criptografia com dados sensíveis, assegurando a privacidade e a proteção das informações inseridas pelos usuários
1. O sistema deve apresentar uma interface simples e intuitiva, facilitando o uso por contadores, consultores e gestores, mesmo sem conhecimentos técnicos avançados
1. O sistema deve ter desempenho estável e responsivo, assegurando rapidez nos cálculos e simulações, sem falhas ou interrupções
1. O sistema deve ser escalável, permitindo integração com serviços externos, como APIs fiscais, e expansão de suas funcionalidades conforme as necessidades do usuário

## Custo e venda
### TO-DO

## Licenciamento e instalação
### TO-DO

## Restrições do ambiente

- **Segurança**: Dados sensíveis exigem criptografia e conformidade com LGPD
- **Disponibilidade**: Sistema deve estar disponível 99% do tempo durante horário comercial
- **Backup**: Dados devem ser salvos automaticamente para evitar perda de informações
- **Auditoria**: Todas as operações devem ser registradas para fins de compliance
- **Acessibilidade**: Interface deve seguir padrões de acessibilidade web (WCAG 2.1)

---

Data: 18 de outubro de 2025

**Validado por:**

<address>
<a href="mailto:davi@dag.com">Davi Leite</a> | Engenheiro de Software<br>
davi@dag.com<br>
dag.com<br>
Box 762, João Pessoa<br>
BRA
</address>

--- 

Criado em outubro de 2025 por __Arthur Araújo__