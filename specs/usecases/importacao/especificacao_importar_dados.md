<table>
  <tbody>
    <tr>
      <td><strong>Caso de uso</strong></td>
      <td>
        <strong><span><a>UC18 - Importar Dados Financeiros</a></span></strong>
      </td>
    </tr>
    <tr>
      <td><strong>Objetivo</strong></td>
      <td>
        Importar dados financeiros de arquivos Excel ou CSV para preencher automaticamente o formulário de simulação.
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
          <li>O sistema exibe modal com:
            <ul>
              <li>Opção de seleção de arquivo Excel (.xlsx) ou CSV (.csv)</li>
              <li>Botão "Baixar modelo" - disponibiliza template com estrutura esperada <a href="#rn2">[RN2]</a></li>
              <li>Instruções: "Faça upload de arquivo com dados financeiros. Use nosso modelo para garantir compatibilidade."</li>
            </ul>
          </li>
          <li>O ator seleciona arquivo Excel (.xlsx) ou CSV (.csv) no seu computador.</li>
          <li>O sistema faz upload do arquivo.</li>
          <li>O sistema valida formato do arquivo. <a href="#e1">[E1]</a></li>
          <li>O sistema identifica as colunas do arquivo e exibe tela de mapeamento. <a href="#a1">[A1]</a></li>
          <li>O sistema extrai dados do arquivo conforme mapeamento.</li>
          <li>O sistema valida cada campo extraído: <a href="#e2">[E2]</a>
            <ul>
              <li>CNAE: valida se é código válido <a href="#e3">[E3]</a></li>
              <li>Valores financeiros: valida se são numéricos e não negativos</li>
              <li>CNPJ (se presente): valida formato</li>
            </ul>
          </li>
          <li>O sistema preenche automaticamente os campos do formulário com os dados validados.</li>
          <li>O sistema exibe mensagem de sucesso: "[X] campos preenchidos com sucesso. Revise os dados antes de simular."</li>
          <li>O sistema destaca em azul os campos que foram preenchidos pela importação.</li>
          <li>O ator pode revisar e ajustar os dados antes de simular.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos alternativos</strong></td>
      <td>
        <a id="a1">[A1] - Mapear colunas manualmente</a>
        <ol>
          <li>No passo 6, o sistema não reconhece automaticamente a estrutura do arquivo (cabeçalhos diferentes do modelo).</li>
          <li>O sistema exibe tela de mapeamento com:
            <ul>
              <li>Lista de campos do sistema (CNPJ, CNAE, Receita Bruta, RBT12, etc.)</li>
              <li>Dropdowns para selecionar coluna correspondente no arquivo</li>
              <li>Preview dos dados de cada coluna</li>
            </ul>
          </li>
          <li>O ator mapeia cada campo do sistema para a coluna correspondente no arquivo.</li>
          <li>O ator confirma o mapeamento.</li>
          <li>O sistema salva o mapeamento para reutilização futura (opcional).</li>
          <li>Retorna ao passo 7 do fluxo principal.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Fluxos de exceção</strong></td>
      <td>
        <a id="e1">[E1] - Formato inválido</a>
        <ol>
          <li>No passo 5, o sistema identifica formato incompatível (arquivo corrompido, extensão errada, etc.).</li>
          <li>O sistema exibe mensagem de erro: "Formato de arquivo inválido. Use arquivos .xlsx ou .csv. Baixe nosso modelo para garantir compatibilidade."</li>
          <li>Retorna ao passo 2.</li>
        </ol>
        <a id="e2">[E2] - Dados inválidos no arquivo</a>
        <ol>
          <li>No passo 8, o sistema identifica valores negativos, não numéricos em campos financeiros, ou campos obrigatórios vazios.</li>
          <li>O sistema exibe lista de erros encontrados com localização (linha/coluna):
            <ul>
              <li>"Linha 3, Coluna 'Receita Bruta': valor negativo"</li>
              <li>"Linha 5, Coluna 'RBT12': valor não numérico"</li>
              <li>"Linha 7, Coluna 'CNAE': campo vazio (obrigatório)"</li>
            </ul>
          </li>
          <li>O sistema oferece opções:
            <ul>
              <li>"Corrigir arquivo e reimportar" - retorna ao passo 2</li>
              <li>"Preencher manualmente" - fecha importação e permite preenchimento manual</li>
            </ul>
          </li>
        </ol>
        <a id="e3">[E3] - CNAE inválido no arquivo</a>
        <ol>
          <li>No passo 8, o sistema valida o CNAE importado e identifica que o código é inválido ou não existe.</li>
          <li>O sistema exibe mensagem: "CNAE [código] na linha [X] é inválido. Verifique o código no arquivo."</li>
          <li>O sistema oferece opções:
            <ul>
              <li>"Corrigir no arquivo" - retorna ao passo 2</li>
              <li>"Selecionar CNAE manualmente" - abre campo de busca para selecionar CNAE válido</li>
              <li>"Ignorar e preencher depois" - importa outros dados e deixa CNAE vazio para preenchimento manual</li>
            </ul>
          </li>
        </ol>
      </td>
    </tr>
    <tr>
      <td><strong>Regras de negócio</strong></td>
      <td>
        <a id="rn1">[RN1] - Validações</a><br>
        <ul>
          <li>Formatos aceitos: .xlsx e .csv</li>
          <li>Valores numéricos devem ser positivos</li>
          <li>CNAE e Receita Bruta são campos obrigatórios</li>
          <li>Tamanho máximo: 5MB</li>
          <li>Máximo de 100 linhas por arquivo</li>
        </ul><br>
        <a id="rn2">[RN2] - Estrutura esperada do arquivo (template)</a><br>
        O template disponibilizado contém as seguintes colunas na primeira linha (cabeçalho):
        <ul>
          <li><strong>CNPJ</strong> (opcional) - formato: 99.999.999/9999-99</li>
          <li><strong>Razao_Social</strong> (opcional)</li>
          <li><strong>CNAE</strong> (obrigatório) - formato: 9999-9/99</li>
          <li><strong>Municipio</strong> (opcional)</li>
          <li><strong>UF</strong> (opcional) - sigla com 2 letras</li>
          <li><strong>Receita_Bruta_Periodo</strong> (obrigatório) - valor numérico sem símbolos</li>
          <li><strong>RBT12</strong> (opcional) - valor numérico sem símbolos</li>
          <li><strong>Folha_Pagamento_12m</strong> (opcional) - valor numérico sem símbolos</li>
          <li><strong>Custos_Despesas</strong> (opcional) - valor numérico sem símbolos</li>
        </ul>
        <strong>Nota:</strong> O sistema aceita arquivos com cabeçalhos diferentes, mas neste caso exigirá mapeamento manual [A1].
      </td>
    </tr>
  </tbody>
</table>
