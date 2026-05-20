# TrackSafe — API

[← Voltar ao README](../README.md)

Backend **REST** do ecossistema **TrackSafe**: processamento de alertas SOS, autenticação, gestão de usuários e contatos de emergência, integração com o aplicativo móvel, e-commerce e serviços externos. Hospedagem em nuvem, com persistência relacional e comunicação segura via HTTPS.

---

## Sobre o serviço

A API é o **núcleo de integração** entre as camadas do sistema:

- **Aplicativo móvel** (React Native + Expo) — cadastro, perfil, grupo familiar, alertas e histórico.
- **E-commerce** (React + TypeScript) — produtos, pedidos, checkout e painel administrativo.
- **Hardware** — indiretamente, via app que encaminha eventos da pulseira após conexão Bluetooth.

Responsável por validar requisições, aplicar regras de negócio, persistir dados e acionar notificações (incluindo SMS de emergência).

---

## Tecnologias e infraestrutura

| Camada | Tecnologia |
|--------|------------|
| API | REST (HTTP/JSON) |
| Hospedagem | Render |
| Banco de dados | PostgreSQL (Supabase) |
| SMS (alertas SOS) | Twilio |
| Pagamentos | Gateway integrado no servidor (PIX e cartão) |

Credenciais, URLs e chaves de integração ficam apenas em variáveis de ambiente — **não versionadas** neste repositório de apresentação.

---

## Papel na arquitetura

```
App móvel ──┐
            ├── HTTPS ──► API REST (Render) ──► PostgreSQL (Supabase)
E-commerce ─┘                              └──► Twilio (SMS SOS)
```

### Fluxo do alerta SOS (resumo)

1. Usuária aciona o SOS na pulseira ou no aplicativo.
2. O app envia o alerta e a localização para a API.
3. A API persiste o evento e dispara notificações.
4. Contatos de emergência recebem SMS (Twilio) e/ou notificações no app.
5. O histórico fica disponível para consulta na aplicação.

---

## Domínios funcionais

| Domínio | Descrição |
|---------|-----------|
| **Autenticação** | Login, tokens de acesso, renovação de sessão e redefinição de senha |
| **Usuários e perfil** | Cadastro, dados da conta e gestão de credenciais |
| **Rede de apoio** | Contatos de emergência e grupo familiar |
| **Alertas SOS** | Registro de acionamentos, localização e histórico |
| **E-commerce** | Catálogo, pedidos, pagamentos e operações administrativas |
| **Administração** | Métricas, usuários, pedidos e ferramentas operacionais para perfis autorizados |

Regras de senha, autorização por perfil e conformidade de dados sensíveis são aplicadas **no servidor**.

---

## Modelo de dados (visão geral)

Banco relacional **PostgreSQL** com modelo orientado a:

- Usuárias e autenticação
- Contatos de emergência e notificações
- Histórico de alertas e eventos
- Dados de e-commerce (produtos, pedidos, etc.)

O diagrama entidade-relacionamento (DER) completo está documentado no [relatório do projeto (PDF)](../DOCS/PI_Final.pdf).

---

## Integrações externas

| Serviço | Uso |
|---------|-----|
| **Twilio** | Disparo de SMS aos contatos cadastrados em emergência |
| **Gateway de pagamento** | Processamento de PIX e cartão no checkout (servidor) |
| **Supabase** | PostgreSQL gerenciado para persistência |

---

## Segurança e conformidade

- Comunicação via **HTTPS** entre clientes e API.
- **Autenticação baseada em tokens**; renovação quando a sessão expira.
- **Autorização no servidor** para rotas de perfil, admin e operações sensíveis.
- Tratamento de **dados de localização** e informações pessoais alinhado à **LGPD**.
- Alinhamento com contexto legal de proteção à mulher (Lei Maria da Penha e legislação correlata).
- Segredos, connection strings e chaves de API **fora do repositório público**.

O alerta SOS **não substitui** serviços oficiais de emergência (190, 180, etc.) — conforme termos do produto.

---

## Requisitos não funcionais (API)

| Aspecto | Abordagem |
|---------|-----------|
| Disponibilidade | Hospedagem contínua em nuvem |
| Desempenho | Resposta rápida ao acionamento do SOS |
| Escalabilidade | API preparada para crescimento de carga na Render |
| Persistência | Dados críticos em PostgreSQL |
| Compatibilidade | Consumo por app Android e frontend web |

---

## Consumidores da API

| Cliente | Principais operações |
|---------|----------------------|
| App móvel | SOS, localização, contatos, perfil, Bluetooth (via app) |
| E-commerce | Loja, checkout, pedidos, admin |
| Painel admin (web) | Dashboards, usuários, pedidos, estatísticas e mapas |

Detalhes de endpoints, contratos e exemplos de payload permanecem nos repositórios privados de implementação.

---

## Contato

- [contato@Yacsu.com.br](mailto:contato@Yacsu.com.br)
- [felipe@tecnbr.com.br](mailto:felipe@tecnbr.com.br)

---

## Referência

Documentação institucional e requisitos completos: [DOCS/PI_Final.pdf](../DOCS/PI_Final.pdf)
