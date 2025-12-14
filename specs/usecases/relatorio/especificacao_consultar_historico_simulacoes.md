<table>
  <tbody>
    <tr>
      <td><strong>Caso de uso</strong></td>
      <td><strong>UC22 - Consultar Histórico de Simulações</strong></td>
    </tr>
    <tr>
      <td><strong>Objetivo</strong></td>
      <td>Permitir que o contador acesse, filtre e visualize seu histórico completo de simulações tributárias realizadas.</td>
    </tr>
    <tr>
      <td><strong>Requisitos</strong></td>
      <td>RF-REL-001</td>
    </tr>
    <tr>
      <td><strong>Atores</strong></td>
      <td>Contador, Gerente</td>
    </tr>
    <tr>
      <td><strong>Condições de entrada</strong></td>
      <td>O ator está autenticado no sistema e seleciona "Histórico de Simulações" no menu principal ou no dashboard.</td>
    </tr>
    <tr>
      <td><strong>Fluxo principal</strong></td>
      <td>
        <ol>
          <li>O ator acessa a página de histórico de simulações e visualiza a lista com colunas de data, cliente, regime, carga tributária, status e ações.</li>
          <li>O ator visualiza os filtros: cliente, período, regime tributário e botão "Aplicar Filtros".</li>
          <li>Seleciona um cliente e define o período dos últimos 30 dias.</li>
          <li>Clica em "Aplicar Filtros".</li>
          <li>O sistema atualiza a lista conforme os critérios.</li>
          <li>O ator clica em "Visualizar" em uma simulação.</li>
          <li>O sistema exibe os detalhes completos da simulação.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos alternativos</strong></td>
      <td>
        <strong>A1 – Limpar filtros</strong>
        <ol>
          <li>O ator clica em "Limpar Filtros".</li>
          <li>O sistema exibe todas as simulações.</li>
        </ol>
        <strong>A2 – Buscar por nome do cliente</strong>
        <ol>
          <li>O ator digita parte do nome do cliente.</li>
          <li>O sistema filtra em tempo real.</li>
        </ol>
        <strong>A3 – Ordenar lista</strong>
        <ol>
          <li>O ator clica no cabeçalho de uma coluna.</li>
          <li>O sistema ordena a lista.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos de exceção</strong></td>
      <td>
        <strong>EX1 – Nenhuma simulação encontrada</strong><br>
        O sistema exibe a mensagem informativa de ausência de resultados.
      </td>
    </tr>
  </tbody>
</table>
