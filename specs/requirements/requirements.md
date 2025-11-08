# Requisitos de Software

## Sistema de simulação tributária (SST)

<small>Versão 1.0</small>

---

## Histórico de revisões

| Data | Versão | Descrição | Autor |
| ---- | ------ | --------- | ----- |
| 07/11/2025 | 1.0 | Criação do documento | Arthur Araújo |
| 08/11/2025 | 1.1 | Adição dos requisitos funcionais de Calculo e Simulação | Davi Leite |

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
- **[RF-CAL-001]**: Como Contador ou Gerente, quero selecionar o setor econômico da empresa (comércio, indústria, serviços, etc.) antes de iniciar uma simulação para que os cálculos tributários sejam realizados de acordo com as regras específicas do setor.
- **[RF-CAL-002]**: Como Contador ou Gerente, quero inserir os dados financeiros da empresa (receitas brutas, despesas operacionais, custos de mercadorias, folha de pagamento, investimentos, etc.) de forma estruturada para que o sistema tenha as informações necessárias para realizar cálculos precisos.
- **[RF-CAL-003]**: Como Contador ou Gerente, quero selecionar o regime tributário aplicável (Simples Nacional, Lucro Presumido, Lucro Real) para que o sistema aplique as regras fiscais corretas na simulação.
- **[RF-CAL-004]**: Como Contador ou Gerente, quero que o sistema calcule automaticamente todos os tributos devidos (IRPJ, CSLL, PIS, COFINS, IPI, ICMS, ISS, etc.) com base nos dados financeiros e no regime tributário selecionado para obter uma simulação precisa e completa.
- **[RF-CAL-005]**: Como Contador ou Gerente, quero visualizar o detalhamento de cada tributo calculado (base de cálculo, alíquota aplicada, deduções, valor final) para compreender como os valores foram obtidos e validar os cálculos.
- **[RF-CAL-006]**: Como Contador ou Gerente, quero criar e salvar múltiplos cenários de simulação com diferentes premissas (variação de receita, diferentes regimes tributários, etc.) para comparar e identificar a melhor estratégia fiscal.
- **[RF-CAL-007]**: Como Contador ou Gerente, quero comparar lado a lado os resultados de diferentes cenários tributários (carga tributária total, tributos por tipo, impacto no resultado líquido) para auxiliar na tomada de decisão estratégica.
- **[RF-CAL-008]**: Como Contador ou Gerente, quero que o sistema indique qual regime tributário é mais vantajoso com base nos dados financeiros inseridos para otimizar o planejamento fiscal do cliente.
- **[RF-CAL-009]**: Como Contador ou Gerente, quero simular o impacto de mudanças em variáveis específicas (aumento de receita, redução de custos, novos investimentos) sobre a carga tributária para realizar análises de sensibilidade.
- **[RF-CAL-010]**: Como Contador ou Gerente, quero que o sistema valide os dados inseridos, identificando inconsistências ou valores atípicos, para evitar erros nos cálculos e garantir a qualidade das simulações.
- **[RF-CAL-011]**: Como Contador ou Gerente, quero salvar simulações realizadas com histórico de alterações para poder recuperar e revisar análises anteriores quando necessário.
- **[RF-CAL-012]**: Como Contador ou Gerente, quero exportar os resultados das simulações em diferentes formatos (PDF, Excel, CSV) para compartilhar com clientes e stakeholders.
- **[RF-CAL-013]**: Como Contador, quero que o sistema calcule automaticamente as obrigações acessórias relacionadas aos tributos (DCTF, EFD-Contribuições, SPED Fiscal) para garantir o compliance completo.
- **[RF-CAL-014]**: Como Gerente, quero visualizar um resumo executivo da simulação tributária com indicadores-chave (carga tributária total, economia potencial, regime recomendado) para apresentar rapidamente aos stakeholders.
- **[RF-CAL-015]**: Como Contador ou Gerente, quero que o sistema permita ajustes manuais em alíquotas e parâmetros específicos (com justificativa obrigatória) para simular situações especiais ou incentivos fiscais regionais.


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