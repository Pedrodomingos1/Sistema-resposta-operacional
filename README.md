🛡️ SROC: Sistema de Resposta Operacional CríticaEste repositório contém uma infraestrutura de microserviços de missão crítica, desenvolvida para eliminar o gargalo da latência em operações de um aglomerado de empresas da região. O sistema integra ingestão de alta performance (FastAPI), resiliência de dados (Redis) e orquestração de contingência (n8n), garantindo conformidade operacional e resposta a incidentes em tempo real.📋 Descrição do ProjetoO objetivo do SROC é estancar o prejuízo gerado pela demora na triagem de crises operacionais. Através de um pipeline de engenharia robusto, eventos críticos de múltiplos canais são centralizados, validados e processados sem intervenção manual lenta, garantindo que o tempo de resposta (MTTR) seja reduzido drasticamente, protegendo o ROI e a continuidade do negócio.A solução utiliza uma arquitetura de microserviços orientada a eventos, focada em resiliência: se a carga aumentar ou um serviço falhar, a fila de mensagens garante que nenhum dado ou alerta seja perdido.🛠️ Stack TecnológicoLinguagem & API: Python 3.9+ com FastAPI (Ingestão assíncrona e segura).Orquestração: n8n (Lógica de decisão e integração de fluxos).Mensageria/Fila: Redis (Resiliência e mitigação de picos de carga).Persistência/Auditoria: PostgreSQL (Log imutável para conformidade LGPD).Infraestrutura: Docker & Docker Compose (Isolamento e escalabilidade).Monitoramento: Webhooks e Logs de Auditoria em tempo real.🏗️ Arquitetura da SoluçãoO fluxo segue um padrão de alta disponibilidade, garantindo que a decisão técnica ocorra em milissegundos.Snippet de códigograph TD
    subgraph Ingestão de Alta Performance
    A["Sistemas Legados / ERP / Monitoramento"] -->|Eventos Críticos| B("API FastAPI (Python)")
    B -->|Validação & Sanitização| C[("Fila de Mensagens Redis")]
    end
    
    subgraph Inteligência Operacional
    C -->|Consumo Assíncrono| D{"n8n (Cérebro do Fluxo)"}
    D -->|Scripts Python Customizados| E{"Cálculo de Impacto"}
    E -->|Urgência Crítica| F["Protocolo de Contingência Instantâneo"]
    E -->|Monitoramento| G["Log de Status"]
    end
    
    subgraph Saída e Auditoria
    F -->|Alerta / Notificação| H["WhatsApp / Slack / Telegram"]
    F -->|Comando de Rede / SSH| I["Remediação Automática"]
    H --> J[("Banco de Dados PostgreSQL (Auditoria)")]
    I --> J
    G --> J
    end

    style B fill:#4a90e2,stroke:#333,stroke-width:2px,color:#fff
    style C fill:#d0021b,stroke:#333,stroke-width:2px,color:#fff
    style D fill:#f5a623,stroke:#333,stroke-width:2px,color:#fff
    style J fill:#7ed321,stroke:#333,stroke-width:2px,color:#fff
⚙️ Funcionalidades PrincipaisIngestão Anti-Gargalo: Endpoint FastAPI otimizado para receber milhares de requisições simultâneas sem perda de performance.Resiliência Operacional: Utilização do Redis como buffer. Mesmo que o orquestrador sofra manutenção, as mensagens permanecem seguras na fila para processamento posterior.Triagem Técnica (Python): Lógica customizada para identificar falsos positivos e priorizar crises reais baseada em parâmetros de negócio.Auditoria e Conformidade (LGPD): Todo incidente gera um log imutável no PostgreSQL, permitindo rastrear o "Quem, Quando e Como" de cada crise resolvida.Notificação Multi-canal: Alertas críticos enviados instantaneamente para os tomadores de decisão, eliminando o tempo de "e-mail parado na caixa de entrada".Containerização Total: Ambiente 100% dockerizado, permitindo que a solução seja replicada em minutos para diferentes unidades ou empresas do aglomerado.🚀 Instalação e ExecuçãoPré-requisitosDocker e Docker Compose instalados.Python 3.9+ (para desenvolvimento local).Passo 1: Configuração do AmbienteClone o repositório e acesse a pasta do projeto:Bashgit clone https://github.com/seu-usuario/sroc-resiliencia-operacional.git
cd sroc-resiliencia-operacional
Passo 2: Subir a Infraestrutura (Docker)O comando abaixo inicia o FastAPI, Redis, n8n e PostgreSQL de forma integrada:Bashdocker-compose up -d
Passo 3: Documentação da APIAcesse a documentação Swagger para testar a ingestão de incidentes:http://localhost:8000/docs📂 Estrutura de Auditoria (Logs de Conformidade)O controle de estado e auditoria é mantido no PostgreSQL com a seguinte estrutura lógica:ID_EventoOrigem (Empresa/Setor)Descrição do IncidenteStatusTempo de RespostaResponsável NotificadoSR-982Unidade_Industrial_01Queda de Link FibraRESOLVIDO14sGestor TI / Diretor OpsSR-983Financeiro_SedeTentativa de Acesso IndevidoBLOQUEADO2msCISO / SegurançaNota: Este sistema é uma ferramenta de infraestrutura crítica. A configuração de segurança de rede e firewall deve acompanhar a implementação conforme a política de cada empresa parceira.
