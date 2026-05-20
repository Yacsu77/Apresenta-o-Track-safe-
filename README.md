<p align="center">
  <img src="Image/Banner%20track%20safe.png" alt="TrackSafe — Dispositivo de segurança pessoal" width="100%" />
</p>

<p align="center">
  <img src="Image/logotipo.png" alt="TrackSafe" width="120" />
</p>

<h1 align="center">TrackSafe</h1>

<p align="center">
  <strong>Dispositivo de segurança pessoal</strong> para mulheres em situações de risco — SOS, localização e rede de apoio.
</p>

<p align="center">
  <a href="docs/ECOMERCE.md">E-commerce</a> ·
  <a href="docs/API.md">API</a> ·
  <a href="docs/HARDWARE.md">Hardware</a> ·
  <a href="docs/SECURITY.md"><strong>Segurança</strong></a> ·
  <a href="DOCS/PI_Final.pdf">Documentação do projeto (PDF)</a> ·
  <a href="LICENSE">Licença</a>
</p>

---

## Sobre o repositório

Este repositório é a **apresentação pública** do ecossistema **TrackSafe**. Aqui você encontra a visão técnica e de produto das três frentes do sistema — sem expor código proprietário ou segredos de ambiente.

O TrackSafe integra **pulseira inteligente**, **aplicativo móvel**, **API em nuvem** e **loja online** para reduzir o tempo de resposta em emergências e ampliar a proteção da usuária.

---

## Arquitetura em três frentes

| Seção | Papel no ecossistema | Documentação |
|-------|----------------------|--------------|
| **E-commerce** | Loja online, checkout, área do cliente e painel administrativo (venda da pulseira) | [docs/ECOMERCE.md](docs/ECOMERCE.md) |
| **API** | Backend REST, autenticação, alertas SOS, pedidos, dados e integrações (Twilio, pagamentos) | [docs/API.md](docs/API.md) |
| **Hardware** | Pulseira física: acionamento SOS, Bluetooth BLE e comunicação com o app | [docs/HARDWARE.md](docs/HARDWARE.md) |
| **Segurança** | Controles da API: JWT, rate limit, idempotência, CORS, pagamentos e WebSocket por família | [docs/SECURITY.md](docs/SECURITY.md) |

### Fluxo resumido

```
Pulseira (SOS) ──BLE──► App móvel ──HTTPS──► API REST ──► Banco + SMS + E-commerce
                              │
                              └── Loja web (React) ──► mesma API
```

---

## Objetivo do projeto

Desenvolver um sistema funcional que permita **acionar alerta de forma rápida e discreta**, **enviar localização** e **notificar a rede de apoio** cadastrada — contribuindo para a redução do tempo de resposta em situações críticas.

Metodologia baseada em **Design Thinking** (imersão, definição, ideação e solução), com pesquisa junto a usuárias para validar necessidades reais.

---

## Equipe

| Integrante | Responsabilidade |
|------------|------------------|
| Felipe Nogueira Silva | Aplicativo móvel |
| Pedro Henrique Carneichuk Rosa | Pulseira (hardware) |
| Stefany Caroline Ferreira Sampaio | Pesquisa, dados e documentação |
| Ranielly Evellyn Cunha | Pesquisa, dados e documentação |

---

## Documentação adicional

- [PI Final — Track Safe (PDF)](DOCS/PI_Final.pdf) — relatório completo do projeto integrador (SENAC)

---

## Contato

- [contato@Yacsu.com.br](mailto:contato@Yacsu.com.br)
- [felipe@tecnbr.com.br](mailto:felipe@tecnbr.com.br)

---

## Licença

Este repositório está sob a licença [MIT](LICENSE).
