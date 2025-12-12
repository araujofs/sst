<table>
  <tbody>
    <tr>
      <td><strong>Caso de uso</strong></td>
      <td>
        <strong
          ><span><a>UCxx - Reportar erro</a></span></strong
        >
      </td>
    </tr>
    <tr>
      <td><strong>Objetivo</strong></td>
      <td>
        Ajudar na resolução rápida e eficiente de erros que possam existir no sistema.
      </td>
    </tr>
    <tr>
      <td><strong>Requisitos</strong></td>
      <td>RF-ADM-011</td>
    </tr>
    <tr>
      <td><strong>Atores</strong></td>
      <td>Usuário</td>
    </tr>
    <tr>
      <td><strong>Condições de entrada</strong></td>
      <td>
        O ator encontrou um erro no sistema e deseja reportá-lo para a equipe de
        desenvolvimento.
      </td>
    </tr>
    <tr>
      <td><strong>Fluxo principal</strong></td>
      <td>
        <ol>
          <li>
            O ator se encontra em qualquer tela do sistema. Ele detecta um erro
            durante o uso. Ele observa que existe um botão com o ícone de um
            "bug" ou "inseto" no canto superior direito da tela. Ele seleciona
            esse botão para iniciar o processo de reporte de erro.
          </li>
          <li>
            O sistema exibe um formulário de reporte de erro. O ator preenche os
            campos obrigatórios, que incluem:
            <ul>
              <li>
                Descrição do erro: Uma breve descrição do problema encontrado.
              </li>
              <li>
                Passos para reproduzir: Instruções detalhadas sobre como
                reproduzir o erro.
              </li>
              <li>
                Anexar arquivos (opcional): O ator pode anexar capturas de tela
                ou arquivos relevantes que ajudem a ilustrar o problema.
              </li>
              <li>
                Opções:
                <ul>
                  <li>
                    Enviar
                  </li>
                  <li>
                    Cancelar
                  </li>
                </ul>
              </li>
            </ul>
          </li>
          <li>
            Após preencher o formulário, o ator clica no botão "Enviar Reporte".
            O sistema valida as informações fornecidas e confirma o envio do
            reporte de erro.
          </li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos alternativos</strong></td>
      <td>
        <a id="a1">A1 - Cancelar envio do reporte</a>
        <ol>
          <li>
            O ator executa o fluxo principal até o passo 2, onde ele decide não enviar o reporte de
            erro e clica no botão "Cancelar".
          </li>
          <li>
            O sistema descarta as informações inseridas no formulário e retorna
            o ator para a tela anterior sem salvar nenhum dado.
          </li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos de exceção</strong></td>
      <td>Nenhum</td>
    </tr>
  </tbody>
</table>
