<table>
  <tbody>
    <tr>
      <td><strong>Caso de uso</strong></td>
      <td>
        <strong><span><a>UC17 - Consultar CNPJ para Autopreenchimento</a></span></strong>
      </td>
    </tr>
    <tr>
      <td><strong>Objetivo</strong></td>
      <td>
        Facilitar o preenchimento do formulário de simulação consultando dados cadastrais via API da Receita Federal quando o usuário informar um CNPJ.
      </td>
    </tr>
    <tr>
      <td><strong>Requisitos</strong></td>
      <td>RF-IMP-001</td>
    </tr>
    <tr>
      <td><strong>Atores</strong></td>
      <td>Contador, Gerente, Sistema (automático)</td>
    </tr>
    <tr>
      <td><strong>Condições de entrada</strong></td>
      <td>O ator está preenchendo o formulário de simulação.</td>
    </tr>
    <tr>
      <td><strong>Fluxo principal</strong></td>
      <td>
        <ol>
          <li>O sistema exibe campo CNPJ com opção "Simulação sem CNPJ (empresa hipotética)" (checkbox).</li>
          <li>O ator preenche o campo CNPJ.</li>
          <li>O sistema valida o formato do CNPJ (14 dígitos numéricos). <a href="#e1">[E1]</a></li>
          <li>O sistema exibe indicador de carregamento: "Consultando dados..."</li>
          <li>O sistema consulta API da Receita Federal (ReceitaWS ou BrasilAPI). <a href="#rn1">[RN1]</a></li>
          <li>A API retorna os dados cadastrais da empresa.</li>
          <li>O sistema preenche automaticamente os seguintes campos:
            <ul>
              <li>Razão Social</li>
              <li>CNAE Principal</li>
              <li>Setor Econômico (derivado do CNAE)</li>
              <li>Data de Abertura</li>
              <li>Município/UF</li>
            </ul>
          </li>
          <li>O sistema exibe a situação cadastral como informação (sem bloquear): <a href="#a2">[A2]</a>
            <ul>
              <li>Se ATIVA: badge verde "CNPJ Ativo"</li>
              <li>Se INAPTA/SUSPENSA/BAIXADA: badge amarelo "CNPJ [STATUS] - Atenção"</li>
            </ul>
          </li>
          <li>O sistema permite edição de todos os campos preenchidos.</li>
          <li>O ator prossegue com o preenchimento dos demais dados financeiros.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos alternativos</strong></td>
      <td>
        <a id="a1">[A1] - Simulação sem CNPJ</a>
        <ol>
          <li>No passo 1, o ator marca a opção "Simulação sem CNPJ (empresa hipotética)".</li>
          <li>O sistema desabilita o campo CNPJ.</li>
          <li>O sistema habilita todos os campos para preenchimento manual.</li>
          <li>O sistema exibe badge azul "Simulação Hipotética".</li>
          <li>Pula para o passo 10.</li>
        </ol>
        <a id="a2">[A2] - CNPJ com situação cadastral inativa</a>
        <ol>
          <li>No passo 8, o sistema identifica situação "INAPTA", "SUSPENSA" ou "BAIXADA".</li>
          <li>O sistema exibe alerta informativo (não bloqueante): "Este CNPJ está com situação cadastral [STATUS]. Você pode prosseguir com a simulação normalmente para análise de cenários ou planejamento de regularização."</li>
          <li>O ator pode prosseguir normalmente ou corrigir o CNPJ.</li>
          <li>Retorna ao passo 9.</li>
        </ol>
        <a id="a3">[A3] - Substituir dados consultados</a>
        <ol>
          <li>No passo 7, o sistema detecta que alguns campos já foram preenchidos manualmente.</li>
          <li>O sistema exibe modal: "Foram encontrados dados do CNPJ. Deseja substituir os dados atuais?"</li>
          <li>Se o ator confirmar, o sistema substitui os dados.</li>
          <li>Se o ator cancelar, o sistema mantém os dados manuais.</li>
          <li>Retorna ao passo 8.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos de exceção</strong></td>
      <td>
        <a id="e1">[E1] - CNPJ com formato inválido</a>
        <ol>
          <li>No passo 3, o sistema identifica que o CNPJ não tem 14 dígitos ou falha na validação do dígito verificador.</li>
          <li>O sistema exibe mensagem: "CNPJ inválido. Verifique o número digitado ou marque 'Simulação sem CNPJ' para prosseguir."</li>
          <li>O sistema não realiza a consulta na API.</li>
          <li>O ator pode corrigir o CNPJ ou marcar a opção sem CNPJ.</li>
        </ol>
        <a id="e2">[E2] - API indisponível</a>
        <ol>
          <li>No passo 5, o sistema não consegue se conectar à API (timeout, erro 500, sem internet).</li>
          <li>O sistema exibe mensagem: "Não foi possível consultar o CNPJ automaticamente. Preencha os dados manualmente para continuar."</li>
          <li>O sistema habilita o preenchimento manual de todos os campos.</li>
          <li>O sistema exibe badge cinza "Dados Manuais".</li>
          <li>O ator preenche manualmente e prossegue.</li>
        </ol>
        <a id="e3">[E3] - CNPJ não encontrado</a>
        <ol>
          <li>No passo 6, a API retorna que o CNPJ não existe na base de dados.</li>
          <li>O sistema exibe mensagem: "CNPJ não encontrado. Verifique se o número está correto ou preencha os dados manualmente."</li>
          <li>O sistema habilita preenchimento manual dos campos.</li>
          <li>O ator pode corrigir o CNPJ ou prosseguir manualmente.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Regras de negócio</strong></td>
      <td>
        <a id="rn1">[RN1] - Consulta de CNPJ</a><br>
        <ul>
          <li>API utilizada: ReceitaWS ou BrasilAPI (fallback)</li>
          <li>Timeout máximo: 10 segundos</li>
          <li>A consulta é <strong>opcional</strong> - apenas facilita preenchimento</li>
          <li>Situação cadastral é <strong>informativa</strong> - não bloqueia simulação</li>
          <li>Todos os campos consultados podem ser editados pelo usuário</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>
