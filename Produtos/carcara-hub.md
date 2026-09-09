# Carcará HUB

## Papel no ecossistema

O **Carcará HUB** é o gateway principal da Linha Fauna e a primeira prioridade de produto da **Automações BIOMA**.

É a central inteligente e resiliente de processamento e transmissão de dados local para salas, casas e indústrias, atuando como o nó central coordenado pelo ecossistema de orquestração.

## Responsabilidades previstas

- conectar dispositivos, sensores e atuadores locais;
- operar rede Zigbee;
- manter estado local dos dispositivos;
- processar regras e eventos;
- comunicar-se com a plataforma BIOMA por canal autenticado;
- publicar eventos e telemetria;
- receber comandos remotos autorizados;
- executar ações físicas em dispositivos compatíveis;
- permitir atualização segura de firmware;
- recuperar conexão e estado após falhas.

## Ações físicas previstas

O Carcará HUB deverá permitir, conforme hardware, integração e política de autorização:

- acionamento de relés;
- abertura e fechamento de portas;
- abertura e fechamento de portões;
- liberação e bloqueio de fechaduras;
- liberação de cadeados eletrônicos;
- controle de iluminação;
- acionamento de motores e outros atuadores compatíveis.

A execução de comandos críticos deverá possuir autenticação, autorização, rastreabilidade e confirmação de resultado sempre que tecnicamente possível.

## Arquitetura conceitual

```text
Sensores / Atuadores
        │
      Zigbee
        │
        ▼
  ┌───────────────┐
  │ Carcará HUB   │
  │               │
  │ Regras locais │
  │ Estado local  │
  │ Segurança     │
  └───────┬───────┘
          │
   MQTT / API segura
          │
          ▼
  Plataforma BIOMA
          │
          ├── Monitoramento
          ├── Orquestração
          ├── APIs / Dashboard
          └── Comandos remotos
                    │
                    ▼
              Mundo físico
```

## Princípios de projeto

1. **Resiliência:** falhas de Internet ou reinicializações não devem provocar perda de configuração crítica.
2. **Operação local:** funções essenciais previamente autorizadas poderão continuar disponíveis localmente quando aplicável.
3. **Rastreabilidade:** cada unidade deve possuir identidade única e versão conhecida de hardware/firmware.
4. **Segurança:** autenticação, autorização, atualização e armazenamento de credenciais devem fazer parte do projeto desde o início.
5. **Confirmação de ação:** comandos físicos não devem ser considerados concluídos apenas porque foram transmitidos.
6. **Observabilidade:** falhas, estado e qualidade de comunicação devem ser mensuráveis.
7. **Interoperabilidade:** protocolos e integrações devem ser documentados e versionados.

## Decisões que ainda precisam ser fechadas

- [ ] microcontrolador/processador definitivo;
- [ ] interfaces de rede definitivas;
- [ ] topologia Zigbee e capacidade alvo;
- [ ] armazenamento local;
- [ ] fonte e proteção elétrica;
- [ ] gabinete;
- [ ] estratégia de provisionamento;
- [ ] protocolo definitivo com a plataforma;
- [ ] modelo de comandos e confirmação de execução;
- [ ] mecanismo OTA;
- [ ] critérios de recuperação e modo seguro;
- [ ] política de autorização para ações físicas críticas;
- [ ] requisitos para homologação Anatel.

## Fases

### Fase 0 — definição

- arquitetura;
- requisitos;
- interfaces;
- custo-alvo;
- estratégia regulatória.

### Fase 1 — protótipo

- módulos de desenvolvimento;
- validação Zigbee;
- comunicação com backend;
- persistência local;
- comandos remotos;
- acionamento de atuadores;
- confirmação de execução;
- testes de reconexão.

### Fase 2 — PCB piloto

- primeira PCB integrada;
- testes elétricos e térmicos;
- testes de RF;
- pré-compliance;
- ajustes de gabinete e fonte.

### Fase 3 — certificação

- congelamento da revisão candidata;
- OCD;
- ensaios;
- homologação Anatel;
- documentação de produção.

### Fase 4 — lote piloto

- produção controlada;
- instalação em campo;
- monitoramento de falhas;
- validação operacional.

### Fase 5 — produção

- liberação comercial;
- controle de versões;
- suporte e atualização contínua.