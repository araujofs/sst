<table>
  <tbody>
    <tr>
      <td><strong>Caso de uso</strong></td>
      <td>
        <strong><span><a>UC4 - Encerrar sessão de outro usuário</a></span></strong>
      </td>
    </tr>
    <tr>
      <td><strong>Objetivo</strong></td>
      <td>
        Permitir que o administrador encerra a sessão de outro usuário para o caso de alguma suspeita ou problema de segurança.
      </td>
    </tr>
    <tr>
      <td><strong>Requisitos</strong></td>
      <td>RF-AUT-006</td>
    </tr>
    <tr>
      <td><strong>Atores</strong></td>
      <td>Administrador</td>
    </tr>
    <tr>
      <td><strong>Condições de entrada</strong></td>
      <td>O ator seleciona 'Encerrar sessão' no menu de gestão de usuários.</td>
    </tr>
    <tr>
      <td><strong>Fluxo principal</strong></td>
      <td>
        <ol>
          <li>
            O ator acessa a página de Gestão de Usuários. Ele verifica que existe uma lista de usuários com informações e opções. Ele observa a opção de 'Encerrar sessão' em um usuário específico listado.
          </li>
          <li>
            O ator seleciona opção de 'Encerrar sessão'.
          </li>
          <li id="li3">
            O ator verifica que foi renderizado um modal em sua tela pedindo a confirmação do encerramento da sessão do outro usuário.
          </li>
          <li>
            O ator seleciona opção de 'Confirmar'.
          </li>
          <li>
            O sistema encerra a sessão do outro usuário, de maneira que ele precisará realizar o login <a href="especificacao_fazer_login.md">[UC1]</a> novamente.
          </li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos alternativos</strong></td>
      <td>
        <a>[A1] - Cancelar encerramento de sessão</a>
        <ol>
          <li>
            O ator segue o fluxo principal até o <a href="#li3">passo 3</a> onde escolhe a opção 'Cancelar'.
          </li>
          <li>
            O modal é fechado.
          </li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos de exceção</strong></td>
      <td>
        Nenhum
      </td>
    </tr>
  </tbody>
</table>
