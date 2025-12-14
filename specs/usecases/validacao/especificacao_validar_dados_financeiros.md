<table>
  <tbody>
    <tr>
      <td><strong>Caso de uso</strong></td>
      <td>
        <strong><span><a>UC19 - Validar Dados Financeiros</a></span></strong>
      </td>
    </tr>
    <tr>
      <td><strong>Objetivo</strong></td>
      <td>
        Validar automaticamente os dados financeiros inseridos pelo usuário antes de processar uma simulação tributária, identificando erros, inconsistências e valores atípicos.
      </td>
    </tr>
    <tr>
      <td><strong>Requisitos</strong></td>
      <td>RF-CAL-008</td>
    </tr>
    <tr>
      <td><strong>Atores</strong></td>
      <td>Sistema (automático), Contador, Gerente</td>
    </tr>
    <tr>
      <td><strong>Condições de entrada</strong></td>
      <td>O usuário preencheu os dados financeiros em <a href="../calculo/especificacao_criar_simulacao.md">[UC10]</a> e clicou em "Simular".</td>
    </tr>
    <tr>
      <td><strong>Fluxo principal</strong></td>
      <td>
        <ol>
          <li>O sistema recebe os dados financeiros informados pelo usuário.</li>
          <li>O sistema executa validações estruturais. <a href="#rn1">[RN1]</a>
            <ul>
              <li>Verifica se campos obrigatórios estão preenchidos</li>
              <li>Verifica se valores são numéricos</li>
              <li>Verifica se valores não são negativos</li>
            </ul>
          </li>
          <li>O sistema executa validações de negócio. <a href="#rn2">[RN2]</a>
            <ul>
              <li>Verifica limites de faturamento por regime</li>
              <li>Verifica coerência entre receitas e despesas</li>
              <li>Verifica se Fator R é consistente (folha vs receita)</li>
            </ul>
          </li>
          <li>O sistema executa validações de consistência. <a href="#rn3">[RN3]</a>
            <ul>
              <li>Identifica valores atípicos (outliers)</li>
              <li>Verifica proporções esperadas (ex: folha/receita)</li>
              <li>Compara com histórico do mesmo cliente (se disponível)</li>
            </ul>
          </li>
          <li>Se todas as validações passarem:
            <ul>
              <li>O sistema marca os dados como "válidos"</li>
              <li>O sistema prossegue com o cálculo tributário</li>
              <li>O caso de uso é concluído com sucesso</li>
            </ul>
          </li>
          <li>Se houver erros críticos, o sistema bloqueia a simulação. <a href="#e1">[E1]</a></li>
          <li>Se houver apenas alertas não-críticos, o sistema exibe avisos. <a href="#a1">[A1]</a></li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos alternativos</strong></td>
      <td>
        <a id="a1">[A1] - Alertas não-críticos (usuário pode prosseguir)</a>
        <ol>
          <li>No passo 7, o sistema identifica situações que merecem atenção mas não impedem o cálculo:
            <ul>
              <li>Valores atípicos (ex: faturamento 300% maior que a média histórica)</li>
              <li>Proporções incomuns (ex: folha de pagamento > 80% da receita)</li>
              <li>Possível inelegibilidade futura (ex: Simples com receita próxima ao limite)</li>
            </ul>
          </li>
          <li>O sistema exibe modal de alertas com ícone amarelo de atenção:
            <ul>
              <li>Lista todos os alertas encontrados</li>
              <li>Explica o motivo de cada alerta</li>
              <li>Oferece sugestões de correção</li>
            </ul>
          </li>
          <li>O sistema oferece opções:
            <ul>
              <li>"Revisar dados" - retorna ao formulário</li>
              <li>"Prosseguir mesmo assim" - continua a simulação</li>
              <li>"Salvar como rascunho" - salva sem calcular</li>
            </ul>
          </li>
          <li>Se o usuário escolher "Prosseguir", o sistema:
            <ul>
              <li>Registra que a simulação foi feita com alertas</li>
              <li>Adiciona observação nos resultados</li>
              <li>Prossegue para o passo 5 do fluxo principal</li>
            </ul>
          </li>
        </ol>
        <a id="a2">[A2] - Validação em tempo real no formulário</a>
        <ol>
          <li>Durante o preenchimento do formulário (antes do passo 1), o sistema valida campos individualmente.</li>
          <li>A cada campo preenchido (evento onBlur ou onChange):
            <ul>
              <li>O sistema valida o valor imediatamente</li>
              <li>Se inválido, exibe mensagem de erro abaixo do campo</li>
              <li>Se válido, exibe ícone verde de confirmação</li>
            </ul>
          </li>
          <li>Isso reduz erros ao final, facilitando a correção progressiva.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos de exceção</strong></td>
      <td>
        <a id="e1">[E1] - Erros críticos (bloqueiam simulação)</a>
        <ol>
          <li>No passo 6, o sistema identifica erros que impedem o cálculo:
            <ul>
              <li><strong>Campos obrigatórios vazios:</strong> "Receita Bruta é obrigatória"</li>
              <li><strong>Valores negativos:</strong> "Receita não pode ser negativa"</li>
              <li><strong>Valores inválidos:</strong> "Campo deve conter apenas números"</li>
              <li><strong>Faturamento acima do limite:</strong> "Receita de R$ 5M excede limite do Simples Nacional (R$ 4.8M)"</li>
              <li><strong>Inconsistências matemáticas:</strong> "Lucro informado não corresponde a Receita - Despesas"</li>
            </ul>
          </li>
          <li>O sistema exibe modal de erro com ícone vermelho:
            <ul>
              <li>Título: "Não foi possível processar a simulação"</li>
              <li>Lista todos os erros encontrados</li>
              <li>Para cada erro, indica o campo específico</li>
            </ul>
          </li>
          <li>O sistema NÃO permite prosseguir até que os erros sejam corrigidos.</li>
          <li>O usuário clica em "Corrigir Dados".</li>
          <li>O sistema retorna ao formulário destacando os campos com erro em vermelho.</li>
          <li>O usuário corrige os erros e tenta novamente.</li>
          <li>Retorna ao passo 1 do fluxo principal.</li>
        </ol>
        <a id="e2">[E2] - Erro de sistema durante validação</a>
        <ol>
          <li>Durante os passos 2-4, ocorre erro inesperado no sistema de validação.</li>
          <li>O sistema registra o erro no log.</li>
          <li>O sistema exibe mensagem genérica: "Erro ao validar dados. Tente novamente."</li>
          <li>Se o erro persistir, o sistema permite que o usuário "Force Prosseguir" (com aviso de risco).</li>
          <li>O sistema notifica o administrador sobre o erro de validação.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Regras de negócio</strong></td>
      <td>
        <a id="rn1">[RN1] - Validações estruturais (obrigatórias)</a><br>
        <strong>Campos obrigatórios por regime:</strong>
        <ul>
          <li><strong>Todos os regimes:</strong> CNAE, Receita Bruta do Período</li>
          <li><strong>Simples Nacional:</strong> RBT12 (Receita Bruta 12 meses)</li>
          <li><strong>Simples Nacional com Fator R:</strong> Folha de Pagamento 12 meses</li>
          <li><strong>Lucro Real:</strong> Custos e Despesas Operacionais</li>
        </ul>
        <strong>Tipos de dados:</strong>
        <ul>
          <li>Valores financeiros: numéricos, não negativos, até 2 casas decimais</li>
          <li>Porcentagens: 0-100%</li>
          <li>CNPJ: 14 dígitos numéricos (se informado)</li>
        </ul><br>
        <a id="rn2">[RN2] - Validações de negócio (bloqueantes)</a><br>
        <ul>
          <li><strong>Simples Nacional:</strong> RBT12 ≤ R$ 4.800.000,00</li>
          <li><strong>Lucro Presumido:</strong> Receita anual ≤ R$ 78.000.000,00</li>
          <li><strong>Lucro Real:</strong> Se Receita > Custos + Despesas, deve haver lucro (coerência)</li>
          <li><strong>Fator R:</strong> Folha de Pagamento / RBT12 deve estar entre 0% e 100%</li>
        </ul>
        Violações dessas regras BLOQUEIAM a simulação.<br><br>
        <a id="rn3">[RN3] - Validações de consistência (alertas)</a><br>
        <strong>Valores atípicos:</strong>
        <ul>
          <li>Faturamento 200%+ maior que a média histórica do cliente</li>
          <li>Folha de pagamento > 70% da receita (incomum)</li>
          <li>Despesas > 95% da receita (margem muito baixa)</li>
          <li>Receita mensal muito próxima ao limite do Simples (risco de desenquadramento)</li>
        </ul>
        <strong>Proporções esperadas por setor:</strong>
        <ul>
          <li><strong>Comércio:</strong> Margem bruta esperada 20-40%</li>
          <li><strong>Serviços:</strong> Folha/Receita esperada 30-50%</li>
          <li><strong>Indústria:</strong> Custos de produção 50-70% da receita</li>
        </ul>
        Desvios significativos geram alertas (não bloqueiam).<br><br>
        <a id="rn4">[RN4] - Comparação com histórico</a><br>
        Se o cliente já possui simulações anteriores salvas:
        <ul>
          <li>O sistema compara os valores atuais com os históricos</li>
          <li>Se houver variação > 50%, exibe alerta: "Receita [aumentou/diminuiu] [X]% em relação à última simulação"</li>
          <li>Sugere revisar dados ou confirmar mudança real no negócio</li>
        </ul><br>
        <a id="rn5">[RN5] - Níveis de validação</a><br>
        <ul>
          <li><strong>ERRO (vermelho):</strong> Bloqueia simulação, correção obrigatória</li>
          <li><strong>AVISO (amarelo):</strong> Permite prosseguir após confirmação do usuário</li>
          <li><strong>INFO (azul):</strong> Informativo, não requer ação</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>
