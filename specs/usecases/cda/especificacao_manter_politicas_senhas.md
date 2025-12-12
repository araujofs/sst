<table>
  <tbody>
    <tr>
      <td><strong>Caso de uso</strong></td>
      <td>
        <strong><span><a>UC10 - Manter políticas de expiração/renovação de senhas</a></span></strong>
      </td>
    </tr>
    <tr>
      <td><strong>Objetivo</strong></td>
      <td>
        Obrigar usuários a trocarem suas senhas de tempos em tempos para mantê-las seguras.
      </td>
    </tr>
    <tr>
      <td><strong>Requisitos</strong></td>
      <td>RF-AUT-005</td>
    </tr>
    <tr>
      <td><strong>Atores</strong></td>
      <td>Administrador</td>
    </tr>
    <tr>
      <td><strong>Condições de entrada</strong></td>
      <td>O ator seleciona 'Gerenciar políticas de senha' no menu de controle de acesso.</td>
    </tr>
    <tr>
      <td><strong>Fluxo principal</strong></td>
      <td>
        <ol>
          <li>
            O ator acessa a página de gerenciamento de políticas de senha. Ele percebe que existem algumas políticas já definidas. Ele observa que há algumas opções:
            <ol>
              <li>Criar nova regra</li>
              <li>Editar regra</li>
              <li>Apagar regra</li>
            </ol>
          </li>
          <li>
            O ator seleciona a primeira opção. Ao selecionar essa opção, ele vê os seguintes campos:
            <ul>
              <li>nome da política</li>
              <li>tempo de expiração</li>
              <li>quanto tempo antes avisar</li>
              <li>usuários afetados</li>
              <li>opções: <ul><li>criar</li><li>cancelar</li></ul></li>
            </ul>
          </li>
          <li>O ator preenche os campos com as informações que desejar e seleciona opção de criar./li>
          <li>O sistema verifica se os dados informados são válidos <a href="#rn2">[RN2]</a> para a criação da política.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos alternativos</strong></td>
      <td>
        <a id="a1">A1 - Buscar política</a>
        <ol>
          <li>O ator quer buscar por uma política específica. Ele observa que há um campo de busca na página de configuração das regras.</li>
          <li>O ator digita o nome pelo qual quer procurar e seleciona 'Buscar'.</li>
          <li>O sistema exibe as políticas com nomes similares à busca do usuário.</li>
        </ol>
        <a id="a2">A2 - Editar política</a>
        <ol>
          <li>O ator segue o fluxo de <a href="#a1">[A1]</a> e acha a polítca que quer editar.</li>
          <li>O ator seleciona a opção 'Editar' na política escolhida.</li>
          <li>O ator vê os mesmos campos do fluxo principal, mas já preenchidos, e observa também um histórico de edições.</li>
          <li>O ator altera as informações desejadas e seleciona a opção 'Salvar'. O sistema verifica a validade das alterações <a href="#rn2">[RN2]</a>.</li>
          <li>O ator é redirecionado para a tela de busca anterior onde pode ver a política de senha que acabou de alterar.</li>
        </ol>
        <a id="a3">A3 - Apagar política</a>
        <ol>
          <li>O ator segue o fluxo de <a href="#a1">[A1]</a> e acha a política que quer apagar.</li>
          <li>O ator seleciona o botão 'Apagar' na política escolhida.</li>
          <li>O ator confirma sua escolha em um modal.</li>
          <li>O ator é redirecionado para a tela de busca anterior onde pode ver que a política escolhida foi apagada.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos de exceção</strong></td>
      <td>
        <a id="rn2">[RN2] - Validação de política de senha</a><br>
        O sistema deve garantir que um usuário seja afetado por no mínimo 1 e no máximo 1 política de senha e que uma política afete pelo menos um usuário.
      </td>
    </tr>
  </tbody>
</table>
