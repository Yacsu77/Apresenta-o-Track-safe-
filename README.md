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
  <a href="docs/APPLICATIVO.md">Aplicativo</a> ·
  <a href="docs/ECOMERCE.md">E-commerce</a> ·
  <a href="docs/API.md">API</a> ·
  <a href="docs/HARDWARE.md">Hardware</a> ·
  <a href="docs/SECURITY.md">Segurança</a> ·
  <a href="docs/WIKI.md">Wiki</a> ·
  <a href="DOCS/PI_Final.pdf">PI (PDF)</a> ·
  <a href="LICENSE">Licença</a>
</p>

---

## Sobre o repositório

Este repositório é a **apresentação pública** do ecossistema **TrackSafe**. Aqui você encontra a visão técnica e de produto de cada frente — sem expor código proprietário ou segredos de ambiente.

O TrackSafe integra **pulseira inteligente**, **aplicativo móvel**, **API em nuvem** e **loja online** para reduzir o tempo de resposta em emergências e ampliar a proteção da usuária.

---

## Documentação

| Seção | Papel | Banner / Doc |
|-------|--------|----------------|
| **Aplicativo** | App Android (SOS, família, BLE, push) | [docs/APPLICATIVO.md](docs/APPLICATIVO.md) |
| **E-commerce** | Loja, checkout e painel admin | [docs/ECOMERCE.md](docs/ECOMERCE.md) |
| **API** | Backend REST, WebSocket, pagamentos, SMS | [docs/API.md](docs/API.md) |
| **Hardware** | Pulseira ESP32, BLE, botão SOS | [docs/HARDWARE.md](docs/HARDWARE.md) |
| **Segurança** | JWT, rate limit, idempotência, RLS em tempo real | [docs/SECURITY.md](docs/SECURITY.md) |
| **Wiki** | Termos de uso e política de privacidade (LGPD) | [docs/WIKI.md](docs/WIKI.md) |

### Fluxo resumido

```
Pulseira (SOS) ──BLE──► App móvel ──HTTPS/WSS──► API ──► Banco + SMS
                              │
                              └── Loja web (React) ──► mesma API
```

---

## Objetivo do projeto

Desenvolver um sistema funcional que permita **acionar alerta de forma rápida e discreta**, **enviar localização** e **notificar a rede de apoio** cadastrada — contribuindo para a redução do tempo de resposta em situações críticas.

Metodologia baseada em **Design Thinking**, com pesquisa junto a usuárias para validar necessidades reais.

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
- [Termos de uso (Wiki)](docs/WIKI.md) — também em [`DOCS/terms.json`](DOCS/terms.json)

---

## Contato

- [contato@Yacsu.com.br](mailto:contato@Yacsu.com.br)
- [felipe@tecnbr.com.br](mailto:felipe@tecnbr.com.br)

---

## Licença

Este repositório está sob a licença [MIT](LICENSE).
