<p align="center">
  <img src="../Image/Banner%20Pulceira.png" alt="TrackSafe — Pulseira inteligente" width="100%" />
</p>

# TrackSafe — Hardware

[← Voltar ao README](../README.md)

**Pulseira inteligente** do ecossistema TrackSafe: dispositivo físico compacto e discreto para **acionamento rápido do SOS**, com comunicação **Bluetooth BLE** ao aplicativo móvel, que encaminha localização e alerta à rede de apoio.

---

## Sobre o dispositivo

A pulseira é a interface **tátil e imediata** da solução em situações de risco:

- Acionamento **rápido e discreto** do botão SOS.
- Comunicação com o smartphone via **Bluetooth Low Energy (BLE 5.0)**.
- Integração ao fluxo do app: alerta → API → notificações e SMS aos contatos cadastrados.

O hardware não substitui o aplicativo: ele **dispara o evento**; o app e a API completam envio de localização, notificações e registro no histórico.

---

## Especificações técnicas

| Item | Especificação |
|------|----------------|
| Microcontrolador | **ESP32-C3 Super Mini** |
| Conectividade | **Bluetooth BLE 5.0** |
| Alimentação | Bateria **Li-Po 3,7 V** recarregável |
| Acionamento | Botão físico **SOS** |
| Formato | Pulseira / acessório discreto |

---

## Papel na arquitetura

```
[ Botão SOS ] ──► ESP32-C3 ── BLE 5.0 ──► App móvel ──► API REST ──► Rede de apoio
```

### Fluxo operacional

1. Usuária pressiona o botão SOS na pulseira.
2. O ESP32 envia o sinal ao aplicativo via Bluetooth.
3. O app obtém localização (GPS) e envia o alerta à API.
4. A API notifica contatos e registra o evento.
5. Histórico disponível no aplicativo.

Também é possível acionar o SOS **diretamente pelo aplicativo**; a pulseira amplia a resposta em situações em que o celular não está à mão ou o acionamento precisa ser mais discreto.

---

## Requisitos de uso

| Requisito | Descrição |
|-----------|-----------|
| Smartphone | Android com Bluetooth e internet ativos |
| Aplicativo | TrackSafe instalado e conta configurada |
| Pulseira | Carregada e **pareada** ao app |
| Rede | Internet no celular para envio do alerta à API |
| Contatos | Rede de apoio cadastrada previamente no app |

---

## Funcionalidades atendidas (hardware)

- Acionamento físico do **alerta de emergência**
- Comunicação **sem fio** com o aplicativo (BLE)
- Uso **discreto** como acessório de segurança pessoal
- Operação com **bateria recarregável** para uso cotidiano

---

## Limitações conhecidas

O funcionamento depende de condições externas ao firmware da pulseira:

| Limitação | Impacto |
|-----------|---------|
| Alcance Bluetooth | Requer proximidade e pareamento com o celular |
| Bateria descarregada | Impede envio do sinal ao app |
| Perda de conexão BLE | Alerta da pulseira não chega ao app até reconectar |
| GPS no celular | Precisão da localização depende do smartphone e do ambiente |
| Internet no celular | Envio final do alerta exige conectividade no dispositivo móvel |

Essas limitações são tratadas na documentação do produto e nos termos de uso do TrackSafe.

---

## Desenvolvimento e protótipo

| Aspecto | Detalhe |
|---------|---------|
| Responsável (hardware) | Pedro Henrique Carneichuk Rosa |
| Etapa do projeto | Protótipo funcional integrado ao app (PI SENAC 2026) |
| Prototipagem visual | Fluxos e telas documentados no [PI Final (PDF)](../DOCS/PI_Final.pdf) |

Esquemáticos, firmware e repositório de código do embarcado **não são publicados** neste repositório de apresentação.

---

## Segurança e uso responsável

- O botão SOS deve ser usado apenas em **situações reais de risco**.
- Alertas falsos podem sobrecarregar a rede de apoio e serviços de mensagem.
- A pulseira é complementar a canais oficiais (190, 180, etc.).
- Manter firmware e app atualizados conforme releases da equipe.

---

## Melhorias futuras (hardware / produto)

Possíveis evoluções mencionadas no planejamento do projeto:

- Maior autonomia de bateria e indicador de carga
- Reforço de robustez do pareamento BLE
- Variantes de design mantendo acionamento discreto
- Integração com sensores adicionais (ex.: detecção de contexto), sujeito a validação com usuárias

---

## Contato

- [contato@Yacsu.com.br](mailto:contato@Yacsu.com.br)
- [felipe@tecnbr.com.br](mailto:felipe@tecnbr.com.br)

---

## Referência

Especificações completas, requisitos funcionais e fluxos de conexão Bluetooth: [DOCS/PI_Final.pdf](../DOCS/PI_Final.pdf)
