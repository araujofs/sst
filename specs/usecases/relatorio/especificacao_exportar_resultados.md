<table>
  <tbody>
    <tr>
      <td><strong>Caso de uso</strong></td>
      <td><strong>UCxxx- Exportar Resultados</strong></td>
    </tr>
    <tr>
      <td><strong>Objetivo</strong></td>
      <td>Permitir que contador ou gerente exporte resultados de simulações em diferentes formatos para compartilhamento ou arquivamento.</td>
    </tr>
    <tr>
      <td><strong>Requisitos</strong></td>
      <td>RF-CAL-007</td>
    </tr>
    <tr>
      <td><strong>Atores</strong></td>
      <td>Contador, Gerente</td>
    </tr>
    <tr>
      <td><strong>Condições de entrada</strong></td>
      <td>O ator está visualizando uma simulação específica ou a lista de simulações.</td>
    </tr>
    <tr>
      <td><strong>Fluxo principal</strong></td>
      <td>
        <ol>
          <li>O ator visualiza os detalhes de uma simulação concluída.</li>
          <li>O ator clica no botão "Exportar".</li>
          <li>O sistema exibe um modal com opções de formato, conteúdo e itens inclusos.</li>
          <li>O ator seleciona formato Excel detalhado, conteúdo resultados + cálculos e inclui gráficos.</li>
          <li>O ator clica em "Gerar Exportação".</li>
          <li>O sistema processa e informa que o arquivo está pronto.</li>
          <li>O ator realiza o download do arquivo.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos alternativos</strong></td>
      <td>
        <strong>A1 – Exportar múltiplas simulações</strong>
        <ol>
          <li>O ator seleciona várias simulações no histórico.</li>
          <li>Clica em "Exportar Selecionadas".</li>
          <li>O sistema gera um arquivo ZIP.</li>
        </ol>
        <strong>A2 – Exportar para CSV simples</strong>
        <ol>
          <li>O ator seleciona o formato CSV.</li>
          <li>O sistema gera arquivo com dados brutos.</li>
        </ol>
        <strong>A3 – Agendar exportação recorrente</strong>
        <ol>
          <li>O ator escolhe "Agendar Exportação".</li>
          <li>Configura periodicidade.</li>
          <li>O sistema envia automaticamente por e-mail.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos de exceção</strong></td>
      <td>
        <strong>EX1 – Simulação muito grande</strong><br>
        O sistema alerta que a simulação é grande demais para Excel e recomenda CSV.
      </td>
    </tr>
  </tbody>
</table>
