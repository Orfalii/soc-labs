# Incident Report – Brute Force Attack

## Data
10/04/2026

## Objetivo
Analisar eventos de autenticação SSH para identificar atividade maliciosa, validar a hipótese de brute force e documentar a classificação do incidente.

---

## Detecção
Durante a análise dos logs, foram identificadas múltiplas tentativas de login falhas para o usuário "admin", seguidas de um login bem-sucedido a partir do mesmo endereço IP.

---

## Linha do Tempo (Timeline)

- 10:01:23 → Falha de login (admin)
- 10:01:25 → Falha de login (admin)
- 10:01:27 → Falha de login (admin)
- 10:02:10 → Login bem-sucedido

---

## Evidências Técnicas

- IP de origem: 192.168.1.50  
- Porta utilizada: 22 (SSH)  
- Tipo de autenticação: senha  
- Padrão de tentativa repetitiva  

Arquivo analisado: [Logs.txt](Logs.txt)  

---

## Análise
O comportamento observado é característico de um ataque de força bruta (brute force), onde um atacante tenta diversas combinações de senha até obter sucesso.

O fato de o login ter sido bem-sucedido após múltiplas falhas indica comprometimento da conta.

---

## Impacto
- Comprometimento da conta "admin"  
- Possível acesso não autorizado ao sistema  
- Risco de movimentação lateral e escalonamento de privilégios  

---

## Ações Recomendadas

- Bloquear o IP no firewall  
- Resetar a senha da conta comprometida  
- Implementar autenticação multifator (MFA)  
- Monitorar atividades suspeitas adicionais  
- Investigar a origem do IP (possível máquina interna comprometida)  

---

## Conclusão
Foi identificado um ataque de brute force com sucesso, resultando no comprometimento da conta "admin". Medidas imediatas devem ser tomadas para conter o incidente e evitar novos acessos não autorizados.

---

## Indicadores de Comprometimento (IOCs)

- IP suspeito: 192.168.1.50  
- Porta: 22 (SSH)  
- Tipo de ataque: Brute Force  

---

## MITRE ATT&CK

- Técnica: Brute Force  
- ID: T1110  
- Tática: Credential Access  

---

## Classificação do Incidente

- Severidade: Alta  
Justificativa: houve sucesso de autenticação após múltiplas falhas consecutivas para a conta admin via SSH, indicando provável comprometimento de credencial com potencial de acesso privilegiado.
- Status: Confirmado  
Justificativa: a sequência temporal, a repetição do mesmo usuário, a origem única e o sucesso subsequente suportam a hipótese de brute force com comprometimento.
- Tipo: Acesso não autorizado
