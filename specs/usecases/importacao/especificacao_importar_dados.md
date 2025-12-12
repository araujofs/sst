<table>
  <tbody>
    <tr>
      <td><strong>Caso de uso</strong></td>
      <td>
        <strong><span><a>UCxx - Importar Dados Financeiros</a></span></strong>
      </td>
    </tr>
    <tr>
      <td><strong>Objetivo</strong></td>
      <td>
        Permitir que o contador ou gerente importe dados financeiros de arquivos Excel ou CSV para agilizar o preenchimento da simulação.
      </td>
    </tr>
    <tr>
      <td><strong>Requisitos</strong></td>
      <td>RF-IMP-002</td>
    </tr>
    <tr>
      <td><strong>Atores</strong></td>
      <td>Contador, Gerente</td>
    </tr>
    <tr>
      <td><strong>Condições de entrada</strong></td>
      <td>O ator está preenchendo uma simulação e deseja importar dados financeiros de um arquivo.</td>
    </tr>
    <tr>
      <td><strong>Fluxo principal</strong></td>
      <td>
        <ol>
          <li>O ator clica no botão "Importar Dados".</li>
          <li>O sistema exibe modal com opções de formato:
            <ul>
              <li>Excel (.xlsx)</li>
              <li>CSV (.csv)</li>
            </ul>
          </li>
          <li>O ator seleciona o formato e clica em "Escolher Arquivo".</li>
          <li>O ator seleciona o arquivo no seu computador.</li>
          <li>O sistema faz upload do arquivo.</li>
          <li>O sistema valida a estrutura do arquivo. <a href="#e1">[E1]</a></li>
          <li>O sistema exibe tela de mapeamento mostrando:
            <ul>
              <li>Colunas identificadas no arquivo (dropdown para cada campo do sistema)</li>
              <li>Preview dos primeiros 5 registros</li>
              <li>Campos do sistema que precisam ser mapeados</li>
            </ul>
          </li>
          <li>O ator mapeia cada coluna do arquivo para os campos do sistema:
            <ul>
              <li>Receita Bruta → Coluna A</li>
              <li>Despesas → Coluna B</li>
              <li>Folha de Pagamento → Coluna C</li>
            </ul>
          </li>
          <li>O sistema valida o mapeamento e os dados. <a href="#e2">[E2]</a></li>
          <li>O ator clica em "Confirmar Importação".</li>
          <li>O sistema preenche automaticamente os campos do formulário com os dados importados.</li>
          <li>O sistema exibe mensagem: "Dados importados com sucesso. [X] campos preenchidos."</li>
          <li>O ator pode revisar e ajustar os dados antes de simular.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos alternativos</strong></td>
      <td>
        <a id="a1">[A1] - Cancelar importação</a>
        <ol>
          <li>A qualquer momento antes do passo 10, o ator pode clicar em "Cancelar".</li>
          <li>O sistema descarta os dados do arquivo.</li>
          <li>O sistema retorna ao formulário de simulação.</li>
          <li>O caso de uso é encerrado.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos de exceção</strong></td>
      <td>
        <a id="e1">[E1] - Arquivo com formato inválido</a>
        <ol>
          <li>No passo 6, o sistema identifica que o arquivo não está no formato esperado.</li>
          <li>O sistema exibe mensagem: "Arquivo inválido. Formatos aceitos: .xlsx, .csv"</li>
          <li>Retorna ao passo 3.</li>
        </ol>
        <a id="e2">[E2] - Dados inconsistentes</a>
        <ol>
          <li>No passo 9, o sistema identifica valores negativos, formatos incorretos ou dados faltantes em campos obrigatórios.</li>
          <li>O sistema exibe lista de erros encontrados:
            <ul>
              <li>"Receita Bruta: valor negativo detectado na linha 5"</li>
              <li>"Folha de Pagamento: valor não numérico na linha 8"</li>
              <li>"Data: formato inválido (esperado DD/MM/AAAA)"</li>
            </ul>
          </li>
          <li>O ator pode corrigir o arquivo localmente e reimportar, ou cancelar a importação.</li>
          <li>Retorna ao passo 3.</li>
        </ol>
        <a id="e3">[E3] - Arquivo muito grande</a>
        <ol>
          <li>No passo 5, o sistema detecta que o arquivo excede o tamanho máximo permitido (5MB).</li>
          <li>O sistema exibe mensagem: "Arquivo muito grande. Tamanho máximo: 5MB"</li>
          <li>Retorna ao passo 3.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Regras de negócio</strong></td>
      <td>
        <a id="rn1">[RN1] - Validações de dados</a><br>
        O sistema deve validar:
        <ul>
          <li><strong>Valores numéricos:</strong> Apenas números positivos para receitas, despesas e folha</li>
          <li><strong>Datas:</strong> Formato DD/MM/AAAA ou AAAA-MM-DD</li>
          <li><strong>Campos obrigatórios:</strong> Receita Bruta (mínimo para simulação)</li>
          <li><strong>Moedas:</strong> Aceita formatos: 1000.00, 1.000,00, R$ 1.000,00</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>
