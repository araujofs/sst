<table>
  <tbody>
    <tr>
      <td><strong>Caso de uso</strong></td>
      <td>
        <strong
          ><span><a>UCxx - Visualizar logs</a></span></strong
        >
      </td>
    </tr>
    <tr>
      <td><strong>Objetivo</strong></td>
      <td>
        Ajudar na identificação de erros que possam existir no sistema.
      </td>
    </tr>
    <tr>
      <td><strong>Requisitos</strong></td>
      <td>RF-ADM-001</td>
    </tr>
    <tr>
      <td><strong>Atores</strong></td>
      <td>Administrador</td>
    </tr>
    <tr>
      <td><strong>Condições de entrada</strong></td>
      <td>
        O ator se encontra no menu 'Logs' da configuração do sistema. 
      </td>
    </tr>
    <tr>
      <td><strong>Fluxo principal</strong></td>
      <td>
        <ol>
          <li>
            O ator se encontrar nas configurações do sistema. Ele observa que há uma lista de logs. Ele verifica que pode ver alguns dados básicos dos logs na lista.
          </li>
          <li>
            O ator seleciona um dos logs.
          </li>
          <li>
            O ator observa que agora está numa tela com mais detalhes do log, como:
            <ul>
              <li>Data e hora</li>
              <li>Tipo</li>
              <li>Origem</li>
              <li>Nível</li>
              <li>Mensagem resumida</li>
              <li>Mensagem detalhada</li>
              <li>Stack Trace</li>
            </ul>
            E a opção 'Fechar'.
          </li>
          <li>
            O ator seleciona a opção 'Fechar'.
          </li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos alternativos</strong></td>
      <td>
        Nenhum
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos de exceção</strong></td>
      <td>Nenhum</td>
    </tr>
  </tbody>
</table>
