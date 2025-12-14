<table>
  <tbody>
    <tr>
      <td><strong>Caso de uso</strong></td>
      <td>
        <strong><span><a>UC12 - Simular Lucro Presumido</a></span></strong>
      </td>
    </tr>
    <tr>
      <td><strong>Objetivo</strong></td>
      <td>
        Calcular a carga tributária no regime Lucro Presumido, aplicando os percentuais de presunção e calculando IRPJ, CSLL, PIS e COFINS.
      </td>
    </tr>
    <tr>
      <td><strong>Requisitos</strong></td>
      <td>RF-CAL-LP-001, RF-CAL-LP-002, RF-CAL-LP-003</td>
    </tr>
    <tr>
      <td><strong>Atores</strong></td>
      <td>Contador, Gerente</td>
    </tr>
    <tr>
      <td><strong>Condições de entrada</strong></td>
      <td>O ator está em <a href="especificacao_criar_simulacao.md">[UC10]</a> e selecionou o regime Lucro Presumido.</td>
    </tr>
    <tr>
      <td><strong>Fluxo principal</strong></td>
      <td>
        <ol>
          <li>O sistema identifica a alíquota de presunção com base no CNAE e tipo de atividade. <a href="#rn1">[RN1]</a></li>
          <li>O ator informa a Receita Bruta do Período (trimestre).</li>
          <li>O sistema calcula a Base de Cálculo do IRPJ: <code>Receita Bruta × Alíquota de Presunção</code></li>
          <li>O sistema calcula a Base de Cálculo da CSLL: <code>Receita Bruta × Alíquota de Presunção</code></li>
          <li>O sistema calcula o PIS: <code>Receita Bruta × 0,65%</code></li>
          <li>O sistema calcula a COFINS: <code>Receita Bruta × 3,00%</code></li>
          <li>O sistema calcula o IRPJ básico: <code>Base de Cálculo IRPJ × 15%</code></li>
          <li>O sistema verifica se há adicional de IRPJ. <a href="#a1">[A1]</a></li>
          <li>O sistema calcula a CSLL: <code>Base de Cálculo CSLL × 9%</code></li>
          <li>O sistema calcula o total: <code>PIS + COFINS + IRPJ + CSLL</code></li>
          <li>O sistema exibe o resultado com:
            <ul>
              <li>Alíquota de presunção aplicada</li>
              <li>Base de cálculo (lucro presumido)</li>
              <li>Detalhamento de cada tributo:
                <ul>
                  <li>PIS (base, alíquota, valor)</li>
                  <li>COFINS (base, alíquota, valor)</li>
                  <li>IRPJ (base, alíquota, adicional se houver, valor)</li>
                  <li>CSLL (base, alíquota, valor)</li>
                </ul>
              </li>
              <li>Valor total a pagar</li>
            </ul>
          </li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos alternativos</strong></td>
      <td>
        <a id="a1">[A1] - Cálculo do adicional de IRPJ</a>
        <ol>
          <li>No passo 8, o sistema verifica se a Base de Cálculo mensal excede R$ 20.000,00.</li>
          <li>Como o período é trimestral, o sistema verifica se a base excede R$ 60.000,00.</li>
          <li>Se Base de Cálculo > R$ 60.000,00:
            <ul>
              <li>O sistema calcula o adicional: <code>(Base de Cálculo - R$ 60.000) × 10%</code></li>
              <li>O sistema soma o adicional ao IRPJ básico</li>
              <li>O sistema exibe no detalhamento: "IRPJ Básico: R$ X | Adicional: R$ Y | Total IRPJ: R$ Z"</li>
            </ul>
          </li>
          <li>O sistema continua no passo 9 do fluxo principal.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos de exceção</strong></td>
      <td>
        Nenhum
        <br><br>
        <a id="rn1">[RN1] - Alíquotas de presunção</a><br>
        O sistema aplica as seguintes alíquotas de presunção conforme a atividade:
        <ul>
          <li>8% - Comércio, indústria, transporte de cargas, serviços hospitalares</li>
          <li>16% - Transporte de passageiros, serviços em geral</li>
          <li>32% - Serviços profissionais (advocacia, engenharia, medicina, contabilidade, consultoria, etc.)</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>
