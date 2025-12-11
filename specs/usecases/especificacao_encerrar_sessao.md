<table>
  <tbody>
    <tr>
      <td><strong>Caso de uso</strong></td>
      <td>
        <strong><span><a>UC3 - Encerrar sessão</a></span></strong>
      </td>
    </tr>
    <tr>
      <td><strong>Objetivo</strong></td>
      <td>
        Dar ao usuário a possibilidade de encerrar sua sessão antes de chegar o tempo máximo da sessão, evitando sessões maiores do que o necessário.
      </td>
    </tr>
    <tr>
      <td><strong>Requisitos</strong></td>
      <td>RF-AUT-008</td>
    </tr>
    <tr>
      <td><strong>Atores</strong></td>
      <td>Usuário</td>
    </tr>
    <tr>
      <td><strong>Condições de entrada</strong></td>
      <td>O ator seleciona 'Sair' no menu do seu avatar.</td>
    </tr>
    <tr>
      <td><strong>Fluxo principal</strong></td>
      <td>
        <ol>
          <li>
            O ator verifica, em qualquer página do sistema, que há uma barra lateral com alguns links de navegação. No fim da barra lateral há um avatar com sua foto de perfil e seu nome.
          </li>
          <li>O ator clica no avatar que contém a sua foto de perfil e um menu abre com suas informações e algumas opções.</li>
          <li>O ator clica na opção 'Sair' encontrada no menu.</li>
          <li>
            O sistema encerra a sessão do usuário.
          </li>
          <li>
            O sistema redireciona o usuário para a página de login <a href="especificacao_fazer_login.md">[UC1]</a>.
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
      <td>
        Nenhum
      </td>
    </tr>
  </tbody>
</table>
