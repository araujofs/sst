# Requisitos de Software

## Sistema de simulação tributária (SST)

<small>Versão 1.0</small>

---

## Histórico de revisões

| Data | Versão | Descrição | Autor |
| ---- | ------ | --------- | ----- |
| 07/11/2025 | 1.0 | Criação do documento | Arthur Araújo |
| 08/11/2025 | 1.1 | Adição dos requisitos funcionais de Calculo e Simulação | Davi Leite |
| 09/11/2025 | 1.2 | Adição dos requisitos funcionais de Relatorio e Notificações | Gabriel Pereira |
| 09/11/2025 | 1.3 | Adição dos requisitos funcionais de Atualização de Legislação e Aliquotas | Davi Leite |
| 10/11/2025 | 1.4 | Adição dos requisitos não-funcionais de Usabilidade e Suportabilidade | Davi Leite | 
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
- **[RF-GES-009]**: Como gerente, quero visualizar **Associados** ativos no momento para monitorar possíveis comportamentos suspeitos.
- **[RF-GES-011]**: Como gestor, quero trocar minha senha para garantir meu acesso ao sistema e a segurança da minha conta.
- **[RF-GES-013]**: Como administrador, quero visualizar **Usuários** ativos no momento para monitorar possíveis comportamentos suspeitos.

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
- **[RF-LEG-001]**: Como administrador, quero que o sistema atualize automaticamente as alíquotas e regras tributárias com base em fontes oficiais (Receita Federal, Secretarias da Fazenda) para garantir que as simulações estejam sempre alinhadas com a legislação vigente.
- **[RF-LEG-002]**: Como contador ou gerente, quero ser notificado sobre atualizações na legislação tributária que possam impactar as simulações realizadas para garantir que estou sempre informado sobre mudanças relevantes.
- **[RF-LEG-003]**: Como administrador, quero manter um histórico de todas as atualizações legislativas aplicadas no sistema para referência futura e auditoria.
- **[RF-LEG-004]**: Como administrador, quero validar as atualizações legislativas antes de aplicá-las no sistema para garantir a precisão e confiabilidade das informações.



## Relatórios e Dashboards
- **[RF-REL-001]**: Como contador, quero conseguir ver um painel com métricas ficais em atualizadas em tempo (carga tributária total, economia potencial, regime recomendado) para compartilhar insights específicos com meu **gerente** para análise conjunta da situação tributária dos clientes.
- **[RF-REL-002]**: Como gerente, quero acessar um painel executivo consolidado com os indicadores de toda minha equipe de **contadores** para tomar decisões estratégicas baseadas no desempenho coletivo da equipe.
- **[RF-REL-003]**: Como administrador, quero disponibilizar templates de dashboards padrão para os **gerentes** e receber feedback deles sobre melhorias necessárias.
- **[RF-REL-004]**: Como contador, gestor, quero poder baixar meus relatórios em PDF com o logo da empresa, para enviar aos clientes com uma aparência mais profissional e personalizada.
- **[RF-REL-005]**: Como contador, gestor, quero escolher o período dos relatórios (mensal, trimestral ou anual), para entender melhor como o desempenho fiscal muda ao longo do tempo.
- **[RF-REL-006]**: Como contador, gestor, quero ver gráficos que comparem a carga tributária entre os diferentes regimes (Simples Nacional, Lucro Presumido e Lucro Real), para visualizar rapidamente qual é mais vantajoso.
- **[RF-REL-007]**: Como contador, gestor, quero ter acesso ao histórico de todas as simulações que já fiz, para poder acompanhar como as estratégias tributárias evoluíram.
- **[RF-REL-008]**: Como gestor, quero gerar relatórios consolidados por setor econômico ou porte de empresa para identificar padrões e oportunidades.
- **[RF-REL-009]**: Como gestor, quero gerar relatórios que mostrem dados por setor ou tamanho da empresa, para identificar tendências e oportunidades de melhoria.
- **[RF-REL-010]**: Como administrador, quero ver relatórios sobre o uso do sistema, como quem acessa, quantas simulações são feitas e quando o sistema tem mais movimento, pois assim ficará melhor para entender o funcionamento da plataforma
- **[RF-REL-011]**: Como contador ou gerente, quero programar o envio automático dos relatórios por e-mail, para que meus clientes recebam as atualizações sem eu precisar enviar manualmente.
- **[RF-REL-012]**: Como contador ou gerente, quero gerar relatórios de compliance fiscal que mostrem o que já foi feito e o que ainda falta cumprir, para manter tudo em dia com segurança.
- **[RF-REL-013]**: Como gestor, quero ver no relatório de alertas de possíveis economias tributárias, baseados nas análises do sistema, para aproveitar oportunidades antes que passem.
- **[RF-REL-014]**: Como contador ou gerente, quero poder montar meu próprio relatorio, arrastando e organizando os widgets como eu quiser, para deixar tudo do meu jeito.
- **[RF-REL-015]**: Como contador, quero solicitar ao **gerente** a criação de relatórios personalizados para **clientes** específicos.

## Notificações e Alertas Legislativos
- **[RF-NOT-001]**: Como contador, quero receber notificações em tempo real sobre mudanças na legislação tributária e compartilhar alertas relevantes com meu **gerente** para discutir impactos futuros nos nossos clientes.
- **[RF-NOT-002]**: Como contador ou gerente, quero ser avisado sempre que mudarem as alíquotas ou regras dos regimes tributários que uso com frequência (Simples Nacional, Lucro Presumido, Lucro Real), para poder ajustar rapidamente minhas simulações.
- **[RF-NOT-003]**: Como gerente ou contador, quero receber lembretes sobre parazos de obrigações acessórias (como DCTF, EFD e SPED), para evitar multas e garantir que tudo esteja em dia com o fisco.
- **[RF-NOT-004]**: Como administrador, quero configurar o sistema para enviar alertas automáticos sobre novas leis, portarias e instruções da Receita Federal, garantindo que todos os **usuários** fiquem informados.
- **[RF-NOT-005]**: Como contador ou gestor, quero escolher como quero receber os avisos (por e-mail, dentro do sistema ou por SMS), para ser notificado da forma mais prática para mim.
- **[RF-NOT-006]**: Como contador ou gestor, quero ser avisado quando uma simulação salva for impactada por alguma mudança na lei, para poder revisar e atualizar os cálculos a tempo.
- **[RF-NOT-007]**: Como gestor, quero poder enviar notificações em massa para todos os **usuários** quando houver alguma atualização importante no sistema ou mudança fiscal urgente.
- **[RF-NOT-008]**: Como contador ou gestor, quero ter acesso a um histórico de todas as notificações que recebi, para poder consultar depois quando precisar ou em caso de auditoria.
- **[RF-NOT-009]**: Como gestor, quero receber alertas quando surgirem novas oportunidades de economia tributária, baseadas em atualizações legais ou interpretações recentes.
- **[RF-NOT-010]**: Como administrador, quero que o sistema notifique automaticamente os **contadores** e **gerentes** sobre o vencimento de certidões negativas e documentos fiscais, para evitar atrasos ou irregularidades.
- **[RF-NOT-011]**: Como técnico de suporte, quero ser notificado quando o sistema de alertas apresentar falhas, para resolver o problema rapidamente e garantir que as notificações continuem funcionando.
- **[RF-NOT-012]**: Como contador ou gerente, quero poder criar minhas próprias regras de notificação por **cliente**, regime tributário ou valor de faturamento para receber só o que for realmente relevante para mim.

## Administração, Segurança e Infraestrutura do Sistema
- **[RF-ADM-001]**: Como administrador, quero visualizar logs de acesso e ações críticas feitas por **Usuário** para monitorar comportamentos suspeitos.
- **[RF-ADM-002]**: Como administrador, quero visualizar logs de erro categorizados (crítico, aviso. informação) e com mensagens claras para corrigir as falhas.
- **[RF-ADM-003]**: Como administrador, quero configurar as políticas de armazenamento e detalhamento de logs (tempo máximo para armazenar, quais dados mostrar, nível de especificade) para garantir uso correto dos dados e sua disponibilidade.
- **[RF-ADM-004]**: Como administrador, quero visualizar e exportar relatórios de auditoria englobando ações de **Usuário** para garantir transparência.
- **[RF-ADM-005]**: Como administrador, quero configurar (agendar e executar manualmente) rotinas automáticas de backup dos dados do sistema para garantir disponibilidade dos dados.
- **[RF-ADM-006]**: Como administrador, quero visualizar métricas de uso e desempenho do sistema (consumo de recursos, taxa de erro) para identificar pontos de melhoria e otimizar o uso de recursos.
- **[RF-ADM-007]**: Como técnico de suporte, quero visualizar temporariamente informações de **Associado** e **Gerente** com autorização de **Gestor** para diagnosticar eventuais problemas.
- **[RF-ADM-008]**: Como gestor, quero autorizar temporariamente o acesso de **Técnico de suporte** a informações de **Associado** e **Gerente** para garantir que ele possa diagnosticar eventuais problemas.
- **[RF-ADM-009]**: Como administrador, quero que o sistema guarde os logs de erros que acontecerem duranto o seu funcionamento com mensagens claras e explicativas para que possam ser visualizados e resolvidos posteriormente.
- **[RF-ADM-010]**: Como gestor, quero visualizar a saúde do sistema no momento (módulos funcionando, tempo médio de resposta, disponibilidade) para acompanhar a situação atual do sistema.
- **[RF-ADM-011]**: Como usuário, quero enviar informações sobre erros encontrados para **Administrador** durante o uso do sistema para garantir que eventuais problemas possam ser resolvidos mais rapidamente.
- **[RF-ADM-012]**: Como administrador, quero ser notificado quando ocorrer um erro crítico para resolver rapidamente o incidente e garantir a "saúde" do sistema.

## Integração com Sistemas Externos (APIs)



# Requisitos não-funcionais
## Disponibilidade
...

## Privacidade e segurança
...

## Usabilidade
- **[RNF-USA-001]**: O sistema deve ser acessível e utilizável por usuários com diferentes níveis de habilidade técnica, garantindo uma experiência intuitiva e amigável.
- **[RNF-USA-002]**: O sistema deve fornecer feedback claro e imediato para as ações do usuário, incluindo confirmações de sucesso e mensagens de erro compreensíveis.
- **[RNF-USA-003]**: O sistema deve ser compatível com dispositivos móveis, permitindo que os usuários acessem suas funcionalidades em smartphones e tablets.
- **[RNF-USA-004]**: O sistema deve oferecer opções de personalização da interface, como temas claros e escuros, para atender às preferências individuais dos usuários.


## Suportabilidade
- **[RNF-SUP-001]**: O sistema deve funcionar nos principais navegadores web (Google Chrome, Mozilla Firefox, Microsoft Edge, Safari) para garantir ampla acessibilidade.
- **[RNF-SUP-002]**: O sistema deve ser compatível com os sistemas operacionais Windows, macOS e Linux para atender a diferentes ambientes de trabalho.

## Interoperabilidade
... Não pensei nisso ainda...

## Manutenibilidade


## Desempenho
...

## Implementação
...

## Implantação
...