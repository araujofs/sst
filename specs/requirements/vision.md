# Visão do produto

## Sistema de simulação tributária (SST)

<small>Versão 1.0</small>

<br />

## Histórico de revisões
| Data       | Versão | Descrição                      | Autor            |
|------------|--------|--------------------------------|------------------|
| 15/10/2025 | 1.0    | Versão inicial do documento     | Arthur Araújo |

---

## Sumário
- [Visão do produto](#visão-do-produto)
  - [Sistema de simulação tributária (SST)](#sistema-de-simulação-tributária-sst)
  - [Histórico de revisões](#histórico-de-revisões)
  - [Sumário](#sumário)
- [Introdução](#introdução)
  - [Propósito](#propósito)
  - [Definições e abreviações](#definições-e-abreviações)
    - [Abreviações](#abreviações)
    - [Definições](#definições)
  - [Escopo do produto](#escopo-do-produto)
- [Posicionamento](#posicionamento)
  - [Oportunidade de negócios](#oportunidade-de-negócios)
  - [Descrição dos benefícios para os clientes e os problemas resolvidos](#descrição-dos-benefícios-para-os-clientes-e-os-problemas-resolvidos)
- [Descrição dos stakeholders e dos usuários](#descrição-dos-stakeholders-e-dos-usuários)
  - [Stakeholders](#stakeholders)

# Introdução

Esse documento visa (DVP - Documento de Visão do Produto) apresentar a visão geral do sistema de simulação tributária, detalhando o propósito, escopo, stakeholders, ambiente de uso e características principais do produto.o

## Propósito

O propósito deste documento é fornecer uma visão clara e concisa do sistema de simulação tributária, que auxiliará empresas e profissionais a calcular e simular impostos de maneira eficiente e precisa. 

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

## Descrição dos benefícios para os clientes e os problemas resolvidos
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
| Clientes | Empresas e profissionais da contabilidade que vão utilizar o sistema para prestar serviços relacionados à simulação e cálculo de tributos. | Usuários finais do sistema 
| Gerente de projeto | Profissional responsável por coordenar as equipes de desenvolvimento, infraestrutura e suporte, garantindo que o projeto seja concluído dentro do prazo e orçamento estabelecidos. | Gerenciamento do projeto |
| Equipe de infraestrutura | Profissionais responsáveis por garantir que o sistema esteja hospedado, seguro e disponível para os usuários. | Administradores de sistemas, especialistas em segurança |
| Equipe de desenvolvimento | Profissionais responsáveis por desenvolver e fazer a manutenção do sistema | Engenheiros de software, designers |
| Equipe de suporte | Profissionais responsáveis por oferecer assistência técnica aos usuários do sistema | Suporte técnico |
| Equipe de marketing e vendas | Profissionais responsáveis por promover e vender o sistema | Marketing, vendas |

