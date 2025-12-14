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
      <td>RF-CAL-001, RF-CAL-006</td>
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
              <li>CNPJ (opcional, com checkbox "Simulação sem CNPJ")</li>
              <li>Razão Social (preenchida automaticamente se CNPJ válido, senão manual)</li>
              <li>CNAE Principal (campo de busca com autocompletar)</li>
              <li>Setor Econômico (preenchido automaticamente após seleção do CNAE)</li>
              <li>Município/UF (preenchido automaticamente se CNPJ válido, senão manual)</li>
              <li>Regime Tributário (radio buttons: Simples Nacional, Lucro Presumido, Lucro Real)</li>
              <li>Botão "Avançar"</li>
            </ul>
          </li>
          <li>O ator pode informar o CNPJ para autopreenchimento ou marcar "Simulação sem CNPJ". <a href="#a0">[A0]</a></li>
          <li>O ator preenche ou confirma a Razão Social.</li>
          <li>O ator preenche o CNAE principal.</li>
          <li>O sistema identifica automaticamente o setor econômico e exibe na tela.</li>
          <li>O ator preenche ou confirma Município/UF.</li>
          <li>O ator seleciona o regime tributário que deseja simular (obrigatório).</li>
          <li>O ator clica em "Avançar".</li>
          <li>O sistema valida se um regime foi selecionado. <a href="#e1">[E1]</a></li>
        </ol>
        <strong>Etapa 2 - Dados Financeiros:</strong>
        <ol start="8">
          <li>O sistema exibe a segunda etapa do formulário com campos específicos conforme o regime selecionado. <a href="#a1">[A1]</a></li>
          <li>O ator preenche todos os dados financeiros solicitados.</li>
          <li>O ator clica no botão "Simular".</li>
          <li>O sistema valida os dados inseridos. <a href="#rn2">[RN2]</a> <a href="#e2">[E2]</a></li>
          <li>O sistema processa o cálculo conforme o regime selecionado.</li>
          <li>O sistema exibe a tela de resultados com os valores calculados para o regime escolhido.</li>
          <li>O sistema oferece botão "Simular Outro Regime" para comparação. <a href="#a2">[A2]</a></li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos alternativos</strong></td>
      <td>
        <a id="a0">[A0] - Consultar CNPJ para autopreenchimento</a>
        <ol>
          <li>No passo 3, o ator informa um CNPJ válido.</li>
          <li>O sistema consulta a API da Receita Federal. <a href="../importacao/especificacao_validar_cnpj.md">[UC15]</a></li>
          <li>O sistema preenche automaticamente: Razão Social, CNAE, Município/UF.</li>
          <li>O ator pode editar qualquer campo preenchido automaticamente.</li>
          <li>Retorna ao passo 5.</li>
        </ol>
        <a id="a1">[A1] - Etapa 2: Campos específicos por regime</a>
        <ol>
          <li>Na Etapa 2, o sistema exibe os campos conforme o regime selecionado:</li>
          <li>Se <strong>Simples Nacional</strong> foi selecionado, o sistema exibe:
            <ul>
              <li>Informação do Anexo identificado: "Anexo [X] - [Descrição]" <a href="#rn1">[RN1]</a></li>
              <li>Campo: Receita Bruta do Período (mês)</li>
              <li>Campo: Receita Bruta Acumulada 12 meses (RBT12)</li>
              <li>Campo: Folha de Pagamento 12 meses (apenas se CNAE sujeito ao Fator R)</li>
            </ul>
          </li>
          <li>Se <strong>Lucro Presumido</strong> foi selecionado, o sistema exibe:
            <ul>
              <li>Campo: Receita Bruta do Período (trimestre)</li>
            </ul>
          </li>
          <li>Se <strong>Lucro Real</strong> foi selecionado, o sistema exibe:
            <ul>
              <li>Campo: Receita Bruta do Período</li>
              <li>Campo: Custos e Despesas Operacionais</li>
              <li>Outros campos específicos</li>
            </ul>
          </li>
          <li>O sistema também exibe um botão "Voltar" para retornar à Etapa 1.</li>
        </ol>
        <a id="a2">[A2] - Simular outro regime para comparação</a>
        <ol>
          <li>No passo 14, após visualizar os resultados, o ator clica em "Simular Outro Regime".</li>
          <li>O sistema exibe modal: "Selecione o regime para nova simulação:" com os regimes disponíveis (exceto o já simulado).</li>
          <li>O ator seleciona o regime desejado.</li>
          <li>O sistema retorna à Etapa 2 com os dados gerais preservados, mas formulário adaptado ao novo regime.</li>
          <li>O ator preenche os dados financeiros específicos do novo regime.</li>
          <li>Retorna ao passo 11 do fluxo principal.</li>
          <li>Após calcular, o sistema oferece comparação entre as simulações realizadas. <a href="../calculo/especificacao_comparar_regimes.md">[UC11]</a></li>
        </ol>
        <a id="a3">[A3] - Voltar para Etapa 1</a>
        <ol>
          <li>No passo 11, o ator clica em "Voltar".</li>
          <li>O sistema retorna para a Etapa 1 preservando os dados já preenchidos (CNPJ, CNAE, regime selecionado).</li>
          <li>O ator pode alterar qualquer dado da Etapa 1, incluindo o regime.</li>
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
          <li>O sistema exibe mensagem: "Selecione um regime tributário para continuar".</li>
          <li>O sistema destaca o campo "Regime Tributário" em vermelho.</li>
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
        </ul>
      </td>
    </tr>
  </tbody>
</table>
