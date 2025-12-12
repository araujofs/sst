<table>
  <tbody>
    <tr>
      <td><strong>Caso de uso</strong></td>
      <td>
        <strong><span><a>UCxx - Manter políticas de logs</a></span></strong>
      </td>
    </tr>
    <tr>
      <td><strong>Objetivo</strong></td>
      <td>
        Permiter que o administrador tenha controle sobre as configurações relacionadas aos logs do sistema.
      </td>
    </tr>
    <tr>
      <td><strong>Requisitos</strong></td>
      <td>RF-ADM-003</td>
    </tr>
    <tr>
      <td><strong>Atores</strong></td>
      <td>Administrador</td>
    </tr>
    <tr>
      <td><strong>Condições de entrada</strong></td>
      <td>O ator seleciona 'Gerenciar políticas de logs' no menu de configurações do sistema.</td>
    </tr>
    <tr>
      <td><strong>Fluxo principal</strong></td>
      <td>
        <ol>
          <li>
            O ator acessa a página de gerenciamento de políticas de logs. Ele observa que há alguns campos:
            <ol>
              <li>Tempo de armazenamento</li>
              <li>Nível de detalhamento</li>
              <li>Categorias</li>
              <li>
                Opções: 
                <ul>
                  <li>Salvar</li>
                  <li>Cancelar</li>
                </ul>
              </li>
            </ol>
          </li>
          <li>
            O ator decide modificar a política. Ele modifica o campo desejado.
          </li>
          <li>
            O ator seleciona a opção 'Salvar'.
          </li>
          <li>O sistema verifica se os dados informados são válidos <a href="#rn3">[RN3]</a> para a modificação da política.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos alternativos</strong></td>
      <td>
        <a id="a1">A1 - Cancelar modificação</a>
        <ol>
          <li>O ator segue o fluxo principal até o passo <a>2</a>.</li>
          <li>O ator decide cancelar a modificação e seleciona a opção 'Cancelar'.</li>
          <li>A política volta ao estado anterior.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos de exceção</strong></td>
      <td>
        <a id="rn3">[RN3] - Validação de política de logs</a><br>
        O sistema deve garantir que a especificação mínima de logs seja atendida.
      </td>
    </tr>
  </tbody>
</table>
  