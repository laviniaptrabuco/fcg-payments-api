> **FIAP Cloud Games (FCG)**: este repositório faz parte do projeto, com um repositório por componente. Guia central e lista de repositórios: [fcg-orchestration](https://github.com/laviniaptrabuco/fcg-orchestration#reposit%C3%B3rios-do-projeto). Entrega da Fase 2 deste componente: [tag `fase-2`](https://github.com/laviniaptrabuco/fcg-payments-api/tree/fase-2).

# FCG Payments API

Microsserviço responsável por processar (simular) pagamentos de compra de jogos da FIAP Cloud Games.

## Responsabilidades

- Consome `OrderPlacedEvent` do RabbitMQ
- Simula o processamento do pagamento (90% aprovação)
- Publica `PaymentProcessedEvent` com status `Approved` ou `Rejected`

## Tipo de Projeto

Worker Service (.NET 8) — sem endpoints HTTP, processa mensagens em background.

## Variáveis de Ambiente

| Variável | Descrição | Exemplo |
|---|---|---|
| `RabbitMQ__Host` | Host do RabbitMQ | `rabbitmq` |
| `RabbitMQ__Username` | Usuário RabbitMQ | `guest` |
| `RabbitMQ__Password` | Senha RabbitMQ | `guest` |

## Fluxo de Mensagens

```
OrderPlacedEvent (consumido) → [Simula Pagamento] → PaymentProcessedEvent (publicado)
```
