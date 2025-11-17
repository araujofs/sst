# Requisitos de Software

## Sistema de simulação tributária (SST)

<small>Versão 1.8</small>

---

## Histórico de revisões

| Data | Versão | Descrição | Autor |
| ---- | ------ | --------- | ----- |
| 07/11/2025 | 1.0 | Criação do documento | Arthur Araújo |
| 08/11/2025 | 1.1 | Adição dos requisitos funcionais de Calculo e Simulação | Davi Leite |
| 09/11/2025 | 1.2 | Adição dos requisitos funcionais de Relatorio e Notificações | Gabriel Pereira |
| 09/11/2025 | 1.3 | Adição dos requisitos funcionais de Atualização de Legislação e Aliquotas | Davi Leite |
| 09/11/2025 | 1.4 | Adição dos requisitos não-funcionais de Usabilidade e Suportabilidade | Davi Leite |
| 09/11/2025 | 1.4.1 | Correção da marcação da versao atual do Sistema e adição do sumário | Davi Leite |
| 09/11/2025 | 1.5 | Adição dos requisitos não-funcionais de Manutenibilidade | Davi Leite |
| 09/11/2025 | 1.6 | Adição dos wireframes e protótipos iniciais | Davi Leite |
| 17/11/2025 | 1.7 | Adição da Especificação Técnica dos Cálculos Tributários | Davi Leite |
| 17/11/2025 | 1.8 | Adição dos requisitos funcionais de Integração com APIS externas | Davi Leite
---

## Sumário

- [Introdução](#introdução)
  - [Definições, acrônimos e abreviações](#definições-acrônimos-e-abreviações)
- [Usuários identificados](#usuários-identificados)
- [Requisitos funcionais (por módulo)](#requisitos-funcionais-por-módulo)
  - [Autenticação e Controle de Acesso](#autenticação-e-controle-de-acesso)
  - [Gestão de Usuários e Organizações](#gestão-de-usuários-e-organizações)
  - [Cálculo e Simulação Tributária](#cálculo-e-simulação-tributária)
  - [Atualização de Legislação e Alíquotas](#atualização-de-legislação-e-alíquotas)
  - [Relatórios e Dashboards](#relatórios-e-dashboards)
  - [Notificações e Alertas Legislativos](#notificações-e-alertas-legislativos)
  - [Administração, Segurança e Infraestrutura do Sistema](#administração-segurança-e-infraestrutura-do-sistema)
  - [Integração com Sistemas Externos (APIs)](#integração-com-sistemas-externos-apis)
- [Requisitos não-funcionais](#requisitos-não-funcionais)
  - [Disponibilidade](#disponibilidade)
  - [Privacidade e segurança](#privacidade-e-segurança)
  - [Usabilidade](#usabilidade)
  - [Suportabilidade](#suportabilidade)
  - [Interoperabilidade](#interoperabilidade)
  - [Manutenibilidade](#manutenibilidade)
  - [Desempenho](#desempenho)
  - [Implantação](#implantação)
- [Wireframes e Protótipos](#wireframes-e-protótipos)
  - [Formulário de Simulação Tributária](#formulário-de-simulação-tributária)
  - [Resultados - Simples Nacional](#resultados---simples-nacional)

---

# Introdução

Este documento tem como objetivo apresentar os requisitos de software do produto **Sistema de simulação tributária (SST)**

## Definições, acrônimos e abreviações

Visando o melhor entendimento do documento faz-se necessário definir alguns termos, abreviações e acrônimos, o que será feito abaixo.

- Identificação dos requisitos: a referência a requisitos de software presentes nesse documento é feita através do identificador de requisitos seguindo o padrão abaixo:

  `[IDENTIFICADOR DO TIPO REQUISITO-IDENTIFICADOR DO MÓDULO-identificador do requisito]`

  O identificador de tipo segue o padrão abaixo;
  - RF -> Requisito funcional
  - RNF -> Requisito não-funcional (nos requisitos não-funcionais não há identificador de módulo)

  O identificador do requisito será uma sequência de números. Esse número deve ser único para cada módulo.

  **Exemplo**: [RF-AUT-001], [RNF-023] 

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

### Requisitos Gerais de Cálculo

- **[RF-CAL-001]**: Como Contador ou Gerente, quero selecionar o setor econômico da empresa (comércio, indústria, serviços) e informar o CNAE principal antes de iniciar uma simulação para que o sistema identifique automaticamente qual anexo do Simples Nacional é aplicável e quais regras tributárias devem ser seguidas.

- **[RF-CAL-002]**: Como Contador ou Gerente, quero selecionar o regime tributário aplicável (Simples Nacional, Lucro Presumido ou Lucro Real) para que o sistema solicite apenas os dados financeiros necessários para aquele regime específico e aplique as regras fiscais corretas na simulação.

- **[RF-CAL-003]**: Como Contador ou Gerente, quero visualizar o detalhamento completo de cada tributo calculado, incluindo: nome do tributo, base de cálculo utilizada, alíquota ou percentual aplicado, deduções permitidas, valor parcial e valor final, para compreender exatamente como os valores foram obtidos e poder validar os cálculos.

- **[RF-CAL-004]**: Como Contador ou Gerente, quero criar e salvar múltiplos cenários de simulação com diferentes premissas (variação de receita, diferentes regimes tributários, mudanças em despesas) para comparar lado a lado e identificar a melhor estratégia fiscal para o cliente.

- **[RF-CAL-005]**: Como Contador ou Gerente, quero comparar lado a lado até 3 cenários tributários simultaneamente, visualizando: carga tributária total de cada regime, valor de cada tributo individual, impacto percentual no resultado líquido, e diferença absoluta e relativa entre os cenários, para auxiliar na tomada de decisão estratégica.

- **[RF-CAL-006]**: Como Contador ou Gerente, quero que o sistema indique automaticamente qual regime tributário resulta na menor carga tributária com base nos dados financeiros inseridos, destacando a economia potencial em reais e percentual em relação aos outros regimes, para otimizar o planejamento fiscal do cliente.

- **[RF-CAL-007]**: Como Contador ou Gerente, quero simular o impacto de mudanças em variáveis específicas (aumento percentual de receita, redução de custos, inclusão de novos investimentos) sobre a carga tributária de cada regime, para realizar análises de sensibilidade e projeções futuras.

- **[RF-CAL-008]**: Como Contador ou Gerente, quero que o sistema valide automaticamente os dados inseridos antes do cálculo, identificando: valores negativos inválidos, inconsistências entre receitas e despesas, faturamento acima do limite do regime selecionado, e alertando sobre valores atípicos que possam indicar erro de digitação, para evitar erros nos cálculos e garantir a qualidade das simulações.

- **[RF-CAL-009]**: Como Contador ou Gerente, quero salvar simulações realizadas com histórico de alterações, incluindo: data e hora da simulação, usuário que realizou, dados de entrada utilizados, regime tributário simulado, e resultados obtidos, para poder recuperar e revisar análises anteriores quando necessário.

- **[RF-CAL-010]**: Como Contador ou Gerente, quero exportar os resultados das simulações em diferentes formatos (PDF com formatação profissional e logo da empresa, Excel com todas as planilhas de cálculo detalhadas, CSV com dados brutos para análise), para compartilhar com clientes e stakeholders.

- **[RF-CAL-011]**: Como Gerente, quero visualizar um resumo executivo da simulação tributária contendo: regime tributário recomendado, carga tributária total anual, economia potencial em relação aos outros regimes, principais tributos (top 3 por valor), e gráfico comparativo visual, para apresentar rapidamente aos stakeholders de forma clara e objetiva.

- **[RF-CAL-012]**: Como Contador ou Gerente, quero que o sistema permita ajustes manuais em alíquotas e parâmetros específicos (com campo obrigatório para justificativa textual de no mínimo 20 caracteres e registro de quem fez o ajuste), para simular situações especiais como incentivos fiscais regionais, benefícios setoriais, ou interpretações específicas da legislação.

### Cálculos do Simples Nacional

- **[RF-CAL-SN-001]**: Como Contador ou Gerente, ao selecionar Simples Nacional, quero informar obrigatoriamente: CNAE principal da empresa, receita bruta acumulada dos últimos 12 meses (mês a mês), receita bruta do mês atual que está sendo simulado, e se a empresa for de serviços (Anexos III, IV ou V), a folha de salários dos últimos 12 meses, para que o sistema tenha os dados necessários para determinar o anexo aplicável e calcular a alíquota efetiva.

- **[RF-CAL-SN-002]**: Como Contador ou Gerente, quero que o sistema identifique automaticamente qual Anexo do Simples Nacional (I - Comércio, II - Indústria, III - Serviços com folha ≥28%, IV - Serviços com folha <28%, ou V - Serviços específicos) se aplica ao CNAE informado, consultando a tabela oficial de mapeamento CNAE→Anexo atualizada pela Receita Federal, e exiba claramente o anexo selecionado antes de prosseguir com o cálculo.

- **[RF-CAL-SN-003]**: Como Contador ou Gerente, quando o CNAE indicar atividade de serviços que pode se enquadrar nos Anexos III ou IV, quero que o sistema calcule automaticamente o percentual da folha de salários em relação à receita bruta dos últimos 12 meses e determine: se ≥28%, aplicar Anexo III; se <28%, aplicar Anexo IV, mostrando o percentual calculado e o anexo resultante para validação.

- **[RF-CAL-SN-004]**: Como Contador ou Gerente, quero que o sistema determine automaticamente em qual faixa de receita a empresa se enquadra (1ª a 6ª faixa) com base na receita bruta acumulada dos últimos 12 meses, consultando a tabela oficial do anexo aplicável com os limites: até R$ 180.000, de R$ 180.000,01 a R$ 360.000, de R$ 360.000,01 a R$ 720.000, de R$ 720.000,01 a R$ 1.800.000, de R$ 1.800.000,01 a R$ 3.600.000, e de R$ 3.600.000,01 a R$ 4.800.000, e exiba claramente a faixa identificada.

- **[RF-CAL-SN-005]**: Como Contador ou Gerente, quero que o sistema calcule a alíquota efetiva do Simples Nacional aplicando a fórmula oficial: Alíquota Efetiva = ((RB12 × Alíquota Nominal da Faixa) - Valor a Deduzir da Faixa) / RB12, onde RB12 é a receita bruta dos últimos 12 meses, utilizando a alíquota nominal e o valor a deduzir da tabela oficial do anexo e faixa identificados, garantindo que o resultado não seja negativo, e exibindo: alíquota nominal da faixa (%), valor a deduzir (R$), e alíquota efetiva calculada (%) com 4 casas decimais.

- **[RF-CAL-SN-006]**: Como Contador ou Gerente, quero que o sistema calcule o valor total do tributo unificado devido no mês multiplicando a receita bruta do mês atual pela alíquota efetiva calculada: Valor Devido = Receita Bruta Mensal × Alíquota Efetiva, e exiba o resultado em reais com 2 casas decimais.

- **[RF-CAL-SN-007]**: Como Contador ou Gerente, quero que o sistema detalhe a distribuição do valor total devido entre os tributos componentes (IRPJ, CSLL, COFINS, PIS, CPP, ICMS ou ISS conforme aplicável), aplicando os percentuais de repartição oficiais da tabela de distribuição de tributos para o anexo e faixa específicos, e exiba para cada tributo: nome, percentual de repartição (%), e valor individual calculado (R$), permitindo validar que a soma dos valores individuais corresponde ao valor total devido.

- **[RF-CAL-SN-008]**: Como Contador ou Gerente, quero que o sistema apresente um resumo da apuração do Simples Nacional contendo: anexo aplicado (I a V), faixa de receita (1ª a 6ª), receita bruta acumulada 12 meses (R$), receita bruta do mês atual (R$), alíquota nominal da faixa (%), valor a deduzir (R$), alíquota efetiva calculada (%), valor total devido no mês (R$), e lista detalhada de todos os tributos componentes com seus valores individuais, para facilitar a compreensão e validação dos cálculos.

- **[RF-CAL-SN-009]**: Como Contador ou Gerente, quero que o sistema valide se a receita bruta acumulada dos últimos 12 meses não excede R$ 4.800.000,00 (limite do Simples Nacional) antes de realizar o cálculo, e caso exceda, exiba mensagem clara informando que a empresa está fora do limite do Simples Nacional e não pode optar por este regime, impedindo o prosseguimento do cálculo.

### Cálculos do Lucro Presumido

- **[RF-CAL-LP-001]**: Como Contador ou Gerente, ao selecionar Lucro Presumido, quero informar obrigatoriamente: tipo de atividade principal da empresa (para determinar percentuais de presunção), receita bruta do trimestre para cálculo de IRPJ e CSLL, receita bruta mensal para cálculo de PIS, COFINS e ISS/ICMS, outras receitas financeiras do trimestre (opcional), estado (UF) para ICMS se for comércio/indústria, e município para ISS se for serviços, para que o sistema calcule todos os tributos devidos corretamente.

- **[RF-CAL-LP-002]**: Como Contador ou Gerente, quero que o sistema consulte automaticamente a tabela de percentuais de presunção com base no tipo de atividade informado, obtendo: percentual de presunção para IRPJ (variando de 1,6% para revenda de combustíveis até 32% para serviços em geral), e percentual de presunção para CSLL (variando de 12% para atividades comerciais até 32% para serviços), e exiba claramente os percentuais que serão aplicados antes de prosseguir com o cálculo.

- **[RF-CAL-LP-003]**: Como Contador ou Gerente, quero que o sistema calcule o IRPJ trimestral seguindo estas etapas: (1) Base de Cálculo = (Receita Bruta Trimestral × Percentual de Presunção IRPJ) + Outras Receitas Financeiras, (2) IRPJ Básico = Base de Cálculo × 15%, (3) identificar se Base de Cálculo > R$ 60.000 no trimestre, (4) se sim, Adicional de IRPJ = (Base de Cálculo - R$ 60.000) × 10%, (5) IRPJ Total = IRPJ Básico + Adicional de IRPJ, e exiba detalhadamente: receita bruta trimestral (R$), percentual de presunção aplicado (%), outras receitas financeiras (R$), base de cálculo (R$), IRPJ básico 15% (R$), adicional de IRPJ 10% se aplicável (R$), e valor total devido (R$).

- **[RF-CAL-LP-004]**: Como Contador ou Gerente, quero que o sistema calcule a CSLL trimestral seguindo estas etapas: (1) Base de Cálculo = (Receita Bruta Trimestral × Percentual de Presunção CSLL) + Outras Receitas Financeiras, (2) CSLL = Base de Cálculo × 9%, e exiba detalhadamente: receita bruta trimestral (R$), percentual de presunção aplicado (%), outras receitas financeiras (R$), base de cálculo (R$), alíquota 9%, e valor total devido (R$).

- **[RF-CAL-LP-005]**: Como Contador ou Gerente, quero que o sistema calcule o PIS mensal no regime cumulativo aplicando: PIS = Receita Bruta Mensal × 0,65%, e exiba: receita bruta mensal (R$), alíquota 0,65%, e valor devido (R$), esclarecendo que no regime cumulativo não há aproveitamento de créditos.

- **[RF-CAL-LP-006]**: Como Contador ou Gerente, quero que o sistema calcule a COFINS mensal no regime cumulativo aplicando: COFINS = Receita Bruta Mensal × 3%, e exiba: receita bruta mensal (R$), alíquota 3%, e valor devido (R$), esclarecendo que no regime cumulativo não há aproveitamento de créditos.

- **[RF-CAL-LP-007]**: Como Contador ou Gerente, quando o tipo de atividade for Comércio ou Indústria, quero que o sistema calcule o ICMS mensal consultando a alíquota do estado (UF) informado na tabela de alíquotas de ICMS atualizada, aplicando: ICMS = Receita Bruta Mensal × Alíquota do Estado, e exiba: receita bruta mensal (R$), estado (UF), alíquota do ICMS (%), e valor devido (R$).

- **[RF-CAL-LP-008]**: Como Contador ou Gerente, quando o tipo de atividade for Serviços, quero que o sistema calcule o ISS mensal consultando a alíquota do município informado na tabela de alíquotas de ISS atualizada (variando de 2% a 5%), aplicando: ISS = Receita Bruta Mensal × Alíquota do Município, e exiba: receita bruta mensal (R$), município, alíquota do ISS (%), e valor devido (R$).

- **[RF-CAL-LP-009]**: Como Contador ou Gerente, quero que o sistema apresente um resumo consolidado do Lucro Presumido separando: (1) Tributos Trimestrais - IRPJ (com detalhamento completo incluindo base de cálculo, percentual de presunção, IRPJ básico, adicional e total) e CSLL (com base de cálculo, percentual de presunção e total), e subtotal trimestral; (2) Tributos Mensais - PIS, COFINS, ICMS ou ISS (cada um com base de cálculo, alíquota e valor), e subtotal mensal; (3) Carga Tributária Total Anualizada - somando tributos trimestrais × 4 + tributos mensais × 12, para facilitar a compreensão completa da tributação no regime de Lucro Presumido.

- **[RF-CAL-LP-010]**: Como Contador ou Gerente, quero que o sistema valide que quando o tipo de atividade for Comércio ou Indústria, o campo município não seja obrigatório (pois não há ISS), e quando for Serviços, o campo estado (UF) não seja obrigatório (pois não há ICMS), garantindo que apenas os dados necessários sejam solicitados.

### Cálculos do Lucro Real (somente Prestação de Serviços)

- **[RF-CAL-LR-001]**: Como Contador ou Gerente, ao selecionar Lucro Real, quero que o sistema exiba um aviso destacado informando que "o cálculo do Lucro Real está disponível apenas para empresas de Prestação de Serviços" e solicite confirmação do tipo de atividade antes de prosseguir, impedindo o cálculo caso o tipo de atividade não seja serviços.

- **[RF-CAL-LR-002]**: Como Contador ou Gerente, ao selecionar Lucro Real para Prestação de Serviços, quero informar obrigatoriamente: lucro líquido contábil antes do IRPJ do trimestre (R$), adições fiscais do trimestre (despesas não dedutíveis como multas fiscais, brindes excessivos, provisões não aceitas - R$), exclusões fiscais do trimestre (receitas não tributáveis, incentivos fiscais, dividendos recebidos - R$), prejuízos fiscais acumulados de períodos anteriores disponíveis para compensação (R$), receita bruta mensal de serviços (R$), custos e despesas operacionais dedutíveis do mês (aluguéis, energia, serviços de PJ - R$), e município para cálculo do ISS, para que o sistema calcule o Lucro Real e todos os tributos devidos.

- **[RF-CAL-LR-003]**: Como Contador ou Gerente, quero que o sistema calcule o Lucro Real (base de cálculo do IRPJ e CSLL) seguindo estas etapas: (1) Lucro Real Antes da Compensação = Lucro Líquido Contábil + Adições Fiscais - Exclusões Fiscais, (2) verificar se resultado é negativo (prejuízo fiscal), (3) se for prejuízo, não há IRPJ/CSLL a pagar e o prejuízo deve ser registrado para compensação futura, (4) se for lucro positivo, calcular Limite de Compensação = Lucro Real × 30%, (5) Compensação Aplicada = menor valor entre (Prejuízos Acumulados Disponíveis) e (Limite de Compensação), (6) Lucro Real Final = Lucro Real Antes da Compensação - Compensação Aplicada, e exibir detalhadamente todos os valores intermediários: lucro líquido contábil (R$), adições fiscais (R$), exclusões fiscais (R$), lucro real antes da compensação (R$), limite de compensação 30% (R$), compensação de prejuízos aplicada (R$), e lucro real final (R$).

- **[RF-CAL-LR-004]**: Como Contador ou Gerente, quero que o sistema calcule o IRPJ trimestral sobre o Lucro Real seguindo estas etapas: (1) IRPJ Básico = Lucro Real Final × 15%, (2) calcular Lucro Real Mensal = Lucro Real Final / 3, (3) verificar se Lucro Real Mensal > R$ 20.000, (4) se sim, Parcela Excedente Total = (Lucro Real Mensal - R$ 20.000) × 3, e Adicional de IRPJ = Parcela Excedente Total × 10%, (5) IRPJ Total = IRPJ Básico + Adicional de IRPJ, e exibir: lucro real final (R$), IRPJ básico 15% (R$), lucro real mensal médio (R$), parcela que excede R$ 20.000/mês (R$), adicional de IRPJ 10% se aplicável (R$), e IRPJ total devido (R$).

- **[RF-CAL-LR-005]**: Como Contador ou Gerente, quero que o sistema calcule a CSLL trimestral aplicando: CSLL = Lucro Real Final × 9% (alíquota para prestadores de serviços), e exiba: lucro real final (R$), alíquota 9%, e valor devido (R$).

- **[RF-CAL-LR-006]**: Como Contador ou Gerente, quero que o sistema calcule o PIS mensal no regime não-cumulativo seguindo estas etapas: (1) Débitos de PIS = Receita Bruta Mensal de Serviços × 1,65%, (2) Créditos de PIS = Custos e Despesas Operacionais Dedutíveis × 1,65%, (3) PIS a Pagar = Débitos - Créditos, (4) se resultado for negativo (créditos > débitos), registrar saldo credor para acumulação em períodos futuros e PIS a Pagar = R$ 0, e exibir: receita bruta mensal (R$), débitos 1,65% (R$), custos/despesas dedutíveis (R$), créditos 1,65% (R$), e valor líquido a pagar (R$) ou saldo credor acumulado (R$).

- **[RF-CAL-LR-007]**: Como Contador ou Gerente, quero que o sistema calcule a COFINS mensal no regime não-cumulativo seguindo estas etapas: (1) Débitos de COFINS = Receita Bruta Mensal de Serviços × 7,6%, (2) Créditos de COFINS = Custos e Despesas Operacionais Dedutíveis × 7,6%, (3) COFINS a Pagar = Débitos - Créditos, (4) se resultado for negativo (créditos > débitos), registrar saldo credor para acumulação em períodos futuros e COFINS a Pagar = R$ 0, e exibir: receita bruta mensal (R$), débitos 7,6% (R$), custos/despesas dedutíveis (R$), créditos 7,6% (R$), e valor líquido a pagar (R$) ou saldo credor acumulado (R$).

- **[RF-CAL-LR-008]**: Como Contador ou Gerente, quero que o sistema calcule o ISS mensal consultando a alíquota do município informado na tabela de alíquotas de ISS atualizada (variando de 2% a 5%), aplicando: ISS = Receita Bruta Mensal de Serviços × Alíquota do Município, e exiba: receita bruta mensal (R$), município, alíquota do ISS (%), e valor devido (R$).

- **[RF-CAL-LR-009]**: Como Contador ou Gerente, quero que o sistema apresente um resumo consolidado do Lucro Real separando: (1) Apuração Contábil - lucro líquido contábil, adições fiscais, exclusões fiscais, lucro real antes da compensação, compensação de prejuízos aplicada, lucro real final; (2) Tributos Trimestrais - IRPJ (com base de cálculo, IRPJ básico, adicional e total) e CSLL (com base de cálculo, alíquota e total), e subtotal trimestral; (3) Tributos Mensais - PIS (com débitos, créditos e líquido), COFINS (com débitos, créditos e líquido), e ISS (com base, alíquota e valor), e subtotal mensal; (4) Carga Tributária Total Anualizada - somando tributos trimestrais × 4 + tributos mensais × 12, destacando a vantagem do regime não-cumulativo com aproveitamento de créditos de PIS e COFINS.

- **[RF-CAL-LR-010]**: Como Contador ou Gerente, quero que o sistema valide que empresas de Prestação de Serviços no Lucro Real não recolhem ICMS nem IPI, garantindo que estes tributos não sejam calculados nem exibidos nos resultados, evitando confusão.

### Obrigações Acessórias e Funcionalidades Complementares

- **[RF-CAL-OA-001]**: Como Contador, quero que o sistema identifique e liste automaticamente as obrigações acessórias aplicáveis ao regime tributário e tipo de atividade selecionados (DCTF - Declaração de Débitos e Créditos Tributários Federais, EFD-Contribuições - Escrituração Fiscal Digital das Contribuições, SPED Fiscal - Sistema Público de Escrituração Digital), informando: nome da obrigação, periodicidade de entrega, prazo de vencimento, e descrição resumida do conteúdo, para garantir o compliance completo e evitar multas por não entrega.

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

### Validação e Consulta de Dados Cadastrais

- **[RF-INT-001]**: Como Contador ou Gerente, quero que o sistema valide automaticamente o CNPJ informado consultando a API da Receita Federal (Serpro ou ReceitaWS) para verificar: situação cadastral (ativa, inapta, suspensa), razão social, CNAE principal, natureza jurídica, e data de abertura, garantindo que os dados da empresa sejam legítimos e atualizados antes de iniciar qualquer simulação.

- **[RF-INT-002]**: Como Contador ou Gerente, quero que o sistema identifique automaticamente o CNAE principal e CNAEs secundários da empresa através da consulta de CNPJ, preenchendo automaticamente o setor econômico e exibindo a descrição completa das atividades, para agilizar o processo de entrada de dados e evitar erros de digitação.

### Consulta de Alíquotas Tributárias Municipais e Estaduais

- **[RF-INT-003]**: Como Contador ou Gerente, quero que o sistema consulte automaticamente a alíquota de ISS aplicável através de API ou base de dados oficial atualizada, informando o município e o código de serviço conforme Lei Complementar 116/2003, exibindo: alíquota vigente (2% a 5%), base legal, e data da última atualização, para garantir cálculos precisos do ISS sem necessidade de consulta manual.

- **[RF-INT-004]**: Como Contador ou Gerente, quero que o sistema consulte automaticamente a alíquota de ICMS aplicável através de API ou base de dados oficial da SEFAZ estadual, informando o estado (UF) e o tipo de produto/operação, exibindo: alíquota interna vigente, alíquota interestadual quando aplicável, base legal, e data da última atualização, para garantir cálculos precisos do ICMS.

- **[RF-INT-005]**: Como Administrador, quero que o sistema mantenha uma base de dados local (cache) das alíquotas de ISS e ICMS consultadas, com validade máxima de 7 dias, e tente renovar automaticamente via API ao atingir 80% da validade, para garantir disponibilidade do sistema mesmo quando as APIs externas estiverem indisponíveis, exibindo alerta visual ao usuário quando estiver utilizando dados em cache próximos ao vencimento.

### Atualização de Tabelas e Legislação Tributária

- **[RF-INT-006]**: Como Administrador, quero que o sistema consulte automaticamente APIs oficiais da Receita Federal para atualizar as tabelas do Simples Nacional (Anexos I a V com faixas, alíquotas nominais e valores a deduzir) mensalmente ou sempre que houver publicação de nova legislação, registrando em log: data da atualização, versão anterior, versão nova, e notificando todos os usuários sobre mudanças relevantes.

- **[RF-INT-007]**: Como Administrador, quero que o sistema armazene localmente as tabelas oficiais do Simples Nacional como fallback, permitindo que o sistema continue funcionando mesmo sem conexão com APIs externas, e exiba alerta destacado informando aos usuários que as tabelas podem estar desatualizadas e recomendem validação manual antes de tomar decisões críticas.

### Importação de Dados Contábeis

- **[RF-INT-008]**: Como Contador ou Gerente, quero que o sistema permita importar dados financeiros (receitas, despesas, folha de pagamento) de arquivos nos formatos Excel (.xlsx), CSV, ou XML do SPED (ECD, ECF, EFD-Contribuições), mapeando automaticamente os campos relevantes e validando a consistência dos dados antes da importação, para agilizar o processo de simulação e reduzir erros de digitação manual.

- **[RF-INT-009]**: Como Contador ou Gerente, quero que o sistema permita conectar via API REST com sistemas ERP populares (TOTVS, SAP, Omie, Conta Azul), mediante configuração de credenciais e autorização, para importar automaticamente balancetes, DREs, e dados de faturamento do período selecionado, sincronizando dados sem necessidade de exportação/importação manual.

### Comunicação e Notificações

- **[RF-INT-010]**: Como Contador ou Gerente, quero que o sistema envie relatórios e notificações por e-mail através de serviço SMTP configurável ou API de envio de e-mails (SendGrid, AWS SES, Mailgun), com templates profissionais personalizáveis contendo logo da empresa, permitindo anexar PDFs de simulações e incluir gráficos comparativos no corpo do e-mail.

- **[RF-INT-011]**: Como Administrador, quero que o sistema possa enviar notificações urgentes via SMS através de APIs de mensageria (Twilio, AWS SNS) para alertar Contadores e Gerentes sobre mudanças críticas na legislação tributária, vencimento de prazos de obrigações acessórias, ou quando houver simulações impactadas por atualizações de alíquotas.

### Monitoramento de Atualizações Legislativas

- **[RF-INT-012]**: Como Administrador, quero que o sistema monitore automaticamente fontes oficiais (Diário Oficial da União, sites da Receita Federal, CONFAZ) através de web scraping ou APIs quando disponíveis, identificando publicações de novas leis, portarias, instruções normativas e convênios que possam impactar cálculos tributários, e gerando alertas para revisão manual antes de aplicar mudanças no sistema.

### Resiliência e Tratamento de Falhas

- **[RF-INT-013]**: Como Contador ou Gerente, quero que o sistema exiba mensagens claras quando APIs externas estiverem indisponíveis, informando: qual serviço está fora do ar, impacto nas funcionalidades (ex: "validação de CNPJ indisponível - dados devem ser inseridos manualmente"), se há dados em cache disponíveis, e previsão de retorno quando conhecida, permitindo que eu decida se desejo prosseguir com dados manuais ou aguardar.

- **[RF-INT-014]**: Como Administrador, quero que o sistema registre em log todas as tentativas de comunicação com APIs externas incluindo: timestamp, endpoint acessado, parâmetros enviados, resposta recebida, tempo de resposta, e erros encontrados, e gere relatórios semanais de disponibilidade e desempenho das integrações para identificar problemas recorrentes e negociar SLAs com fornecedores de APIs.

# Requisitos não-funcionais
## Disponibilidade
- **[RNF-001]**: O sistema deve estar disponível 24h por dia, 7 dias por semana, 365 dias por ano.
- **[RNF-002]**: O sistema deve utilizar menos recursos em dias de menor fluxo (finais de semana, feriados).
- **[RNF-003]**: O sistema deve estar disponível através da web, não havendo instalação local para o uso.

## Privacidade e segurança
- **[RNF-005]**: O sistema deve cumprir o que a LGPD (Lei Geral de Proteção de Dados) determina quanto a privacidade dos dados.
- **[RNF-006]**: O sistema deve criptografar utilizando algoritmos de *salt*, como bcrypt dados sensíveis gerados durante seu uso, como senhas, e garantir integridade de documentos gerados como relatórios e dados fiscais utilizando algoritmos de hash.
- **[RNF-007]**: O sistema deve garantir que os dados sejam acessados apenas por usuários autorizados e autenticados.


## Usabilidade
- **[RNF-008]**: O sistema deve ser fácil de utilizar e entender e deve usar símbolos e nomenclaturas conhecidas pelo usuário alvo.
- **[RNF-009]**: O sistema deve oferecer meios (assistente de voz, código da página facilmente identificável por leitores) para que usuários com deficiência visual possam utilizá-lo.
- **[RNF-010]**: O sistema deve ser acessível e utilizável por usuários com diferentes níveis de habilidade técnica, garantindo uma experiência intuitiva e amigável.
- **[RNF-011]**: O sistema deve fornecer feedback claro e imediato para as ações do usuário, incluindo confirmações de sucesso e mensagens de erro compreensíveis.
- **[RNF-012]**: O sistema deve oferecer opções de personalização da interface, como temas claros e escuros, para atender às preferências individuais dos usuários.
- **[RNF-014]**: O sistema deve oferecer uma documentação do usuário separada explicando seu uso.

## Suportabilidade
- **[RNF-013]**: O sistema deve funcionar nos seguintes navegadores: Chrome, Firefox, Safari e Edge através de computador com Windows, Linux e MacOS ou tablet e celular com Android e IOS.

## Interoperabilidade
... Não pensei nisso ainda...

## Manutenibilidade
- **[RNF-015]**: O sistema deve ser desenvolvido seguindo padrões de codificação bem definidos e documentados para facilitar a leitura, compreensão e manutenção por diferentes desenvolvedores.
- **[RNF-016]**: O sistema deve ser desenvolvido utilizando testes (unitários, E2E, integração) garantindo que funcione como esperado.
- **[RNF-019]**: O sistema deve ser desenvolvido de maneira que todas as funções, classes e módulos críticos possuam documentação inline explicando seu propósito, parâmetros, retorno e exemplos de uso.
- **[RNF-020]**: O sistema deve possuir documentação técnica atualizada incluindo diagramas de arquitetura, fluxos de dados, APIs e guias de desenvolvimento.
- **[RNF-021]**: O sistema deve ser desenvolvido utilizando controle de versionamento (Git) com estratégia de branching bem definida para facilitar o desenvolvimento colaborativo e rastreabilidade de mudanças.
- **[RNF-022]**: O sistema deve ser desenvolvido utilizando ambientes de desenvolvimento e staging que repliquem fielmente o ambiente de produção para testes seguros de mudanças antes da implantação.


## Desempenho
- **[RNF-017]**: O sistema deve possuir alto grau de precisão em seus cálculos (utilizando tipos decimais exatos no banco e no código).

## Implantação
- **[RNF-004]**: O sistema deve ser implantado utilizando containeres Docker em servidores Linux.
- **[RNF-018]**: O sistema deve ser implantado em múltiplas instâncias para garantir redundância em caso de falha de um servidor.

---

# Wireframes e Protótipos

Esta seção apresenta os wireframes desenvolvidos para as principais interfaces do Sistema de Simulação Tributária (SST), demonstrando a estrutura visual e o fluxo de interação das funcionalidades de cálculo e simulação tributária.

> **Nota importante:** Os wireframes apresentados são **protótipos iniciais** para validação conceitual. Os formulários e interfaces finais serão **adaptados dinamicamente** de acordo com os regimes tributários selecionados e as necessidades específicas identificadas durante o desenvolvimento. O conteúdo exato dos campos, validações e fluxos de navegação ainda será definido nas próximas iterações do projeto.

## Formulário de Simulação Tributária

O formulário de simulação tributária é dividido em etapas para facilitar a entrada de dados pelo usuário (Contador ou Gerente). A interface foi projetada considerando os requisitos funcionais **RF-CAL-001**, **RF-CAL-002** e **RF-CAL-003**.

![Formulário de Simulação Tributária](../../assets/image/simulacao/form-simulacao.png)

**Figura 1** - Wireframe do formulário de entrada de dados para simulação tributária

**Elementos principais:**
- **Informações básicas da empresa**: Setor econômico, subsetor, número de funcionários, faturamento anual e localização
- **Navegação progressiva**: Interface dividida em etapas para não sobrecarregar o usuário
- **Validação em tempo real**: Campos com indicação de erros e sugestões de preenchimento
- **Botões de ação**: Salvar rascunho, limpar formulário e Proceder para simulação

## Resultados - Simples Nacional (Exemplo)

Após o preenchimento do formulário e execução dos cálculos, o sistema apresenta os resultados detalhados da simulação. O wireframe abaixo exemplifica a tela de resultados para o regime do **Simples Nacional**, conforme requisitos **RF-CAL-004**, **RF-CAL-005** e **RF-CAL-014**.

> **Observação:** Este wireframe representa **apenas um exemplo** de visualização de resultados. As telas de resultados serão **moldadas e adaptadas** para cada regime tributário (Simples Nacional, Lucro Presumido, Lucro Real), com campos e cálculos específicos que ainda serão detalhados nas próximas fases do projeto.

![Resultados da Simulação - Simples Nacional](../../assets/image/simulacao/simples-nacional.png)

**Figura 2** - Wireframe da tela de resultados da simulação tributária para o regime Simples Nacional (exemplo ilustrativo)

**Elementos principais (sujeitos a alterações):**
- **Resumo executivo**: Carga tributária total, regime aplicável (anexo do Simples Nacional) e economia potencial
- **Detalhamento dos tributos**: Base de cálculo, alíquota aplicada, deduções e valor final de cada tributo
- **Comparação com outros regimes**: Gráfico comparativo mostrando Simples Nacional vs. Lucro Presumido vs. Lucro Real
- **Indicadores visuais**: Uso de cores e ícones para facilitar a interpretação dos resultados
- **Ações disponíveis**: Exportar relatório (PDF/Excel), salvar cenário, criar nova simulação e compartilhar
- **Histórico de simulações**: Acesso rápido a simulações anteriores para comparação

Estes wireframes servem como **referência visual inicial** para o desenvolvimento das interfaces, garantindo alinhamento com os requisitos funcionais e não-funcionais de usabilidade (**RNF-001** a **RNF-004**). As interfaces finais serão refinadas com base em feedback dos stakeholders e requisitos técnicos detalhados.
