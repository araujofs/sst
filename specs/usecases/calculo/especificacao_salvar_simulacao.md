<table>
  <tbody>
    <tr>
      <td><strong>Caso de uso</strong></td>
      <td>
        <strong><span><a>UC10 - Salvar Simulação</a></span></strong>
      </td>
    </tr>
    <tr>
      <td><strong>Objetivo</strong></td>
      <td>
        Permitir que o contador ou gerente salve uma simulação tributária com todos os dados de entrada, resultados calculados e histórico de alterações para consulta futura.
      </td>
    </tr>
    <tr>
      <td><strong>Requisitos</strong></td>
      <td>RF-CAL-003, RF-CAL-004</td>
    </tr>
    <tr>
      <td><strong>Atores</strong></td>
      <td>Contador, Gerente</td>
    </tr>
    <tr>
      <td><strong>Condições de entrada</strong></td>
      <td>O ator finalizou uma simulação e está visualizando os resultados.</td>
    </tr>
    <tr>
      <td><strong>Fluxo principal</strong></td>
      <td>
        <ol>
          <li>O ator clica no botão "Salvar Simulação".</li>
          <li>O sistema exibe modal solicitando:
            <ul>
              <li>Nome da simulação (campo obrigatório)</li>
              <li>Descrição/Observações (campo opcional)</li>
              <li>Cliente associado (dropdown com lista de clientes cadastrados)</li>
              <li>Tags para categorização (campo opcional, múltipla seleção)</li>
            </ul>
          </li>
          <li>O ator preenche os dados.</li>
          <li>O ator clica em "Confirmar".</li>
          <li>O sistema valida que o nome foi preenchido. <a href="#e1">[E1]</a></li>
          <li>O sistema salva no banco de dados:
            <ul>
              <li>Nome e descrição da simulação</li>
              <li>Cliente associado</li>
              <li>Data e hora do salvamento</li>
              <li>Usuário que salvou</li>
              <li>Todos os dados de entrada (CNPJ, CNAE, receitas, despesas, etc.)</li>
              <li>Regime(s) tributário(s) simulado(s)</li>
              <li>Todos os resultados calculados</li>
              <li>Versão das tabelas tributárias utilizadas</li>
              <li>Tags selecionadas</li>
            </ul>
          </li>
          <li>O sistema gera um ID único para a simulação.</li>
          <li>O sistema exibe mensagem de sucesso: "Simulação '[Nome]' salva com sucesso!"</li>
          <li>O sistema fecha o modal e retorna à tela de resultados.</li>
          <li>O sistema habilita o botão "Atualizar Simulação" na tela. <a href="#a1">[A1]</a></li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos alternativos</strong></td>
      <td>
        <a id="a1">[A1] - Alterar simulação para análise de sensibilidade</a>
        <ol>
          <li>No passo 1, se a simulação já foi salva anteriormente, o ator pode clicar em "Alterar Valores".</li>
          <li>O sistema exibe modal de edição permitindo alterar:
            <ul>
              <li>Valores de receita</li>
              <li>Valores de despesas</li>
              <li>Outros parâmetros financeiros</li>
            </ul>
          </li>
          <li>O ator modifica os valores desejados para análise de sensibilidade.</li>
          <li>O sistema recalcula automaticamente os resultados com os novos valores.</li>
          <li>O sistema exibe modal: "Deseja salvar esta variação?"
            <ul>
              <li>Opção: "Salvar como nova versão no histórico"</li>
              <li>Opção: "Apenas visualizar (não salvar)"</li>
              <li>Opção: "Cancelar alterações"</li>
            </ul>
          </li>
          <li>Se o ator selecionar "Salvar como nova versão":
            <ul>
              <li>O sistema solicita nome para a nova versão (ex: "Projeção +10% receita")</li>
              <li>O sistema cria um registro no histórico vinculado à simulação original com:
                <ul>
                  <li>Data/hora da criação</li>
                  <li>Usuário responsável</li>
                  <li>Valores originais vs. novos valores</li>
                  <li>Resultados calculados</li>
                </ul>
              </li>
              <li>O sistema exibe: "Nova versão salva no histórico da simulação."</li>
            </ul>
          </li>
          <li>Se o ator selecionar "Apenas visualizar", retorna à tela de resultados sem salvar.</li>
          <li>Se o ator selecionar "Cancelar", restaura os valores originais.</li>
        </ol>
        <a id="a2">[A2] - Cancelar salvamento</a>
        <ol>
          <li>A qualquer momento antes do passo 6, o ator pode clicar em "Cancelar".</li>
          <li>O sistema fecha o modal sem salvar.</li>
          <li>O sistema retorna à tela de resultados.</li>
          <li>O caso de uso é encerrado.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos de exceção</strong></td>
      <td>
        <a id="e1">[E1] - Nome não preenchido</a>
        <ol>
          <li>No passo 5, o sistema identifica que o campo "Nome" está vazio.</li>
          <li>O sistema exibe mensagem de validação: "O nome da simulação é obrigatório."</li>
          <li>O sistema destaca o campo "Nome" em vermelho.</li>
          <li>Retorna ao passo 3 do fluxo principal.</li>
        </ol>
        <a id="e2">[E2] - Nome duplicado</a>
        <ol>
          <li>No passo 6, o sistema identifica que já existe uma simulação com o mesmo nome para o mesmo cliente.</li>
          <li>O sistema exibe alerta: "Já existe uma simulação com esse nome. Deseja:
            <ul>
              <li>Substituir a existente</li>
              <li>Usar outro nome</li>
            </ul>
          </li>
          <li>Se o ator escolher "Substituir", prossegue aplicando o fluxo [A1].</li>
          <li>Se o ator escolher "Usar outro nome", retorna ao passo 3.</li>
        </ol>
        <a id="e3">[E3] - Erro ao salvar no banco</a>
        <ol>
          <li>No passo 6, ocorre erro ao tentar salvar no banco de dados.</li>
          <li>O sistema registra o erro no log.</li>
          <li>O sistema exibe mensagem: "Erro ao salvar simulação. Tente novamente. Se o problema persistir, contate o suporte."</li>
          <li>O sistema mantém o modal aberto para o ator tentar novamente.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Regras de negócio</strong></td>
      <td>
        <a id="rn1">[RN1] - Histórico de alterações</a><br>
        Todas as atualizações em simulações salvas devem ser registradas em histórico, mantendo:
        <ul>
          <li>Snapshot completo dos dados anteriores</li>
          <li>Data/hora da modificação</li>
          <li>Usuário responsável pela alteração</li>
          <li>Versão das tabelas tributárias usadas</li>
        </ul>
        Isso permite auditoria e rastreabilidade completa.<br><br>
        <a id="rn2">[RN2] - Versionamento de tabelas tributárias</a><br>
        Ao salvar, o sistema deve registrar qual versão das tabelas do Simples Nacional, alíquotas de presunção e demais parâmetros tributários foi utilizada. Se as tabelas forem atualizadas posteriormente, a simulação salva preserva os valores calculados com a versão original.<br><br>
        <a id="rn3">[RN3] - Associação com cliente</a><br>
        Sempre que possível, a simulação deve ser associada a um cliente cadastrado para:
        <ul>
          <li>Facilitar consultas futuras por cliente</li>
          <li>Gerar relatórios consolidados por cliente</li>
          <li>Rastrear histórico de análises do cliente</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>
