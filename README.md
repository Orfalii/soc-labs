# SOC Labs – Raphael Orfali

Este repositório reúne estudos práticos em cibersegurança com foco em Blue Team, análise de logs e investigação inicial de incidentes.

---

## Lab 1 – Investigação de Brute Force

### Cenário
Este laboratório simula um caso de brute force contra uma conta com privilégio elevado em um servidor Linux exposto via SSH. O objetivo é analisar os eventos de autenticação, separar ruído de atividade suspeita e documentar a investigação como um caso de triagem inicial em SOC.


### Objetivo
Identificar se a sequência de autenticações observada indica tentativa de acesso não autorizado e justificar a classificação do incidente com base nos logs disponíveis.

---

### Principais Achados
- Múltiplas falhas de autenticação via SSH para a conta `admin` em curto intervalo.
- Origem: IP `192.168.1.50` (identificado nos logs)  
- Login bem-sucedido para a mesma conta após a sequência de falhas.
- Evidências compatíveis com brute force bem-sucedido e potencial comprometimento de credencial.

---

### Impacto
Possível comprometimento da conta "admin", com risco de acesso não autorizado ao sistema.

---

### Conclusão
Foi identificado um ataque de brute force, com múltiplas tentativas de login seguidas de sucesso, indicando comprometimento de conta.

---

### Mitigações
- Bloqueio do IP no firewall  
- Reset de credenciais 
- Bloqueio de conta após múltiplas tentativas
- Implementação de MFA  
- Monitoramento contínuo via SIEM 
- Investigação da origem interna  

---

## Ferramentas utilizadas
- Logs de autenticação  
- Análise manual   

---

## Evidências

Os logs analisados estão disponíveis abaixo:

Logs analisados: [Logs.txt](Logs.txt)

## Evidência Visual

![Evidência](evidence.png)

---

## Relatório Completo

O relatório detalhado da investigação está disponível abaixo:

[incident-report.md](incident-report.md)

## Anotações
Os logs deste repositório representam um cenário simulado para fins de estudo e prática em investigação de incidentes.
