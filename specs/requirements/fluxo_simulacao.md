# Fluxo de Simulação Tributária (Simples Nacional e Lucro Presumido)

Este documento descreve o fluxo de dados e processos para a simulação de impostos nos regimes Simples Nacional e Lucro Presumido, focado na visão de desenvolvimento.

> **Nota:** O regime Lucro Real foi ignorado nesta versão do fluxo.

## 1. Dados de Entrada Comuns (Início da Simulação)

Para iniciar qualquer simulação, o sistema precisa de dados básicos da empresa e do período.

**Campos Esperados (Input do Usuário):**
*   **CNAE Principal** (Código da Atividade Econômica): Define o tipo de atividade (Comércio, Indústria, Serviço).
    *   *Importância:* Define qual tabela (Anexo) usar no Simples e qual alíquota de presunção usar no Lucro Presumido.
*   **Receita Bruta (Faturamento) do Período**: O valor que a empresa faturou no mês/trimestre que está sendo simulado.
*   **Receita Bruta Acumulada (Últimos 12 meses - RBT12)**: Soma do faturamento dos últimos 12 meses.
    *   *Importância:* Crucial para definir a faixa de alíquota no Simples Nacional.

---

## 2. Fluxo: Simples Nacional

O Simples Nacional é calculado baseando-se em tabelas progressivas (Anexos).

### Dados Específicos Necessários
*   **Folha de Pagamento (Últimos 12 meses)**: Necessário apenas para atividades de serviço sujeitas ao "Fator R".
    *   *Regra:* Se a folha de pagamento for maior ou igual a 28% do faturamento, a empresa pode pagar menos imposto (muda de Anexo).

### Dados do Sistema (Backend/Banco de Dados)
*   **Tabelas do Simples Nacional (Anexos I a V)**:
    *   Cada Anexo tem faixas de faturamento (Ex: Faixa 1: até 180k, Faixa 2: 180k a 360k...).
    *   Cada faixa tem uma **Alíquota Nominal** e uma **Parcela a Deduzir**.

### Passo a Passo do Cálculo (Algoritmo)
1.  **Identificar Anexo**: O sistema consulta o CNAE para saber qual Anexo usar (Ex: Comércio -> Anexo I, Serviço de Limpeza -> Anexo IV).
2.  **Verificar Fator R (Se aplicável)**:
    *   Calcula `Razão = Folha 12 meses / Receita 12 meses`.
    *   Se `Razão >= 0.28`, usa o Anexo com alíquota menor (Ex: Anexo III ao invés do V).
3.  **Encontrar Faixa**: Usa a **Receita Bruta Acumulada (RBT12)** para encontrar a linha correta na tabela do Anexo.
4.  **Calcular Alíquota Efetiva**:
    *   Fórmula: `((RBT12 * Alíquota Nominal) - Parcela a Deduzir) / RBT12`
5.  **Calcular Imposto Final**:
    *   `Imposto a Pagar = Receita do Período * Alíquota Efetiva`

---

## 3. Fluxo: Lucro Presumido

No Lucro Presumido, o governo "presume" uma margem de lucro sobre o faturamento e cobra impostos sobre essa margem, mais PIS/COFINS sobre o total.

### Dados do Sistema (Backend/Banco de Dados)
*   **Alíquotas de Presunção**: Porcentagem do faturamento considerada lucro (Ex: 8% para Comércio, 32% para Serviços).
*   **Alíquotas de Impostos Fixas**:
    *   IRPJ: 15%
    *   CSLL: 9%
    *   PIS: 0.65%
    *   COFINS: 3.00%
*   **Adicional de IRPJ**: 10% sobre o que exceder R$ 20.000,00 de lucro presumido por mês.

### Passo a Passo do Cálculo (Algoritmo)
1.  **Calcular Base de Cálculo (Lucro Presumido)**:
    *   `Base IRPJ = Receita do Período * Alíquota de Presunção (Ex: 32%)`
    *   `Base CSLL = Receita do Período * Alíquota de Presunção (Ex: 32%)`
2.  **Calcular PIS e COFINS**:
    *   `PIS = Receita do Período * 0.65%`
    *   `COFINS = Receita do Período * 3.00%`
3.  **Calcular IRPJ**:
    *   `IRPJ Básico = Base IRPJ * 15%`
    *   **Adicional**: Se `Base IRPJ > 20.000`, calcula `(Base IRPJ - 20.000) * 10%`.
    *   `IRPJ Total = IRPJ Básico + Adicional`
4.  **Calcular CSLL**:
    *   `CSLL = Base CSLL * 9%`
5.  **Calcular Total**:
    *   `Total a Pagar = PIS + COFINS + IRPJ + CSLL`

---

## 4. Resumo da Comparação (Saída para o Usuário)

Ao final, o sistema deve exibir:

1.  **Valor Total Simples Nacional**: R$ X.XXX,XX (Alíquota Efetiva: Y%)
2.  **Valor Total Lucro Presumido**: R$ Y.YYY,YY (Soma de PIS, COFINS, IRPJ, CSLL)
3.  **Diferença**: Qual regime é mais barato e a economia gerada.
4.  **Detalhamento**: Opção para ver como cada valor foi calculado (quais alíquotas foram usadas).
