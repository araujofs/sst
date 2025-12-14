<table>
  <tbody>
    <tr>
      <td><strong>Caso de uso</strong></td>
      <td>
        <strong><span><a>UC12 - Atualizar Tabelas Tributárias</a></span></strong>
      </td>
    </tr>
    <tr>
      <td><strong>Objetivo</strong></td>
      <td>
        Atualizar tabelas tributárias (Simples Nacional, alíquotas de presunção, IRPJ/CSLL, PIS/COFINS) conforme mudanças na legislação.
      </td>
    </tr>
    <tr>
      <td><strong>Requisitos</strong></td>
      <td>RF-LEG-001, RF-LEG-002</td>
    </tr>
    <tr>
      <td><strong>Atores</strong></td>
      <td>Administrador</td>
    </tr>
    <tr>
      <td><strong>Condições de entrada</strong></td>
      <td>O administrador recebeu notificação de atualização na legislação tributária (Receita Federal) ou identificou necessidade de correção.</td>
    </tr>
    <tr>
      <td><strong>Fluxo principal</strong></td>
      <td>
        <ol>
          <li>O administrador acessa "Administração > Legislação > Tabelas Tributárias".</li>
          <li>O sistema exibe lista de tabelas disponíveis.</li>
          <li>O administrador clica em "Atualizar" na tabela desejada.</li>
          <li>O administrador importa arquivo (.xlsx ou .csv) ou edita manualmente. <a href="#a1">[A1]</a></li>
          <li>O sistema valida estrutura e dados. <a href="#e1">[E1]</a></li>
          <li>O sistema solicita data de vigência e base legal (número da lei/resolução).</li>
          <li>O administrador preenche e confirma.</li>
          <li>O sistema atualiza a tabela no banco de dados.</li>
          <li>O sistema registra a atualização no histórico com data, usuário e base legal.</li>
          <li>O sistema dispara notificação visual sobre mudança legislativa. (<<include>> <a href="../calculo/especificacao_notificar_impacto_legislativo.md">[UC17]</a>)</li>
          <li>O sistema exibe mensagem de sucesso.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos alternativos</strong></td>
      <td>
        <a id="a1">[A1] - Editar manualmente</a>
        <ol>
          <li>No passo 4, o administrador seleciona "Editar manualmente".</li>
          <li>O sistema exibe formulário com os dados atuais em campos editáveis.</li>
          <li>O administrador altera os valores necessários.</li>
          <li>Retorna ao passo 6 do fluxo principal.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos de exceção</strong></td>
      <td>
        <a id="e1">[E1] - Dados inválidos</a>
        <ol>
          <li>No passo 5, o sistema identifica erros (formato inválido, alíquotas fora do intervalo 0-100%, valores negativos).</li>
          <li>O sistema exibe lista de erros encontrados.</li>
          <li>O administrador corrige os erros.</li>
          <li>Retorna ao passo 5.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Regras de negócio</strong></td>
      <td>
        <a id="rn1">[RN1] - Validações</a><br>
        <ul>
          <li>Alíquotas devem estar entre 0-100%</li>
          <li>Valores devem ser numéricos e não negativos</li>
          <li>Data de vigência deve ser futura ou atual</li>
          <li>Base legal é obrigatória para auditoria</li>
        </ul><br>
        <a id="rn2">[RN2] - Rastreabilidade</a><br>
        Toda atualização deve ser registrada no histórico com data, usuário e base legal.
      </td>
    </tr>
  </tbody>
</table>
