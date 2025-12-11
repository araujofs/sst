<table>
  <tbody>
    <tr>
      <td><strong>Caso de uso</strong></td>
      <td>
        <strong><em>UC2 - Bloquear acesso</em></strong>
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
        O ator não está credenciado e falha duas vezes ao tentar acessar o
        sistema.
      </td>
    </tr>
    <tr>
      <td><strong>Fluxo principal</strong></td>
      <td>
        <ol>
          <li>
            O ator segue o fluxo principal de
            <a href="especificacao_fazer_login.html">UC1 - Fazer login</a> e
            falha pela segunda vez ao tentar se credenciar no sistema.
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
  </tbody>
</table>
