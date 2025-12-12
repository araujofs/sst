<table>
  <tbody>
    <tr>
      <td><strong>Caso de uso</strong></td>
      <td>
        <strong
          ><span><a>UCxx - Reportar erro</a></span></strong
        >
      </td>
    </tr>
    <tr>
      <td><strong>Objetivo</strong></td>
      <td>
        Ajudar na resolução rápida e eficiente de erros que possam existir no sistema.
      </td>
    </tr>
    <tr>
      <td><strong>Requisitos</strong></td>
      <td>RF-ADM-012</td>
    </tr>
    <tr>
      <td><strong>Atores</strong></td>
      <td>Administrador</td>
    </tr>
    <tr>
      <td><strong>Condições de entrada</strong></td>
      <td>
        O sistema detectou um erro crítico.
      </td>
    </tr>
    <tr>
      <td><strong>Fluxo principal</strong></td>
      <td>
        <ol>
          <li>
            O ator se encontra em qualquer página do sistema. Ele verifica no menu lateral que existe um ícone de sino com um número. Ele clica no sino.
          </li>
          <li>
            O ator observa que apareceu uma lista com notificações de erros críticos com mensagens curtas do sistema. Ele seleciona uma delas.
          </li>
          <li>
            O ator é levado à página de saúde do sistema <a href="especificacao_visualizar_saude_sistema.md">[UCxx]</a> onde pode ver várias informações. Dentre elas há uma lista com os erros do sistema onde ele consegue ver o erro crítico do qual foi notificado com algumas informações:
            <ul>
              <li>Data e hora</li>
              <li>Tipo</li>
              <li>Severidade</li>
              <li>Stack Trace</li>
              <li>Mensagem clara</li>
            </ul>
          </li>
          <li>
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
