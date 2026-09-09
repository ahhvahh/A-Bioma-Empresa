# Serviços

Esta pasta documenta os serviços digitais e operacionais da **Automações BIOMA**.

## Serviço principal

### Acompanhamento, publicação de dados e operação de dispositivos

A plataforma receberá dados dos dispositivos da Linha Fauna, acompanhará seu estado operacional e disponibilizará essas informações para aplicações, dashboards e integrações externas.

Além do monitoramento, a plataforma também deverá permitir o envio de comandos autorizados para atuação sobre dispositivos físicos conectados ao ecossistema BIOMA.

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
- confirmação e auditoria da execução de comandos;
- controle de versão e atualização de firmware;
- auditoria de operações relevantes.

## Operação sobre dispositivos físicos

A plataforma poderá orquestrar ações como:

- abrir ou fechar portas;
- abrir ou fechar portões;
- liberar ou bloquear fechaduras;
- liberar cadeados eletrônicos;
- acionar relés;
- controlar iluminação;
- comandar motores e outros atuadores compatíveis.

A disponibilidade de cada ação dependerá das capacidades do dispositivo, das permissões do usuário e das regras de segurança configuradas.

## Modelo de serviço

A plataforma poderá operar em modalidades distintas:

1. **Cloud/SaaS:** infraestrutura gerenciada pela Automações BIOMA.
2. **Local/On-premises:** instalação controlada em ambiente do cliente, quando necessário.
3. **Híbrido:** processamento e operação local com sincronização seletiva para a plataforma.

## Princípios

- segurança por padrão;
- comunicação autenticada;
- isolamento lógico entre clientes;
- operação resiliente;
- APIs versionadas;
- observabilidade;
- retenção de dados configurável;
- minimização de dados pessoais;
- rastreabilidade das ações administrativas e físicas;
- confirmação de resultado para comandos críticos sempre que possível.

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
- [ ] comandos para atuadores;
- [ ] confirmação de execução;
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

## Identidade dos ecossistemas

As plataformas e serviços da Automações BIOMA deverão seguir a identidade baseada exclusivamente na **fauna e flora brasileiras**. Novos nomes de plataformas e serviços serão formalizados apenas quando seus respectivos escopos estiverem definidos.