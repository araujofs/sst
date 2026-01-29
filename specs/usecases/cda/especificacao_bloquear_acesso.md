<table>
  <tbody>
    <tr>
      <td><strong>Caso de uso</strong></td>
      <td>
        <strong><span><a>UC02 - Bloquear acesso</a></span></strong>
      </td>
    </tr>
    <tr>
      <td><strong>Objetivo</strong></td>
      <td>
        Impedir acessos indesejados por invasores nas contas dos usuários do
        sistema.
      </td>
    </tr>
    <tr>
      <td><strong>Requisitos</strong></td>
      <td>RF-AUT-009</td>
    </tr>
    <tr>
      <td><strong>Atores</strong></td>
      <td>Usuário</td>
    </tr>
    <tr>
      <td><strong>Condições de entrada</strong></td>
      <td>
        O ator falha duas vezes ao tentar se credenciar no sistema.
      </td>
    </tr>
    <tr>
      <td><strong>Fluxo principal</strong></td>
      <td>
        <ol>
          <li>
            O ator segue o fluxo alternativo <a href="especificacao_fazer_login.md#a2">[A2]</a> do caso de uso <a href="especificacao_fazer_login.md">[UC1]</a>.
          </li>
          <li>
            O sistema bloqueia o acesso do usuário, impedindo novas tentativas
            de credenciamento até que um administrador realize a liberação.
          </li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos alternativos</strong></td>
      <td>Nenhum</td>
    </tr>
    <tr>
      <td><strong>Fluxos de exceção</strong></td>
      <td>
        <a>[RN1] - Credenciamento de usuário</a><br>
        O usuário deve ser cadastrado previamente no sistema por um gestor e usar as credenciais informadas para ter acesso aos outros módulos.
      </td>
    </tr>
  </tbody>
</table>
