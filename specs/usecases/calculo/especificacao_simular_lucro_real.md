<table>
  <tbody>
    <tr>
      <td><strong>Caso de uso</strong></td>
      <td>
        <strong><span><a>UC9 - Simular Lucro Real</a></span></strong>
      </td>
    </tr>
    <tr>
      <td><strong>Objetivo</strong></td>
      <td>
        Calcular a carga tributária no regime Lucro Real, apurando o lucro líquido ajustado e calculando IRPJ, CSLL, PIS e COFINS no regime não-cumulativo.
      </td>
    </tr>
    <tr>
      <td><strong>Requisitos</strong></td>
      <td>RF-CAL-LR-001, RF-CAL-LR-002, RF-CAL-LR-003</td>
    </tr>
    <tr>
      <td><strong>Atores</strong></td>
      <td>Contador, Gerente</td>
    </tr>
    <tr>
      <td><strong>Condições de entrada</strong></td>
      <td>O ator está em <a href="especificacao_criar_simulacao.md">[UC5]</a> e selecionou o regime Lucro Real.</td>
    </tr>
    <tr>
      <td><strong>Fluxo principal</strong></td>
      <td>
        <ol>
          <li>O ator informa os seguintes dados do período:
            <ul>
              <li>Receita Bruta Total</li>
              <li>Custos e Despesas Operacionais</li>
              <li>Outras Receitas</li>
              <li>Outras Despesas</li>
              <li>Despesas com PIS/COFINS (para créditos não-cumulativos)</li>
            </ul>
          </li>
          <li>O sistema calcula o Lucro Líquido Contábil: <code>Receita Total - Custos - Despesas</code></li>
          <li>O sistema permite que o ator informe ajustes fiscais (adições, exclusões, compensações). <a href="#a1">[A1]</a></li>
          <li>O sistema calcula a Base de Cálculo do IRPJ: <code>Lucro Líquido + Adições - Exclusões</code></li>
          <li>O sistema calcula o IRPJ básico: <code>Base de Cálculo × 15%</code></li>
          <li>O sistema verifica se há adicional de IRPJ. <a href="#a2">[A2]</a></li>
          <li>O sistema calcula a Base de Cálculo da CSLL: <code>Lucro Líquido + Adições - Exclusões</code></li>
          <li>O sistema calcula a CSLL: <code>Base de Cálculo × 9%</code></li>
          <li>O sistema calcula o PIS não-cumulativo: <code>(Receita Bruta × 1,65%) - Créditos de PIS</code></li>
          <li>O sistema calcula a COFINS não-cumulativa: <code>(Receita Bruta × 7,60%) - Créditos de COFINS</code></li>
          <li>O sistema permite compensação de prejuízos fiscais. <a href="#a3">[A3]</a></li>
          <li>O sistema calcula o total: <code>IRPJ + CSLL + PIS + COFINS</code></li>
          <li>O sistema exibe o resultado com:
            <ul>
              <li>Lucro Líquido Contábil</li>
              <li>Ajustes fiscais aplicados (adições e exclusões)</li>
              <li>Lucro Real (base de cálculo)</li>
              <li>Detalhamento de cada tributo:
                <ul>
                  <li>IRPJ (base, alíquota, adicional se houver, valor)</li>
                  <li>CSLL (base, alíquota, valor)</li>
                  <li>PIS não-cumulativo (débitos, créditos, valor líquido)</li>
                  <li>COFINS não-cumulativa (débitos, créditos, valor líquido)</li>
                </ul>
              </li>
              <li>Valor total a pagar</li>
              <li>Saldo de prejuízos fiscais remanescente (se aplicável)</li>
            </ul>
          </li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos alternativos</strong></td>
      <td>
        <a id="a1">[A1] - Informar ajustes fiscais</a>
        <ol>
          <li>No passo 3, o ator clica em "Adicionar Ajustes Fiscais".</li>
          <li>O sistema exibe campos para:
            <ul>
              <li><strong>Adições:</strong> Despesas não dedutíveis, multas, brindes, etc.</li>
              <li><strong>Exclusões:</strong> Receitas não tributáveis, incentivos fiscais, etc.</li>
            </ul>
          </li>
          <li>O ator informa os valores dos ajustes com descrição.</li>
          <li>O sistema valida que os valores são numéricos e não negativos.</li>
          <li>O sistema aplica os ajustes no cálculo da base.</li>
          <li>Retorna ao passo 4 do fluxo principal.</li>
        </ol>
        <a id="a2">[A2] - Cálculo do adicional de IRPJ</a>
        <ol>
          <li>No passo 6, o sistema verifica se a Base de Cálculo mensal excede R$ 20.000,00.</li>
          <li>Se Base de Cálculo > R$ 20.000,00:
            <ul>
              <li>O sistema calcula o adicional: <code>(Base de Cálculo - R$ 20.000) × 10%</code></li>
              <li>O sistema soma o adicional ao IRPJ básico</li>
              <li>O sistema exibe no detalhamento: "IRPJ Básico: R$ X | Adicional: R$ Y | Total IRPJ: R$ Z"</li>
            </ul>
          </li>
          <li>O sistema continua no passo 7 do fluxo principal.</li>
        </ol>
        <a id="a3">[A3] - Compensar prejuízos fiscais</a>
        <ol>
          <li>No passo 11, o ator informa que possui prejuízos fiscais de períodos anteriores.</li>
          <li>O sistema solicita o valor do saldo de prejuízos disponíveis.</li>
          <li>O sistema calcula o limite de compensação: <code>Base de Cálculo do IRPJ × 30%</code> <a href="#rn1">[RN1]</a></li>
          <li>O sistema aplica a compensação: <code>min(Prejuízos Disponíveis, Limite 30%)</code></li>
          <li>O sistema recalcula o IRPJ sobre a base reduzida.</li>
          <li>O sistema exibe:
            <ul>
              <li>Prejuízos compensados no período</li>
              <li>Saldo remanescente de prejuízos</li>
            </ul>
          </li>
          <li>Retorna ao passo 12 do fluxo principal.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos de exceção</strong></td>
      <td>
        <a id="e1">[E1] - Lucro Líquido negativo (prejuízo)</a>
        <ol>
          <li>No passo 2, o sistema identifica que Receitas < Custos + Despesas.</li>
          <li>O sistema exibe: "Prejuízo contábil de R$ [valor]. Não haverá IRPJ e CSLL neste período."</li>
          <li>O sistema registra o prejuízo para compensação futura.</li>
          <li>O sistema continua calculando PIS e COFINS normalmente.</li>
          <li>O sistema exibe o resultado com tributos = 0 para IRPJ e CSLL.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Regras de negócio</strong></td>
      <td>
        <a id="rn1">[RN1] - Limite de compensação de prejuízos</a><br>
        Conforme art. 15 da Lei nº 9.065/1995 e Decreto nº 9.580/2018 (RIR/2018), a compensação de prejuízos fiscais e bases negativas de CSLL está limitada a 30% do lucro real do período.<br><br>
        <a id="rn2">[RN2] - Créditos de PIS/COFINS não-cumulativos</a><br>
        No regime não-cumulativo, são permitidos créditos sobre:
        <ul>
          <li>Aquisição de mercadorias para revenda</li>
          <li>Aquisição de insumos utilizados na prestação de serviços</li>
          <li>Energia elétrica e aluguéis de prédios</li>
          <li>Máquinas, equipamentos e outros bens incorporados ao ativo imobilizado</li>
          <li>Armazenagem e fretes</li>
        </ul>
        Alíquotas de crédito: 1,65% (PIS) e 7,60% (COFINS)<br><br>
        <a id="rn3">[RN3] - Adicional de IRPJ</a><br>
        Conforme art. 542 do Decreto nº 9.580/2018, é devido adicional de 10% sobre a parcela do lucro real que exceder R$ 20.000,00 mensais (R$ 60.000,00 trimestral ou R$ 240.000,00 anual).
      </td>
    </tr>
  </tbody>
</table>
