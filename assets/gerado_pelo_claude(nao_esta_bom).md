# Tabelas de Verbos e Substantivos para Diagrama de Classes

## 1. TABELA DE SUBSTANTIVOS (Candidatos a Classes)

| Substantivo | Origem (UC) | Categoria | Relevância | Justificativa/Observações |
|------------|-------------|-----------|------------|---------------------------|
| **Simulação** | UC10, UC15, UC16 | Classe Central | ⭐⭐⭐ | Entidade principal do sistema - armazena dados de entrada, resultados e histórico |
| **Regime Tributário** | UC10, UC11, UC12, UC14, UC16 | Classe/Enum | ⭐⭐⭐ | Representa os regimes: Simples Nacional, Lucro Presumido, Lucro Real |
| **CNAE** | UC10, UC11, UC12, UC14, UC17, UC19 | Classe | ⭐⭐⭐ | Código de atividade econômica - determina anexos, alíquotas e elegibilidade |
| **Empresa** | UC10, UC17 | Classe | ⭐⭐⭐ | Representa a empresa sendo simulada (CNPJ, razão social, dados cadastrais) |
| **Tributo** | UC11, UC12, UC13, UC14 | Classe | ⭐⭐⭐ | Representa cada imposto calculado (IRPJ, CSLL, PIS, COFINS, ISS, ICMS) |
| **Resultado** | UC11, UC12, UC13, UC14, UC16 | Classe | ⭐⭐⭐ | Contém os valores calculados de cada tributo e totais |
| **Anexo Simples** | UC11 | Classe/Enum | ⭐⭐⭐ | Anexos I a V do Simples Nacional com faixas e alíquotas |
| **Faixa Faturamento** | UC11 | Classe | ⭐⭐ | Faixas progressivas do Simples Nacional com alíquotas nominais |
| **Fator R** | UC11 | Atributo/Valor | ⭐⭐ | Cálculo para determinar anexo (III ou V) - pode ser método da classe Simulação |
| **Alíquota Presunção** | UC12 | Classe | ⭐⭐⭐ | Percentuais de presunção por atividade (8%, 16%, 32%) |
| **Ajuste Fiscal** | UC14 | Classe | ⭐⭐ | Adições e exclusões na base de cálculo do Lucro Real |
| **Prejuízo Fiscal** | UC14 | Classe | ⭐⭐ | Saldo de prejuízos acumulados para compensação |
| **Tabela Tributária** | UC20 | Classe | ⭐⭐⭐ | Armazena dados legislativos (anexos, alíquotas, faixas) com versionamento |
| **Alíquota ISS** | UC21 | Classe | ⭐⭐⭐ | Alíquota municipal por município/UF |
| **Alíquota ICMS** | UC21 | Classe | ⭐⭐⭐ | Alíquota estadual (interna e interestadual) por UF |
| **Dados Financeiros** | UC10, UC18, UC19 | Classe | ⭐⭐⭐ | Agrupa receitas, custos, despesas, folha de pagamento |
| **Município** | UC10, UC17, UC21 | Classe | ⭐⭐ | Localização da empresa - determina ISS aplicável |
| **UF** | UC10, UC17, UC21 | Classe/Enum | ⭐⭐ | Estado - determina ICMS aplicável |
| **Cliente/Associado** | UC15 | Classe | ⭐⭐ | Cliente do escritório contábil - dono das simulações |
| **Usuário** | UC15, UC20, UC21 | Classe | ⭐⭐⭐ | Contador, Gerente, Administrador - acesso ao sistema |
| **Histórico** | UC15, UC20, UC21 | Classe | ⭐⭐ | Registra alterações em simulações e tabelas |
| **Versão Tabela** | UC15, UC17, UC20 | Atributo | ⭐⭐ | Versionamento das tabelas para auditoria |
| **Notificação** | UC17 | Classe | ⭐⭐ | Avisos sobre mudanças legislativas |
| **Arquivo Importação** | UC18 | Classe Auxiliar | ⭐ | Representa arquivo Excel/CSV - pode ser apenas serviço |
| **Validação** | UC19 | Serviço | ⭐ | Regras de validação - melhor como serviço que como classe |
| **Base Cálculo** | UC11, UC12, UC14 | Atributo | ⭐⭐ | Valor sobre o qual se aplica alíquota - pode ser atributo de Tributo |
| **Setor Econômico** | UC10 | Atributo | ⭐ | Derivado do CNAE - pode ser atributo de CNAE |
| **DAS** | UC11 | Classe | ⭐⭐ | Documento de Arrecadação do Simples Nacional |
| **Comparação** | UC16 | Classe | ⭐⭐ | Resultado da comparação entre regimes |
| **Base Legal** | UC20, UC21 | Atributo | ⭐ | Referência legislativa - atributo de TabelaTributaria |

---

## 2. TABELA DE VERBOS (Candidatos a Métodos/Operações)

| Verbo | Origem (UC) | Classe Candidata | Relevância | Descrição da Operação |
|-------|-------------|------------------|------------|----------------------|
| **criar** | UC10 | Simulacao | ⭐⭐⭐ | Criar nova simulação com dados iniciais |
| **calcular** | UC11, UC12, UC14 | Simulacao, RegimeTributario | ⭐⭐⭐ | Calcular tributos conforme regime selecionado |
| **validar** | UC10, UC19 | DadosFinanceiros, CNAE | ⭐⭐⭐ | Validar dados antes da simulação |
| **consultar** | UC17 | Empresa, CNAE | ⭐⭐⭐ | Consultar CNPJ na API da Receita Federal |
| **preencher** | UC10, UC17, UC18 | DadosFinanceiros | ⭐⭐ | Preencher formulário (manual ou automático) |
| **importar** | UC18 | DadosFinanceiros | ⭐⭐⭐ | Importar dados de arquivo Excel/CSV |
| **mapear** | UC18 | ArquivoImportacao | ⭐⭐ | Mapear colunas do arquivo para campos do sistema |
| **identificar** | UC11 | AnexoSimples, CNAE | ⭐⭐⭐ | Identificar anexo do Simples com base no CNAE |
| **aplicar** | UC11, UC12, UC14 | RegimeTributario | ⭐⭐⭐ | Aplicar alíquotas e regras tributárias |
| **calcular Fator R** | UC11 | Simulacao | ⭐⭐ | Calcular razão folha/receita para Simples |
| **calcular adicional IRPJ** | UC12, UC14 | Tributo | ⭐⭐ | Calcular adicional de 10% sobre base excedente |
| **calcular DAS** | UC11 | DAS | ⭐⭐ | Calcular valor do Documento de Arrecadação |
| **segregar tributos** | UC11 | DAS | ⭐⭐ | Segregar valor total do DAS por tributo |
| **ajustar base** | UC14 | AjusteFiscal | ⭐⭐ | Aplicar adições e exclusões fiscais |
| **compensar prejuízos** | UC14 | PrejuizoFiscal | ⭐⭐ | Compensar prejuízos fiscais (limite 30%) |
| **comparar regimes** | UC16 | Comparacao | ⭐⭐⭐ | Comparar resultados de 3 regimes |
| **identificar melhor regime** | UC16 | Comparacao | ⭐⭐ | Identificar regime com menor carga tributária |
| **calcular economia** | UC16 | Comparacao | ⭐⭐ | Calcular diferença entre regimes |
| **salvar** | UC15 | Simulacao | ⭐⭐⭐ | Salvar simulação no banco de dados |
| **atualizar** | UC15, UC20, UC21 | Simulacao, TabelaTributaria | ⭐⭐⭐ | Atualizar dados existentes |
| **versionar** | UC15 | Historico | ⭐⭐ | Criar nova versão da simulação |
| **exportar** | UC16 | Comparacao, Resultado | ⭐⭐ | Exportar resultados (PDF, Excel, PNG) |
| **visualizar** | UC13 | Resultado | ⭐⭐ | Exibir detalhamento de tributos |
| **expandir** | UC13 | Resultado | ⭐ | Expandir/recolher detalhamento |
| **atualizar tabelas** | UC20 | TabelaTributaria | ⭐⭐⭐ | Atualizar legislação tributária |
| **registrar histórico** | UC15, UC20, UC21 | Historico | ⭐⭐ | Registrar alterações no histórico |
| **notificar** | UC17 | Notificacao | ⭐⭐ | Notificar usuário sobre mudanças |
| **marcar desatualizada** | UC17 | Simulacao | ⭐⭐ | Marcar simulação impactada por mudança |
| **gerenciar alíquotas** | UC21 | AliquotaISS, AliquotaICMS | ⭐⭐⭐ | Cadastrar/editar alíquotas locais |
| **verificar vigência** | UC20, UC21 | TabelaTributaria, AliquotaISS | ⭐⭐ | Verificar se alíquota está vigente na data |
| **reutilizar dados** | UC16 | Simulacao | ⭐⭐ | Reutilizar simulações existentes para comparação |
| **projetar receita** | UC11, UC12 | DadosFinanceiros | ⭐⭐ | Projetar receita anual a partir de período |
| **verificar limite** | UC11, UC12, UC19 | RegimeTributario | ⭐⭐⭐ | Verificar se receita está dentro do limite do regime |
| **obter alíquota** | UC11, UC12 | TabelaTributaria | ⭐⭐⭐ | Obter alíquota aplicável por CNAE/anexo/faixa |
| **calcular base presumida** | UC12 | Simulacao | ⭐⭐ | Calcular base de cálculo pela presunção |
| **calcular lucro líquido** | UC14 | Simulacao | ⭐⭐ | Calcular lucro líquido contábil |
| **calcular créditos PIS/COFINS** | UC14 | Tributo | ⭐⭐ | Calcular créditos no regime não-cumulativo |
| **validar CNAE para Lucro Real** | UC10, UC14 | CNAE | ⭐⭐⭐ | Validar se CNAE é de prestação de serviços |
| **autocompletar** | UC10 | CNAE | ⭐ | Buscar CNAE com autocompletar |
| **preencher automaticamente** | UC17 | Empresa | ⭐⭐ | Preencher campos com dados da API |
| **editar** | UC15, UC20, UC21 | Simulacao, TabelaTributaria | ⭐⭐ | Editar dados existentes |
| **excluir** | UC21 | AliquotaISS, AliquotaICMS | ⭐⭐ | Marcar alíquota como inativa |
| **restaurar** | UC21 | AliquotaISS | ⭐ | Restaurar alíquota histórica |

---

## 3. ANÁLISE DE CANDIDATOS A CLASSES (Filtrados)

### Classes Centrais do Domínio
1. **Simulacao** - Entidade principal
2. **RegimeTributario** (pode ser herança: SimplesNacional, LucroPresumido, LucroReal)
3. **Tributo** (IRPJ, CSLL, PIS, COFINS, ISS, ICMS, CPP)
4. **Resultado** - Agrega tributos calculados
5. **DadosFinanceiros** - Value Object com receitas, custos, despesas

### Classes de Domínio Tributário
6. **CNAE** - Código de atividade econômica
7. **AnexoSimples** - Anexos I a V com faixas
8. **FaixaFaturamento** - Faixas progressivas do Simples
9. **AliquotaPresuncao** - Percentuais do Lucro Presumido
10. **TabelaTributaria** - Legislação versionada
11. **AliquotaISS** - Alíquotas municipais
12. **AliquotaICMS** - Alíquotas estaduais

### Classes de Apoio
13. **Empresa** - Dados cadastrais
14. **Municipio** - Localização
15. **UF** - Estado (pode ser enum)
16. **Cliente** - Cliente do escritório
17. **Usuario** - Usuário do sistema
18. **AjusteFiscal** - Adições/exclusões do Lucro Real
19. **PrejuizoFiscal** - Saldo de prejuízos

### Classes de Controle
20. **Comparacao** - Comparação entre regimes
21. **Historico** - Auditoria de alterações
22. **Notificacao** - Avisos ao usuário

### Serviços (não são classes de domínio)
- **ValidacaoService** - Validar dados
- **ImportacaoService** - Importar arquivos
- **ConsultaCNPJService** - Integração API Receita
- **CalculoTributarioService** - Orquestrar cálculos
- **ExportacaoService** - Exportar relatórios

---

## 4. CANDIDATOS A ATRIBUTOS (por Classe Principal)

### Simulacao
- id: Long
- nome: String
- descricao: String
- dataSimulacao: Date
- empresa: Empresa
- dadosFinanceiros: DadosFinanceiros
- regimeSelecionado: RegimeTributario
- resultado: Resultado
- versaoTabela: String
- status: StatusSimulacao (enum: rascunho, finalizada, desatualizada)
- cliente: Cliente
- usuario: Usuario

### DadosFinanceiros
- receitaBrutaPeriodo: BigDecimal
- receitaBruta12Meses: BigDecimal
- folhaPagamento12Meses: BigDecimal
- custosOperacionais: BigDecimal
- despesasOperacionais: BigDecimal
- outrasReceitas: BigDecimal
- outrasDespesas: BigDecimal

### Tributo
- tipo: TipoTributo (enum: IRPJ, CSLL, PIS, COFINS, ISS, ICMS, CPP)
- baseCalculo: BigDecimal
- aliquota: BigDecimal
- valor: BigDecimal
- creditos: BigDecimal (opcional, PIS/COFINS não-cumulativo)
- adicional: BigDecimal (opcional, IRPJ)

### Resultado
- simulacao: Simulacao
- tributos: List&lt;Tributo&gt;
- totalTributos: BigDecimal
- aliquotaEfetiva: BigDecimal
- observacoes: String

### CNAE
- codigo: String (formato: 9999-9/99)
- descricao: String
- setorEconomico: String
- anexoSimples: AnexoSimples
- aliquotaPresuncao: BigDecimal
- prestacaoServicos: boolean (para validação Lucro Real)

### TabelaTributaria
- id: Long
- tipo: TipoTabela (enum: SIMPLES_NACIONAL, PRESUNCAO, IRPJ_CSLL, PIS_COFINS)
- versao: String
- dataVigencia: Date
- baseLegal: String
- conteudo: JSON/BLOB
- usuarioAtualizacao: Usuario
- dataAtualizacao: Date

### AliquotaISS
- id: Long
- municipio: Municipio
- aliquota: BigDecimal
- dataVigenciaInicio: Date
- dataVigenciaFim: Date
- baseLegal: String
- ativa: boolean

### AliquotaICMS
- id: Long
- uf: UF
- aliquotaInterna: BigDecimal
- aliquotaInterestadual: BigDecimal
- dataVigenciaInicio: Date
- dataVigenciaFim: Date
- baseLegal: String
- ativa: boolean

---

## 5. RELACIONAMENTOS IDENTIFICADOS

| Classe A | Relacionamento | Classe B | Cardinalidade |
|----------|----------------|----------|---------------|
| Simulacao | possui | DadosFinanceiros | 1:1 |
| Simulacao | gera | Resultado | 1:1 |
| Simulacao | usa | RegimeTributario | 1:1 |
| Simulacao | pertence a | Cliente | N:1 |
| Simulacao | criada por | Usuario | N:1 |
| Simulacao | usa versão de | TabelaTributaria | N:1 |
| Resultado | contém | Tributo | 1:N |
| CNAE | determina | AnexoSimples | N:1 |
| CNAE | determina | AliquotaPresuncao | N:1 |
| AnexoSimples | possui | FaixaFaturamento | 1:N |
| Empresa | possui | CNAE | N:1 |
| Empresa | localizada em | Municipio | N:1 |
| Municipio | pertence a | UF | N:1 |
| Municipio | possui | AliquotaISS | 1:N (histórico) |
| UF | possui | AliquotaICMS | 1:N (histórico) |
| Comparacao | compara | Simulacao | 1:3 |
| Simulacao | possui | Historico | 1:N |
| TabelaTributaria | possui | Historico | 1:N |
| Notificacao | referencia | Simulacao | N:N |
| AjusteFiscal | pertence a | Simulacao | N:1 |
| PrejuizoFiscal | pertence a | Empresa | N:1 |

---

## 6. OBSERVAÇÕES PARA MODELAGEM

### Padrões Sugeridos
1. **Strategy Pattern** para `RegimeTributario` (SimplesNacional, LucroPresumido, LucroReal com algoritmos diferentes)
2. **Factory Pattern** para criar instâncias de Tributo
3. **Value Objects** para DadosFinanceiros, Endereco
4. **Repository Pattern** para persistência
5. **Service Layer** para operações complexas (cálculos, importação, validação)

### Enumerações Identificadas
- `TipoRegime`: SIMPLES_NACIONAL, LUCRO_PRESUMIDO, LUCRO_REAL
- `TipoTributo`: IRPJ, CSLL, PIS, COFINS, ISS, ICMS, CPP
- `TipoAnexoSimples`: I, II, III, IV, V
- `StatusSimulacao`: RASCUNHO, FINALIZADA, DESATUALIZADA
- `TipoUsuario`: CONTADOR, GERENTE, ADMINISTRADOR
- `TipoTabela`: SIMPLES_NACIONAL, PRESUNCAO, IRPJ_CSLL, PIS_COFINS
- `UF`: AC, AL, AM, ... (27 estados)

### Validações Críticas (para implementar)
- CNAE obrigatório para todos os regimes
- CNAE de prestação de serviços obrigatório para Lucro Real
- Limites de faturamento por regime (Simples ≤ 4.8M, Presumido ≤ 78M)
- Valores numéricos positivos
- Alíquotas entre 0-100%
- Folha obrigatória quando Fator R aplicável

### Regras de Negócio Importantes
- Versionamento de tabelas tributárias
- Histórico completo de alterações
- Simulações preservam valores mesmo após atualização de tabelas
- Marcação de simulações desatualizadas
- Limite de 30% para compensação de prejuízos (Lucro Real)
- Fator R: Folha/Receita >= 28% → Anexo III, senão Anexo V
