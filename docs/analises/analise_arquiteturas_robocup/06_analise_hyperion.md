# Análise Detalhada: Hyperion (Brisbane Boys College)
## Arquitetura e Inovações - Insights para ESP32

**Equipe**: Hyperion  
**País**: Austrália  
**Instituição**: Brisbane Boys' College  
**Competição**: RoboCup Junior Soccer Lightweight League 2025  
**Membros**:
- Thomas McCabe (Software & Documentation)
- Luke Atherton (Hardware & Structural)
- Samaksh Garg (Software & Strategy)
- Matthew Adams (Hardware & Electrical)

---

## 🏗️ 1. ARQUITETURA DE HARDWARE

### 1.1 Visão Geral do Sistema

```
┌─────────────────────────────────────────────┐
│         Main Controller Board               │
│         (Placa Principal Integrada)         │
│                                             │
│  Componentes:                               │
│  - Teensy 4.1                              │
│  - OpenMV H7 Plus                          │
│  - IMU BNO055                               │
│  - Módulo Bluetooth HC-05                  │
│  - Circuito de Fonte de Alimentação         │
└─────┬───────┬───────┬───────────────────────┘
      │       │       │
      ▼       ▼       ▼
┌────────┐ ┌────┐ ┌─────────┐
│Placa   │ │IMU │ │4x Motor  │
│Sensor  │ │BNO │ │Driver    │
│Luz     │ │055 │ │DRV8870   │
│(32     │ │    │ │          │
│clusters│ │    │ │          │
│)       │ │    │ │          │
└────────┘ └────┘ └─────────┘
```

### 1.2 Componentes Principais

#### Main Controller Board (Placa Principal Integrada)
- **Teensy 4.1**: CPU principal
- **OpenMV H7 Plus**: Módulo de visão dedicado
- **IMU BNO055**: Orientação
- **Bluetooth HC-05**: Comunicação sem fio
- **Fonte de Alimentação**: Reguladores 5V/3.3V

#### Light Sensor Board (Placa de Sensor de Luz)
- **32 clusters** de componentes (fototransistores + LEDs)
- **2x MTX90DIPW** (multiplexadores 4 bits)
- **Layout circular** para detecção 360°
- **Propósito**: Detectar posição da bola, limites do campo

#### Sensores TSSPS8038
- **16 sensores** dispostos em layout circular
- **Visão 360°** para detecção de bola
- **Alta resolução** e taxa de quadros
- **Conectados à Placa Principal**

### 1.3 Fluxograma Lógico Elétrico

```
Entradas:
  - 16x Sensor de Luz (TSSPS8038)
  - 32x Clusters Sensor de Luz (Placa)
  - 1x IMU (BNO055)
  - 1x Câmera (OpenMV H7 Plus)
         │
         ▼
┌─────────────────┐
│   Teensy 4.1     │
│   (Processamento)│
└────────┬─────────┘
         │
    ┌────┴────┐
    ▼         ▼
┌────────┐ ┌──────────┐
│4x Motor│ │Bluetooth │
│Driver  │ │HC-05     │
│DRV8870 │ │          │
└────────┘ └──────────┘
```

---

## 🔄 2. ANÁLISE DE VIABILIDADE COM ESP32

### 2.1 Substituição do Teensy 4.1

#### Comparação Técnica

| Aspecto | Teensy 4.1 | ESP32-S3 | Viabilidade |
|---------|-----------|----------|-------------|
| **Clock** | 600 MHz | 240 MHz | ⚠️ Menos, mas suficiente |
| **RAM** | 1 MB | 512 KB | ⚠️ Menos, mas adequado |
| **GPIOs** | 55 | 45 | ✅ Suficiente |
| **ADC** | 14 canais | 20 canais | ✅ Melhor! |
| **PWM** | 10 canais | 16 canais | ✅ Melhor! |
| **I2C** | 3 | 2 | ✅ Suficiente |
| **UART** | 8 | 3 | ⚠️ Menos, mas suficiente |
| **WiFi/Bluetooth** | Não (precisa HC-05) | Sim (integrado) | ✅ Grande vantagem! |
| **Custo** | ~R$ 300 | ~R$ 60 | ✅ 5x mais barato! |

#### Conclusão: **VIÁVEL** ⭐⭐⭐⭐ (4/5)

### 2.2 Análise de Cada Subsistema

#### 2.2.1 Sensores TSSPS8038 (16 unidades)

**Requisitos**:
- 16 leituras analógicas
- Alta frequência de amostragem
- Processamento para detecção de bola

**Com ESP32-S3**:
- ✅ **20 canais ADC** (suficiente para 16 sensores)
- ✅ **DMA disponível** para leitura eficiente
- ✅ **Taxa de amostragem**: Até 2 MSPS
- ✅ **Muito viável**

**Implementação**:
```cpp
// ESP32-S3 tem 20 ADCs, suficiente para 16 sensores
const int IR_SENSORS = 16;
const int ADC_PINS[16] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16};

void readAllIRSensors(int* values) {
  for(int i = 0; i < IR_SENSORS; i++) {
    values[i] = analogRead(ADC_PINS[i]);
  }
}
```

**Viabilidade**: ⭐⭐⭐⭐⭐ (5/5)

#### 2.2.2 Placa de Sensor de Luz (32 clusters)

**Requisitos**:
- 32 clusters de sensores
- Multiplexadores para reduzir pinos
- Detecção de linha branca

**Com ESP32-S3**:
- ✅ **Multiplexadores funcionam igual** (protocolo padrão)
- ✅ **20 ADCs** podem ler via multiplexador
- ✅ **Processamento similar** ao Teensy

**Viabilidade**: ⭐⭐⭐⭐⭐ (5/5)

#### 2.2.3 OpenMV H7 Plus

**Requisitos**:
- Módulo de visão dedicado
- Comunicação UART com CPU principal
- Processamento de imagens

**Com ESP32-S3**:
- ✅ **Pode usar OpenMV** (comunicação UART)
- ✅ **OU melhor**: Usar câmera OV2640 diretamente via DVP
- ✅ **Interface DVP dedicada** (mais eficiente que UART)

**Viabilidade**: ⭐⭐⭐⭐⭐ (5/5) - Pode até ser melhor!

#### 2.2.4 IMU BNO055

**Requisitos**:
- Comunicação I2C
- Frequência: ~100 Hz

**Com ESP32-S3**:
- ✅ **I2C nativo**
- ✅ **Bibliotecas disponíveis**
- ✅ **Muito simples**

**Viabilidade**: ⭐⭐⭐⭐⭐ (5/5)

#### 2.2.5 Bluetooth HC-05

**Requisitos**:
- Comunicação sem fio
- Coordenação entre robôs

**Com ESP32-S3**:
- ✅ **Bluetooth integrado** (não precisa módulo!)
- ✅ **Custo zero adicional**
- ✅ **Mais flexível** (BLE e Classic)

**Viabilidade**: ⭐⭐⭐⭐⭐ (5/5) - Melhor que original!

#### 2.2.6 Motores (4x DRV8870)

**Requisitos**:
- Controle PWM
- 4 motores independentes

**Com ESP32-S3**:
- ✅ **16 canais PWM** (suficiente para 4 motores)
- ✅ **Hardware PWM** (LEDC)
- ✅ **Muito viável**

**Viabilidade**: ⭐⭐⭐⭐⭐ (5/5)

---

## 💡 3. INOVAÇÕES ESTRATÉGICAS RELEVANTES

### 3.1 Sistema TSSPP Melhorado

**Conceito**: Cálculo de direção da bola usando média ponderada

**Sistema Anterior**:
- Amostra cada sensor 255 vezes
- Falha se um sensor falhar

**Sistema Novo**:
- Calcula 4 principais leituras
- Média ponderada por coordenadas X e Y
- Mais preciso e confiável

**Relevância para ESP32**:
- ✅ **Fácil de implementar** (cálculo simples)
- ✅ **Não requer muito processamento**
- ✅ **Pode melhorar ainda mais** com filtros

**Viabilidade**: ⭐⭐⭐⭐⭐ (5/5)

### 3.2 Estratégia de Velocidade Variável

**Conceito**: Ajustar velocidade baseado na distância da bola

**Mecanismo**:
- Mais perto da bola → velocidade mais lenta (controle preciso)
- Mais longe da bola → velocidade mais alta (posicionamento rápido)

**Relevância para ESP32**:
- ✅ **Fácil de implementar** (função exponencial)
- ✅ **Não requer muito processamento**
- ✅ **Melhora controle** significativamente

**Viabilidade**: ⭐⭐⭐⭐⭐ (5/5)

### 3.3 Estratégia de Defensor com 3 PIDs

**Conceito**: Três controladores PID para movimento eficaz

1. **PID 1**: Força do robô para a posição
2. **PID 2**: Posição do robô em relação ao gol
3. **PID 3**: Posição do robô em relação à bola

**Relevância para ESP32**:
- ✅ **PIDs são simples** (cálculos básicos)
- ✅ **ESP32 pode rodar múltiplos PIDs** facilmente
- ✅ **Hardware timer** para loops precisos

**Viabilidade**: ⭐⭐⭐⭐⭐ (5/5)

### 3.4 Detecção de Cluster de Linha

**Conceito**: Detectar 1, 2 ou 3 clusters de linha branca

**Algoritmo**:
- Identifica clusters de sensores ativados
- Calcula ângulo médio
- Estima direção da linha

**Relevância para ESP32**:
- ✅ **Processamento de arrays** (ESP32 faz bem)
- ✅ **Cálculos trigonométricos** (bibliotecas disponíveis)
- ✅ **Não muito intensivo**

**Viabilidade**: ⭐⭐⭐⭐ (4/5)

---

## 🔧 4. ARQUITETURA RECOMENDADA COM ESP32-S3

### 4.1 Estrutura Proposta

```
┌─────────────────────────────────────────────┐
│         ESP32-S3 (CPU Único)                │
│         FreeRTOS - Múltiplas Tasks           │
│                                              │
│  Core 0:                                     │
│    Task 1: Leitura Sensores IR (50Hz)       │
│    Task 2: Leitura Sensores Linha (100Hz)   │
│    Task 3: Leitura IMU (100Hz)              │
│    Task 4: Captura Câmera (10-20Hz)         │
│    Task 5: Processamento Visão              │
│                                              │
│  Core 1:                                     │
│    Task 6: Controle Motores (1kHz)          │
│    Task 7: Controle Kicker                  │
│    Task 8: Lógica de Jogo (50Hz)            │
│    Task 9: Comunicação Bluetooth            │
└─────┬───────┬───────┬───────────────────────┘
      │       │       │
      ▼       ▼       ▼
┌────────┐ ┌────┐ ┌─────────┐
│16 Sens.│ │IMU │ │Câmera   │
│IR      │ │BNO │ │OV2640   │
│TSSPS   │ │055 │ │(DVP)    │
│8038    │ │    │ │         │
└────────┘ └────┘ └─────────┘
      │
      ▼
┌────────┐
│32 Sens.│
│Linha   │
│(via    │
│MUX)    │
└────────┘
```

### 4.2 Vantagens sobre Arquitetura Original

✅ **Custo**: 5x mais barato (R$ 60 vs R$ 300)
✅ **Bluetooth**: Integrado (não precisa HC-05)
✅ **Câmera**: Interface DVP (melhor que UART)
✅ **Mais ADCs**: 20 vs 14 (vantagem)
✅ **Mais PWMs**: 16 vs 10 (vantagem)
✅ **WiFi**: Integrado para debug

---

## 📊 5. COMPARAÇÃO DE DESEMPENHO

### 5.1 Métricas Esperadas

| Métrica | Teensy 4.1 | ESP32-S3 | Adequado? |
|---------|-----------|----------|-----------|
| **Leitura 16 Sensores IR** | < 1 ms | < 2 ms | ✅ Sim |
| **Leitura 32 Sensores Linha** | < 2 ms | < 3 ms | ✅ Sim |
| **Processamento Visão** | ~10-20 ms | ~20-50 ms | ⚠️ Mais lento, mas aceitável |
| **Controle 4 Motores** | < 0.5 ms | < 1 ms | ✅ Sim |
| **Lógica de Jogo** | < 5 ms | < 10 ms | ✅ Sim |
| **Latência Total** | ~20-30 ms | ~30-60 ms | ✅ Aceitável para lightweight |

### 5.2 Análise de Carga

**Com FreeRTOS e dual-core**:
- **Core 0**: Sensores + Visão (~70% carga)
- **Core 1**: Controle + Comunicação (~50% carga)
- **Margem**: Suficiente

**Conclusão**: ESP32-S3 é **suficiente** para lightweight league

---

## 💰 6. ANÁLISE DE CUSTOS

### 6.1 Arquitetura Original (Hyperion)

| Componente | Custo |
|------------|-------|
| Teensy 4.1 | R$ 300 |
| OpenMV H7 Plus | R$ 750 |
| Bluetooth HC-05 | R$ 30 |
| **TOTAL MCU + Visão** | **R$ 1080** |

### 6.2 Arquitetura ESP32-S3

| Componente | Custo |
|------------|-------|
| ESP32-S3 | R$ 60 |
| Câmera OV2640 | R$ 25 |
| Multiplexador (se necessário) | R$ 3 |
| **TOTAL MCU + Visão** | **R$ 88** |

**Economia**: R$ 992 (92% de redução!) ✅

---

## 🎯 7. INSIGHTS ESPECÍFICOS PARA SEU TCC

### 7.1 Sistema de Visão

**Hyperion usa**: OpenMV H7 Plus (módulo dedicado)

**Você pode usar**: ESP32-S3 + OV2640 (mais barato e integrado)

**Vantagens do seu approach**:
- ✅ **Custo 30x menor** (R$ 25 vs R$ 750)
- ✅ **Integração melhor** (DVP vs UART)
- ✅ **Menos componentes** (mais simples)
- ✅ **Mesma funcionalidade** (detecção de objetos)

### 7.2 Placa de Sensor de Luz

**Conceito interessante**: 32 clusters em layout circular

**Relevância**:
- Pode ser mencionado como **trabalho futuro**
- Útil para detecção de limites do campo
- Complementa sistema de visão

**Para seu TCC**:
- Focar apenas em visão (câmera)
- Documentar possibilidade de adicionar sensores de linha futuramente

### 7.3 Estratégias de Software

**Algoritmos relevantes**:
1. **Média ponderada** para direção da bola
2. **Velocidade variável** baseada em distância
3. **Múltiplos PIDs** para controle

**Relevância**:
- Pode ser mencionado como **trabalho futuro**
- Após validar módulo de visão
- Para implementação de lógica de controle

---

## ✅ 8. CONCLUSÕES E RECOMENDAÇÕES

### 8.1 Viabilidade Geral

**ESP32-S3 pode substituir Teensy 4.1**: ⭐⭐⭐⭐ (4/5)

**Justificativa**:
- ✅ Todos os protocolos suportados
- ✅ Mais recursos em alguns aspectos (ADC, PWM)
- ✅ WiFi/Bluetooth integrado (grande vantagem)
- ⚠️ Menos potente, mas suficiente para lightweight
- ✅ Custo 92% menor

### 8.2 Para Seu TCC

**Recomendações**:
1. ✅ **Usar ESP32-S3** como CPU principal
2. ✅ **Usar câmera OV2640** via DVP (melhor que OpenMV)
3. ✅ **Implementar com FreeRTOS** para múltiplas tarefas
4. ✅ **Documentar trade-offs** com Teensy 4.1
5. ✅ **Mencionar possibilidade de expansão** (sensores de linha, etc.)

### 8.3 Inovações a Considerar

1. **Média ponderada**: Para cálculo de direção de objetos
2. **Velocidade variável**: Para controle suave
3. **Múltiplos PIDs**: Para trabalhos futuros
4. **Detecção de clusters**: Para trabalhos futuros

---

## 📚 9. REFERÊNCIAS PARA SEU TCC

### Como Citar Hyperion

**Hyperion (2025)**: Equipe australiana de RoboCup Junior Soccer Lightweight que utiliza Teensy 4.1 com OpenMV H7 Plus, demonstrando uso de módulos de visão dedicados e estratégias avançadas de software para controle de robôs autônomos.

**Pontos para destacar**:
- Uso de módulo de visão dedicado (OpenMV)
- Estratégias de software sofisticadas
- Sistema de sensores múltiplos
- Comunicação Bluetooth para coordenação

**Comparação com seu projeto**:
- Você usa ESP32-S3 (mais barato que Teensy)
- Você usa OV2640 direto (mais barato que OpenMV)
- Você foca em módulo de visão (escopo menor)
- Custo 92% menor mantendo funcionalidade similar

---

**Última atualização**: Novembro 2025  
**Relevância**: Alta - Arquitetura similar, estratégias relevantes

