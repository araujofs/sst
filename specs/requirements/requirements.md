# Requisitos de Software

## Sistema de simulação tributária (SST)

<small>Versão 1.0</small>

---

## Histórico de revisões

| Data | Versão | Descrição | Autor |
| ---- | ------ | --------- | ----- |
| 07/11/2025 | 1.0 | Criação do documento | Arthur Araújo |

---

## Sumário


---

# Introdução

Este documento tem como objetivo apresentar os requisitos de software do produto **Sistema de simulação tributária (SST)**

## Definições, acrônimos e abreviações

Visando o melhor entendimento do documento faz-se necessário definir alguns termos, abreviações e acrônimos, o que será feito abaixo.

- Identificação dos requisitos: a referência a requisitos de software é feita através do identificador de requisitos seguindo a convenção:

  `[IDENTIFICADOR DO TIPO E DO MÓDULO DO REQUISITOidentificador do requisito]`

  O identificador de tipo segue o padrão abaixo;
  - RF -> Requisito funcional
  - RNF -> Requisito não-funcional
  - NR -> Não requisito

  O identificador do requisito será uma sequência de números. Esse número deve ser único para todo o conjunto de tipos.

  **Exemplo**: [RFAUT001], [RF1234], [RNF1234], [NR1212]

- Atributos dos requisitos:
  - **Requisitos vinculados**: fornece uma lista dos requisitos que mantém rastreabilidade
  - **Prioridade**: Essencial, Importante, Desejável
  - **Complexidade**: Complexa, Alta, Média ou Baixa
  - **Risco**: Alto, Médio ou Baixo

# Usuários identificados

- **Usuário**
  - **Gestor**
    - **Gerente** (*Pode fazer tudo que **Contador** faz e gere apenas sua empresa*) 
    - **Administrador** (*Gere de maneira mais geral, pois podem haver várias empresas utilizando o sistema isoladamente*)
  - **Usuário comum**
    - **Associado**
      - **Cliente** (*Cliente da empresa contratante do sistema*)
      - **Contador**
    - **Técnico de suporte**

# Requisitos funcionais (por módulo)
## Autenticação e Controle de Acesso

- **[RF-AUT-001]**: Como usuário do sistema, quero me autenticar com credenciais pré-definidas para ter acesso aos outros módulos do sistema.
- **[RF-AUT-002]**: Como usuário do sistema, quero definir quanto tempo durará minha sessão (intervalo de opções configurado por **Gestor**, ver [**RF-GES-006**]) para ter mais segurança e evitar ficar logado indefinidamente.
- **[RF-AUT-003]**: Como usuário do sistema, quero ser notificado caso haja uma tentativa falha de entrar na minha conta para conseguir tomar as providências cabíveis.
- **[RF-AUT-004]**: Como gestor, quero ser notificado caso haja uma tentativa falha de entrar em qualquer conta para conseguir tomar as providências cabíveis.
- **[RF-AUT-005]**: Como administrador, quero definir políticas de expiração e renovação de senhas para **Usuário** para garantir maior segurança com os acessos.
- **[RF-AUT-006]**: Como administrador, quero encerrar a sessão de um **Usuário** para evitar acessos indesejados.
- **[RF-AUT-007]**: Como gerente, quero encerrar a sessão de um **Associado** para evitar acessos indesejados.
- **[RF-AUT-008]**: Como usuário do sistema, quero encerrar manualmente minha sessão atual para garantir que não hajam acessos indevidos na minha ausência.
- **[RF-AUT-009]**: Como administrador, quero que o sistema bloqueie o acesso de um usuário caso haja mais de 2 tentativas falhas de acesso a sua conta para garantir a segurança do sistema.
- **[RF-AUT-010]**: Como administrador, quero que o sistema permita o acesso às funcionalidades a **Usuário** de acordo com seu perfil e permissões para impedir acesso indevido à funcionalidades protegidas.
- **[RF-AUT-011]**: Como administrador, quero que o sistema impeça o acesso de um usuário em mais de um dispositivo ao mesmo tempo para garantir a segurança e evitar compartilhamento de credenciais. 

## Gestão de Usuários e Organizações
- **[RF-GES-001]**: Como administrador, quero gerenciar (criar, atualizar, desativar, excluir, mudar permissões) **Usuário** para garantir acesso apenas a pessoas autorizadas.
- **[RF-GES-002]**: Como gerente, quero gerenciar (criar, atualizar, desativar, mudar permissões) **Associado** da minha empresa para garantir acesso apenas de pessoas autorizadas e a funcionalidades específicas.
- **[RF-GES-003]**: Como gerente, quero solicitar a **Administrador** que crie mais gerente(s) na minha empresa para dividir as tarefas de gestão.
- **[RF-GES-004]**: Como gerente, quero autorizar ou negar atualizações no perfil de **Associado** para garantir que não hajam mudanças indesejadas.
- **[RF-GES-005]**: Como associado, quero gerenciar meu perfil (foto, nome, e-mail associado, senha) no sistema com autorização do **Gerente** para manter as informações atualizadas e minhas credenciais seguras.
- **[RF-GES-006]**: Como administrador, quero autorizar ou negar atualizações no perfil de **Técnico de suporte** para garantir que não hajam mudanças indesejadas.
- **[RF-GES-007]**: Como técnico de suporte, quero gerenciar meu perfil (foto, nome, e-mail associado, senha) no sistema com autorização do **Administrador** para manter as informações atualizadas e minhas credenciais seguras.
- **[RF-GES-008]**: Como gestor, quero definir o intervalo da duração máxima da sessão de **Associado** para evitar possíveis acessos maliciosos em máquinas desprotegidas.
- **[RF-GES-009]**: Como gerente, quero visualizar **Associado** ativo no momento para monitorar possíveis comportamentos suspeitos.
- **[RF-GES-010]**: Como administrador, quero ser notificado quando **Gestor** trocar de senha para monitorar comportamento suspeito.
- **[RF-GES-011]**: Como gestor, quero trocar minha senha para garantir meu acesso ao sistema e a segurança da minha conta.
- **[RF-GES-012]**: Como técnico de suporte, quero visualizar temporariamente informações de **Associado** e **Gerente** com autorização de **Gestor** para diagnostica eventuais problemas.

## Cálculo e Simulação Tributária


## Atualização de Legislação e Alíquotas


## Relatórios e Dashboards


## Notificações e Alertas Legislativos


## Administração, Segurança e Infraestrutura do Sistema


## Integração com Sistemas Externos (APIs)


# Requisitos não-funcionais
## Disponibilidade
...

## Privacidade e segurança
...

## Usabilidade
...

## Suportabilidade
...

## Interoperabilidade
...

## Manutenibilidade
...

## Desempenho
...

## Implementação
...

## Implantação
...