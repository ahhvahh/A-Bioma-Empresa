# Carcará HUB

## Papel no ecossistema

O **Carcará HUB** é o gateway principal da Linha Fauna e a primeira prioridade de produto da Bioma Brasil Automações.

## Responsabilidades previstas

- conectar dispositivos e sensores locais;
- operar rede Zigbee;
- manter estado local dos dispositivos;
- executar automações essenciais mesmo sem Internet;
- comunicar-se com a plataforma Bioma por canal autenticado;
- publicar eventos e telemetria;
- receber comandos remotos autorizados;
- permitir atualização segura de firmware;
- recuperar conexão e estado após falhas.

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
  APIs / Dashboards /
  Integrações externas
```

## Princípios de projeto

1. **Local-first:** funções essenciais não devem depender integralmente da nuvem.
2. **Resiliência:** falhas de Internet ou reinicializações não devem provocar perda de configuração crítica.
3. **Rastreabilidade:** cada unidade deve possuir identidade única e versão conhecida de hardware/firmware.
4. **Segurança:** autenticação, autorização, atualização e armazenamento de credenciais devem fazer parte do projeto desde o início.
5. **Observabilidade:** falhas, estado e qualidade de comunicação devem ser mensuráveis.
6. **Interoperabilidade:** protocolos e integrações devem ser documentados e versionados.

## Decisões que ainda precisam ser fechadas

- [ ] microcontrolador/processador definitivo;
- [ ] interfaces de rede definitivas;
- [ ] topologia Zigbee e capacidade alvo;
- [ ] armazenamento local;
- [ ] fonte e proteção elétrica;
- [ ] gabinete;
- [ ] estratégia de provisionamento;
- [ ] protocolo definitivo com a plataforma;
- [ ] mecanismo OTA;
- [ ] critérios de recuperação e modo seguro;
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
