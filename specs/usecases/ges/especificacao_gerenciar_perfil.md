<table>
  <tbody>
    <tr>
      <td><strong>Caso de uso</strong></td>
      <td>
        <strong
          ><span><a>UCxx - Gerenciar perfil</a></span></strong
        >
      </td>
    </tr>
    <tr>
      <td><strong>Objetivo</strong></td>
      <td>
        Permitir que o usuário gerencie suas informações de perfil (foto, nome, e-mail, senha) mantendo os dados atualizados e as credenciais seguras.
      </td>
    </tr>
    <tr>
      <td><strong>Requisitos</strong></td>
      <td>RF-GES-005</td>
    </tr>
    <tr>
      <td><strong>Atores</strong></td>
      <td>Usuário</td>
    </tr>
    <tr>
      <td><strong>Condições de entrada</strong></td>
      <td>
        O ator se encontra na página 'Meu perfil'.
      </td>
    </tr>
    <tr>
      <td><strong>Fluxo principal</strong></td>
      <td>
        <ol>
          <li>
            O ator acessa o menu de perfil do usuário no menu lateral.
          </li>
          <li>
            O ator observa na tela de perfil as informações atuais:
            <ul>
              <li>Foto de perfil</li>
              <li>Nome completo</li>
              <li>E-mail</li>
              <li>Senha (mascarada)</li>
              <li>Opções:</li>
              <ul>
                <li>Editar perfil</li>
              </ul>
            </ul>
          </li>
          <li>
            O ator seleciona a opção 'Editar perfil', onde vê campos editáveis:
            <ul>
              <li>Foto de perfil (com opção de upload)</li>
              <li>Nome completo</li>
              <li>E-mail</li>
              <li>Senha atual</li>
              <li>Nova senha</li>
              <li>Confirmação de nova senha</li>
              <li>Opções:</li>
              <ul>
                <li>Limpar alterações</li>
                <li>Salvar</li>
              </ul>
            </ul>
          </li>
          <li>
            O ator altera as informações que deseja e escolhe a opção 'Salvar'.
          </li>
          <li>
            O sistema valida e salva as alterações do perfil. <a href="#rn1">[RN1]</a>, <a, href="#rn2">[RN2]</a,> <a href="#rn3">[RN3]</a>, <a href="#rn4">[RN4]</a>
          </li>
          <li>
            O ator visualiza uma mensagem de confirmação e as informações atualizadas no perfil.
          </li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos alternativos</strong></td>
      <td>
        <a id="a1">A1 - Limpar alterações</a>
        <ol>
          <li>O ator segue o fluxo principal até o passo <a>3</a> e altera algumas informações.</li>
          <li>O ator seleciona o botão 'Limpar alterações' no formulário de edição.</li>
          <li>Os campos do formulário retornam aos valores originais antes da edição.</li>
        </ol>
        <a id="a2">A2 - Remover foto de perfil</a>
        <ol>
          <li>O ator segue o fluxo principal até o passo <a>3</a>.</li>
          <li>O ator seleciona a opção 'Remover foto' ao lado da foto de perfil atual.</li>
          <li>O ator seleciona 'Salvar'.</li>
          <li>O ator visualiza o perfil com a foto padrão do sistema.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos de exceção</strong></td>
      <td>
        <a id="rn1">[RN1] - E-mail único</a><br>
        O sistema deve garantir que o e-mail informado não esteja já cadastrado para outro usuário. Caso esteja, o sistema exibe mensagem de erro: "Este e-mail já está em uso por outro usuário."<br><br>
        <a id="rn2">[RN2] - Validação de senha atual</a><br>
        Para alterar a senha, o usuário deve informar corretamente a senha atual. Caso a senha atual esteja incorreta, o sistema exibe mensagem de erro: "Senha atual incorreta."<br><br>
        <a id="rn3">[RN3] - Política de senha</a><br>
        A nova senha deve atender aos requisitos de segurança: mínimo de 8 caracteres, pelo menos uma letra maiúscula, uma minúscula, um número e um caractere especial. As senhas 'Nova senha' e 'Confirmação de nova senha' devem ser iguais. Caso não atendam, o sistema exibe mensagem de erro específica.<br><br>
        <a id="rn4">[RN4] - Validação de imagem</a><br>
        A foto de perfil deve estar em formato JPG, PNG ou GIF e ter tamanho máximo de 2MB. Caso não atenda, o sistema exibe mensagem de erro: "Formato ou tamanho de imagem inválido. Use JPG, PNG ou GIF com até 2MB."
      </td>
    </tr>
  </tbody>
</table>
