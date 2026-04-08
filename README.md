# SOC Labs – Raphael Orfali

Este repositório contém meus estudos práticos em cibersegurança, com foco em análise de incidentes e Blue Team.

---

## Lab 1 – Investigação de Brute Force

### Objetivo
Identificar tentativas de acesso não autorizado através da análise de logs.

---

### Análise
- Detectadas múltiplas tentativas de login falhas  
- Origem: IP 192.168.1.50 (identificado nos logs)  
- Comportamento consistente com ataque de força bruta  

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
- Implementação de MFA  
- Monitoramento contínuo  
- Investigação da origem interna  

---

## Ferramentas utilizadas
- Logs de autenticação  
- Análise manual  
- OSINT (VirusTotal)  

---

## Evidências

Os logs analisados estão disponíveis abaixo:

Logs analisados: [logs.txt](logs.txt)

---

## Relatório Completo

O relatório detalhado da investigação está disponível abaixo:

[incident-report.md](incident-report.md)
