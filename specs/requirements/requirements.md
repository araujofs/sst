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

- **Usuário do sistema**
  - **Gestor**
    - **Gerente** (*Pode fazer tudo que **Contador** faz*) 
    - **Administrador**
  - **Usuário comum**
    - **Cliente**
    - **Contador**
    - **Técnico de suporte**

# Requisitos funcionais (por módulo)
## Autenticação e Controle de Acesso

- **[RF-AUT-001]**: Como usuário do sistema, quero me autenticar com credenciais pré-definidas para ter acesso aos outros módulos do sistema.
- **[RF-AUT-002]**: Como usuário comum, quero solicitar a troca da minha senha a **Gestor** para garantir meu acesso ao sistema e a segurança da minha conta.
- **[RF-AUT-003]**: Como usuário do sistema, quero definir quanto tempo durará minha sessão (intervalo de opções configurado por **Gestor** -- ver [**RF-GES-00x**]) para ter mais segurança e evitar ficar logado indefinidamente.
- **[RF-AUT-004]**: Como usuário do sistema, quero ser notificado caso haja uma tentativa falha de entrar na minha conta para conseguir tomar as providências cabíveis.
- **[RF-AUT-005]**: Como gestor, quero ser notificado caso haja uma tentativa falha de entrar em qualquer conta cadastrada no sistema para conseguir tomar as providências cabíveis.
- **[RF-AUT-006]**: Como gestor, quero definir políticas de expiração e renovação de senhas para **Contador** e **Cliente** associados para garantir maior segurança com os acessos.
- **[RF-AUT-007]**: Como usuário do sistema, quero encerrar manualmente minha sessão atual para garantir que não hajam acessos indevidos na minha ausência.
- **[RF-AUT-008]**: Como administrador, quero que o sistema bloqueie o acesso de um usuário caso haja mais de 2 tentativas falhas de acesso a sua conta para garantir a segurança do sistema.
- **[RF-AUT-009]**: Como administrador, quero que o sistema permita o acesso às funcionalidades a **Usuário do sistema** de acordo com seu perfil e permissões para impedir acesso indevido à funcionalidades protegidas.
- **[RF-AUT-010]**: Como administrador, quero que o sistema impeça o acesso de um usuário em mais de um dispositivo ao mesmo tempo para garantir a segurança e evitar compartilhamento de credenciais. 

## Gestão de Usuários e Organizações


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