# Monitoramento, Publicação de Dados e Orquestração

## Objetivo

Criar o serviço responsável por receber, acompanhar, armazenar e disponibilizar os dados produzidos pelos sensores e hubs do ecossistema **Automações BIOMA**, além de encaminhar comandos autorizados para dispositivos físicos.

## Fluxo conceitual

```text
Sensores / Atuadores
   │
   ▼
Carcará HUB
   │
   │ MQTT / HTTPS / protocolo seguro
   ▼
Plataforma BIOMA
   │
   ├──► Normalização
   │       │
   │       └──► Regras / Eventos / Alertas
   │
   ├──► Armazenamento
   │       ├── estado atual
   │       └── histórico
   │
   ├──► Publicação
   │       ├── API
   │       ├── Webhooks
   │       ├── MQTT/event bus
   │       └── Dashboard
   │
   └──► Orquestração
           ├── comandos
           ├── autorização
           ├── confirmação
           └── auditoria
                    │
                    ▼
              Carcará HUB
                    │
                    ▼
              Atuadores físicos
```

## Entidades mínimas

- **Cliente** — organização ou usuário responsável pelo ambiente.
- **Ambiente** — residência, sala, loja, galpão ou área monitorada.
- **Hub** — Carcará HUB associado ao cliente/ambiente.
- **Dispositivo** — sensor ou atuador conectado ao HUB.
- **Sensor** — origem de uma ou mais grandezas medidas.
- **Atuador** — dispositivo capaz de executar uma ação física.
- **Medição** — valor capturado em determinado instante.
- **Evento** — ocorrência relevante derivada de dispositivo, regra ou sistema.
- **Comando** — solicitação enviada da plataforma para o HUB/dispositivo.

## Identificação

Cada HUB deverá possuir uma identidade única de fabricação.

Fluxo inicial proposto:

1. HUB inicializa.
2. Carrega identidade e configuração local.
3. Conecta ao serviço BIOMA.
4. Autentica o dispositivo.
5. Informa identificação, versão de hardware, firmware e capacidades.
6. Plataforma associa o HUB a um cliente quando provisionado.
7. Plataforma devolve configuração autorizada e estado conhecido.
8. HUB passa a publicar telemetria usando sua identidade e o contexto do cliente.
9. HUB passa a receber comandos compatíveis com suas permissões e capacidades.

## Telemetria mínima do HUB

- timestamp;
- identificador do HUB;
- cliente/ambiente quando provisionado;
- versão do firmware;
- revisão de hardware;
- uptime;
- conectividade;
- qualidade de rede quando disponível;
- quantidade de dispositivos conectados;
- estado de armazenamento local;
- erros relevantes;
- reinicializações e causa, quando detectável.

## Dados de sensores

Cada medição deve possuir no mínimo:

- identificador do dispositivo;
- identificador do sensor/canal;
- tipo da grandeza;
- valor;
- unidade;
- timestamp de origem;
- qualidade/status da leitura, quando aplicável.

## Atuadores e ações físicas

Cada atuador deverá declarar suas capacidades. Exemplos:

- relé: ligar/desligar;
- porta: abrir/fechar, quando houver mecanismo compatível;
- portão: abrir/fechar/parar;
- fechadura: bloquear/liberar;
- cadeado eletrônico: bloquear/liberar;
- iluminação: ligar/desligar/regular, quando suportado;
- motor: iniciar/parar/posicionar, conforme dispositivo.

A plataforma não deve assumir capacidades que o dispositivo não tenha declarado.

## Publicação para terceiros

### API

Usar APIs versionadas para:

- consultar dispositivos;
- consultar estado atual;
- consultar histórico;
- consultar eventos;
- consultar capacidades de atuadores;
- enviar comandos autorizados;
- consultar resultado de comandos.

### Webhooks

Permitir publicação de eventos relevantes sem exigir polling constante.

Exemplos:

- sensor excedeu limite;
- dispositivo ficou offline;
- HUB reiniciou;
- presença detectada;
- bateria baixa;
- comando concluído/falhou;
- alteração de estado de uma porta, portão ou fechadura.

### Mensageria

Quando necessário, disponibilizar integração por MQTT ou sistema interno de eventos para clientes que precisem de consumo contínuo de telemetria.

## Comandos remotos

Todo comando deve possuir:

- identificador único;
- origem/usuário/serviço;
- destino;
- tipo de comando;
- parâmetros;
- timestamp;
- expiração;
- política de autorização;
- estado: criado, autorizado, enviado, recebido, executado, falhou ou expirou;
- resultado.

Não assumir que a entrega da mensagem significa execução do comando.

Para operações físicas críticas, a plataforma deverá registrar quem solicitou a ação, qual dispositivo recebeu o comando e qual foi o resultado informado.

## Segurança

Requisitos iniciais:

- identidade única por HUB;
- autenticação mútua ou mecanismo equivalente;
- TLS;
- rotação/revogação de credenciais;
- autorização por cliente, usuário e dispositivo;
- segregação multi-tenant;
- trilha de auditoria;
- proteção contra replay de comandos;
- expiração de comandos;
- atualização segura de firmware;
- princípio do menor privilégio;
- políticas específicas para comandos de acesso físico.

## Operação offline

O HUB deverá manter funções essenciais previamente definidas quando a plataforma estiver indisponível.

Quando a conexão retornar:

1. autenticar novamente;
2. sincronizar estado;
3. enviar eventos pendentes conforme política de retenção;
4. resolver divergências de configuração;
5. reconciliar comandos pendentes conforme validade e política de segurança;
6. retomar publicação normal.

## Retenção

Definir políticas separadas para:

- estado atual;
- telemetria bruta;
- eventos;
- comandos;
- confirmações de execução;
- logs técnicos;
- auditoria;
- dados pessoais, se existirem.

## LGPD e privacidade

Antes de armazenar dados que possam identificar ou ser associados a pessoas:

- definir finalidade;
- minimizar coleta;
- definir base legal adequada;
- definir retenção;
- controlar acesso;
- registrar compartilhamentos;
- permitir atendimento aos direitos aplicáveis dos titulares.

Sensores ambientais sem identificação pessoal direta ainda devem ser avaliados pelo contexto de uso, especialmente presença, ocupação, controle de acesso e rotinas.

## Próximas decisões técnicas

- [ ] MQTT, HTTPS ou combinação dos dois para dispositivo ↔ plataforma.
- [ ] formato de mensagem e versionamento.
- [ ] estratégia de autenticação do HUB.
- [ ] cadastro/provisionamento inicial.
- [ ] modelo de capacidades dos dispositivos.
- [ ] modelo de comandos e respostas.
- [ ] política de autorização para ações físicas.
- [ ] banco para estado atual.
- [ ] banco para séries temporais/histórico.
- [ ] sistema interno de eventos.
- [ ] política de retenção.
- [ ] modelo multi-tenant.
- [ ] API pública.
- [ ] webhooks.
- [ ] observabilidade e SLA.