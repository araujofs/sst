<table>
  <tbody>
    <tr>
      <td><strong>Caso de uso</strong></td>
      <td><strong>UCxxx - Gerar Relatório Comparativo</strong></td>
    </tr>
    <tr>
      <td><strong>Objetivo</strong></td>
      <td>Permitir que o contador compare múltiplas simulações por meio de gráficos e gere relatórios personalizados para clientes.</td>
    </tr>
    <tr>
      <td><strong>Requisitos</strong></td>
      <td>RF-REL-002, RF-REL-003</td>
    </tr>
    <tr>
      <td><strong>Atores</strong></td>
      <td>Contador</td>
    </tr>
    <tr>
      <td><strong>Condições de entrada</strong></td>
      <td>O ator está no histórico de simulações e selecionou pelo menos duas simulações.</td>
    </tr>
    <tr>
      <td><strong>Fluxo principal</strong></td>
      <td>
        <ol>
          <li>O ator seleciona duas ou três simulações no histórico.</li>
          <li>O ator clica no botão "Comparar".</li>
          <li>O sistema exibe a tela de comparação com gráficos e tabela detalhada.</li>
          <li>O ator personaliza o relatório (logo, observações, gráficos e formato).</li>
          <li>O ator clica em "Gerar Relatório".</li>
          <li>O sistema processa e exibe o relatório formatado.</li>
          <li>O ator faz o download do relatório em PDF.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos alternativos</strong></td>
      <td>
        <strong>A1 – Comparar apenas 2 simulações</strong>
        <ol>
          <li>O ator seleciona duas simulações.</li>
          <li>O sistema destaca a economia percentual entre elas.</li>
        </ol>

  <strong>A2 – Gerar relatório sem personalização</strong>
        <ol>
          <li>O ator ignora a etapa de personalização.</li>
          <li>O sistema gera o relatório padrão.</li>
        </ol>

  <strong>A3 – Enviar relatório por e-mail</strong>
        <ol>
          <li>O ator clica em "Enviar por E-mail".</li>
          <li>Informa o destinatário.</li>
          <li>O sistema envia o relatório em anexo.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos de exceção</strong></td>
      <td>
        <strong>EX1 – Seleção acima do limite</strong><br>
        O sistema alerta que é permitido comparar no máximo três simulações.
      </td>
    </tr>
  </tbody>
</table>
