<table>
  <tbody>
    <tr>
      <td><strong>Caso de uso</strong></td>
      <td>
        <strong><span><a>UC13 - Gerenciar Alíquotas de ISS e ICMS</a></span></strong>
      </td>
    </tr>
    <tr>
      <td><strong>Objetivo</strong></td>
      <td>
        Permitir que o administrador cadastre e atualize manualmente as alíquotas de ISS (por município) e ICMS (por UF) para uso nas simulações tributárias.
      </td>
    </tr>
    <tr>
      <td><strong>Requisitos</strong></td>
      <td>RF-LEG-003</td>
    </tr>
    <tr>
      <td><strong>Atores</strong></td>
      <td>Administrador</td>
    </tr>
    <tr>
      <td><strong>Condições de entrada</strong></td>
      <td>O administrador precisa cadastrar ou atualizar alíquotas de impostos municipais (ISS) ou estaduais (ICMS).</td>
    </tr>
    <tr>
      <td><strong>Fluxo principal</strong></td>
      <td>
        <ol>
          <li>O administrador acessa o módulo "Administração > Legislação > Alíquotas Locais".</li>
          <li>O sistema exibe duas abas:
            <ul>
              <li>ISS (Imposto Sobre Serviços - Municipal)</li>
              <li>ICMS (Imposto sobre Circulação de Mercadorias - Estadual)</li>
            </ul>
          </li>
          <li>O administrador seleciona a aba desejada.</li>
          <li>O sistema exibe tabela com as alíquotas cadastradas:
            <ul>
              <li><strong>ISS:</strong> Município, UF, Alíquota, Data Vigência, Base Legal, Ações</li>
              <li><strong>ICMS:</strong> UF, Alíquota Interna, Alíquota Interestadual, Data Vigência, Base Legal, Ações</li>
            </ul>
          </li>
          <li>O sistema oferece:
            <ul>
              <li>Campo de busca para filtrar por município/UF</li>
              <li>Botão "Cadastrar Nova Alíquota"</li>
              <li>Botão "Importar Planilha"</li>
            </ul>
          </li>
          <li>O administrador clica em "Cadastrar Nova Alíquota".</li>
          <li>O sistema exibe formulário modal:
            <ul>
              <li><strong>Para ISS:</strong>
                <ul>
                  <li>Município (dropdown com autocomplete)</li>
                  <li>UF (dropdown)</li>
                  <li>Código IBGE do município (preenchido automaticamente)</li>
                  <li>Alíquota (%) (campo numérico, min: 2%, max: 5%)</li>
                  <li>Data de Início de Vigência (campo data)</li>
                  <li>Base Legal (texto, ex: "Lei Municipal nº 1234/2023")</li>
                  <li>Observações (opcional)</li>
                </ul>
              </li>
              <li><strong>Para ICMS:</strong>
                <ul>
                  <li>UF (dropdown)</li>
                  <li>Alíquota Interna (%) (campo numérico, geralmente 17-18%)</li>
                  <li>Alíquota Interestadual (%) (campo numérico, geralmente 7-12%)</li>
                  <li>Data de Início de Vigência</li>
                  <li>Base Legal (texto, ex: "Decreto Estadual nº 5678/2024")</li>
                  <li>Observações (opcional)</li>
                </ul>
              </li>
            </ul>
          </li>
          <li>O administrador preenche os campos.</li>
          <li>O sistema valida os dados em tempo real. <a href="#e1">[E1]</a></li>
          <li>O administrador clica em "Salvar".</li>
          <li>O sistema verifica se já existe alíquota vigente para aquele município/UF. <a href="#a1">[A1]</a></li>
          <li>O sistema salva a nova alíquota no banco de dados.</li>
          <li>O sistema registra no histórico:
            <ul>
              <li>Data/hora do cadastro</li>
              <li>Usuário responsável</li>
              <li>Dados cadastrados</li>
            </ul>
          </li>
          <li>O sistema exibe mensagem: "Alíquota cadastrada com sucesso para [Município/UF]."</li>
          <li>O sistema atualiza a tabela com a nova entrada.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos alternativos</strong></td>
      <td>
        <a id="a1">[A1] - Alíquota já existe (atualização)</a>
        <ol>
          <li>No passo 11, o sistema identifica que já existe alíquota vigente para o município/UF selecionado.</li>
          <li>O sistema exibe modal: "Já existe alíquota cadastrada para [Local]:
            <ul>
              <li>Alíquota atual: [X]%</li>
              <li>Vigente desde: [Data]</li>
              <li>Base legal: [Lei]</li>
            </ul>
            Deseja:
            <ul>
              <li>[Botão] Atualizar alíquota (nova vigência)</li>
              <li>[Botão] Cancelar e manter atual</li>
            </ul>
          </li>
          <li>Se o administrador escolher "Atualizar":
            <ul>
              <li>O sistema marca a alíquota anterior como "histórica" (fim de vigência = data anterior à nova)</li>
              <li>O sistema salva a nova alíquota</li>
              <li>O sistema exibe: "Alíquota atualizada. A anterior permanece no histórico."</li>
            </ul>
          </li>
          <li>Se o administrador escolher "Cancelar", retorna ao passo 8.</li>
        </ol>
        <a id="a2">[A2] - Editar alíquota existente</a>
        <ol>
          <li>No passo 6, o administrador clica no ícone "Editar" de uma alíquota existente.</li>
          <li>O sistema exibe o formulário preenchido com os dados atuais.</li>
          <li>O administrador altera os campos desejados.</li>
          <li>O sistema valida as mudanças.</li>
          <li>O administrador confirma.</li>
          <li>O sistema pergunta: "Deseja criar nova versão ou sobrescrever?"</li>
          <li>Se "Nova versão", aplica fluxo [A1].</li>
          <li>Se "Sobrescrever", atualiza diretamente e registra no log de auditoria.</li>
        </ol>
        <a id="a3">[A3] - Importar planilha em lote</a>
        <ol>
          <li>No passo 6, o administrador clica em "Importar Planilha".</li>
          <li>O sistema exibe modal solicitando arquivo .xlsx ou .csv.</li>
          <li>O sistema fornece link "Baixar Template" com formato esperado.</li>
          <li>O administrador faz upload do arquivo.</li>
          <li>O sistema valida a estrutura e os dados. <a href="#e2">[E2]</a></li>
          <li>O sistema exibe preview em tabela com as alíquotas a serem importadas.</li>
          <li>O sistema indica se cada linha será "Nova" ou "Atualização de existente".</li>
          <li>O administrador revisa e confirma.</li>
          <li>O sistema processa em lote:
            <ul>
              <li>Cadastra novas alíquotas</li>
              <li>Atualiza existentes conforme regras</li>
              <li>Registra todas as operações no histórico</li>
            </ul>
          </li>
          <li>O sistema exibe resumo: "[X] cadastradas, [Y] atualizadas, [Z] com erro".</li>
          <li>Se houver erros, o sistema exibe relatório com as linhas que falharam e os motivos.</li>
        </ol>
        <a id="a4">[A4] - Consultar histórico de alíquotas</a>
        <ol>
          <li>No passo 6, o administrador clica no ícone "Histórico" de um município/UF.</li>
          <li>O sistema exibe linha do tempo com todas as alíquotas que já vigoraram:
            <ul>
              <li>Alíquota (%)</li>
              <li>Período de vigência (início - fim)</li>
              <li>Base legal</li>
              <li>Usuário que cadastrou</li>
            </ul>
          </li>
          <li>O administrador pode visualizar detalhes de cada período.</li>
          <li>O administrador pode restaurar uma alíquota histórica (ela se torna a vigente com nova data).</li>
        </ol>
        <a id="a5">[A5] - Excluir alíquota</a>
        <ol>
          <li>No passo 6, o administrador clica no ícone "Excluir" de uma alíquota.</li>
          <li>O sistema exibe confirmação: "Tem certeza? Esta alíquota será movida para o histórico e não estará mais disponível para novas simulações."</li>
          <li>Se o administrador confirmar:
            <ul>
              <li>O sistema marca a alíquota como inativa (não exclui do banco)</li>
              <li>O sistema registra a exclusão no log</li>
              <li>Simulações antigas que usaram essa alíquota preservam os valores</li>
            </ul>
          </li>
          <li>O sistema exibe: "Alíquota removida das opções ativas."</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos de exceção</strong></td>
      <td>
        <a id="e1">[E1] - Dados inválidos no formulário</a>
        <ol>
          <li>No passo 9, o sistema identifica erros de validação:
            <ul>
              <li>Alíquota ISS fora do intervalo 2%-5%</li>
              <li>Alíquota ICMS fora do intervalo válido (0%-25%)</li>
              <li>Data de vigência no passado</li>
              <li>Município/UF não selecionado</li>
              <li>Base legal vazia</li>
            </ul>
          </li>
          <li>O sistema exibe mensagens de erro específicas ao lado de cada campo inválido.</li>
          <li>O sistema destaca os campos em vermelho.</li>
          <li>O administrador corrige os erros.</li>
          <li>Retorna ao passo 9.</li>
        </ol>
        <a id="e2">[E2] - Erro na importação de planilha</a>
        <ol>
          <li>No fluxo [A3], o sistema identifica problemas no arquivo:
            <ul>
              <li>Formato incorreto (colunas faltando ou nomes errados)</li>
              <li>Valores inválidos (alíquotas fora do range, datas inválidas)</li>
              <li>Municípios não encontrados no cadastro IBGE</li>
              <li>Arquivo corrompido ou muito grande (> 5MB)</li>
            </ul>
          </li>
          <li>O sistema exibe relatório de erros:
            <ul>
              <li>Linha X: "Município não encontrado: [Nome]"</li>
              <li>Linha Y: "Alíquota ISS inválida: 8% (máximo 5%)"</li>
            </ul>
          </li>
          <li>O administrador pode corrigir o arquivo e reimportar.</li>
        </ol>
        <a id="e3">[E3] - Erro ao salvar no banco</a>
        <ol>
          <li>No passo 12, ocorre erro ao salvar no banco de dados.</li>
          <li>O sistema faz rollback da transação.</li>
          <li>O sistema registra o erro no log.</li>
          <li>O sistema exibe: "Erro ao salvar alíquota. Tente novamente. Se persistir, contate o suporte."</li>
          <li>Retorna ao passo 8.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Regras de negócio</strong></td>
      <td>
        <a id="rn1">[RN1] - Limites de alíquotas</a><br>
        <strong>ISS:</strong> Alíquota mínima de 2% e máxima de 5% conforme Lei Complementar nº 116/2003.<br>
        <strong>ICMS:</strong> Alíquotas variam por estado, geralmente entre 17-18% (interna) e 7-12% (interestadual).<br><br>
        <a id="rn2">[RN2] - Código IBGE</a><br>
        Todo município deve estar vinculado ao seu código IBGE oficial (7 dígitos). O sistema deve manter tabela atualizada de municípios brasileiros com seus códigos.<br><br>
        <a id="rn3">[RN3] - Vigência e histórico</a><br>
        <ul>
          <li>Apenas uma alíquota pode estar "vigente" por município/UF em um dado momento</li>
          <li>Alíquotas antigas não são excluídas, apenas marcadas como históricas</li>
          <li>Simulações antigas preservam os valores calculados com a alíquota vigente na época</li>
          <li>O sistema deve alertar se a data de vigência for muito recente (< 30 dias) para dar tempo de adaptação</li>
        </ul><br>
        <a id="rn4">[RN4] - Base legal obrigatória</a><br>
        Toda alíquota cadastrada DEVE ter base legal (lei municipal/estadual) informada para garantir rastreabilidade e conformidade.<br><br>
        <a id="rn5">[RN5] - Uso nas simulações</a><br>
        Durante uma simulação, quando o usuário informa o município/UF da empresa:
        <ul>
          <li>O sistema busca automaticamente a alíquota vigente naquela localidade</li>
          <li>Se não houver alíquota cadastrada, o sistema usa valor padrão (ISS: 5%, ICMS: 18%) e exibe alerta</li>
          <li>O usuário pode sobrescrever manualmente a alíquota na simulação</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>
