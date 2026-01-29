<table>
  <tbody>
    <tr>
      <td><strong>Caso de uso</strong></td>
      <td>
        <strong><span><a>UC - 17 Notificar Usuário sobre Impacto de Mudança Legislativa</a></span></strong>
      </td>
    </tr>
    <tr>
      <td><strong>Objetivo</strong></td>
      <td>
        Exibir aviso visual simples para o usuário quando uma simulação salva foi impactada por mudança na legislação tributária.
      </td>
    </tr>
    <tr>
      <td><strong>Requisitos</strong></td>
      <td>RF-CAL-007</td>
    </tr>
    <tr>
      <td><strong>Atores</strong></td>
      <td>Sistema (automático), Contador, Gerente</td>
    </tr>
    <tr>
      <td><strong>Condições de entrada</strong></td>
      <td>O administrador atualizou as tabelas tributárias em <a href="../atualizacao/especificacao_atualizar_tabelas_tributarias.md">[UC12]</a> ou <a href="../atualizacao/especificacao_gerenciar_aliquotas_iss_icms.md">[UC13]</a>.</td>
    </tr>
    <tr>
      <td><strong>Fluxo principal</strong></td>
      <td>
        <ol>
          <li>O sistema detecta que houve atualização nas tabelas tributárias em <a href="../atualizacao/especificacao_atualizar_tabelas_tributarias.md">[UC12]</a> ou <a href="../atualizacao/especificacao_gerenciar_aliquotas_iss_icms.md">[UC13]</a>.</li>
          <li>O sistema identifica todas as simulações salvas que utilizaram as tabelas antigas.</li>
          <li>Para cada simulação impactada:
            <ul>
              <li>O sistema marca a simulação com flag "desatualizada"</li>
              <li>O sistema adiciona badge visual vermelho no card da simulação com texto "Desatualizada"</li>
            </ul>
          </li>
          <li>O sistema cria uma notificação simples no ícone de sino.</li>
          <li>A notificação contém apenas: "Algumas simulações foram impactadas por atualização legislativa"</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos alternativos</strong></td>
      <td>
        <a id="a1">[A1] - Usuário visualiza notificação</a>
        <ol>
          <li>O usuário acessa o sistema e visualiza o ícone de notificações com contador.</li>
          <li>O usuário clica no ícone de notificações.</li>
          <li>O sistema exibe lista de notificações.</li>
          <li>O usuário clica em uma notificação de mudança legislativa.</li>
          <li>O sistema exibe detalhes da mudança: descrição, data de vigência e simulações impactadas.</li>
          <li>O usuário pode clicar em "Visualizar Simulação" para abrir a simulação em modo de leitura.</li>
          <li>O usuário pode clicar em "Marcar como Lida" para remover a notificação.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos de exceção</strong></td>
      <td>Não há fluxos alternativos.</td>
    </tr>
    <tr>
      <td><strong>Fluxos de exceção</strong></td>
      <td>
        Não há fluxos de exceção.
      </td>
    </tr>
    <tr>
      <td><strong>Regras de negócio</strong></td>
      <td>
        <a id="rn1">[RN1] - Badge visual</a><br>
        O badge "Desatualizada" aparece com fundo vermelho no card da simulação na lista de histórico. O usuário pode ver quais simulações foram impactadas pela cor diferenciada.
      </td>
    </tr>