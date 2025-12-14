<table>
  <tbody>
    <tr>
      <td><strong>Caso de uso</strong></td>
      <td>
        <strong><span><a>UC18 - Importar Dados Financeiros</a></span></strong>
      </td>
    </tr>
    <tr>
      <td><strong>Objetivo</strong></td>
      <td>
        Importar dados financeiros de arquivos Excel ou CSV para preencher automaticamente o formulário de simulação.
      </td>
    </tr>
    <tr>
      <td><strong>Requisitos</strong></td>
      <td>RF-IMP-002</td>
    </tr>
    <tr>
      <td><strong>Atores</strong></td>
      <td>Contador, Gerente</td>
    </tr>
    <tr>
      <td><strong>Condições de entrada</strong></td>
      <td>O ator está preenchendo uma simulação e deseja importar dados financeiros de um arquivo.</td>
    </tr>
    <tr>
      <td><strong>Fluxo principal</strong></td>
      <td>
        <ol>
          <li>O ator clica no botão "Importar Dados".</li>
          <li>O ator seleciona arquivo Excel (.xlsx) ou CSV (.csv) no seu computador.</li>
          <li>O sistema faz upload do arquivo.</li>
          <li>O sistema valida formato e estrutura. <a href="#e1">[E1]</a></li>
          <li>O sistema extrai dados do arquivo e valida valores. <a href="#e2">[E2]</a></li>
          <li>O sistema preenche automaticamente os campos do formulário.</li>
          <li>O sistema exibe mensagem de sucesso.</li>
          <li>O ator pode revisar e ajustar os dados antes de simular.</li>
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
        <a id="e1">[E1] - Formato inválido</a>
        <ol>
          <li>No passo 4, o sistema identifica formato incompatível.</li>
          <li>O sistema exibe mensagem de erro.</li>
          <li>Retorna ao passo 2.</li>
        </ol>
        <a id="e2">[E2] - Dados inválidos</a>
        <ol>
          <li>No passo 5, o sistema identifica valores negativos ou não numéricos.</li>
          <li>O sistema exibe lista de erros.</li>
          <li>Retorna ao passo 2.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Regras de negócio</strong></td>
      <td>
        <a id="rn1">[RN1] - Validações</a><br>
        <ul>
          <li>Formatos aceitos: .xlsx e .csv</li>
          <li>Valores numéricos devem ser positivos</li>
          <li>Receita Bruta é campo obrigatório</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>
