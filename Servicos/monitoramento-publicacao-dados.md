# Monitoramento e Publicação de Dados

## Objetivo

Criar o serviço responsável por receber, acompanhar, armazenar e disponibilizar os dados produzidos pelos sensores e hubs do ecossistema Bioma.

## Fluxo conceitual

```text
Sensores
   │
   ▼
Carcará HUB
   │
   │ MQTT / HTTPS / protocolo seguro
   ▼
Ingestão BIOMA
   │
   ├──► Normalização
   │       │
   │       └──► Regras / Eventos / Alertas
   │
   ├──► Armazenamento
   │       ├── estado atual
   │       └── histórico
   │
   └──► Publicação
           ├── API
           ├── Webhooks
           ├── MQTT/event bus
           └── Dashboard
```

## Entidades mínimas

- **Cliente** — organização ou usuário responsável pelo ambiente.
- **Ambiente** — residência, sala, loja, galpão ou área monitorada.
- **Hub** — Carcará HUB associado ao cliente/ambiente.
- **Dispositivo** — sensor ou atuador conectado ao HUB.
- **Sensor** — origem de uma ou mais grandezas medidas.
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

## Publicação para terceiros

### API

Usar APIs versionadas para:

- consultar dispositivos;
- consultar estado atual;
- consultar histórico;
- consultar eventos;
- enviar comandos autorizados.

### Webhooks

Permitir publicação de eventos relevantes sem exigir polling constante.

Exemplos:

- sensor excedeu limite;
- dispositivo ficou offline;
- HUB reiniciou;
- presença detectada;
- bateria baixa;
- comando concluído/falhou.

### Mensageria

Quando necessário, disponibilizar integração por MQTT ou barramento de eventos para clientes que precisem consumo contínuo de telemetria.

## Comandos remotos

Todo comando deve possuir:

- identificador único;
- origem/usuário/serviço;
- destino;
- tipo de comando;
- parâmetros;
- timestamp;
- expiração;
- estado: criado, enviado, recebido, executado, falhou ou expirou;
- resultado.

Não assumir que a entrega da mensagem significa execução do comando.

## Segurança

Requisitos iniciais:

- identidade única por HUB;
- autenticação mútua ou mecanismo equivalente;
- TLS;
- rotação/revogação de credenciais;
- autorização por cliente e dispositivo;
- segregação multi-tenant;
- trilha de auditoria;
- proteção contra replay de comandos;
- atualização segura de firmware;
- princípio do menor privilégio.

## Operação offline

O HUB deverá manter funções essenciais quando a plataforma estiver indisponível.

Quando a conexão retornar:

1. autenticar novamente;
2. sincronizar estado;
3. enviar eventos pendentes conforme política de retenção;
4. resolver divergências de configuração;
5. retomar publicação normal.

## Retenção

Definir políticas separadas para:

- estado atual;
- telemetria bruta;
- eventos;
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

Sensores ambientais sem identificação pessoal direta ainda devem ser avaliados pelo contexto de uso, especialmente presença, ocupação e rotinas.

## Próximas decisões técnicas

- [ ] MQTT, HTTPS ou combinação dos dois para dispositivo ↔ plataforma.
- [ ] formato de mensagem e versionamento.
- [ ] estratégia de autenticação do HUB.
- [ ] cadastro/provisionamento inicial.
- [ ] banco para estado atual.
- [ ] banco para séries temporais/histórico.
- [ ] barramento interno de eventos.
- [ ] política de retenção.
- [ ] modelo multi-tenant.
- [ ] API pública.
- [ ] webhooks.
- [ ] observabilidade e SLA.
