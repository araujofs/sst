<table>
  <tbody>
    <tr>
      <td><strong>Caso de uso</strong></td>
      <td>
        <strong><span><a>UC11 - Comparar Regimes Tributários</a></span></strong>
      </td>
    </tr>
    <tr>
      <td><strong>Objetivo</strong></td>
      <td>
        Permitir que o contador ou gerente compare os três regimes tributários (Simples Nacional, Lucro Presumido, Lucro Real) lado a lado, onde o sistema reutiliza dados de simulações já realizadas e solicita apenas as informações faltantes, identificando automaticamente qual regime resulta na menor carga tributária.
      </td>
    </tr>
    <tr>
      <td><strong>Requisitos</strong></td>
      <td>RF-CAL-005</td>
    </tr>
    <tr>
      <td><strong>Atores</strong></td>
      <td>Contador, Gerente</td>
    </tr>
    <tr>
      <td><strong>Condições de entrada</strong></td>
      <td>O ator deseja comparar os três regimes tributários para uma empresa. Pode ou não ter simulações anteriores salvas.</td>
    </tr>
    <tr>
      <td><strong>Fluxo principal</strong></td>
      <td>
        <ol>
          <li>O ator acessa o módulo de simulação e clica em "Comparar Regimes Tributários".</li>
          <li>O sistema exibe opções:
            <ul>
              <li>"Nova comparação (preencher dados)"</li>
              <li>"Usar simulações existentes"</li>
            </ul>
          </li>
          <li>O ator seleciona uma das opções. <a href="#a1">[A1]</a></li>
          <li><strong>Se nova comparação:</strong> O sistema exibe formulário unificado solicitando:
            <ul>
              <li>Dados gerais (CNPJ, CNAE, município/UF) - comum aos 3 regimes</li>
              <li>Receita bruta do período e RBT12 - comum aos 3 regimes</li>
              <li>Folha de pagamento (se aplicável para Fator R)</li>
              <li>Dados específicos apenas se necessário por regime</li>
            </ul>
          </li>
          <li>O ator preenche os dados solicitados.</li>
          <li>O sistema calcula automaticamente os três regimes em paralelo.</li>
          <li>O sistema exibe uma tabela comparativa contendo:
            <ul>
              <li>Uma coluna para cada regime: Simples Nacional, Lucro Presumido, Lucro Real</li>
              <li>Status de elegibilidade (se aplicável ou não) <a href="#e1">[E1]</a></li>
            </ul>
          </li>
          <li>Para cada regime elegível, o sistema apresenta:
            <ul>
              <li>Carga tributária total</li>
              <li>Alíquota efetiva (%)</li>
              <li>Detalhamento por tributo (IRPJ, CSLL, PIS, COFINS, CPP, ICMS/ISS)</li>
              <li>Observações específicas (ex: "Anexo III - Fator R", "Presunção 32%")</li>
            </ul>
          </li>
          <li>O sistema destaca em verde o regime com menor carga tributária.</li>
          <li>O sistema calcula e exibe a economia potencial:
            <ul>
              <li>"Melhor opção: [Regime X]"</li>
              <li>"Economia em relação a [Regime Y]: R$ [valor] ([percentual]%)"</li>
              <li>"Economia em relação a [Regime Z]: R$ [valor] ([percentual]%)"</li>
            </ul>
          </li>
          <li>O sistema exibe gráfico comparativo de barras mostrando:
            <ul>
              <li>Eixo X: Regimes tributários</li>
              <li>Eixo Y: Valor em reais</li>
              <li>Barras empilhadas por tipo de tributo</li>
            </ul>
          </li>
          <li>O sistema oferece botões:
            <ul>
              <li>"Salvar Comparação" - salva todas as 3 simulações no histórico</li>
              <li>"Exportar Comparação" - gera relatório <a href="#a2">[A2]</a></li>
              <li>"Ver Detalhes" - abre detalhamento de um regime específico</li>
            </ul>
          </li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos alternativos</strong></td>
      <td>
        <a id="a1">[A1] - Usar simulações existentes (reuso inteligente)</a>
        <ol>
          <li>No passo 3, o ator seleciona "Usar simulações existentes".</li>
          <li>O sistema exibe lista de empresas/clientes com simulações salvas.</li>
          <li>O ator seleciona a empresa desejada.</li>
          <li>O sistema verifica quais regimes já possuem simulações salvas.</li>
          <li>O sistema identifica dados comuns disponíveis (CNPJ, CNAE, receitas, etc.).</li>
          <li>Se os 3 regimes já foram simulados:
            <ul>
              <li>O sistema exibe mensagem: "Simulações encontradas para todos os regimes. Deseja usar os dados existentes ou atualizar?"</li>
              <li>Se "Usar existentes", pula para o passo 7 do fluxo principal.</li>
              <li>Se "Atualizar", permite editar valores e recalcular.</li>
            </ul>
          </li>
          <li>Se apenas 1 ou 2 regimes foram simulados:
            <ul>
              <li>O sistema reutiliza dados gerais (CNPJ, CNAE, receitas) das simulações existentes.</li>
              <li>O sistema solicita apenas dados faltantes específicos do(s) regime(s) não simulado(s).</li>
              <li>O ator preenche apenas os campos faltantes.</li>
              <li>O sistema calcula os regimes faltantes.</li>
              <li>Prossegue para o passo 7 do fluxo principal.</li>
            </ul>
          </li>
        </ol>
        <a id="a2">[A2] - Exportar comparação</a>
        <ol>
          <li>No passo 12, o ator clica em "Exportar Comparação".</li>
          <li>O sistema exibe opções de formato:
            <ul>
              <li>PDF (relatório formatado com gráficos)</li>
              <li>Excel (planilha com dados detalhados)</li>
              <li>PNG (imagem do gráfico comparativo)</li>
            </ul>
          </li>
          <li>O ator seleciona o formato desejado.</li>
          <li>O sistema gera o arquivo contendo:
            <ul>
              <li>Dados da empresa (Razão Social, CNPJ, CNAE)</li>
              <li>Data da simulação</li>
              <li>Tabela comparativa completa</li>
              <li>Gráficos visuais</li>
              <li>Análise do regime mais vantajoso</li>
              <li>Rodapé com observações e disclaimers</li>
            </ul>
          </li>
          <li>O sistema inicia o download do arquivo.</li>
          <li>Retorna ao passo 12 do fluxo principal.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos de exceção</strong></td>
      <td>
        <a id="e1">[E1] - Regime inelegível</a>
        <ol>
          <li>Durante o cálculo, o sistema identifica que um regime não é aplicável (ex: faturamento > R$ 4,8M para Simples).</li>
          <li>O sistema exibe na tabela comparativa:
            <ul>
              <li>Coluna do regime com fundo cinza</li>
              <li>Texto: "Não aplicável - Faturamento acima do limite"</li>
              <li>Ícone de informação com detalhes da restrição</li>
            </ul>
          </li>
          <li>O sistema compara apenas os regimes elegíveis.</li>
          <li>O sistema exibe nota explicativa no rodapé.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Regras de negócio</strong></td>
      <td>
        <a id="rn1">[RN1] - Critério de melhor regime</a><br>
        O regime "mais vantajoso" é determinado pela menor carga tributária total em reais. Em caso de valores muito próximos (diferença < 1%), o sistema deve indicar empate técnico e sugerir análise de outros critérios (complexidade de apuração, obrigações acessórias).<br><br>
        <a id="rn2">[RN2] - Inelegibilidade de regimes</a><br>
        O sistema deve validar automaticamente:
        <ul>
          <li><strong>Simples Nacional:</strong> Faturamento até R$ 4,8 milhões, sem restrições de atividade</li>
          <li><strong>Lucro Presumido:</strong> Faturamento até R$ 78 milhões</li>
          <li><strong>Lucro Real:</strong> Sem limite de faturamento, obrigatório para empresas acima de R$ 78 milhões</li>
        </ul>
        Se um regime não for aplicável, deve ser indicado visualmente na comparação.<br><br>
        <a id="rn3">[RN3] - Precisão da comparação</a><br>
        Todos os cálculos devem usar os mesmos dados de entrada (receita, despesas, etc.) para garantir comparabilidade justa entre os regimes. Qualquer ajuste feito em um regime deve ser refletido automaticamente nos demais.
      </td>
    </tr>
  </tbody>
</table>
