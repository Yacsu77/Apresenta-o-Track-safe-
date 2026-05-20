# TrackSafe — E-commerce

[← Voltar ao README](../README.md)

Interface web da **TrackSafe**: loja online e painel administrativo para uma pulseira inteligente com foco em segurança pessoal (SOS, localização e rede de apoio). Projeto em **React + TypeScript**, com backend em serviço separado.

---

## Sobre o projeto

O ecossistema TrackSafe combina hardware, aplicativo e comércio eletrônico. **Este repositório** entrega a experiência no navegador:

- **Loja** — vitrine, catálogo, personalização do produto, carrinho e checkout.
- **Área do cliente** — cadastro, login, perfil, histórico de pedidos e gestão da conta.
- **Painel administrativo** — produtos, pedidos, usuários, métricas e ferramentas operacionais.

---

## Tecnologias utilizadas

| Camada | Tecnologia |
|--------|------------|
| Interface | React 18, TypeScript |
| Ferramenta de build | Vite |
| Navegação | React Router |
| Estilização | CSS customizado (design system com variáveis) |
| Estado compartilhado | React Context |
| Requisições | Fetch API |

---

## Integrações (visão geral)

| Integração | Uso no projeto |
|------------|----------------|
| **API REST** | Autenticação, produtos, pedidos, perfil e operações do admin |
| **Gateway de pagamento** | Checkout com PIX e cartão (processamento no servidor) |
| **Visualização 3D** | Modelo da pulseira na home e na página de personalização |
| **Mapas e gráficos** | Painel admin (localização de eventos e dashboards) |

Detalhes de URLs, chaves e endpoints ficam em variáveis de ambiente locais (não versionadas).

---

## Bibliotecas utilizadas

| Biblioteca | Finalidade |
|------------|------------|
| **React** / **React DOM** | Componentes e renderização |
| **React Router** | Rotas públicas, área logada e admin |
| **Lucide React** | Ícones da interface |
| **Motion** | Transições e animações em páginas |
| **GSAP** | Animações de scroll e hero |
| **Three.js** + **React Three Fiber** | Experiência 3D na página institucional |
| **Vanta.js** | Fundo animado na landing |
| **Recharts** | Gráficos no painel administrativo |
| **Leaflet** | Mapas no admin |
| **Vite** | Desenvolvimento e build de produção |
| **TypeScript** | Tipagem e manutenção do código |

SDK de pagamento carregado apenas onde o checkout exige tokenização segura do cartão.

---

## Segurança (abordagem)

- **Autenticação** com tokens de acesso e renovação automática quando a sessão expira.
- **Rotas privadas** para perfil, checkout e painel admin.
- **Pagamentos**: dados de cartão tokenizados no navegador; credenciais sensíveis não ficam no frontend.
- **Conta do usuário**: fluxo de suspensão com confirmação explícita e prazos informados na interface.
- **Configuração**: segredos e URLs da API apenas em ambiente local/produção, fora do repositório público.

Regras de senha, autorização no servidor e conformidade de dados são tratadas no backend.

---

## Experiência do usuário (loja)

| Área | Funcionalidades |
|------|-----------------|
| Home | Apresentação do produto, benefícios e destaques |
| Produtos | Listagem e página de detalhe |
| Personalizar | Visualização 3D da pulseira |
| Institucional | Quem somos, termos e privacidade |
| Carrinho | Itens, quantidades e total |
| Conta | Login, cadastro, perfil e pedidos |
| Checkout | Finalização com PIX ou cartão (usuário autenticado) |

Fluxo típico: escolher produto → carrinho → identificar-se → pagar → acompanhar pedido no perfil.

---

## Painel administrativo

Acesso restrito a perfis autorizados. Layout dedicado com menu lateral:

| Módulo | Descrição |
|--------|-----------|
| Dashboard | Visão geral e indicadores |
| Produtos | Cadastro e edição do catálogo |
| Pedidos | Acompanhamento de vendas e status |
| Usuários | Gestão de contas |
| Estatísticas | Gráficos e análises |
| E-mail | Ferramentas de comunicação (ex.: convites) |

Inclui visualização geográfica de eventos quando os dados estão disponíveis na API.

---

## Estrutura

```
src/
├── api/         # Camada de comunicação com o backend
├── components/  # Componentes reutilizáveis
├── context/     # Autenticação e carrinho
├── pages/       # Páginas da loja
├── pages/admin/ # Painel administrativo
└── lib/         # Utilitários
```

---

## Contato

Para dúvidas sobre o projeto, parcerias ou portfólio:

- [contato@Yacsu.com.br](mailto:contato@Yacsu.com.br)
- [felipe@tecnbr.com.br](mailto:felipe@tecnbr.com.br)

---

## Portfólio

Projeto desenvolvido no contexto **TrackSafe** (segurança pessoal + e-commerce). Demonstra SPA completa, integração com API, checkout, painel admin e interfaces com animação e 3D. Créditos da equipe na página **Quem somos** da aplicação.
