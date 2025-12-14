<table>
  <tbody>
    <tr>
      <td><strong>Caso de uso</strong></td>
      <td>
        <strong
          ><span><a>UC06 - Manter usuário</a></span></strong
        >
      </td>
    </tr>
    <tr>
      <td><strong>Objetivo</strong></td>
      <td>
        Permitir que o administrador gerencie os usuários do sistema, garantindo acesso apenas às pessoas autorizadas e modificando permissões quando necessário.
      </td>
    </tr>
    <tr>
      <td><strong>Requisitos</strong></td>
      <td>RF-GES-001</td>
    </tr>
    <tr>
      <td><strong>Atores</strong></td>
      <td>Administrador</td>
    </tr>
    <tr>
      <td><strong>Condições de entrada</strong></td>
      <td>
        O ator se encontra no menu de gerenciamento de usuários.
      </td>
    </tr>
    <tr>
      <td><strong>Fluxo principal</strong></td>
      <td>
        <ol>
          <li>
            O ator verifica no menu de gerenciamento que há uma lista de usuários cadastrados. Ele vê que há a opção de 'Criar usuário'. Ele também verifica que em cada usuário listado há algumas informações:
            <ul>
              <li>Foto de perfil</li>
              <li>Nome</li>
              <li>E-mail</li>
              <li>Tipo de usuário (Gerente, Administrador, Contador, Cliente, Técnico de suporte)</li>
              <li>Status (Ativo/Inativo)</li>
              <li>Opções:</li>
              <ul>
                <li>Visualizar</li>
                <li>Editar</li>
                <li>Desativar/Ativar</li>
              </ul>
            </ul>
          </li>
          <li>
            O ator seleciona a opção de 'Criar usuário', onde vê um formulário com:
            <ul>
              <li>Tipo de usuário (seleção entre: Gerente, Administrador, Contador, Cliente, Técnico de suporte)</li>
              <li>Nome</li>
              <li>E-mail</li>
              <li>Senha</li>
              <li>Confirmação de senha</li>
              <li>Foto de perfil (com opção de upload)</li>
              <li>Campos específicos por tipo de usuário <a href="#rn1">[RN1]</a>:</li>
              <ul>
                <li>Gerente: CNPJ do escritório</li>
                <li>Cliente: Tipo (Pessoa física/Jurídica), Razão social (se empresa), CPF (se pessoa física), CNPJ da empresa (se empresa), CNPJ do escritório associado</li>
              </ul>
              <li>Opções:</li>
              <ul>
                <li>Limpar</li>
                <li>Criar</li>
              </ul>
            </ul>
          </li>
          <li>
            O ator seleciona o tipo de usuário desejado e preenche os campos obrigatórios.
          </li>
          <li>
            O ator define as informações que deseja e escolhe a opção 'Criar'.
          </li>
          <li>
            O sistema valida e salva o novo usuário. <a href="#rn2">[RN2]</a> <a href="#rn3">[RN3]</a> <a href="#rn4">[RN4]</a> <a href="#rn5">[RN5]</a>
          </li>
          <li>
            O ator visualiza uma mensagem de confirmação e é redirecionado para a lista de usuários, onde o novo usuário aparece.
          </li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos alternativos</strong></td>
      <td>
        <a id="a1">A1 - Buscar usuários</a>
        <ol>
          <li>O ator quer buscar por um usuário específico. Ele observa que há um campo de busca na página de gerenciamento de usuários.</li>
          <li>O ator digita o nome ou e-mail do usuário pela qual quer procurar e seleciona 'Buscar'.</li>
          <li>O sistema exibe os usuários com nomes ou e-mails similares à busca.</li>
        </ol>
        <a id="a2">A2 - Filtrar usuários por tipo</a>
        <ol>
          <li>O ator observa que há opções de filtro por tipo de usuário na página de listagem.</li>
          <li>O ator seleciona um ou mais tipos de usuário para filtrar.</li>
          <li>O sistema exibe apenas os usuários do(s) tipo(s) selecionado(s).</li>
        </ol>
        <a id="a3">A3 - Editar usuário</a>
        <ol>
          <li>O ator segue o fluxo de <a href="#a1">[A1]</a> e encontra o usuário que deseja editar.</li>
          <li>O ator seleciona a opção 'Editar' no usuário escolhido.</li>
          <li>O ator vê os mesmos campos do fluxo principal de criação, mas já preenchidos (exceto senha), e observa também um histórico de edições.</li>
          <li>O ator altera as informações desejadas e seleciona a opção 'Salvar'. O sistema valida as alterações <a href="#rn2">[RN2]</a> <a href="#rn3">[RN3]</a> <a href="#rn4">[RN4]</a> <a href="#rn5">[RN5]</a>.</li>
          <li>O ator é redirecionado para a lista de usuários onde vê o usuário que acabou de alterar.</li>
        </ol>
        <a id="a4">A4 - Desativar usuário</a>
        <ol>
          <li>O ator segue o fluxo de <a href="#a1">[A1]</a> e encontra o usuário que deseja desativar.</li>
          <li>O ator seleciona o botão 'Desativar' no usuário escolhido.</li>
          <li>O ator confirma sua escolha em um modal.</li>
          <li>O sistema desativa o usuário, impedindo seu acesso ao sistema.</li>
          <li>O ator visualiza o usuário na lista com status 'Inativo'.</li>
        </ol>
        <a id="a5">A5 - Reativar usuário</a>
        <ol>
          <li>O ator segue o fluxo de <a href="#a1">[A1]</a> e encontra um usuário inativo que deseja reativar.</li>
          <li>O ator seleciona o botão 'Ativar' no usuário escolhido.</li>
          <li>O ator confirma sua escolha em um modal.</li>
          <li>O sistema reativa o usuário, permitindo seu acesso ao sistema novamente.</li>
          <li>O ator visualiza o usuário na lista com status 'Ativo'.</li>
        </ol>
        <a id="a6">A6 - Limpar formulário de criação</a>
        <ol>
          <li>O ator segue o fluxo principal até o passo <a>3</a> e define algumas informações.</li>
          <li>O ator seleciona o botão 'Limpar' no formulário de criação de usuário.</li>
          <li>Os campos do formulário são resetados.</li>
        </ol>
        <a id="a7">A7 - Redefinir senha de usuário</a>
        <ol>
          <li>O ator segue o fluxo de <a href="#a3">[A3]</a> e está editando um usuário.</li>
          <li>O ator seleciona a opção 'Redefinir senha'.</li>
          <li>O ator vê campos para 'Nova senha' e 'Confirmação de nova senha'.</li>
          <li>O ator define a nova senha e seleciona 'Salvar'. O sistema valida a senha <a href="#rn3">[RN3]</a>.</li>
          <li>O sistema envia um e-mail ao usuário informando sobre a alteração de senha.</li>
        </ol>
        <a id="a8">A8 - Alterar permissões de usuário</a>
        <ol>
          <li>O ator segue o fluxo de <a href="#a3">[A3]</a> e está editando um usuário.</li>
          <li>O ator observa uma seção 'Permissões especiais' com checkboxes de permissões adicionais.</li>
          <li>O ator marca ou desmarca as permissões desejadas.</li>
          <li>O ator seleciona 'Salvar' e o sistema atualiza as permissões do usuário.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos de exceção</strong></td>
      <td>
        <a id="rn1">[RN1] - Campos específicos por tipo de usuário</a><br>
        O sistema deve exibir dinamicamente os campos específicos conforme o tipo de usuário selecionado:
        <ul>
          <li><strong>Gerente:</strong> nome, email, senha, CNPJ do escritório, foto de perfil</li>
          <li><strong>Administrador:</strong> nome, email, senha, foto de perfil</li>
          <li><strong>Contador:</strong> nome, email, senha, foto de perfil</li>
          <li><strong>Cliente:</strong> tipo (PF/PJ), nome ou razão social, email, senha, CPF ou CNPJ da empresa, CNPJ do escritório associado, foto de perfil</li>
          <li><strong>Técnico de suporte:</strong> nome, email, senha, foto de perfil</li>
        </ul>
        <br>
        <a id="rn2">[RN2] - E-mail único</a><br>
        O sistema deve garantir que o e-mail informado não esteja já cadastrado para outro usuário. Caso esteja, o sistema exibe mensagem de erro: "Este e-mail já está em uso por outro usuário."<br><br>
        <a id="rn3">[RN3] - Política de senha</a><br>
        A senha deve atender aos requisitos de segurança: mínimo de 8 caracteres, pelo menos uma letra maiúscula, uma minúscula, um número e um caractere especial. As senhas 'Senha' e 'Confirmação de senha' devem ser iguais. Caso não atendam, o sistema exibe mensagem de erro específica.<br><br>
        <a id="rn4">[RN4] - Validação de imagem</a><br>
        A foto de perfil deve estar em formato JPG, PNG ou GIF e ter tamanho máximo de 2MB. Caso não atenda, o sistema exibe mensagem de erro: "Formato ou tamanho de imagem inválido. Use JPG, PNG ou GIF com até 2MB."<br><br>
        <a id="rn5">[RN5] - Validação de documentos</a><br>
        O sistema deve validar os formatos de CPF e CNPJ informados. Caso sejam inválidos, o sistema exibe mensagem de erro: "CPF/CNPJ inválido."<br><br>
        <a id="rn6">[RN6] - Associação de Cliente a Escritório</a><br>
        Todo cliente deve estar obrigatoriamente associado a um escritório de contabilidade válido através do CNPJ. Caso o CNPJ do escritório não seja encontrado, o sistema exibe mensagem de erro: "Escritório de contabilidade não encontrado."
      </td>
    </tr>
  </tbody>
</table>
