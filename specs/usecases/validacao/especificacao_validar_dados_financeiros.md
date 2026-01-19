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
        Validar dados financeiros antes da simulação, verificando campos obrigatórios e limites de enquadramento por regime.
      </td>
    </tr>
    <tr>
      <td><strong>Requisitos</strong></td>
      <td>RF-CAL-006</td>
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
          <li>O sistema valida campos obrigatórios por regime. <a href="#rn1">[RN1]</a> <a href="#e2">[E2]</a></li>
          <li>O sistema valida tipos de dados (valores numéricos positivos). <a href="#e3">[E3]</a></li>
          <li>O sistema valida se o CNAE é válido e está mapeado no sistema. <a href="#e4">[E4]</a></li>
          <li>O sistema verifica limites de enquadramento por regime. <a href="#rn2">[RN2]</a> <a href="#e5">[E5]</a></li>
          <li>Se todas as validações passarem, o sistema prossegue com o cálculo tributário.</li>
          <li>Se houver erros, o sistema bloqueia a simulação e exibe lista de erros. <a href="#e1">[E1]</a></li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos alternativos</strong></td>
      <td>
        <a id="a1">[A1] - Validação em tempo real (progressiva)</a>
        <ol>
          <li>Antes do passo 1, o sistema pode validar campos à medida que o usuário preenche (opcional, melhoria de UX).</li>
          <li>O sistema exibe ícones de status ao lado de cada campo:
            <ul>
              <li>✓ Verde: campo válido</li>
              <li>⚠ Amarelo: campo com aviso (ex: valor muito alto)</li>
              <li>✗ Vermelho: campo inválido</li>
            </ul>
          </li>
          <li>O sistema exibe mensagens de erro inline, logo abaixo de cada campo inválido.</li>
          <li>O botão "Simular" permanece desabilitado enquanto houver erros.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos de exceção</strong></td>
      <td>
        <a id="e1">[E1] - Dados inválidos (genérico)</a>
        <ol>
          <li>No passo 7, o sistema identifica um ou mais erros de validação.</li>
          <li>O sistema exibe mensagem com lista de erros encontrados agrupados por tipo.</li>
          <li>O sistema bloqueia o botão "Simular" até que os erros sejam corrigidos.</li>
          <li>O usuário corrige os dados no formulário.</li>
          <li>Retorna ao passo 1.</li>
        </ol>
        <a id="e2">[E2] - Campo obrigatório não preenchido</a>
        <ol>
          <li>No passo 2, o sistema identifica que um campo obrigatório está vazio.</li>
          <li>O sistema exibe mensagem: "Campo obrigatório: [nome do campo] deve ser preenchido."</li>
          <li>O sistema destaca o campo em vermelho.</li>
          <li>Exemplos por regime:
            <ul>
              <li><strong>Simples Nacional:</strong> "RBT12 é obrigatório para calcular o Simples Nacional"</li>
              <li><strong>Simples Nacional com Fator R:</strong> "Folha de Pagamento é obrigatória para calcular o Fator R"</li>
              <li><strong>Lucro Real:</strong> "Custos e Despesas são obrigatórios para calcular o Lucro Real"</li>
            </ul>
          </li>
          <li>Retorna ao formulário para correção.</li>
        </ol>
        <a id="e3">[E3] - Valor inválido (não numérico ou negativo)</a>
        <ol>
          <li>No passo 3, o sistema identifica valor não numérico ou negativo em campo financeiro.</li>
          <li>O sistema exibe mensagem: "[Campo]: valor deve ser numérico e não negativo."</li>
          <li>O sistema destaca o campo em vermelho.</li>
          <li>Retorna ao formulário para correção.</li>
        </ol>
        <a id="e4">[E4] - CNAE inválido ou não mapeado</a>
        <ol>
          <li>No passo 4, o sistema valida o CNAE informado.</li>
          <li>O sistema identifica que o CNAE:
            <ul>
              <li>É inválido (não existe na tabela oficial), OU</li>
              <li>Não está mapeado no sistema para o regime selecionado</li>
            </ul>
          </li>
          <li>O sistema exibe mensagem de erro específica (igual ao <a href="../calculo/especificacao_criar_simulacao.md">[UC10 - E3]</a>).</li>
          <li>O sistema bloqueia a simulação.</li>
          <li>Retorna ao formulário para correção.</li>
        </ol>
        <a id="e5">[E5] - Limite de enquadramento excedido</a>
        <ol>
          <li>No passo 5, o sistema identifica que os valores informados excedem os limites do regime.</li>
          <li>O sistema exibe alerta específico:
            <ul>
              <li><strong>Simples Nacional:</strong> "RBT12 de R$ [valor] excede o limite de R$ 4.800.000,00"</li>
              <li><strong>Lucro Presumido:</strong> "Receita anual projetada de R$ [valor] excede o limite de R$ 78.000.000,00"</li>
            </ul>
          </li>
          <li>O sistema sugere regime alternativo compatível.</li>
          <li>O sistema bloqueia a simulação no regime atual.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Regras de negócio</strong></td>
      <td>
        <a id="rn1">[RN1] - Campos obrigatórios por regime</a><br>
        <ul>
          <li><strong>Todos os regimes:</strong> CNAE (obrigatório), Receita Bruta do Período</li>
          <li><strong>Simples Nacional:</strong> RBT12 (Receita Bruta 12 meses), CNAE válido para identificação do anexo</li>
          <li><strong>Simples Nacional com Fator R:</strong> Folha de Pagamento 12 meses</li>
          <li><strong>Lucro Presumido:</strong> CNAE válido para determinação das alíquotas de presunção</li>
          <li><strong>Lucro Real:</strong> Custos e Despesas Operacionais, CNAE válido (somente atividades de prestação de serviços)</li>
        </ul>
        O campo CNAE é obrigatório para todos os regimes pois é fundamental para determinar alíquotas, anexos e elegibilidade. Para o regime Lucro Real, o CNAE deve corresponder <strong>exclusivamente a atividades de prestação de serviços</strong>, uma vez que o sistema não contempla a complexidade de cálculos para atividades comerciais, industriais ou de transporte. Valores financeiros devem ser numéricos e não negativos.<br><br>
        <a id="rn2">[RN2] - Limites de enquadramento</a><br>
        <ul>
          <li><strong>Simples Nacional:</strong> RBT12 ≤ R$ 4.800.000,00</li>
          <li><strong>Lucro Presumido:</strong> Receita anual ≤ R$ 78.000.000,00</li>
        </ul>
        Violações dessas regras bloqueiam a simulação.<br><br>
        <a id="rn3">[RN3] - Validação de CNAE</a><br>
        O sistema deve validar o CNAE em dois níveis:
        <ol>
          <li><strong>Validade:</strong> Verifica se o código CNAE existe na tabela oficial (IBGE/Receita Federal)</li>
          <li><strong>Mapeamento:</strong> Verifica se o CNAE está cadastrado no sistema com mapeamento para:
            <ul>
              <li><strong>Simples Nacional:</strong> Anexo (I, II, III, IV ou V)</li>
              <li><strong>Lucro Presumido:</strong> Alíquota de presunção (8%, 16% ou 32%)</li>
              <li><strong>Lucro Real:</strong> Tipo de atividade (exclusivamente prestação de serviços). CNAEs de comércio, indústria, transporte de cargas e outras atividades que não sejam serviços são incompatíveis com este regime no sistema.</li>
            </ul>
          </li>
        </ol>
        Se o CNAE for válido mas não mapeado, o sistema deve solicitar cadastro via suporte. Para o Lucro Real, se o CNAE corresponder a atividade que não seja prestação de serviços, o sistema deve bloquear a simulação e orientar o uso de outros regimes.
      </td>
    </tr>
  </tbody>
</table>
