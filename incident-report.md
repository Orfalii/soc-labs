# Incident Report – Brute Force Attack

## Data
10/04/2026

## Objetivo
Analisar eventos de autenticação SSH para identificar atividade maliciosa, validar a hipótese de brute force e documentar a classificação do incidente.

---

## Resumo Executivo
Foi identificada uma sequência de 24 falhas de autenticação contra a conta `admin`, seguida por um login bem-sucedido a partir do mesmo endereço IP (`192.168.1.50`).

O padrão observado é compatível com brute force bem-sucedido, com provável comprometimento de credencial e potencial acesso não autorizado a conta privilegiada.

---

## Escopo da Análise
- Fonte de dados: [Logs.txt](Logs.txt)
- Serviço analisado: SSH
- Conta afetada: `admin`
- IOC principal: `192.168.1.50`
- Janela principal do incidente: `10:01:23` a `10:02:13`

---

## Detecção
Durante a revisão do arquivo de autenticação, foi observada repetição anômala de falhas para o mesmo usuário, sempre a partir da mesma origem, intercalada com alguns acessos legítimos de outros usuários.

O ponto crítico da análise é que a sequência termina com autenticação bem-sucedida para a mesma conta e o mesmo IP, o que eleva o caso de tentativa suspeita para provável comprometimento.

---

## Linha do Tempo
- 10:01:23 -> início das falhas de autenticação para `admin`
- 10:01:32 -> acesso legítimo de outro usuário aparece no mesmo intervalo, sem quebrar o padrão do ataque
- 10:01:35 a 10:02:12 -> continuidade das falhas repetidas para `admin`
- 10:02:13 -> login bem-sucedido para `admin` a partir de `192.168.1.50`
- 10:02:18 em diante -> ambiente volta a apresentar eventos regulares de autenticação

---

## Evidências Técnicas
- 24 falhas de autenticação para `admin`
- 1 autenticação bem-sucedida para `admin` logo após a sequência de falhas
- Mesmo IP de origem ao longo de todo o ataque: `192.168.1.50`
- Mesmo serviço alvo: SSH na porta `22`
- Conta visada com perfil privilegiado: `admin`

Trecho mais relevante:
- `10:01:23` a `10:02:12` -> falhas repetidas
- `10:02:13` -> `Accepted password for admin from 192.168.1.50 port 22`

---

## Análise
O comportamento observado é consistente com brute force por tentativa repetitiva de senha contra uma conta administrativa exposta via SSH.

Apesar de existirem eventos benignos misturados no mesmo período, eles não alteram a conclusão da análise. O padrão malicioso permanece claro por causa da repetição, da persistência no mesmo alvo, da origem única e do sucesso final obtido pelo mesmo IP.

O login bem-sucedido após 24 falhas consecutivas contra `admin` é o principal indicador de comprometimento de credencial neste cenário.

---

## Impacto Potencial
- acesso não autorizado a conta administrativa
- possibilidade de persistência no host
- risco de movimentação lateral
- risco de coleta de credenciais adicionais
- exposição operacional do servidor analisado

---

## Indicadores de Comprometimento (IOCs)
- IP suspeito: `192.168.1.50`
- Conta alvo: `admin`
- Serviço: `SSH`
- Porta: `22`
- Técnica observada: `Brute Force`

---

## MITRE ATT&CK
- Técnica: `Brute Force`
- ID: `T1110`
- Tática: `Credential Access`

---

## Classificação do Incidente
- Severidade: Alta
- Status: Confirmado
- Tipo: Acesso não autorizado

Justificativa:
Houve repetição de falhas para a mesma conta administrativa, a partir da mesma origem, seguida por autenticação bem-sucedida. Esse encadeamento é suficiente para classificar o evento como brute force com provável comprometimento de credencial.

---

## Ações Recomendadas
- bloquear temporariamente o IP `192.168.1.50`
- resetar imediatamente a senha da conta `admin`
- revisar se houve atividade pós-login a partir da conta comprometida
- habilitar MFA para acessos administrativos
- restringir exposição do SSH
- aplicar política de bloqueio por tentativas de autenticação
- correlacionar esse IOC com outras fontes de log

---

## Conclusão
Com base nos logs analisados, o incidente deve ser tratado como brute force bem-sucedido contra a conta `admin`, com forte indicação de comprometimento.

O caso exige contenção imediata e validação de possíveis ações executadas após o login bem-sucedido.
