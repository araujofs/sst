<table>
  <tbody>
    <tr>
      <td><strong>Caso de uso</strong></td>
      <td>
        <strong><em>UC1 - Fazer login</em></strong>
      </td>
    </tr>
    <tr>
      <td><strong>Objetivo</strong></td>
      <td>
        Permitir que o usuário se credencie no sistema para ter acesso aos
        outros módulos.
      </td>
    </tr>
    <tr>
      <td><strong>Requisitos</strong></td>
      <td>RF-AUT-001</td>
    </tr>
    <tr>
      <td><strong>Atores</strong></td>
      <td>Usuário</td>
    </tr>
    <tr>
      <td><strong>Condições de entrada</strong></td>
      <td>O ator não está credenciado e tenta acessar o sistema.</td>
    </tr>
    <tr>
      <td><strong>Fluxo principal</strong></td>
      <td>
        <ol>
          <li>
            O ator acessa a tela de login. Ele verifica no título da aba e
            também dentro da própria página que o título é 'Acesse sua conta'.
            Ele observa que existem os seguintes campos:
            <ul>
              <li>e-mail</li>
              <li>senha</li>
            </ul>
            Além de um botão 'Entrar'.
          </li>
          <li>O ator preenche os campos e seleciona a opção 'Entrar'.</li>
          <li>
            O sistema verifica se as credencias informadas estão corretas.
            <a href="#rn1">[RN1]</a>
          </li>
          <li>
            O sistema exibe uma mensagem de sucesso no credeciamento e
            redireciona o usuário para a página inicial. <a href="#a1">[A1]</a>,
            <a href="#a2">[A2]</a>
          </li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos alternativos</strong></td>
      <td>
        <a id="a1">[A1] - Inserir credenciais erradas pela primeira vez</a>
        <ol>
          <li>
            O ator executa o fluxo principal, mas digitando credenciais
            incorretas pela primeira vez.
          </li>
          <li>
            O sistema exibe uma mensagem de erro informando que as credenciais
            estão incorretas e solicita que o ator tente novamente.
          </li>
        </ol>
        <a id="a2">[A2] - Inserir credenciais erradas pela segunda vez</a>
        <ol>
          <li>O ator executa <a href="#a1">[A1]</a> pela segunda vez.</li>
          <li>
            O sistema informa que seu acesso foi bloqueado <a href="especificacao_bloquear_acesso.md">[UC2 - Bloquear acesso]</a> e
            solicita que o ator entre em contato com o suporte.
          </li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos de exceção</strong></td>
      <td>
        <a id="rn1">[RN1] - Credenciamento de usuário</a><br>
        O usuário deve ser cadastrado previamente no sistema por um gestor para ter acesso aos outros módulos.
      </td>
    </tr>
  </tbody>
</table>
