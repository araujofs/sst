<table>
  <tbody>
    <tr>
      <td><strong>Caso de uso</strong></td>
      <td>
        <strong><span><a>UC13 - Visualizar Detalhamento de Tributos</a></span></strong>
      </td>
    </tr>
    <tr>
      <td><strong>Objetivo</strong></td>
      <td>
        Permitir que o contador ou gerente visualize o detalhamento completo de cada tributo calculado na simulação.
      </td>
    </tr>
    <tr>
      <td><strong>Requisitos</strong></td>
      <td>RF-CAL-003</td>
    </tr>
    <tr>
      <td><strong>Atores</strong></td>
      <td>Contador, Gerente</td>
    </tr>
    <tr>
      <td><strong>Condições de entrada</strong></td>
      <td>O ator finalizou uma simulação e está visualizando os resultados.</td>
    </tr>
    <tr>
      <td><strong>Fluxo principal</strong></td>
      <td>
        <ol>
          <li>O ator visualiza a tela de resultados da simulação.</li>
          <li>O ator clica no botão "Ver Detalhamento" ou "Expandir Cálculo".</li>
          <li>O sistema exibe uma seção expandida ou modal contendo o detalhamento de cada tributo calculado.</li>
          <li>Para cada tributo, o sistema exibe:
            <ul>
              <li>Nome do tributo (ex: IRPJ, CSLL, PIS, COFINS, etc.)</li>
              <li>Base de cálculo utilizada</li>
              <li>Alíquota ou percentual aplicado</li>
              <li>Deduções permitidas (se houver)</li>
              <li>Valor parcial (antes de deduções)</li>
              <li>Valor final</li>
              <li>Fórmula utilizada no cálculo</li>
            </ul>
          </li>
          <li>O ator pode recolher o detalhamento clicando novamente no botão.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos alternativos</strong></td>
      <td>
        Nenhum
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos de exceção</strong></td>
      <td>
        Nenhum
      </td>
    </tr>
  </tbody>
</table>
