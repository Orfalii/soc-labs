#  SOC Labs – Raphael Orfali

Este repositório contém meus estudos práticos em cibersegurança, com foco em análise de incidentes e Blue Team.

---

##  Lab 1 – Investigação de Brute Force

###  Objetivo
Identificar tentativas de acesso não autorizado através da análise de logs.

###  Análise
- Detectadas múltiplas tentativas de login falhas
- Origem: IP suspeito (ex: 192.168.1.10)
- Comportamento consistente com ataque de força bruta

###  Conclusão
O padrão indica tentativa automatizada de acesso indevido.

###  Mitigações
- Bloqueio do IP no firewall
- Implementação de MFA
- Monitoramento contínuo

---

##  Ferramentas utilizadas
- Logs de autenticação
- Análise manual
- OSINT (VirusTotal)
