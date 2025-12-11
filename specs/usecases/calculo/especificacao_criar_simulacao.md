<table>
  <tbody>
    <tr>
      <td><strong>Caso de uso</strong></td>
      <td>
        <strong><span><a>UC5 - Criar Nova Simulação Tributária</a></span></strong>
      </td>
    </tr>
    <tr>
      <td><strong>Objetivo</strong></td>
      <td>
        Permitir que o contador ou gerente crie uma nova simulação tributária informando os dados da empresa e escolhendo o(s) regime(s) a simular.
      </td>
    </tr>
    <tr>
      <td><strong>Requisitos</strong></td>
      <td>RF-CAL-001, RF-CAL-002, RF-CAL-008</td>
    </tr>
    <tr>
      <td><strong>Atores</strong></td>
      <td>Contador, Gerente</td>
    </tr>
    <tr>
      <td><strong>Condições de entrada</strong></td>
      <td>O ator está autenticado e deseja criar uma simulação tributária.</td>
    </tr>
    <tr>
      <td><strong>Fluxo principal</strong></td>
      <td>
        <strong>Etapa 1 - Dados Iniciais:</strong>
        <ol>
          <li>O ator acessa o módulo de simulação e clica em "Nova Simulação".</li>
          <li>O sistema exibe o formulário inicial (Etapa 1) com os campos:
            <ul>
              <li>CNAE Principal (campo de busca com autocompletar)</li>
              <li>Setor Econômico (preenchido automaticamente após seleção do CNAE)</li>
              <li>Regime(s) a simular (checkboxes: Simples Nacional, Lucro Presumido, Lucro Real)</li>
              <li>Botão "Avançar"</li>
            </ul>
          </li>
          <li>O ator preenche o CNAE principal.</li>
          <li>O sistema identifica automaticamente o setor econômico e exibe na tela.</li>
          <li>O ator seleciona o(s) regime(s) tributário(s) que deseja simular.</li>
          <li>O ator clica em "Avançar".</li>
          <li>O sistema valida se pelo menos um regime foi selecionado. <a href="#e1">[E1]</a></li>
        </ol>
        <strong>Etapa 2 - Dados Financeiros:</strong>
        <ol start="8">
          <li>O sistema exibe a segunda etapa do formulário com informações e campos específicos conforme o(s) regime(s) selecionado(s). <a href="#a1">[A1]</a></li>
          <li>O ator preenche todos os dados financeiros solicitados.</li>
          <li>O ator clica no botão "Simular".</li>
          <li>O sistema valida os dados inseridos. <a href="#rn2">[RN2]</a> <a href="#e2">[E2]</a></li>
          <li>O sistema processa o cálculo conforme o(s) regime(s) selecionado(s).</li>
          <li>O sistema exibe a tela de resultados com os valores calculados.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos alternativos</strong></td>
      <td>
        <a id="a1">[A1] - Etapa 2: Campos e informações específicas por regime</a>
        <ol>
          <li>Na Etapa 2, o sistema exibe os campos conforme o(s) regime(s) selecionado(s):</li>
          <li>Se Simples Nacional foi selecionado, o sistema exibe:
            <ul>
              <li>Informação do Anexo identificado: "Anexo [X] - [Descrição]" <a href="#rn1">[RN1]</a></li>
              <li>Campo: Receita Bruta do Período (mês)</li>
              <li>Campo: Receita Bruta Acumulada 12 meses (RBT12)</li>
              <li>Campo: Folha de Pagamento 12 meses (apenas se CNAE sujeito ao Fator R)</li>
            </ul>
          </li>
          <li>Se Lucro Presumido foi selecionado, o sistema exibe:
            <ul>
              <li>Campo: Receita Bruta do Período (trimestre)</li>
            </ul>
          </li>
          <li>Se Lucro Real foi selecionado, o sistema exibe:
            <ul>
              <li>Campo: Receita Bruta do Período</li>
              <li>Campo: Custos e Despesas Operacionais</li>
              <li>Outros campos específicos</li>
            </ul>
          </li>
          <li>O sistema também exibe um botão "Voltar" para retornar à Etapa 1.</li>
        </ol>
        <a id="a2">[A2] - Voltar para Etapa 1</a>
        <ol>
          <li>No passo 10, o ator clica em "Voltar".</li>
          <li>O sistema retorna para a Etapa 1 preservando os dados já preenchidos (CNAE e regimes selecionados).</li>
          <li>O ator pode alterar o CNAE ou os regimes selecionados.</li>
          <li>Retorna ao passo 6.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos de exceção</strong></td>
      <td>
        <a id="e1">[E1] - Nenhum regime selecionado</a>
        <ol>
          <li>No passo 7, o sistema identifica que nenhum regime foi selecionado.</li>
          <li>O sistema exibe mensagem: "Selecione pelo menos um regime tributário para continuar".</li>
          <li>Retorna ao passo 5 do fluxo principal.</li>
        </ol>
        <a id="e2">[E2] - Dados financeiros inválidos</a>
        <ol>
          <li>No passo 11, o sistema identifica valores negativos, campos obrigatórios vazios, faturamento acima do limite do regime ou valores atípicos.</li>
          <li>O sistema exibe mensagens de erro específicas para cada problema identificado.</li>
          <li>O ator corrige os dados e tenta novamente.</li>
          <li>Retorna ao passo 10 do fluxo principal.</li>
        </ol>
        <a id="rn1">[RN1] - Identificação automática do anexo</a><br>
        O sistema mantém uma tabela de mapeamento entre CNAE e Anexo do Simples Nacional. Na Etapa 2, quando Simples Nacional foi selecionado, o sistema consulta essa tabela e exibe automaticamente qual anexo será aplicado.<br><br>
        <a id="rn2">[RN2] - Validação de dados financeiros</a><br>
        O sistema deve validar na Etapa 2:
        <ul>
          <li>Valores negativos não são permitidos em campos financeiros</li>
          <li>Faturamento não pode exceder R$ 4.8 milhões para Simples Nacional</li>
          <li>Campos obrigatórios devem estar preenchidos</li>
          <li>Valores muito altos ou muito baixos devem gerar alertas</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>
