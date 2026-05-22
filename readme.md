# README — Fundamentos de Internet das Coisas (IoT)

## Introdução

A **Internet das Coisas (IoT)** conecta dispositivos físicos à internet, permitindo coleta, troca e análise de dados em tempo real. Sensores, atuadores, redes de comunicação e plataformas inteligentes trabalham juntos para automatizar processos, monitorar ambientes e gerar informações estratégicas.

Este repositório apresenta os principais conceitos da arquitetura IoT, protocolos de comunicação e o conceito de **Digital Twin**.

---

# Arquitetura em Três Camadas

A arquitetura clássica de sistemas IoT é dividida em três camadas principais:

1. Camada de Percepção (Hardware)  
2. Camada de Rede (Conectividade)  
3. Camada de Aplicação  

---

## Camada de Percepção (Hardware)

A **Camada de Percepção** é responsável pela interação direta com o mundo físico.

Ela utiliza:

- **Sensores** → coletam dados do ambiente.
- **Atuadores** → executam ações físicas com base nos comandos recebidos.

### Exemplos de Sensores
- Sensor de temperatura
- Sensor de umidade
- Sensor de movimento
- Sensor de luminosidade
- GPS

### Exemplos de Atuadores
- Motores
- Relés
- LEDs
- Válvulas automáticas

### Função Principal
Capturar informações do ambiente e transformar fenômenos físicos em dados digitais.

### Exemplo Prático
Um sensor de temperatura mede o calor de uma sala e envia os dados para o sistema IoT.

---

## Camada de Rede (Conectividade)

A **Camada de Rede** é responsável pela comunicação entre dispositivos, servidores e aplicações.

Ela garante que os dados coletados pelos sensores sejam transmitidos corretamente.

### Tecnologias Utilizadas
- Wi-Fi
- Bluetooth
- Zigbee
- LoRaWAN
- Ethernet
- 4G/5G

### Protocolos de Transporte
- MQTT
- HTTP/REST
- CoAP

### Função Principal
Transportar dados entre dispositivos IoT e sistemas de processamento.

### Exemplo Prático
Um sensor envia dados via MQTT para um broker na nuvem.

---

## Camada de Aplicação

A **Camada de Aplicação** é onde os dados são:

- Processados
- Armazenados
- Analisados
- Exibidos ao usuário

Essa camada normalmente utiliza:
- APIs
- Bancos de dados
- Dashboards
- Inteligência Artificial
- Computação em nuvem

### Função Principal
Transformar dados em informações úteis para tomada de decisão.

### Exemplo Prático
Um aplicativo mostra gráficos de temperatura em tempo real para o usuário.

---

# Fluxo de Funcionamento da Arquitetura IoT

```text
[Sensores/Atuadores]
        ↓
[Camada de Rede]
        ↓
[Servidor/Nuvem]
        ↓
[Aplicação/Dashboard]
        ↓
[Usuário Final]
```

---

# Protocolos de Comunicação em IoT

Os protocolos de comunicação definem como os dispositivos trocam informações.

## Tabela Comparativa

| Protocolo | Modelo | Consumo de Banda | Velocidade | Segurança | Uso Ideal |
|---|---|---|---|---|---|
| MQTT | Publish/Subscribe | Baixo | Alta | TLS/SSL | Sensores e dispositivos com pouca energia |
| HTTP (REST) | Cliente/Servidor | Médio/Alto | Média | HTTPS | APIs web e integração com sistemas |
| CoAP | Cliente/Servidor | Muito Baixo | Alta | DTLS | Dispositivos restritos e redes IoT leves |

---

## MQTT

O **MQTT (Message Queuing Telemetry Transport)** é um protocolo leve muito utilizado em IoT.

### Características
- Baixo consumo de banda
- Comunicação eficiente
- Modelo Publish/Subscribe
- Ideal para dispositivos limitados

### Funcionamento
- **Publisher** envia mensagens.
- **Broker** distribui mensagens.
- **Subscriber** recebe mensagens.

### Vantagens
- Baixo consumo de energia
- Alta eficiência
- Excelente para tempo real

### Desvantagens
- Necessita de broker MQTT
- Menor compatibilidade direta com navegadores

---

## 🔹 HTTP (REST)

O **HTTP** é o protocolo mais utilizado na internet.

### Características
- Comunicação Cliente/Servidor
- Amplamente compatível
- Fácil integração com APIs

### Vantagens
- Simples implementação
- Compatível com aplicações web
- Grande suporte

### Desvantagens
- Maior consumo de banda
- Mais pesado para dispositivos IoT pequenos

---

## CoAP

O **CoAP (Constrained Application Protocol)** foi criado especificamente para IoT.

### Características
- Muito leve
- Baseado em UDP
- Baixo consumo energético

### Vantagens
- Excelente para dispositivos limitados
- Baixa latência
- Menor overhead

### Desvantagens
- Menos popular que MQTT e HTTP
- Menor suporte em plataformas tradicionais

---

# Digital Twin

## O que é?

O **Digital Twin (Gêmeo Digital)** é uma representação virtual de um objeto, sistema ou processo físico.

Ele recebe dados em tempo real de sensores IoT e simula o comportamento do elemento físico.

---

## Como Funciona

```text
Objeto Físico
      ↓
Sensores IoT
      ↓
Coleta de Dados
      ↓
Modelo Virtual (Digital Twin)
      ↓
Análise e Simulação
```

---

## Objetivos do Digital Twin

- Monitoramento em tempo real
- Simulação de cenários
- Previsão de falhas
- Otimização de processos
- Redução de custos

---

## Exemplos de Uso

### Indústria
Monitoramento de máquinas industriais para manutenção preditiva.

### Saúde
Representação virtual de pacientes para análise médica.

### Cidades Inteligentes
Simulação de trânsito, energia e infraestrutura urbana.

### Agricultura
Monitoramento de solo, irrigação e clima.

---

# Sistema de Monitoramento de Nível de Água com ESP32

## Objetivo

Projetar a arquitetura de um sistema IoT capaz de monitorar o nível de água utilizando um sensor ultrassônico conectado a um microcontrolador ESP32, enviando os dados para a nuvem via rede Wi-Fi.

---

# Arquitetura Técnica do Sistema

## Fluxo da Comunicação

```text
[Sensor Ultrassônico HC-SR04]
        │
        │ Sinal Digital (Trigger/Echo)
        ▼
[ESP32 - Microcontrolador]
        │
        │ Wi-Fi + MQTT
        ▼
[Roteador Wi-Fi]
        │
        │ Internet/TCP-IP
        ▼
[Servidor/Nuvem]
        │
        │ Dashboard / Banco de Dados
        ▼
[Usuário Final]
```

---

# Descrição das Etapas

## Sensor Físico — Sensor Ultrassônico HC-SR04

O sensor ultrassônico é responsável por medir a distância entre o sensor e a superfície da água.

### Funcionamento
- O pino **Trigger** envia um pulso ultrassônico.
- O pino **Echo** recebe o retorno do sinal refletido.
- O tempo de retorno é utilizado para calcular a distância.

###  Tipo de Comunicação
- **Sinal Digital**

### Dados Coletados
- Distância em centímetros
- Nível da água calculado

---

## Microcontrolador — ESP32

O ESP32 processa os dados recebidos do sensor e realiza a comunicação com a internet.

### Funções
- Ler os dados do sensor
- Calcular o nível da água
- Conectar ao Wi-Fi
- Enviar dados para a nuvem

### Protocolos Utilizados
- Wi-Fi
- MQTT

### Vantagens do ESP32
- Baixo custo
- Wi-Fi integrado
- Baixo consumo energético
- Alta compatibilidade com IoT

---

## Rede — Roteador Wi-Fi

O roteador é responsável por fornecer acesso à internet para o ESP32.

### Funções
- Transmitir os dados do ESP32
- Fazer a conexão com servidores externos

### Protocolos Utilizados
- TCP/IP
- Wi-Fi IEEE 802.11

---

## Servidor / Nuvem

O servidor recebe os dados enviados pelo ESP32 e os armazena para análise e visualização.

### Funções
- Armazenamento de dados
- Monitoramento em tempo real
- Geração de alertas
- Dashboard de visualização

### Tecnologias Possíveis
- Firebase
- AWS IoT
- ThingsBoard
- Node-RED
- MQTT Broker

---

# Exemplo do Fluxo de Dados

```text
Sensor mede distância da água
        ↓
ESP32 calcula o nível
        ↓
ESP32 envia dados via MQTT
        ↓
Roteador Wi-Fi transmite para internet
        ↓
Servidor recebe e armazena
        ↓
Dashboard exibe informações em tempo real
```

---

# Protocolos Utilizados

| Etapa | Protocolo/Conexão |
|---|---|
| Sensor ➜ ESP32 | Sinal Digital |
| ESP32 ➜ Roteador | Wi-Fi |
| ESP32 ➜ Nuvem | MQTT |
| Roteador ➜ Internet | TCP/IP |

---

# Benefícios da Arquitetura

- Monitoramento remoto em tempo real
- Baixo custo de implementação
- Fácil escalabilidade
- Baixo consumo de energia
- Comunicação eficiente usando MQTT

---
