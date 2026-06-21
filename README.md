# 🌱 AgroSmart — Proteção Inteligente de Lavoura com Visão Computacional e IA

> Projeto desenvolvido para a disciplina de **Introdução à Computação** — Centro Universitário CEUB  
> Ciência da Computação · 1º Semestre · Turma A · 2025  
> **Alunas:** Amanda Barros dos Santos & Maria Eduarda Moreira Costa

---

## 📌 Sobre o Projeto

O **AgroSmart** é um sistema integrado de hardware e software que substitui a pulverização indiscriminada de defensivos agrícolas por uma **aplicação cirúrgica guiada por Inteligência Artificial**.

O sistema utiliza câmeras multiespectrais acopladas ao pulverizador agrícola e uma rede neural convolucional (CNN) embarcada em um microcomputador NVIDIA Jetson Nano. A IA analisa cada ponto da lavoura em tempo real e aciona válvulas solenoides individualmente — liberando o defensivo **exclusivamente onde a presença de praga é confirmada**.

### O problema que resolvemos

| Problema | Impacto |
|----------|---------|
| 💸 Desperdício financeiro | Defensivo aplicado em 100% da área, mesmo onde não há praga |
| 🌿 Dano ambiental | Contaminação do solo, lençóis freáticos e insetos polinizadores |
| 🦟 Resistência de pragas | Exposição contínua acelera resistência genética nos insetos |

### Resultado com o AgroSmart

✅ Redução de até **90% no volume de defensivo** utilizado  
✅ Economia de até **R$ 240.000/ano** em propriedades de 500 ha  
✅ Log automático de rastreabilidade por ponto de aplicação  
✅ Payback em menos de **2 safras**

---

## 🏗️ Arquitetura do Sistema

```
CÂMERA (5MP · 30fps)
      │ USB 3.0 / PoE
      ▼
NVIDIA JETSON NANO
  └─ CNN (inferência em ms)
      │ MQTT / Wi-Fi
      ▼
GATEWAY DA FAZENDA
  └─ LoRaWAN / 4G LTE
      │ HTTPS / TLS 1.3
      ▼
NUVEM (AWS IoT Core)
  └─ Logs · Rastreabilidade · Retreinamento do modelo
```

### Camadas de operação

- **Edge (Borda):** câmeras + Jetson Nano no maquinário — processamento local, sem internet
- **Fog (Intermediário):** gateway na sede da fazenda — agrega dados de múltiplas máquinas
- **Cloud (Nuvem):** AWS IoT Core — armazenamento, retreinamento da IA e acesso via app

---

## ⚙️ Componentes de Hardware

| Componente | Especificação |
|------------|---------------|
| Câmera | Multiespectral + RGB · mín. 5 MP · 30 fps |
| Microcomputador | NVIDIA Jetson Nano (4GB RAM) |
| Válvula solenóide | Eletromagnética 12V · resposta < 50ms |
| Conectividade | USB 3.0 · PoE · Wi-Fi · 4G/LTE · LoRaWAN |
| Proteção | Encapsulamento IP67 · conectores industriais M12 |

---

## 🧠 Software — Rede Neural (CNN)

- Modelo de **Rede Neural Convolucional** treinado com imagens de pragas das culturas de soja, milho, algodão e café
- Processamento **100% local** no Jetson Nano (sem dependência de internet no campo)
- Limiar de confiança de **92%** — abaixo disso, o bico é acionado por precaução (fail-safe)
- Atualização remota do modelo via **HTTPS** quando novas pragas são identificadas na região

---

## 🔒 Segurança e Infraestrutura

- **MQTT sobre TLS 1.3** (porta 8883) com autenticação por certificado X.509
- **Firewall iptables** — acesso à porta MQTT restrito à rede interna da fazenda
- **VLANs separadas** — VLAN 10 (controle dos bicos) e VLAN 20 (telemetria/logs)
- **Rate limiting** — máximo 100 mensagens/segundo por cliente no broker MQTT
- **Watchdog** de software reinicia a CNN automaticamente em caso de travamento

---

## 🗂️ Estrutura do Repositório

```
agrismart-av01/
├── Agri Smart.pdf        # Documentação técnica completa (AV01 + AV Final)
└── README.md             # Este arquivo
```

---

## 🔗 Evidências de Desenvolvimento

| Artefato | Link |
|----------|------|
| 📄 Documentação (AV01) | [Agri Smart.pdf](./Agri%20Smart.pdf) |
| ⚡ Simulação Tinkercad (Amanda) | [Circuito Válvula Solenóide](https://www.tinkercad.com/things/8gYeofGD9lP-grand-curcan?sharecode=O0AvYXGHf59nbXQRadszevT4JtV-biezNFlxqrj7DvQ) |
| ⚡ Simulação Tinkercad (Maria) | [Circuito Válvula Solenóide](https://www.tinkercad.com/things/9JTYdJ0XMlV) |
| 💻 Repositório da Maria | [MariihCosta/agrismart-av01](https://github.com/MariihCosta/agrismart-av01) |

---

## 📚 Referências

- EMBRAPA. Tecnologia de Aplicação de Defensivos Agrícolas, 2022.
- IBGE. Censo Agropecuário 2017.
- NVIDIA. Jetson Nano Developer Kit, 2024.
- LeCUN, Y.; Bengio, Y.; Hinton, G. Deep Learning. *Nature*, v. 521, 2015.
- OASIS. MQTT Version 5.0 Specification, 2019.

---

<p align="center">
  Feito com 💚 por Amanda Barros dos Santos & Maria Eduarda Moreira Costa · CEUB 2025
</p>
