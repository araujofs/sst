<table>
  <tbody>
    <tr>
      <td><strong>Caso de uso</strong></td>
      <td>
        <strong><span><a>UC10 - Criar Nova Simulação Tributária</a></span></strong>
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
        <strong>Etapa 2 - Dados Financeiros e Cálculo:</strong>
        <ol start="11">
          <li>O sistema redireciona para o use case específico do regime selecionado:
            <ul>
              <li>Se <strong>Simples Nacional</strong>: executa <a href="especificacao_simular_simples_nacional.md">[UC11 - Simular Simples Nacional]</a></li>
              <li>Se <strong>Lucro Presumido</strong>: executa <a href="especificacao_simular_lucro_presumido.md">[UC12 - Simular Lucro Presumido]</a></li>
              <li>Se <strong>Lucro Real</strong>: <strong>valida se o CNAE corresponde a prestação de serviços <a href="#e2">[E2]</a> e</strong> executa <a href="especificacao_simular_lucro_real.md">[UC14 - Simular Lucro Real]</a></li>
            </ul>
          </li>
          <li>O use case específico solicita dados financeiros necessários, realiza validações e calcula os tributos.</li>
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
          <li>O sistema consulta a API da Receita Federal. <a href="../importacao/especificacao_validar_cnpj.md">[UC17]</a></li>
          <li>O sistema preenche automaticamente: Razão Social, CNAE, Município/UF.</li>
          <li>O ator prossegue para o passo 8.</li>
        </ol>
        <a id="a1">[A1] - Visualizar dados financeiros já preenchidos</a>
        <ol>
          <li>No passo 11, o sistema identifica que já existem dados financeiros salvos em rascunho.</li>
          <li>O sistema exibe modal: "Foram encontrados dados financeiros salvos. Deseja carregar?"
            <ul>
              <li>Se "Sim": carrega os dados e preenche o formulário da Etapa 2</li>
              <li>Se "Não": limpa o rascunho e inicia formulário vazio</li>
            </ul>
          </li>
          <li>O sistema também exibe um botão "Voltar" para retornar à Etapa 1.</li>
        </ol>
        <a id="a2">[A2] - Simular outro regime para comparação</a>
        <ol>
          <li>No passo 14, após visualizar os resultados, o ator clica em "Simular Outro Regime".</li>
          <li>O sistema exibe modal: "Selecione o regime para nova simulação:" com os regimes disponíveis (exceto o já simulado).</li>
          <li>O ator seleciona o regime desejado.</li>
          <li>Se selecionar <strong>Lucro Real</strong>, o sistema valida o CNAE. <a href="#e2">[E2]</a></li>
          <li>O sistema retorna à Etapa 2 com os dados gerais preservados, mas formulário adaptado ao novo regime.</li>
          <li>O ator preenche os dados financeiros específicos do novo regime.</li>
          <li>Retorna ao passo 11 do fluxo principal.</li>
          <li>Após calcular, o sistema oferece comparação entre as simulações realizadas. <a href="../calculo/especificacao_comparar_regimes.md">[UC16]</a></li>
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
          <li>No passo 10, o sistema identifica que nenhum regime foi selecionado.</li>
          <li>O sistema exibe mensagem: "Selecione um regime tributário para continuar".</li>
          <li>O sistema destaca o campo "Regime Tributário" em vermelho.</li>
          <li>Retorna ao passo 8.</li>
        </ol>
        <a id="e2">[E2] - CNAE incompatível com Lucro Real</a>
        <ol>
          <li>Ao selecionar Lucro Real (passo 11 ou fluxo A2), o sistema valida o CNAE informado.</li>
          <li>O sistema identifica que o CNAE não corresponde a prestação de serviços (ex: comércio, indústria).</li>
          <li>O sistema exibe alerta em modal:
            <ul>
              <li><strong>Título:</strong> "CNAE incompatível com Lucro Real"</li>
              <li><strong>Mensagem:</strong> "O cálculo de Lucro Real neste sistema está limitado a <strong>prestadores de serviços</strong>."</li>
              <li><strong>Detalhe:</strong> "O CNAE informado ([código] - [descrição]) corresponde a atividade de [comércio/indústria]."</li>
              <li><strong>Sugestão:</strong> "Para este tipo de atividade, utilize os regimes <strong>Simples Nacional</strong> ou <strong>Lucro Presumido</strong>."</li>
            </ul>
          </li>
          <li>O sistema oferece opções no modal:
            <ul>
              <li><strong>"Voltar e selecionar outro regime"</strong> (retorna ao passo 8)</li>
              <li><strong>"Alterar CNAE"</strong> (retorna ao passo 5)</li>
            </ul>
          </li>
          <li>O cálculo do Lucro Real não é realizado.</li>
        </ol>
        <strong>Nota:</strong> As validações de dados financeiros específicas de cada regime e exceções relacionadas são tratadas nos use cases detalhados: <a href="especificacao_simular_simples_nacional.md">[UC11]</a>, <a href="especificacao_simular_lucro_presumido.md">[UC12]</a> e <a href="especificacao_simular_lucro_real.md">[UC14]</a>.
      </td>
    </tr>
    <tr>
      <td><strong>Regras de negócio</strong></td>
      <td>
        <a id="rn1">[RN1] - Seleção obrigatória de regime</a><br>
        O ator deve obrigatoriamente selecionar um regime tributário na Etapa 1 antes de avançar para a Etapa 2. O sistema não permite prosseguir sem essa seleção.<br><br>
        <a id="rn2">[RN2] - Preservação de dados entre etapas</a><br>
        Os dados gerais preenchidos na Etapa 1 (CNPJ, Razão Social, CNAE, Município/UF) são preservados e reutilizados quando o ator decide simular outro regime ou voltar para ajustes.<br><br>
        <a id="rn3">[RN3] - Validação de CNAE para Lucro Real</a><br>
        O regime Lucro Real está limitado neste sistema a empresas prestadoras de serviços. O sistema deve validar o CNAE informado e, caso corresponda a atividades de comércio ou indústria, bloquear a simulação e orientar o usuário a utilizar Simples Nacional ou Lucro Presumido. Esta limitação se deve à complexidade das regras de creditamento de PIS/COFINS não-cumulativo para atividades comerciais e industriais.
      </td>
    </tr>
  </tbody>
</table>