# Análise Detalhada: LNX ROBOTS (RoboCup Junior Soccer Open)
## Arquitetura de Hardware e Software - Insights para ESP32

**Equipe**: LNX ROBOTS  
**País**: Eslováquia (Bratislava)  
**Competição**: RoboCup Junior Soccer Open 2025  
**Conquistas**: 2º lugar Mundial, 1º lugar Europeu  
**Membros**: 4 estudantes do ensino médio

---

## 🏗️ 1. ARQUITETURA DE PROCESSAMENTO

### 1.1 Sistema Multi-Microcontrolador

**Arquitetura Principal**:
```
┌─────────────────────────────────────┐
│   Raspberry Pi 5 (8 GB)             │
│   - Processamento de câmera          │
│   - Comunicação com STM32s           │
│   - Python                           │
└──────────────┬──────────────────────┘
               │ Comunicação
               │
    ┌──────────┴──────────┐
    │                     │
┌───▼──────────┐   ┌──────▼──────────┐
│ STM32F767    │   │ STM32G474        │
│ - UI         │   │ - Sensores linha │
│ - Giroscópio │   │ - Dados LiDAR    │
│ - Motores    │   │                  │
│ - Kicker     │   │                  │
└──────────────┘   └─────────────────┘
```

**Justificativa**:
- **Raspberry Pi 5**: Processamento de visão e IA
- **STM32F767**: Controle de interface, motores, kicker
- **STM32G474**: Processamento de sensores (linha, LiDAR)
- **Distribuição de carga**: Cada MCU tem responsabilidades específicas

### 1.2 Relevância para ESP32

**Como ESP32 poderia substituir os STM32s**:

✅ **ESP32 substituindo STM32F767**:
- **UI (Display OLED)**: ESP32 suporta I2C/SPI ✅
- **Giroscópio (IMU)**: ESP32 suporta I2C/SPI ✅
- **Motores**: ESP32 tem PWM ✅
- **Kicker (Solenoide)**: ESP32 pode controlar via GPIO/MOSFET ✅

✅ **ESP32 substituindo STM32G474**:
- **Sensores de linha**: ESP32 tem múltiplos ADCs ✅
- **LiDAR**: ESP32 suporta UART/Serial ✅
- **Processamento de dados**: ESP32 tem capacidade suficiente ✅

⚠️ **Considerações**:
- **Múltiplos ESP32s**: Poderia usar 2 ESP32s (similar à arquitetura deles)
- **Ou um ESP32-S3**: Mais potente, pode consolidar funções
- **Raspberry Pi**: Ainda necessário para IA/visão complexa

**Arquitetura Proposta com ESP32**:
```
Raspberry Pi 5 (IA/Visão)
    ↓
ESP32-S3 (Controle principal)
    ↓
ESP32 (Sub-controlador sensores) [opcional]
```

---

## 📷 2. SISTEMA DE VISÃO

### 2.1 Implementação do LNX ROBOTS

**Hardware**:
- **Câmera**: OpenMV Cam H7
- **Espelho**: Espelho omnidirecional (termoformagem a vácuo)
- **Configuração**: 
  - 1 câmera frontal grande angular
  - 1 câmera apontada para espelho de 360°
- **Simulação**: Blender para testar configuração

**Processamento**:
- **Modelo**: YOLOv8 personalizado
- **Hardware IA**: Hailo-8L (13 TOPS) via Raspberry Pi AI Kit
- **Treinamento**: 
  - ~7.000 frames rotulados manualmente
  - De 2 milhões de frames coletados
- **Resolução**: Não especificada, mas processada no Raspberry Pi

### 2.2 Comparação com Seu Projeto

| Aspecto | LNX ROBOTS | Seu TCC |
|---------|------------|---------|
| **Câmera** | OpenMV H7 | ESP32-S3 + OV2640 |
| **Processamento IA** | Hailo-8L (13 TOPS) | ESP32-S3 (TinyML) |
| **Modelo** | YOLOv8 | Modelo TinyML custom |
| **Custo Visão** | ~R$ 800-1000 | ~R$ 100 |
| **Performance IA** | Muito alta | Boa (otimizada) |
| **Espelho 360°** | Sim | Não (trabalho futuro) |

**Insights**:
- ✅ **YOLOv8 é state-of-the-art**, mas muito pesado para ESP32
- ✅ **TinyML é adequado** para seu escopo de baixo custo
- ✅ **Espelho 360°** pode ser trabalho futuro
- ✅ **Treinamento com muitos dados** é importante (você pode fazer similar)

---

## 🗺️ 3. SISTEMA DE LOCALIZAÇÃO (LiDAR)

### 3.1 Implementação do LNX ROBOTS

**Hardware**: LiDAR de 360° (modelo não especificado)

**Processamento**:
- Detecta segmentos retos na nuvem de pontos
- Usa transformada de Hough
- Identifica paredes do campo
- Estima posição com precisão < 5 cm

**Integração**:
- Combinado com visão
- Localização precisa
- Base para estratégia

### 3.2 Relevância para ESP32

**ESP32 pode processar LiDAR?**:

✅ **Leitura de dados**: Sim (via UART)
⚠️ **Transformada de Hough**: Computacionalmente intensiva
⚠️ **Processamento de nuvem de pontos**: Pode ser limitado

**Recomendação**:
- ESP32 pode ler dados do LiDAR
- Processamento básico é viável
- Transformada de Hough pode ser simplificada ou delegada

**Para seu TCC**: LiDAR não é parte do escopo, mas pode ser mencionado como trabalho futuro.

---

## 🔌 4. ELETRÔNICA E PCBs

### 4.1 PCBs do LNX ROBOTS

**4 PCBs personalizadas** (projetadas no Autodesk Eagle):

1. **Main PCB**: Raspberry Pi 5 + interfaces
2. **Power PCB**: Distribuição de energia
3. **Control PCB**: STM32F767 + interfaces
4. **Sensor PCB**: STM32G474 + sensores

**Componentes principais**:
- **Raspberry Pi 5**: Processador principal
- **STM32F767**: UI, giroscópio, motores, kicker
- **STM32G474**: Sensores de linha, LiDAR
- **Motores**: Brushless de acionamento direto com encoders
- **ESCs**: Escon 24/2 para controle de motor

### 4.2 Adaptação para ESP32

**PCBs necessárias**:

**1. Main Board (ESP32-S3)**:
- ESP32-S3
- Reguladores de tensão
- Interface de câmera (DVP)
- Conectores para sensores
- Interface serial para comunicação

**2. Power Board**:
- Conversores buck
- Distribuição de energia
- Proteção de bateria

**3. Sensor Board** (opcional):
- Se usar múltiplos sensores
- Multiplexadores se necessário

**Vantagem**: ESP32 pode reduzir número de PCBs devido à integração.

---

## 🎯 5. SISTEMA DE VISÃO - DETALHES TÉCNICOS

### 5.1 YOLOv8 no Hailo-8L

**YOLOv8**:
- State-of-the-art em detecção de objetos
- Muito preciso
- Requer hardware dedicado (Hailo-8L)

**Hailo-8L**:
- ASIC dedicado para IA
- 13 TOPS (trilhões de operações por segundo)
- Otimizado para inferência ML
- Custo: ~R$ 500-800

### 5.2 Comparação com TinyML

| Aspecto | YOLOv8 + Hailo | TinyML + ESP32 |
|---------|----------------|----------------|
| **Precisão** | Muito alta (>95%) | Boa (>80%) |
| **Velocidade** | Muito rápida | Rápida (otimizada) |
| **Custo** | Alto (~R$ 800) | Baixo (~R$ 60) |
| **Consumo** | Médio | Muito baixo |
| **Complexidade** | Alta | Média |

**Conclusão**: Para seu TCC, TinyML é adequado. YOLOv8 seria overkill e caro.

---

## 📊 6. ANÁLISE DE CUSTOS

### 6.1 Custo do LNX ROBOTS

**Componentes principais** (estimado):
- Raspberry Pi 5: ~R$ 600
- Hailo-8L: ~R$ 800
- STM32F767: ~R$ 150
- STM32G474: ~R$ 100
- Câmeras: ~R$ 300
- **Total estimado**: ~R$ 2000-3000

### 6.2 Custo com ESP32

**Componentes principais**:
- ESP32-S3: ~R$ 60
- Câmera OV2640: ~R$ 25
- Componentes diversos: ~R$ 15
- **Total**: ~R$ 100

**Redução de custo**: **20-30x menor!** ✅

---

## 💡 7. INSIGHTS PARA SEU TCC

### 7.1 Arquitetura Multi-MCU

**LNX usa**: Raspberry Pi + 2x STM32

**Você pode usar**:
- **Opção 1**: ESP32-S3 único (mais simples)
- **Opção 2**: ESP32-S3 + ESP32 (distribuição de carga)
- **Opção 3**: ESP32-S3 + Arduino (se precisar de mais I/O)

**Recomendação**: Começar com ESP32-S3 único, expandir se necessário.

### 7.2 Sistema de Visão

**LNX usa**: YOLOv8 + Hailo-8L (muito caro)

**Você usa**: TinyML + ESP32-S3 (muito mais barato)

**Vantagem**: Seu approach é mais acessível e ainda eficaz.

### 7.3 Treinamento do Modelo

**LNX**: 7.000 frames rotulados de 2 milhões coletados

**Para seu TCC**:
- Meta: 500-1000 imagens rotuladas
- Coletar em diferentes condições
- Data augmentation
- Treinar no Google Colab

---

## 🔬 8. ANÁLISE TÉCNICA DETALHADA

### 8.1 Processamento de Sensores

**LNX ROBOTS**:
- STM32G474 processa sensores de linha e LiDAR
- Multiplexadores para reduzir pinos
- Filtros para estabilizar leituras

**Com ESP32**:
- ESP32 pode fazer o mesmo
- Múltiplos ADCs para sensores analógicos
- I2C/SPI para sensores digitais
- Multiplexadores se necessário

### 8.2 Controle de Motores

**LNX ROBOTS**:
- ESCs Escon 24/2
- Motores brushless com encoders
- Controle preciso

**Com ESP32**:
- PWM para controle de velocidade
- GPIOs para direção
- Leitura de encoders via GPIOs
- Drivers de motor (DRV8870 ou similar)

---

## 📈 9. COMPARAÇÃO DE DESEMPENHO

### 9.1 Métricas Esperadas

**LNX ROBOTS** (hardware de alto desempenho):
- Latência de visão: < 20 ms (Hailo-8L)
- Precisão de detecção: > 95%
- FPS: > 30

**Seu Projeto** (ESP32-S3):
- Latência de visão: < 100 ms (meta)
- Precisão de detecção: > 80% (meta)
- FPS: > 10 (idealmente > 15)

**Trade-off**: Performance menor, mas custo 20-30x menor.

---

## 🎓 10. CONCLUSÕES E RECOMENDAÇÕES

### 10.1 Arquitetura Recomendada

**Para seu TCC (Módulo de Visão)**:
```
ESP32-S3 + Câmera OV2640
    ↓
Pipeline TinyML
    ↓
Coordenadas (x, y) via Serial
    ↓
Arduino (sistema de controle)
```

**Para Sistema Completo (Trabalho Futuro)**:
```
Raspberry Pi (IA avançada) [opcional]
    ↓
ESP32-S3 (Visão + Controle)
    ↓
Sensores, Motores, Atuadores
```

### 10.2 Lições Aprendidas

1. ✅ **Multi-MCU** pode ser útil, mas não é obrigatório
2. ✅ **IA dedicada** (Hailo) é cara, TinyML é suficiente
3. ✅ **Treinamento com muitos dados** melhora precisão
4. ✅ **PCBs personalizadas** melhoram integração
5. ✅ **Espelho 360°** pode ser trabalho futuro

### 10.3 Diferenciais do Seu Projeto

1. **Custo 20-30x menor**
2. **TinyML** adequado para baixo custo
3. **Modularidade** permite expansão
4. **Acessibilidade** para mais times

---

**Última atualização**: Novembro 2025  
**Relevância**: Alta - Arquitetura similar, mas com hardware mais caro

