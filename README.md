SROC: Sistema de Resposta Operacional Crítica

🛡️O SROC é um microssistema de engenharia desenvolvido para eliminar a latência em respostas a incidentes. Ele centraliza, filtra e resolve crises operacionais que afetam o faturamento (ROI) de empresas da região.

🛠️ Como o Sistema Funciona (Fluxo de Trabalho)
Para garantir clareza total, o fluxo segue este caminho lógico:

ENTRADA: A API (FastAPI) recebe um alerta de erro ou evento crítico.

TRIAGEM: O sistema valida os dados e joga para uma fila de segurança (Redis).

DECISÃO: O orquestrador (n8n) avalia a gravidade:

Se for Média/Baixa: Apenas registra no banco de dados para relatório.

Se for ALTA/CRÍTICA: Dispara protocolos de urgência.

AÇÃO: O sistema envia avisos imediatos (WhatsApp/Slack) ou executa comandos de correção.

AUDITORIA: Tudo é gravado no PostgreSQL para conformidade com a LGPD.

⚙️ O Que o SROC Faz na Prática
Ingestão Sem Quedas: Usa FastAPI para receber milhares de alertas sem travar o sistema.

Fila de Proteção: O Redis impede que mensagens se percam se houver uma sobrecarga de incidentes.

Ramos de Resposta: O sistema sabe diferenciar um "teste de rotina" de uma "queda de servidor".

Log de Conformidade: Gera uma tabela de auditoria para que o gestor saiba quem resolveu o quê e em quanto tempo.

🛠️ Ferramentas Utilizadas (Stack)
Linguagem: Python (FastAPI)

Fila/Resiliência: Redis

Orquestração: n8n

Banco de Dados: PostgreSQL

Infraestrutura: Docker
