# Produtos

Esta pasta documenta a hierarquia de produtos da Bioma Brasil Automações.

## Hierarquia

```text
BIOMA BRASIL AUTOMAÇÕES
└── Linha Fauna
    ├── Carcará HUB
    │   └── Hub principal / gateway / processamento local
    ├── Guará Sensor
    │   └── Sensores periféricos e telemetria ambiental
    └── Tatu Guard
        └── Segurança, resiliência e armazenamento local
```

## Estratégia da Linha Fauna

A linha utiliza nomes de animais brasileiros para identificar famílias de dispositivos físicos. Cada família deverá ter finalidade clara e evitar sobreposição desnecessária de funções.

## 1. Carcará HUB

**Status:** produto principal / primeira prioridade.

Funções previstas:

- concentrar dispositivos e sensores;
- operar como gateway Zigbee;
- processar regras e eventos localmente;
- comunicar-se com a plataforma Bioma;
- publicar telemetria;
- receber comandos remotos autorizados;
- manter operação degradada quando a conexão externa falhar.

Diretriz: priorizar resiliência, operação local e recuperação automática após falhas de energia/rede.

Arquivo: [`carcara-hub.md`](carcara-hub.md)

## 2. Guará Sensor

**Status:** roadmap.

Família destinada a módulos periféricos de aquisição de dados.

Exemplos:

- temperatura;
- umidade;
- presença/movimento;
- abertura;
- luminosidade;
- qualidade ambiental;
- outros sensores definidos por aplicação.

Diretriz: baixo consumo, instalação simples e comunicação confiável com o Carcará HUB.

## 3. Tatu Guard

**Status:** roadmap.

Família destinada a funções de proteção e continuidade do ecossistema.

Possíveis responsabilidades:

- armazenamento local seguro;
- backup de eventos;
- gestão de chaves/credenciais;
- isolamento de serviços;
- contingência de conectividade;
- auditoria e integridade de dados.

## Regras para novos produtos

Todo novo produto deve registrar:

1. problema que resolve;
2. público-alvo;
3. posição na Linha Fauna;
4. interfaces físicas e de comunicação;
5. relação com o Carcará HUB e a plataforma;
6. requisitos de energia;
7. requisitos regulatórios;
8. estratégia de atualização;
9. modelo de comercialização;
10. status: conceito, protótipo, validação, piloto ou produção.

## Próximos passos

- [ ] Fechar requisitos da primeira revisão do Carcará HUB.
- [ ] Definir arquitetura da plataforma de serviços.
- [ ] Definir contrato de comunicação dispositivo ↔ plataforma.
- [ ] Definir primeiro conjunto de sensores Guará.
- [ ] Revisar a necessidade e o escopo do Tatu Guard após validar o HUB.
