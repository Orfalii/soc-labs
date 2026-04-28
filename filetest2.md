
### Incident Summary
- Severity: High
- Status: Confirmed
- MITRE ATT&CK: `T1110 - Brute Force`
- Primary IOC: `192.168.1.50`
- Affected Account: `admin`
- Exposed Service: `SSH / port 22`

### Why This Lab Matters
Este caso demonstra competências importantes para funções de SOC/Blue Team:
- leitura e interpretação de logs
- montagem de timeline
- triagem inicial de alertas
- identificação de IOC
- classificação de incidente
- definição de contenção e mitigação

### Data Sources
- Arquivo de log analisado: [Logs.txt](Logs.txt)
- Evidência visual: `evidence.png`
- Relatório técnico completo: [incident-report.md](incident-report.md)

### Investigation Flow
1. Revisão do arquivo de autenticação para separar eventos benignos e suspeitos.
2. Identificação de repetição de falhas para a mesma conta e mesma origem.
3. Validação de sucesso de autenticação após tentativas consecutivas.
4. Classificação do incidente com base em IOC, timeline, impacto e técnica MITRE.
5. Definição de ações imediatas de contenção e fortalecimento de controle.


