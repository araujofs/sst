<table>
  <tbody>
    <tr>
      <td><strong>Caso de uso</strong></td>
      <td>
        <strong><span><a>UC14 - Validar Dados Financeiros</a></span></strong>
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
      <td>O usuário preencheu os dados financeiros em <a href="../calculo/especificacao_criar_simulacao.md">[UC5]</a> e clicou em "Simular".</td>
    </tr>
    <tr>
      <td><strong>Fluxo principal</strong></td>
      <td>
        <ol>
          <li>O sistema recebe os dados financeiros informados pelo usuário.</li>
          <li>O sistema valida campos obrigatórios. <a href="#rn1">[RN1]</a></li>
          <li>O sistema valida tipos de dados (valores numéricos positivos).</li>
          <li>O sistema verifica limites de enquadramento por regime. <a href="#rn2">[RN2]</a></li>
          <li>Se todas as validações passarem, o sistema prossegue com o cálculo tributário.</li>
          <li>Se houver erros, o sistema bloqueia a simulação e exibe lista de erros. <a href="#e1">[E1]</a></li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos alternativos</strong></td>
      <td>
        N/A
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos de exceção</strong></td>
      <td>
        <a id="e1">[E1] - Dados inválidos</a>
        <ol>
          <li>No passo 6, o sistema identifica erros de validação.</li>
          <li>O sistema exibe mensagem com lista de erros encontrados.</li>
          <li>O sistema bloqueia o botão "Simular" até que os erros sejam corrigidos.</li>
          <li>O usuário corrige os dados no formulário.</li>
          <li>Retorna ao passo 1.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Regras de negócio</strong></td>
      <td>
        <a id="rn1">[RN1] - Campos obrigatórios por regime</a><br>
        <ul>
          <li><strong>Todos os regimes:</strong> CNAE, Receita Bruta do Período</li>
          <li><strong>Simples Nacional:</strong> RBT12 (Receita Bruta 12 meses)</li>
          <li><strong>Simples Nacional com Fator R:</strong> Folha de Pagamento 12 meses</li>
          <li><strong>Lucro Real:</strong> Custos e Despesas Operacionais</li>
        </ul>
        Valores financeiros devem ser numéricos e não negativos.<br><br>
        <a id="rn2">[RN2] - Limites de enquadramento</a><br>
        <ul>
          <li><strong>Simples Nacional:</strong> RBT12 ≤ R$ 4.800.000,00</li>
          <li><strong>Lucro Presumido:</strong> Receita anual ≤ R$ 78.000.000,00</li>
        </ul>
        Violações dessas regras bloqueiam a simulação.
      </td>
    </tr>
  </tbody>
</table>
