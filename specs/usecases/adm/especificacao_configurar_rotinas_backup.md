<table>
  <tbody>
    <tr>
      <td><strong>Caso de uso</strong></td>
      <td>
        <strong
          ><span><a>UCxx - Configurar rotinas de backup</a></span></strong
        >
      </td>
    </tr>
    <tr>
      <td><strong>Objetivo</strong></td>
      <td>
        Permitir que o administrador configure rotinas de backup em intervalos de tempo, ou dispare manualmente, garantindo disponibilidade dos dados caso haja algum problema.
      </td>
    </tr>
    <tr>
      <td><strong>Requisitos</strong></td>
      <td>RF-ADM-007</td>
    </tr>
    <tr>
      <td><strong>Atores</strong></td>
      <td>Administrador</td>
    </tr>
    <tr>
      <td><strong>Condições de entrada</strong></td>
      <td>
        O ator se encontra no menu de configuração do sistema.
      </td>
    </tr>
    <tr>
      <td><strong>Fluxo principal</strong></td>
      <td>
        <ol>
          <li>
            O ator verifica no menu de configuração do sistema que há um menu relacionado a rotinas de backup. Ele seleciona esse menu.
          </li>
          <li>
            O ator observa na nova tela que se abriu uma lista de rotinas de backup configuradas. Ele vê que há a opção de 'Criar rotina'. Ele também verifica que em cada rotina lisada há algumas informações:
            <ul>
              <li>Nome da rotina</li>
              <li>Data da próxima execução</li>
              <li>Intervalo configurado</li>
              <li>Opções:</li>
              <ul>
                <li>Editar</li>
                <li>Apagar</li>
              </ul>
            </ul>
          </li>
          <li>
            O ator seleciona a opção de 'Criar rotina', onde vê campos para definir as informações que aparecem na listagem e mais algumas:
            <ul>
              <li>Nome da rotina</li>
              <li>Data da próxima execução</li>
              <li>Intervalo configurado</li>
              <li>Dados selecionados para backup</li>
              <li>Destino do backup</li>
              <li>Tipo de criptografia</li>
              <li>Tipo de compactação</li>
              <li>Opções:</li>
              <ul>
                <li>Limpar</li>
                <li>Criar</li>
              </ul>
            </ul>
          </li>
          <li>
            O ator define as informações que deseja e escolhe a opção 'Criar'.
          </li>
          <li>
            O sistema salva a nova rotina de backup configurada. <a href="#rn4">[RN4]</a>
          </li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos alternativos</strong></td>
      <td>
        <a id="a1">A1 - Buscar rotinas</a>
        <ol>
          <li>O ator quer buscar por uma rotina específica. Ele observa que há um campo de busca na página de configuração das rotinas.</li>
          <li>O ator digita o nome da rotina pela qual quer procurar e seleciona 'Buscar'.</li>
          <li>O sistema exibe as rotinas com nomes similares à busca do usuário.</li>
        </ol>
        <a id="a2">A2 - Editar rotina</a>
        <ol>
          <li>O ator segue o fluxo de <a href="#a1">[A1]</a> e acha a rotina que quer editar.</li>
          <li>O ator seleciona a opção 'Editar' na rotina escolhida.</li>
          <li>O ator vê os mesmos campos do fluxo principal, mas já preenchidos, e observa também um histórico de edições.</li>
          <li>O ator altera as informações desejadas e seleciona a opção 'Salvar'. O sistema verifica a validade das alterações <a href="#rn4">[RN4]</a>.</li>
          <li>O ator é redirecionado para a tela de busca anterior onde vê a rotina que acabou de alterar.</li>
        </ol>
        <a id="a3">A3 - Apagar rotina</a>
        <ol>
          <li>O ator segue o fluxo de <a href="#a1">[A1]</a> e acha a rotina que quer apagar.</li>
          <li>O ator seleciona o botão 'Apagar' na rotina escolhida.</li>
          <li>O ator confirma sua escolha em um modal.</li>
          <li>O ator é redirecionado para a tela de busca anterior onde verifica que a política escolhida foi apagada.</li>
        </ol>
        <a id="a3">A4 - Limpar formulário de criação de política</a>
        <ol>
          <li>O ator segue o fluxo principal até o passo <a>3</a> e define as informações.</li>
          <li>O ator seleciona o botão 'Limpar' no formulário de criação de rotina.</li>
          <li>Os campos do formulário são resetados.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos de exceção</strong></td>
      <td>
        <a id="rn4">[RN4] - Backup mínimo</a><br>
        O sistema deve garantir que um tipo de dado está incluso em pelo menos uma rotina de backup.
      </td>
    </tr>
  </tbody>
</table>
