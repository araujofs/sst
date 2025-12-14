<table>
  <tbody>
    <tr>
      <td><strong>Caso de uso</strong></td>
      <td>
        <strong><span><a>UC20 - Atualizar Tabelas Tributárias</a></span></strong>
      </td>
    </tr>
    <tr>
      <td><strong>Objetivo</strong></td>
      <td>
        Permitir que o administrador atualize manualmente as tabelas do Simples Nacional e outras alíquotas tributárias para manter o sistema alinhado com a legislação vigente.
      </td>
    </tr>
    <tr>
      <td><strong>Requisitos</strong></td>
      <td>RF-LEG-001, RF-LEG-002</td>
    </tr>
    <tr>
      <td><strong>Atores</strong></td>
      <td>Administrador</td>
    </tr>
    <tr>
      <td><strong>Condições de entrada</strong></td>
      <td>O administrador recebeu notificação de atualização na legislação tributária (Receita Federal) ou identificou necessidade de correção.</td>
    </tr>
    <tr>
      <td><strong>Fluxo principal</strong></td>
      <td>
        <ol>
          <li>O administrador acessa o módulo "Administração > Legislação > Tabelas Tributárias".</li>
          <li>O sistema exibe as tabelas atuais com suas versões:
            <ul>
              <li>Tabela Simples Nacional (Anexos I a V)</li>
              <li>Alíquotas de Presunção (Lucro Presumido)</li>
              <li>Alíquotas de IRPJ e CSLL</li>
              <li>Alíquotas de PIS e COFINS</li>
              <li>Mapeamento CNAE → Anexo</li>
            </ul>
          </li>
          <li>Para cada tabela, o sistema mostra:
            <ul>
              <li>Versão atual (ex: "v2.1 - vigente desde 01/01/2024")</li>
              <li>Data da última atualização</li>
              <li>Usuário responsável pela última atualização</li>
              <li>Botões: "Visualizar", "Atualizar", "Histórico"</li>
            </ul>
          </li>
          <li>O administrador clica em "Atualizar" na tabela desejada.</li>
          <li>O sistema exibe modal com opções de atualização:
            <ul>
              <li>"Importar arquivo (.xlsx ou .csv)"</li>
              <li>"Editar manualmente"</li>
            </ul>
          </li>
          <li>O administrador seleciona "Importar arquivo". <a href="#a1">[A1]</a></li>
          <li>O administrador faz upload do arquivo.</li>
          <li>O sistema valida a estrutura do arquivo. <a href="#e1">[E1]</a> <a href="#rn1">[RN1]</a></li>
          <li>O sistema exibe preview dos dados a serem importados em tabela comparativa:
            <ul>
              <li>Coluna 1: Dados atuais no sistema</li>
              <li>Coluna 2: Dados do arquivo importado</li>
              <li>Destacando em amarelo as diferenças</li>
            </ul>
          </li>
          <li>O sistema solicita:
            <ul>
              <li>Data de início da vigência (campo obrigatório)</li>
              <li>Base legal (número da lei/resolução/IN) (campo obrigatório)</li>
              <li>Descrição resumida das mudanças (campo obrigatório)</li>
            </ul>
          </li>
          <li>O administrador preenche os campos e confirma.</li>
          <li>O sistema valida os dados. <a href="#e2">[E2]</a></li>
          <li>O sistema exibe confirmação: "Confirmar atualização? Esta ação será registrada no histórico."</li>
          <li>O administrador confirma.</li>
          <li>O sistema cria backup da versão anterior com timestamp.</li>
          <li>O sistema atualiza as tabelas no banco de dados.</li>
          <li>O sistema cria registro no histórico de atualizações:
            <ul>
              <li>Data/hora da atualização</li>
              <li>Versão anterior → Nova versão</li>
              <li>Usuário responsável</li>
              <li>Base legal</li>
              <li>Descrição das mudanças</li>
              <li>Arquivo importado (anexo)</li>
            </ul>
          </li>
          <li>O sistema notifica todos os usuários sobre a atualização. <a href="#a2">[A2]</a></li>
          <li>O sistema exibe mensagem de sucesso: "Tabela atualizada com sucesso. Vigência a partir de [data]."</li>
          <li>O sistema identifica simulações salvas que foram calculadas com a versão anterior. <a href="#a3">[A3]</a></li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos alternativos</strong></td>
      <td>
        <a id="a1">[A1] - Editar manualmente</a>
        <ol>
          <li>No passo 6, o administrador seleciona "Editar manualmente".</li>
          <li>O sistema exibe formulário com os dados atuais em campos editáveis.</li>
          <li>Para Simples Nacional, exibe 6 faixas × 5 anexos com campos:
            <ul>
              <li>Limite inferior e superior da faixa</li>
              <li>Alíquota Nominal (%)</li>
              <li>Parcela a Deduzir (R$)</li>
            </ul>
          </li>
          <li>O administrador altera os valores necessários.</li>
          <li>O sistema valida em tempo real (alíquotas entre 0-100%, valores numéricos positivos).</li>
          <li>Retorna ao passo 10 do fluxo principal.</li>
        </ol>
        <a id="a2">[A2] - Notificar usuários</a>
        <ol>
          <li>No passo 18, o sistema envia notificação in-app e por e-mail para todos os usuários ativos:</li>
          <li>Assunto: "Atualização de Legislação Tributária - [Tabela]"</li>
          <li>Conteúdo:
            <ul>
              <li>Descrição resumida das mudanças</li>
              <li>Data de vigência</li>
              <li>Base legal</li>
              <li>Link para visualizar detalhes completos</li>
            </ul>
          </li>
          <li>A notificação fica visível no sino de notificações até ser lida.</li>
        </ol>
        <a id="a3">[A3] - Marcar simulações afetadas</a>
        <ol>
          <li>No passo 20, o sistema busca no banco todas as simulações salvas que usaram a versão anterior.</li>
          <li>Para cada simulação encontrada, o sistema:
            <ul>
              <li>Adiciona badge "Alerta de Atualização Legislativa"</li>
              <li>Registra log indicando mudança na legislação</li>
              <li>Exibe banner ao reabrir: "Esta simulação foi calculada com legislação anterior. Deseja recalcular com os valores atualizados?"</li>
            </ul>
          </li>
          <li>O sistema contabiliza quantas simulações foram afetadas.</li>
          <li>O sistema exibe ao administrador: "[X] simulações salvas foram afetadas pela atualização."</li>
        </ol>
        <a id="a4">[A4] - Visualizar histórico</a>
        <ol>
          <li>No passo 4, o administrador clica em "Histórico" de uma tabela.</li>
          <li>O sistema exibe linha do tempo cronológica reversa com:
            <ul>
              <li>Data da atualização</li>
              <li>Versão</li>
              <li>Usuário responsável</li>
              <li>Base legal</li>
              <li>Descrição das mudanças</li>
              <li>Botões: "Ver detalhes", "Restaurar versão"</li>
            </ul>
          </li>
          <li>O administrador pode clicar em "Ver detalhes" para visualizar os dados daquela versão.</li>
          <li>O administrador pode clicar em "Restaurar versão" para reverter. <a href="#a5">[A5]</a></li>
        </ol>
        <a id="a5">[A5] - Restaurar versão anterior</a>
        <ol>
          <li>No fluxo [A4], o administrador clica em "Restaurar versão".</li>
          <li>O sistema exibe confirmação: "Tem certeza que deseja restaurar a versão [v] de [data]? A versão atual será substituída."</li>
          <li>O administrador confirma.</li>
          <li>O sistema cria backup da versão atual.</li>
          <li>O sistema restaura a versão selecionada.</li>
          <li>O sistema registra a restauração no histórico como nova entrada.</li>
          <li>O sistema notifica os usuários sobre a restauração.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos de exceção</strong></td>
      <td>
        <a id="e1">[E1] - Arquivo com formato inválido</a>
        <ol>
          <li>No passo 8, o sistema identifica que o arquivo não está no formato esperado.</li>
          <li>O sistema exibe mensagem: "Arquivo inválido. Verifique:
            <ul>
              <li>Formato deve ser .xlsx ou .csv</li>
              <li>Deve conter as colunas obrigatórias: [lista]</li>
              <li>Valores devem ser numéricos</li>
            </ul>
          </li>
          <li>O sistema oferece botão "Baixar Template" para download de modelo correto.</li>
          <li>Retorna ao passo 7.</li>
        </ol>
        <a id="e2">[E2] - Dados inconsistentes</a>
        <ol>
          <li>No passo 12, o sistema identifica inconsistências:
            <ul>
              <li>Alíquotas fora do intervalo válido (0-100%)</li>
              <li>Faixas de receita com sobreposição</li>
              <li>Valores negativos em campos que deveriam ser positivos</li>
              <li>Data de vigência no passado (antes da data atual)</li>
            </ul>
          </li>
          <li>O sistema exibe lista de erros encontrados com localização (linha/coluna).</li>
          <li>O sistema destaca em vermelho os campos com erro.</li>
          <li>O administrador corrige os erros.</li>
          <li>Retorna ao passo 12.</li>
        </ol>
        <a id="e3">[E3] - Erro ao salvar no banco</a>
        <ol>
          <li>No passo 16, ocorre erro ao atualizar as tabelas no banco de dados.</li>
          <li>O sistema faz rollback automático para a versão anterior.</li>
          <li>O sistema restaura o backup.</li>
          <li>O sistema registra o erro no log.</li>
          <li>O sistema exibe mensagem: "Erro ao atualizar tabela. As alterações foram revertidas. Contate o suporte técnico."</li>
          <li>O caso de uso é encerrado sem aplicar mudanças.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Regras de negócio</strong></td>
      <td>
        <a id="rn1">[RN1] - Estrutura esperada dos arquivos de importação</a><br>
        <strong>Simples Nacional (Anexos I a V):</strong>
        <ul>
          <li>Colunas obrigatórias: Anexo, Faixa, Limite_Inferior, Limite_Superior, Aliquota_Nominal, Parcela_Deduzir</li>
          <li>6 faixas por anexo × 5 anexos = 30 linhas</li>
        </ul>
        <strong>Alíquotas de Presunção:</strong>
        <ul>
          <li>Colunas: Tipo_Atividade, Aliquota_IRPJ, Aliquota_CSLL</li>
        </ul>
        <strong>Mapeamento CNAE:</strong>
        <ul>
          <li>Colunas: CNAE, Descricao, Anexo, Sujeito_Fator_R (Sim/Não)</li>
        </ul><br>
        <a id="rn2">[RN2] - Versionamento semântico</a><br>
        As versões seguem padrão vX.Y onde:
        <ul>
          <li><strong>X (Major):</strong> Mudança significativa na legislação (ex: nova faixa, novo anexo)</li>
          <li><strong>Y (Minor):</strong> Ajustes de alíquotas, correções</li>
        </ul><br>
        <a id="rn3">[RN3] - Auditoria e rastreabilidade</a><br>
        Toda atualização de tabela DEVE ser:
        <ul>
          <li>Registrada no histórico com data/hora e usuário</li>
          <li>Acompanhada de justificativa (base legal)</li>
          <li>Notificada a todos os usuários</li>
          <li>Reversível (através do histórico de versões)</li>
        </ul>
        Simulações antigas preservam os valores calculados com a versão usada na época.
      </td>
    </tr>
  </tbody>
</table>
