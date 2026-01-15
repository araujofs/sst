<table>
  <tbody>
    <tr>
      <td><strong>Caso de uso</strong></td>
      <td>
        <strong><span><a>UC11 - Simular Simples Nacional</a></span></strong>
      </td>
    </tr>
    <tr>
      <td><strong>Objetivo</strong></td>
      <td>
        Calcular a carga tributária no regime Simples Nacional com base nos dados da empresa, identificando automaticamente o anexo, faixa e aplicando o Fator R quando necessário.
      </td>
    </tr>
    <tr>
      <td><strong>Requisitos</strong></td>
      <td>RF-CAL-SN-001, RF-CAL-SN-002, RF-CAL-SN-003, RF-CAL-SN-004</td>
    </tr>
    <tr>
      <td><strong>Atores</strong></td>
      <td>Contador, Gerente</td>
    </tr>
    <tr>
      <td><strong>Condições de entrada</strong></td>
      <td>O ator está em <a href="especificacao_criar_simulacao.md">[UC10]</a> e selecionou o regime Simples Nacional.</td>
    </tr>
    <tr>
      <td><strong>Fluxo principal</strong></td>
      <td>
        <ol>
          <li>O sistema valida se o CNAE foi informado. <a href="#e2">[E2]</a></li>
          <li>O sistema identifica o Anexo aplicável (I a V) com base no CNAE informado. <a href="#rn1">[RN1]</a> <a href="#e3">[E3]</a></li>
          <li>O ator informa a Receita Bruta do Período (mês) e a Receita Bruta Acumulada dos últimos 12 meses (RBT12).</li>
          <li>O sistema valida se o RBT12 está dentro do limite de R$ 4.8 milhões. <a href="#e1">[E1]</a></li>
          <li>O sistema identifica a Faixa de faturamento na tabela do Anexo com base no RBT12. <a href="#rn2">[RN2]</a></li>
          <li>O sistema obtém a Alíquota Nominal e a Parcela a Deduzir correspondentes à faixa.</li>
          <li>O sistema calcula a Alíquota Efetiva usando a fórmula: <code>((RBT12 × Alíquota Nominal) - Parcela a Deduzir) / RBT12</code></li>
          <li>O sistema calcula o valor do DAS: <code>Receita do Período × Alíquota Efetiva</code></li>
          <li>O sistema segrega os tributos (IRPJ, CSLL, PIS, COFINS, CPP, ICMS, ISS) conforme percentuais de repartição do anexo.</li>
          <li>O sistema exibe o resultado com:
            <ul>
              <li>Anexo utilizado</li>
              <li>Faixa de faturamento</li>
              <li>Alíquota Nominal e Efetiva</li>
              <li>Valor total do DAS</li>
              <li>Detalhamento de cada tributo</li>
            </ul>
          </li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos alternativos</strong></td>
      <td>
        <a id="a1">[A1] - CNAE sujeito ao Fator R</a>
        <ol>
          <li>No passo 2, o sistema identifica que o CNAE está sujeito ao Fator R (geralmente Anexo V - serviços).</li>
          <li>O sistema solicita ao ator a Folha de Pagamento dos últimos 12 meses (campo obrigatório).</li>
          <li>O ator informa o valor da folha.</li>
          <li>O sistema valida se o valor foi informado e é numérico positivo. <a href="#e4">[E4]</a></li>
          <li>O sistema calcula o Fator R: <code>Folha de Pagamento 12m / RBT12</code></li>
          <li>O sistema exibe o Fator R calculado em porcentagem.</li>
          <li>Se Fator R >= 28%:
            <ul>
              <li>O sistema utiliza o Anexo III (alíquota menor)</li>
              <li>O sistema exibe: "Enquadrado no Anexo III devido ao Fator R >= 28%"</li>
            </ul>
          </li>
          <li>Se Fator R < 28%:
            <ul>
              <li>O sistema utiliza o Anexo V (alíquota maior)</li>
              <li>O sistema exibe: "Enquadrado no Anexo V (Fator R < 28%)"</li>
            </ul>
          </li>
          <li>O sistema continua no passo 5 do fluxo principal.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos de exceção</strong></td>
      <td>
        <a id="e1">[E1] - Faturamento acima do limite</a>
        <ol>
          <li>O sistema identifica que o RBT12 é superior a R$ 4.800.000,00.</li>
          <li>O sistema exibe alerta: "Faturamento de R$ [valor] excede o limite de R$ 4.8 milhões para o Simples Nacional".</li>
          <li>O sistema sugere simular nos regimes Lucro Presumido ou Lucro Real.</li>
          <li>O cálculo do Simples Nacional não é realizado.</li>
        </ol>
        <a id="e2">[E2] - CNAE não informado</a>
        <ol>
          <li>No passo 1, o sistema identifica que o CNAE não foi informado (campo vazio).</li>
          <li>O sistema exibe mensagem de erro: "CNAE é obrigatório para calcular o Simples Nacional. Retorne à etapa anterior e informe o CNAE."</li>
          <li>O sistema oferece botão "Voltar" para retornar ao <a href="especificacao_criar_simulacao.md">[UC10 - Etapa 1]</a>.</li>
          <li>O cálculo não é realizado.</li>
        </ol>
        <a id="e3">[E3] - CNAE não mapeado para nenhum anexo</a>
        <ol>
          <li>No passo 2, o sistema não encontra o CNAE informado na tabela de mapeamento CNAE → Anexo.</li>
          <li>O sistema exibe mensagem: "CNAE [código] - [descrição] não possui anexo definido no Simples Nacional. Entre em contato com o suporte para inclusão."</li>
          <li>O sistema oferece opções:
            <ul>
              <li>"Voltar e alterar CNAE" - retorna ao <a href="especificacao_criar_simulacao.md">[UC10]</a></li>
              <li>"Simular outro regime" - oferece Lucro Presumido ou Lucro Real</li>
            </ul>
          </li>
          <li>O cálculo do Simples Nacional não é realizado.</li>
        </ol>
        <a id="e4">[E4] - Folha de Pagamento não informada (Fator R)</a>
        <ol>
          <li>No passo 4 do fluxo A1, o sistema identifica que a Folha de Pagamento não foi informada ou é inválida (zero ou negativa).</li>
          <li>O sistema exibe mensagem: "Folha de Pagamento é obrigatória para calcular o Fator R. Informe o valor da folha dos últimos 12 meses."</li>
          <li>O sistema destaca o campo em vermelho.</li>
          <li>Retorna ao passo 3 do fluxo A1.</li>
        </ol>
        <a id="rn1">[RN1] - Mapeamento CNAE para Anexo</a><br>
        O sistema mantém uma tabela que mapeia cada CNAE para o anexo correspondente:
        <ul>
          <li>Anexo I: Comércio</li>
          <li>Anexo II: Indústria</li>
          <li>Anexo III: Serviços com Fator R >= 28%</li>
          <li>Anexo IV: Serviços específicos (limpeza, vigilância, obras, etc.)</li>
          <li>Anexo V: Serviços gerais com Fator R < 28%</li>
        </ul><br>
        <a id="rn2">[RN2] - Faixas de faturamento</a><br>
        Cada anexo possui 6 faixas progressivas de faturamento (até 180k, 180k-360k, 360k-720k, 720k-1.8M, 1.8M-3.6M, 3.6M-4.8M), cada uma com sua Alíquota Nominal e Parcela a Deduzir específicas.
      </td>
    </tr>
  </tbody>
</table>
