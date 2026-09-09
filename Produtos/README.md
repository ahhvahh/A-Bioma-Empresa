# Produtos

Esta pasta documenta a hierarquia de produtos da **Automações BIOMA**.

## 🏢 Arquitetura de Marca

* **Nome Comercial:** Automações BIOMA
* **Significado do Acrônimo Técnico (BIOMA):**
  * **B**arramento de
  * **I**ntegração e
  * **O**rquestração de
  * **M**ódulos
  * **A**utônomos

## 🐾 Portfólio de Hardware (Linha Fauna)

```text
AUTOMAÇÕES BIOMA
└── Linha Fauna
    └── Carcará HUB
        └── Central de processamento,
            integração e transmissão local
```

### 🦅 Carcará HUB

**Status:** produto principal / primeira prioridade.

Central inteligente e resiliente de processamento e transmissão de dados local para salas, casas e indústrias. Atua como o nó central coordenado pelo ecossistema de orquestração.

Funções previstas:

- concentrar dispositivos, sensores e atuadores;
- operar como gateway Zigbee;
- processar regras e eventos localmente;
- comunicar-se com a plataforma BIOMA;
- publicar telemetria;
- receber comandos remotos autorizados;
- acionar dispositivos físicos compatíveis;
- manter operação degradada quando a conexão externa falhar.

Exemplos de dispositivos que poderão ser controlados conforme integração e autorização:

- relés;
- fechaduras;
- cadeados eletrônicos;
- portas;
- portões;
- iluminação;
- motores e outros atuadores compatíveis.

Diretriz: priorizar resiliência, segurança, rastreabilidade e recuperação automática após falhas de energia ou rede.

Arquivo: [`carcara-hub.md`](carcara-hub.md)

## 🌿 Regra de identidade para novos produtos

A nomenclatura dos produtos e ecossistemas da Automações BIOMA deverá utilizar exclusivamente referências à **fauna e flora brasileiras**.

- **Linha Fauna:** famílias de hardware, dispositivos, sensores, gateways e atuadores.
- **Flora:** nomes destinados a plataformas, serviços ou ecossistemas digitais quando esses produtos forem formalmente definidos.

Nenhum novo produto deve ser incluído no portfólio oficial antes de sua função e posicionamento serem documentados.

## Regras para novos produtos

Todo novo produto deve registrar:

1. problema que resolve;
2. público-alvo;
3. posição no ecossistema BIOMA;
4. relação com fauna ou flora brasileira;
5. interfaces físicas e de comunicação;
6. relação com o Carcará HUB e a plataforma;
7. requisitos de energia;
8. requisitos regulatórios;
9. estratégia de atualização;
10. modelo de comercialização;
11. status: conceito, protótipo, validação, piloto ou produção.

## Próximos passos

- [ ] Fechar requisitos da primeira revisão do Carcará HUB.
- [ ] Definir arquitetura da plataforma de serviços.
- [ ] Definir contrato de comunicação dispositivo ↔ plataforma.
- [ ] Definir modelo de comandos e respostas para atuadores.
- [ ] Definir regras de autorização para ações físicas críticas.
- [ ] Formalizar novos produtos apenas após definição de escopo.