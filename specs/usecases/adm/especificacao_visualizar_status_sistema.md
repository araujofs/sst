<table>
  <tbody>
    <tr>
      <td><strong>Caso de uso</strong></td>
      <td>
        <strong
          ><span><a>UC28 - Visualizar status do sistema</a></span></strong
        >
      </td>
    </tr>
    <tr>
      <td><strong>Objetivo</strong></td>
      <td>
        Facilitar a detecção de problemas relacionados a consumo de recursos, quedas de módulos, dentre outros.
      </td>
    </tr>
    <tr>
      <td><strong>Requisitos</strong></td>
      <td>RF-ADM-010</td>
    </tr>
    <tr>
      <td><strong>Atores</strong></td>
      <td>Gestor</td>
    </tr>
    <tr>
      <td><strong>Condições de entrada</strong></td>
      <td>
        Ator se encontra no módulo de configuração do sistema.
      </td>
    </tr>
    <tr>
      <td><strong>Fluxo principal</strong></td>
      <td>
        <ol>
          <li>
            O ator se encontra na área de configurações e acessa o menu "Status do sistema". Ele vê um painel com indicadores gerais (recursos utilizados, módulos funcionando, tempo médio de resposta, disponibilidade, usuários ativos) e a data/hora da última atualização.
          </li>
          <li>
            O ator verifica que cada módulo mostra o status (OK/Degradado/Indisponível) com cor/ícone, além de métricas resumidas (por exemplo, uso de CPU/memória, latência média, taxa de erros).
          </li>
          <li>
            O ator seleciona um módulo ou serviço específico para detalhar. Ele observa dados mais completos, como:
            <ul>
              <li>Uptime e histórico recente de disponibilidade</li>
              <li>Consumo de CPU, memória e disco</li>
              <li>Latência média e picos</li>
              <li>Alertas recentes associados ao módulo</li>
            </ul>
            E a opção "Fechar".
          </li>
          <li>
            O ator seleciona a opção "Fechar" para retornar ao painel geral.
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
      <td>Nenhum</td>
    </tr>
  </tbody>
</table>
