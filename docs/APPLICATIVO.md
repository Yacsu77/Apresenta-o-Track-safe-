<p align="center">
  <img src="../Image/Banner%20track%20safe.png" alt="TrackSafe — Aplicativo móvel" width="100%" />
</p>

# TrackSafe — Aplicativo

[← Voltar ao README](../README.md) · [API](API.md) · [Hardware](HARDWARE.md) · [Segurança](SECURITY.md)

Aplicativo **móvel** da **TrackSafe** para Android: SOS, localização, rede de apoio, grupo familiar e conexão com a **pulseira inteligente** via Bluetooth. Desenvolvido em **React Native** com **Expo**, integrado à API em nuvem.

---

## Sobre o aplicativo

O app é o **centro operacional** da solução no dia a dia da usuária:

- Acionamento do **alerta SOS** (pelo app ou pela pulseira).
- **Compartilhamento de localização** com contatos e familiares cadastrados.
- **Notificações push** e encaminhamento de **SMS** em emergência (via API).
- **Grupo familiar** para recebimento mútuo de alertas.
- **Histórico** de acionamentos e gestão de perfil.
- **Pareamento Bluetooth** com a pulseira TrackSafe.

O e-commerce e o painel web complementam a experiência (compra da pulseira e administração); o app concentra a **segurança em tempo real**.

---

## Tecnologias utilizadas

| Camada | Tecnologia |
|--------|------------|
| Framework | React Native |
| Toolchain | Expo |
| Plataforma alvo | Android |
| Comunicação API | HTTPS (REST) + WebSocket (tempo real) |
| Dispositivo | Bluetooth BLE (pulseira) |
| Notificações | Push (Expo) |

---

## Funcionalidades principais

| Área | Descrição |
|------|-----------|
| **SOS** | Envio imediato de alerta com localização à rede cadastrada |
| **Pulseira** | Conexão BLE; acionamento físico repassado ao app |
| **Grupo familiar** | Membros autorizados recebem alertas e atualizações |
| **Contatos de emergência** | Cadastro para SMS em situações críticas |
| **Perfil** | Conta, foto opcional, alteração de dados e exclusão |
| **Histórico** | Consulta de alertas anteriores |
| **Tempo real** | Atualizações via canal autenticado (escopo da família) |

---

## Integrações

| Integração | Uso no app |
|------------|------------|
| **API REST** | Login, perfil, SOS, família, contatos |
| **WebSocket** | Rastreamento e eventos em tempo real (família) |
| **Pulseira (BLE)** | Sinal do botão SOS e estado de conexão |
| **Expo / Push** | Notificações de alerta |
| **GPS** | Localização no acionamento do SOS |

Credenciais e URLs da API vêm de configuração de build — **não** versionadas neste repositório público.

---

## Fluxo típico de emergência

1. Usuária aciona SOS no app **ou** na pulseira (Bluetooth).
2. O app obtém localização e envia o alerta à API.
3. A API notifica familiares (push/SMS) e regista o evento.
4. Membros do grupo acompanham atualizações em tempo real, quando aplicável.

**Importante:** o TrackSafe **não substitui** serviços oficiais (190, 180, 192, 193). Em risco à vida, contactar as autoridades imediatamente.

---

## Requisitos de uso

| Requisito | Detalhe |
|-----------|---------|
| Sistema | Android com Bluetooth e internet |
| Conta | Cadastro com e-mail verificado |
| Idade | A partir de 16 anos (16–18 com autorização dos responsáveis) |
| Pulseira | Opcional; carregada e pareada para acionamento remoto |
| Rede de apoio | Contatos e familiares configurados previamente |

---

## Segurança e privacidade (app)

- Autenticação com tokens; sessão renovada conforme política da API.
- Localização tratada sob **LGPD**, em geral apenas no contexto do SOS.
- Senhas e regras de acesso validadas no **servidor** — ver [Segurança da API](SECURITY.md).
- Termos completos: [Wiki — Termos de uso](WIKI.md).

---

## Papel na arquitetura

```
Pulseira ──BLE──► App (Expo) ──HTTPS/WSS──► API ──► Banco · SMS · Push
                      │
                      └── Utilizadora + grupo familiar
```

---

## Equipe

Desenvolvimento do aplicativo móvel: **Felipe Nogueira Silva**.

---

## Contato

- [contato@Yacsu.com.br](mailto:contato@Yacsu.com.br)
- [felipe@tecnbr.com.br](mailto:felipe@tecnbr.com.br)

---

## Referências

- [Hardware — Pulseira](HARDWARE.md)
- [API](API.md)
- [Wiki — Termos e privacidade](WIKI.md)
- [PI Final (PDF)](../DOCS/PI_Final.pdf)
