<p align="center">
  <img src="../Image/Banner%20.png" alt="TrackSafe — API" width="100%" />
</p>

# TrackSafe — API

[← Voltar ao README](../README.md) · [Aplicativo](APPLICATIVO.md) · **[Segurança](SECURITY.md)** · [Wiki](WIKI.md)

Backend **REST** e canais **em tempo real** do ecossistema **TrackSafe**: processamento de alertas SOS, autenticação, gestão de usuários e contatos de emergência, integração com aplicativo móvel, e-commerce e serviços externos. Hospedagem em nuvem, com persistência relacional e comunicação segura via HTTPS.

---

## Sobre o serviço

A API é o **núcleo de integração** entre as camadas do sistema:

| Cliente | Função |
|---------|--------|
| **Aplicativo móvel** (React Native + Expo) | Cadastro, perfil, grupo familiar, alertas, histórico e pareamento com a pulseira |
| **E-commerce** (React + TypeScript) | Produtos, pedidos, checkout e painel administrativo |
| **Hardware** | Eventos da pulseira encaminhados pelo app após conexão Bluetooth |

Responsável por validar requisições, aplicar regras de negócio, persistir dados, acionar notificações (SMS) e servir **atualizações em tempo real** ao grupo familiar autorizado.

---

## Tecnologias e infraestrutura

| Camada | Tecnologia |
|--------|------------|
| API HTTP | REST (JSON) sobre Express |
| Tempo real | WebSocket com isolamento por família |
| Hospedagem | Render |
| Banco de dados | PostgreSQL (Supabase) |
| SMS (alertas SOS) | Twilio |
| Pagamentos | Gateway Mercado Pago (servidor) |
| Ficheiros | Storage compatível (via API, chaves só no servidor) |

Credenciais e URLs ficam **apenas** em variáveis de ambiente — não versionadas neste repositório.

---

## Papel na arquitetura

```
App móvel ──┐
            ├── HTTPS (REST) ──► API ──► PostgreSQL
E-commerce ─┘         │              └──► Twilio (SMS)
                      └── WSS (tempo real, por família)
Pulseira ──BLE──► App ──► API
```

### Fluxo do alerta SOS (resumo)

1. Usuária aciona o SOS na pulseira ou no aplicativo.
2. O app envia alerta e localização para a API.
3. A API persiste, notifica contatos e regista histórico.
4. Membros autorizados do grupo podem receber atualizações em tempo real no canal WebSocket.

---

## Domínios funcionais

| Domínio | Descrição |
|---------|-----------|
| **Autenticação** | Login, access/refresh token, redefinição de senha |
| **Usuários e perfil** | Cadastro, conta e gestão de credenciais |
| **Rede de apoio** | Contatos de emergência e grupo familiar |
| **Alertas SOS** | Acionamentos, localização e histórico |
| **Tempo real** | Rastreamento e eventos via WebSocket (escopo familiar) |
| **E-commerce** | Catálogo, pedidos, pagamentos, webhooks |
| **Administração** | Métricas, utilizadores, pedidos e operações `master` |
| **Storage** | Upload de avatares e imagens de produto (com autorização) |

---

## Segurança (resumo)

Controles principais implementados no backend — detalhes na página dedicada **[Segurança da API](SECURITY.md)** (documento público, sem segredos nem código).

| Área | Medida |
|------|--------|
| **Transporte** | HTTPS obrigatório em produção |
| **Autenticação** | JWT access + refresh (segredos distintos) |
| **Autorização** | Papéis `user` / `master`; regra próprio recurso ou admin |
| **Abuso HTTP** | Rate limiter por IP |
| **Duplicação** | Chave de identidade para idempotência (instância única hoje) |
| **E-commerce** | Preço e totais calculados só no servidor |
| **Dados** | Senhas em bcrypt; SQL parametrizado; Postgres com SSL |
| **CORS** | Restringir origens em produção |
| **Tempo real** | WebSocket autenticado + isolamento por família (RLS no canal) |
| **Pagamentos** | Credenciais e webhooks só no servidor; cartão tokenizado no cliente |

→ Documentação completa: **[docs/SECURITY.md](SECURITY.md)**

---

## Modelo de dados (visão geral)

Banco relacional **PostgreSQL** com entidades para utilizadores, grupo familiar, alertas, e-commerce (produtos, pedidos, pagamentos) e registo de eventos de webhook. DER completo no [relatório PDF](../DOCS/PI_Final.pdf).

---

## Integrações externas

| Serviço | Uso |
|---------|-----|
| **Twilio** | SMS aos contatos em emergência |
| **Mercado Pago** | PIX, cartão (token) e notificações de pagamento |
| **Supabase** | PostgreSQL e storage de objetos (acesso via API) |

---

## Requisitos não funcionais

| Aspecto | Abordagem |
|---------|-----------|
| Disponibilidade | Hospedagem contínua em nuvem |
| Desempenho | Resposta rápida ao SOS |
| Proteção | Rate limit e validação em todas as rotas sensíveis |
| Escalabilidade | API na Render; idempotência por chave evolui para store partilhado em multi-instância |
| Persistência | PostgreSQL em produção; modo em memória apenas em testes |

---

## Consumidores

| Cliente | Operações principais |
|---------|----------------------|
| App móvel | SOS, família, perfil, Bluetooth, WebSocket |
| Loja web | Catálogo, checkout, conta |
| Painel admin | Gestão, estatísticas, mapas |

Contratos de API, endpoints e payloads: **repositórios privados** da equipa.

---

## Contato

- [contato@Yacsu.com.br](mailto:contato@Yacsu.com.br)
- [felipe@tecnbr.com.br](mailto:felipe@tecnbr.com.br)

---

## Referência

- [Segurança da API](SECURITY.md)
- [PI Final (PDF)](../DOCS/PI_Final.pdf)
