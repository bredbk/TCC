# Conceitos Técnicos Explicados
## Guia Didático para o TCC

---

## 🧠 1. TinyML (Tiny Machine Learning)

### O que é?
TinyML é a área que estuda como colocar inteligência artificial (machine learning) para rodar em dispositivos muito pequenos, como microcontroladores.

### Analogia
Imagine que você precisa mudar uma geladeira de casa. Você tem duas opções:
1. **Cloud AI**: Contratar uma empresa de mudanças (nuvem) → mais poderosa, mas lenta e cara
2. **TinyML**: Você mesmo carrega com amigos (local) → menos poderoso, mas rápido e barato

### Por que é importante para seu TCC?
No seu robô, você precisa que ele:
- **Veja a bola rapidamente** (baixa latência)
- **Funcione sem internet** (não depende da nuvem)
- **Consuma pouca energia** (bateria dura mais)
- **Seja barato** (ESP32 custa ~R$50)

### Desafios Principais

#### 1. **Memória Limitada**
- Microcontrolador: ~500 KB RAM
- Seu computador: 8-16 GB RAM (16.000 a 32.000 vezes mais!)

**Solução**: Modelos "magros" e otimizados

#### 2. **Processamento Limitado**
- ESP32-S3: ~240 MHz
- Seu computador: ~3 GHz (12 vezes mais rápido!)

**Solução**: Algoritmos eficientes e aceleradores de hardware

#### 3. **Sem Precisão Float**
- Microcontroladores não têm FPU (unidade de ponto flutuante)
- Precisa usar inteiros (int8, int16)

**Solução**: Quantização (explicada abaixo)

---

## 🔢 2. Quantização

### O que é?
Quantização é transformar números com muita precisão em números com pouca precisão para economizar memória e processamento.

### Analogia
É como medir a temperatura:
- **Float32 (Alta precisão)**: 23.45678912°C → Ocupa 32 bits
- **Int8 (Baixa precisão)**: 23°C → Ocupa 8 bits (4x menor!)

Você perde um pouco de precisão, mas ganha muito em velocidade e memória.

### Tipos de Quantização

#### Post-Training Quantization
- Treina o modelo normalmente (float32)
- Depois converte para int8
- Mais fácil, mas perde um pouco de precisão

#### Quantization-Aware Training
- Treina já pensando na quantização
- Modelo aprende a lidar com menos precisão
- Melhor resultado, mas mais complexo

### No seu TCC
Você vai treinar um modelo no Google Colab (float32) e depois converter para int8 para rodar no ESP32-S3.

**Ferramenta**: TensorFlow Lite Converter

---

## 📷 3. Visão Computacional

### O que é?
Fazer computadores "enxergarem" e entenderem imagens, como humanos fazem.

### Pipeline Básico de Visão no seu Projeto

```
Câmera → Captura Imagem → Pré-Processamento → Modelo ML → Detecção → Ação
```

#### 1. **Captura de Imagem**
- Câmera captura frames (imagens)
- Resolução: Ex: 320x240 pixels
- Taxa: Ex: 10-30 FPS (frames por segundo)

#### 2. **Pré-Processamento**
Preparar a imagem para o modelo:
- **Redimensionar**: De 640x480 para 224x224 (menor = mais rápido)
- **Normalizar**: Pixels de 0-255 para 0-1
- **Converter cor**: RGB para Grayscale (se necessário)

#### 3. **Inferência (Modelo ML)**
O modelo neural analisa a imagem e diz:
- "Tem uma bola aqui!"
- "Posição: x=120, y=80"
- "Confiança: 95%"

#### 4. **Pós-Processamento**
- Filtrar detecções ruins (confiança baixa)
- Calcular distância da bola
- Decidir ação do robô

---

## 🏃 4. Tempo Real e Latência

### O que é Latência?
É o tempo que o sistema demora para responder.

**No seu projeto**:
```
Câmera vê bola → [LATÊNCIA] → Robô move
```

### Por que é crítico?
No futebol de robôs, a bola se move rápido. Se o robô demora muito para reagir, a bola já passou!

### Metas de Latência

| Aplicação | Latência Aceitável |
|-----------|-------------------|
| Vídeo chamada | < 150 ms |
| Jogo online | < 50 ms |
| Futebol de robôs | < 100 ms |
| Direção autônoma | < 50 ms |

**No seu TCC**: Tente manter < 100 ms (idealmente < 50 ms)

### Como Medir?
```cpp
unsigned long start = millis();
// Seu código aqui
unsigned long latency = millis() - start;
Serial.print("Latência: ");
Serial.println(latency);
```

---

## 🤖 5. Edge AI vs Cloud AI

### Comparação

| Característica | Edge AI (Local) | Cloud AI (Nuvem) |
|---------------|-----------------|------------------|
| **Latência** | Baixa (< 100 ms) | Alta (> 200 ms) |
| **Privacidade** | Alta (dados locais) | Baixa (dados na nuvem) |
| **Conectividade** | Não precisa internet | Precisa internet |
| **Poder computacional** | Limitado | Muito alto |
| **Custo** | Baixo (uma vez) | Alto (mensal) |
| **Bateria** | Economiza (sem transmissão) | Gasta (transmissão WiFi) |

### No Futebol de Robôs

**Edge AI (Seu projeto)** ✅
- Robô decide sozinho
- Sem atraso de rede
- Funciona sem WiFi

**Cloud AI** ❌
- Enviar imagem → Nuvem analisa → Recebe resposta
- Muito lento para tempo real
- Depende de internet

---

## 🔌 6. ESP32-S3

### O que é?
Um microcontrolador (computador pequeno) da Espressif, otimizado para IA.

### Especificações Principais

| Item | Especificação |
|------|---------------|
| **Processador** | Dual-core 240 MHz |
| **RAM** | 512 KB SRAM |
| **Flash** | 4-16 MB |
| **WiFi/Bluetooth** | Sim |
| **Câmera** | Interface dedicada |
| **Preço** | ~R$ 50-80 |

### Por que ESP32-S3?

#### Vantagens
- ✅ Barato
- ✅ Tem aceleradores de IA
- ✅ Interface de câmera nativa
- ✅ WiFi (para debug/monitoramento)
- ✅ Grande comunidade

#### Desvantagens
- ❌ Memória limitada
- ❌ Sem GPU
- ❌ Processamento limitado

### Comparação com Outras Opções

| Plataforma | RAM | Custo | Poder Comp. | Ideal para |
|------------|-----|-------|-------------|-----------|
| **ESP32-S3** | 512 KB | R$ 50 | Baixo | TinyML ✅ |
| **Raspberry Pi 4** | 4 GB | R$ 500 | Médio | Edge AI |
| **Jetson Nano** | 4 GB | R$ 1.000 | Alto | Edge AI pesado |
| **Arduino Uno** | 2 KB | R$ 80 | Muito baixo | IoT simples |

**Seu TCC usa ESP32-S3 porque é o melhor custo-benefício para TinyML!**

---

## 🎯 7. Detecção de Objetos

### Tipos de Modelos

#### 1. **YOLO (You Only Look Once)**
- **Vantagem**: Muito rápido
- **Desvantagem**: Pesado para MCU
- **Uso**: Quando tem GPU

#### 2. **MobileNet-SSD**
- **Vantagem**: Otimizado para mobile/embedded
- **Desvantagem**: Menos preciso que YOLO
- **Uso**: Smartphones, tablets

#### 3. **MicroNet / Modelos TinyML**
- **Vantagem**: Muito leve (KB, não MB)
- **Desvantagem**: Menos capaz
- **Uso**: Microcontroladores ✅

### No seu TCC
Você provavelmente vai usar um **modelo customizado baseado em MobileNet** ou treinar do zero um modelo muito simples.

### Arquitetura Simplificada

```
Imagem (224x224) 
    ↓
[Camadas Convolucionais]  ← Detectam bordas, formas
    ↓
[Pooling]  ← Reduz tamanho
    ↓
[Mais Convoluções]  ← Detectam padrões complexos
    ↓
[Dense Layers]  ← Classificam
    ↓
Saída: [tem_bola: 0.95, posição: (x, y)]
```

---

## ⚽ 8. Detecção de Bola Específica

### Abordagens Possíveis

#### Abordagem 1: Cor (Simples, Rápida)
```
1. Converte imagem para HSV
2. Aplica threshold na cor laranja
3. Encontra contornos
4. Maior contorno circular = bola
```

**Prós**: Muito rápido, funciona no ESP32 sem ML  
**Contras**: Sensível à iluminação

#### Abordagem 2: Machine Learning (Robusta)
```
1. Treina rede neural com imagens de bolas
2. Modelo aprende features da bola
3. Detecta mesmo com iluminação variável
```

**Prós**: Mais robusto  
**Contras**: Mais complexo, precisa treinar

#### Abordagem 3: Híbrida (Recomendada)
```
1. Usa cor para pré-filtrar regiões
2. Aplica ML apenas nas regiões candidatas
3. Melhor dos dois mundos
```

**Prós**: Rápido e robusto  
**Contras**: Mais código

---

## 🏗️ 9. Arquitetura do Sistema

### Diagrama Simplificado do seu Projeto

```
┌─────────────────────────────────────┐
│           HARDWARE                   │
│  ┌──────────┐        ┌────────────┐│
│  │  Câmera  │───────►│  ESP32-S3  ││
│  └──────────┘        └──────┬─────┘│
│                              │      │
│                              ▼      │
│                      ┌───────────┐ │
│                      │  Motores  │ │
│                      └───────────┘ │
└─────────────────────────────────────┘

┌─────────────────────────────────────┐
│          SOFTWARE                    │
│                                      │
│  1. Captura Imagem                  │
│           ↓                          │
│  2. Pré-Processamento                │
│           ↓                          │
│  3. Inferência TinyML                │
│           ↓                          │
│  4. Detecção da Bola                 │
│           ↓                          │
│  5. Controle de Movimento            │
│           ↓                          │
│  6. Atuação nos Motores              │
└─────────────────────────────────────┘
```

### Componentes de Software

#### 1. **Módulo de Visão**
```cpp
class VisionModule {
    Camera cam;
    TFLiteModel model;
    
    Detection detectBall(Image img) {
        // Seu código aqui
    }
};
```

#### 2. **Módulo de Controle**
```cpp
class ControlModule {
    Motor leftMotor;
    Motor rightMotor;
    
    void moveTowardsBall(float angle, float distance) {
        // Seu código aqui
    }
};
```

#### 3. **Loop Principal**
```cpp
void loop() {
    Image img = vision.captureImage();
    Detection ball = vision.detectBall(img);
    
    if (ball.found) {
        control.moveTowardsBall(ball.angle, ball.distance);
    }
}
```

---

## 📊 10. Métricas de Avaliação

### Para o Modelo de Visão

#### 1. **Precisão (Precision)**
De todas as vezes que disse "é uma bola", quantas estavam certas?
```
Precisão = Acertos / (Acertos + Falsos Positivos)
```

#### 2. **Recall**
De todas as bolas reais, quantas foram detectadas?
```
Recall = Acertos / (Acertos + Falsos Negativos)
```

#### 3. **F1-Score**
Média harmônica de Precisão e Recall
```
F1 = 2 * (Precisão * Recall) / (Precisão + Recall)
```

#### 4. **mAP (mean Average Precision)**
Métrica padrão para detecção de objetos

### Para o Sistema Completo

#### 1. **FPS (Frames Per Second)**
Quantas imagens o sistema processa por segundo?
- **Meta**: > 10 FPS (idealmente > 20 FPS)

#### 2. **Latência**
Tempo total do pipeline
- **Meta**: < 100 ms

#### 3. **Consumo de Memória**
Quanto de RAM é usado?
- **Restrição**: < 400 KB (deixar margem)

#### 4. **Taxa de Acerto**
Em testes práticos, quantas vezes o robô acerta a bola?
- **Meta**: > 80%

#### 5. **Consumo Energético**
Quanto tempo a bateria dura?
- **Meta**: > 30 minutos de operação

---

## 🎓 11. RoboCup - Contexto da Aplicação

### O que é RoboCup?
Campeonato mundial de futebol de robôs. Objetivo: até 2050, robôs humanoides vencerem a seleção campeã da Copa do Mundo!

### Categorias Principais

#### 1. **Small Size League (SSL)**
- Robôs pequenos (~15 cm diâmetro)
- **Visão centralizada** (câmera externa)
- Muito rápido e preciso
- **Não é o que você vai fazer**

#### 2. **Middle Size League (MSL)**
- Robôs médios (~50 cm altura)
- **Visão embarcada** (câmera no robô)
- Mais desafiador
- **É o que você vai fazer (conceito)**

#### 3. **Humanoid League**
- Robôs humanoides (andam com 2 pernas)
- Muito complexo
- Estado da arte em robótica

### Visão Centralizada vs Embarcada

#### Centralizada (SSL)
```
Câmeras no teto
    ↓
Computador externo processa
    ↓
Envia comandos via rádio para robôs
```

**Vantagens**:
- Visão global do campo
- Muito processamento disponível
- Coordenação perfeita

**Desvantagens**:
- Precisa de infraestrutura
- Menos realista

#### Embarcada (MSL / Seu projeto)
```
Câmera no robô
    ↓
Robô processa localmente
    ↓
Robô decide sozinho
```

**Vantagens**:
- Totalmente autônomo
- Mais realista
- Portátil

**Desvantagens**:
- Visão limitada
- Menos processamento
- Mais difícil

### Desafios do Futebol de Robôs

1. **Ambiente Dinâmico**: Bola e outros robôs se movem rápido
2. **Tempo Real**: Precisa reagir instantaneamente
3. **Oclusões**: Robô pode tampar a bola
4. **Iluminação**: Varia durante o jogo
5. **Vibração**: Câmera treme quando robô se move

**Seu TCC vai abordar esses desafios com TinyML!**

---

## 💡 12. Co-design: Hardware + Software

### O que é?
Otimizar hardware E software juntos para melhor desempenho.

### No seu Projeto

#### Decisões de Hardware influenciam Software
- ESP32-S3 tem 512 KB RAM → Modelo deve ser < 400 KB
- Câmera  é VGA (640x480) → Pode redimensionar para 224x224
- Tem WiFi → Pode fazer debug remoto

#### Decisões de Software influenciam Hardware
- Quer 20 FPS → Precisa de clock alto (240 MHz)
- Modelo complexo → Precisa de mais memória
- Controle preciso → Precisa de encoders nos motores

### Exemplo de Trade-offs

| Escolha | Vantagem | Desvantagem |
|---------|----------|-------------|
| **Modelo maior** | Mais preciso | Mais lento, mais memória |
| **Modelo menor** | Mais rápido | Menos preciso |
| **Resolução alta** | Melhor detecção | Mais processamento |
| **Resolução baixa** | Mais rápido | Pode perder detalhes |

**Seu trabalho é encontrar o equilíbrio ideal!**

---

## 🔬 13. Metodologia de Experimentação

### Como Validar seu Sistema?

#### Fase 1: Testes em Bancada
```
1. Imagens estáticas
2. Ambiente controlado
3. Iluminação fixa
4. Medir: Precisão, Latência
```

#### Fase 2: Testes com Movimento Lento
```
1. Bola se movendo devagar
2. Robô estático
3. Medir: Taxa de detecção
```

#### Fase 3: Testes com Robô em Movimento
```
1. Robô seguindo bola
2. Movimento real
3. Medir: Taxa de sucesso, Comportamento
```

#### Fase 4: Testes em Condições Adversas
```
1. Iluminação variável
2. Múltiplas bolas
3. Obstáculos
4. Medir: Robustez
```

### Dados a Coletar

| Métrica | Como Medir | Meta |
|---------|-----------|------|
| **Precisão** | TP/(TP+FP) | > 90% |
| **Recall** | TP/(TP+FN) | > 85% |
| **FPS** | Contador de frames | > 15 |
| **Latência** | millis() | < 100 ms |
| **Alcance** | Teste em distâncias | 0.5-3 metros |
| **Bateria** | Tempo até descarregar | > 30 min |

---

## 📈 14. Contribuições Esperadas do TCC

### O que seu TCC vai contribuir?

#### 1. **Técnica**
- Sistema funcional de baixo custo
- Código open source
- Documentação técnica

#### 2. **Científica**
- Análise de TinyML para robótica
- Comparação de abordagens
- Identificação de limitações e soluções

#### 3. **Educacional**
- Solução acessível para ensino
- Material didático
- Inspiração para outros projetos

#### 4. **Prática**
- Times de robótica podem usar
- Base para projetos futuros
- Demonstração de viabilidade

---

## 🎯 Resumo: O que você precisa saber

### Conceitos Essenciais
1. **TinyML**: ML em microcontroladores
2. **Edge AI**: Processamento local, sem nuvem
3. **Quantização**: Reduzir precisão para economizar recursos
4. **Latência**: Tempo de resposta (crítico!)
5. **FPS**: Velocidade de processamento de vídeo
6. **ESP32-S3**: Plataforma hardware escolhida
7. **Visão Embarcada**: Câmera no robô vs externa
8. **Co-design**: Otimizar HW e SW juntos

### Desafios do Projeto
1. Pouca memória (512 KB)
2. Processamento limitado (240 MHz)
3. Tempo real (< 100 ms)
4. Baixo custo (< R$ 200 total)
5. Iluminação variável
6. Movimento rápido

### Soluções
1. Modelo TinyML otimizado
2. Quantização int8
3. Pipeline eficiente
4. Pré-processamento inteligente
5. Algoritmos leves
6. Testes iterativos

---

**Próximo Passo**: Use os documentos de pesquisa e cronograma para começar seu TCC de forma organizada!

🚀 **Sucesso no seu projeto!**

