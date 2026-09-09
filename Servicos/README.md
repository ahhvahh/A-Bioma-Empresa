# Serviços

Esta pasta documenta os serviços digitais e operacionais da Bioma Brasil Automações.

## Serviço principal

### Acompanhamento e publicação de dados dos sensores

A plataforma receberá dados dos dispositivos da Linha Fauna, acompanhará seu estado operacional e disponibilizará essas informações para aplicações, dashboards e integrações externas.

Arquivo: [`monitoramento-publicacao-dados.md`](monitoramento-publicacao-dados.md)

## Escopo inicial

- cadastro de clientes, ambientes, hubs e dispositivos;
- provisionamento e associação de dispositivos;
- recepção de telemetria;
- normalização de eventos;
- armazenamento de histórico;
- acompanhamento de disponibilidade e saúde dos dispositivos;
- publicação de dados por APIs e/ou mensageria;
- dashboards operacionais;
- alertas;
- envio de comandos autorizados para dispositivos;
- controle de versão e atualização de firmware;
- auditoria de operações relevantes.

## Modelo de serviço

A plataforma poderá operar em modalidades distintas:

1. **Cloud/SaaS:** infraestrutura gerenciada pela Bioma.
2. **Local/On-premises:** instalação controlada em ambiente do cliente, quando necessário.
3. **Híbrido:** processamento e automação local com sincronização seletiva para a plataforma.

## Princípios

- segurança por padrão;
- comunicação autenticada;
- isolamento lógico entre clientes;
- operação resiliente;
- APIs versionadas;
- observabilidade;
- retenção de dados configurável;
- minimização de dados pessoais;
- rastreabilidade das ações administrativas.

## Roadmap

### Etapa 1 — Telemetria básica

- [ ] identidade do HUB;
- [ ] cadastro do cliente;
- [ ] recepção de status;
- [ ] recepção de sensores;
- [ ] histórico básico.

### Etapa 2 — Operação remota

- [ ] comandos para o HUB;
- [ ] configuração remota;
- [ ] sincronização de dispositivos;
- [ ] acompanhamento de firmware;
- [ ] alertas operacionais.

### Etapa 3 — Plataforma comercial

- [ ] multi-tenant;
- [ ] dashboards;
- [ ] gestão de usuários e permissões;
- [ ] APIs públicas controladas;
- [ ] webhooks;
- [ ] faturamento/licenciamento;
- [ ] SLA e suporte.

### Etapa 4 — Ecossistema

- [ ] integrações com plataformas de automação;
- [ ] conectores de terceiros;
- [ ] análise de dados;
- [ ] regras e automações avançadas;
- [ ] catálogo de dispositivos e serviços.
