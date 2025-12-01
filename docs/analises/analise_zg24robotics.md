# Análise do Projeto ZG24Robotics
## Insights para o TCC - Módulo de Visão Computacional Embarcado

**Fonte**: Pôster técnico do time ZG24Robotics (RoboCup Junior, Zagreb, Croácia)

---

## 🎯 Visão Geral

O ZG24Robotics é um time de estudantes do ensino médio e universitários que desenvolveu um robô autônomo de futebol para competições RoboCup Junior. O projeto demonstra uma implementação real e bem-sucedida de vários conceitos relevantes para seu TCC.

---

## 📷 1. SISTEMA DE VISÃO - Análise Detalhada

### Arquitetura do Sistema de Visão

**Configuração**:
- **4 câmeras Maxon Bix** posicionadas em 360° (frente, trás, esquerda, direita)
- **3 câmeras** com lentes de 170° FOV (campo de visão)
- **1 câmera** com lente de 120° FOV (maior clareza)
- **Posicionamento**: Câmeras inclinadas a 45° para máxima visibilidade

### Técnicas Utilizadas

1. **Color Blob Detection em MaxPy**
   - Detecção baseada em cor (não deep learning)
   - Mais leve que ML, adequado para recursos limitados
   - **Relevância para seu TCC**: Alternativa ou complemento ao TinyML

2. **Transformação Homográfica**
   - Correção de distorção de perspectiva
   - Mapeamento de coordenadas da imagem para coordenadas do campo
   - **Exatamente o que você precisa!** - Transformação de (x1,y1) para (X1,Y1)

3. **Cobertura 360°**
   - 4 câmeras eliminam pontos cegos
   - Overlap de campos de visão
   - **Para seu TCC**: Você pode começar com 1 câmera, mas documentar a possibilidade de expansão

### Insights para Seu Projeto

✅ **O que você pode aprender**:
- Sistema de múltiplas câmeras é viável
- Transformação homográfica é essencial para coordenadas precisas
- Detecção por cor pode ser alternativa/complemento ao ML
- Posicionamento da câmera (45°) melhora visibilidade

⚠️ **Diferenças do seu projeto**:
- Eles usam Maxon Bix (câmeras mais caras)
- Você está usando ESP32-S3 + OV2640 (mais barato)
- Eles usam detecção por cor, você está usando TinyML
- Eles têm 4 câmeras, você começa com 1

---

## 🔌 2. COMUNICAÇÃO - ESP32-C6

### Sistema de Comunicação

**Hardware**: ESP32-C6 module
**Função**: Comunicação entre robôs
**Dados transmitidos**:
- Coordenadas dos robôs
- Posição da bola
- Informações compartilhadas para estratégia

### Relevância para Seu TCC

✅ **Conceito similar ao seu**:
- Eles usam ESP32 (você usa ESP32-S3)
- Comunicação serial/UART para troca de dados
- Transmissão de coordenadas (x, y)

💡 **Aplicação no seu projeto**:
- Seu módulo pode usar WiFi do ESP32-S3 para comunicação
- Pode enviar coordenadas para múltiplos sistemas
- Protocolo similar ao que você está desenvolvendo

---

## 🧠 3. ELETRÔNICA E PROCESSAMENTO

### Arquitetura de Controle

**Microcontroladores utilizados**:
- **4x Teensy 4.0**: Processamento de sensores, controle de saídas
- **1x Teensy 4.1**: Controlador principal para tomada de decisão
- **ESP32-C6**: Comunicação sem fio

### Comparação com Seu Projeto

| Aspecto | ZG24Robotics | Seu TCC |
|---------|--------------|---------|
| **MCU Principal** | Teensy 4.0/4.1 | ESP32-S3 |
| **Custo MCU** | ~R$ 200-300 | ~R$ 60-80 |
| **RAM** | 1 MB (Teensy 4.1) | 512 KB |
| **Clock** | 600 MHz | 240 MHz |
| **Arquitetura** | Múltiplos MCUs | Um MCU |
| **Custo Total** | Alto | Baixo |

### Insights

✅ **Vantagens do seu approach**:
- **Custo muito menor** (ESP32-S3 vs Teensy)
- **Adequado para módulo de visão** (não precisa de múltiplos MCUs)
- **WiFi integrado** (ESP32-S3 tem WiFi, Teensy precisa de módulo)

⚠️ **Desafios**:
- Menos poder de processamento que Teensy
- Menos memória
- **Solução**: Otimização com TinyML (exatamente o que você está fazendo!)

---

## 🎮 4. ESTRATÉGIA E PROCESSAMENTO

### Sistema de Decisão

**Dois modos operacionais**:
1. **Attacker** (Atacante)
2. **Goalkeeper** (Goleiro)

**Lógica de decisão** (baseada em flowchart):
- "See Ball?" → "See Line?" → "Ball In Dribbler?" → "Where Is Robot" → "Facing Goal?"
- Mudança dinâmica entre modos baseada no estado do jogo

### Relevância para Seu TCC

✅ **O que você pode documentar**:
- O módulo de visão fornece dados para tomada de decisão
- Coordenadas (x, y) são suficientes para estratégia básica
- Sistema modular permite expansão futura

💡 **Para trabalhos futuros**:
- Após validar o módulo de visão, pode-se implementar lógica de decisão
- Arduino pode usar as coordenadas para estratégia similar

---

## 🔧 5. HARDWARE E MANUFATURA

### Componentes Relevantes

**Motores**: Maxon EC 45 Flat, Maxon EC 16
**Câmeras**: Maxon Bix (4 unidades)
**Baterias**: 11.1V (3S) LiPo, 2200 mAh
**Voltagens**: 3.3V, 5V, 24V, 48V

### Comparação de Custos

| Componente | ZG24Robotics | Seu TCC |
|------------|--------------|---------|
| **MCU** | Teensy 4.1 (~R$ 300) | ESP32-S3 (~R$ 60) |
| **Câmera** | Maxon Bix (~R$ 500-1000 cada) | OV2640 (~R$ 25) |
| **Total Visão** | ~R$ 2000-4000 | ~R$ 100 |

**Redução de custo**: Seu projeto é **20-40x mais barato**! ✅

---

## 📊 6. ANÁLISE COMPARATIVA - ZG24 vs Seu Projeto

### Pontos Fortes do ZG24Robotics

1. ✅ Sistema completo e funcional
2. ✅ Cobertura 360° com múltiplas câmeras
3. ✅ Transformação homográfica implementada
4. ✅ Comunicação entre robôs
5. ✅ Estratégia avançada

### Pontos Fortes do Seu Projeto

1. ✅ **Custo drasticamente menor** (20-40x)
2. ✅ **Foco em TinyML** (mais moderno que detecção por cor)
3. ✅ **Modularidade** (módulo independente)
4. ✅ **Acessibilidade** (viável para mais times)
5. ✅ **Análise comparativa** (diferentes plataformas)

### Onde Seu Projeto Pode Contribuir

1. **Democratização**: Solução de baixo custo para times com orçamento limitado
2. **TinyML**: Demonstração de ML em MCUs (mais avançado que detecção por cor)
3. **Análise comparativa**: Documentação de trade-offs entre plataformas
4. **Base para pesquisa**: Módulo reutilizável para outros projetos

---

## 🎯 7. INSIGHTS ESPECÍFICOS PARA SEU TCC

### 1. Transformação Homográfica

**O que é**: Correção matemática de distorção de perspectiva

**Como funciona** (do pôster):
- Entrada: Coordenadas distorcidas (x1, y1) a (x4, y4)
- Saída: Coordenadas corrigidas (X1, Y1) a (X4, Y4)
- Permite mapear coordenadas da imagem para coordenadas reais do campo

**Para seu TCC**:
- Você pode mencionar isso como **trabalho futuro**
- Ou implementar uma versão simplificada
- Documentar a necessidade de calibração

### 2. Sistema de Coordenadas

**Do pôster**: Eles usam transformação homográfica para coordenadas precisas

**Para seu TCC**:
- Você pode começar com coordenadas simples (pixels)
- Documentar a necessidade de transformação para trabalhos futuros
- Mencionar ZG24Robotics como referência de implementação avançada

### 3. Múltiplas Câmeras

**Do pôster**: 4 câmeras para cobertura 360°

**Para seu TCC**:
- Começar com 1 câmera (escopo do projeto)
- Documentar possibilidade de expansão
- Mencionar ZG24 como exemplo de sistema multi-câmera

### 4. Comunicação

**Do pôster**: ESP32-C6 para comunicação entre robôs

**Para seu TCC**:
- ESP32-S3 também tem WiFi
- Pode implementar comunicação similar
- Útil para trabalhos futuros (múltiplos robôs)

---

## 📚 8. REFERÊNCIAS PARA SEU TCC

### Como Citar Este Projeto

Você pode usar o ZG24Robotics como:
1. **Trabalho relacionado** (implementação real)
2. **Benchmark de comparação** (sistema de alto custo vs seu de baixo custo)
3. **Validação de conceitos** (prova que visão embarcada funciona)
4. **Referência técnica** (transformação homográfica, múltiplas câmeras)

### Informações para Referência

- **Time**: ZG24Robotics
- **Localização**: Zagreb, Croácia
- **Competição**: RoboCup Junior
- **Categoria**: Soccer Open League
- **Website**: Provavelmente tem site ou GitHub (buscar por "ZG24Robotics")

---

## 💡 9. RECOMENDAÇÕES PARA SEU TCC

### O que Adicionar ao Projeto

1. **Mencionar ZG24Robotics na seção de Trabalhos Relacionados**
   - Como exemplo de implementação bem-sucedida
   - Comparar custos e abordagens
   - Destacar diferenças (TinyML vs detecção por cor)

2. **Expandir seção sobre Transformação Homográfica**
   - Explicar o conceito
   - Mencionar como trabalho futuro
   - Referenciar ZG24 como exemplo

3. **Adicionar discussão sobre múltiplas câmeras**
   - Começar com 1 câmera
   - Documentar possibilidade de expansão
   - Comparar com sistemas multi-câmera

4. **Incluir análise de comunicação**
   - WiFi do ESP32-S3
   - Possibilidade de comunicação entre módulos
   - Protocolo de dados

### O que Destacar como Diferencial

1. ✅ **Custo 20-40x menor** que soluções existentes
2. ✅ **Uso de TinyML** (mais moderno que detecção por cor)
3. ✅ **Análise comparativa** de plataformas
4. ✅ **Modularidade** (módulo independente)
5. ✅ **Acessibilidade** (viável para times com orçamento limitado)

---

## 🎓 10. CONCLUSÃO

O projeto ZG24Robotics demonstra que:
- ✅ Visão embarcada é viável e funcional
- ✅ Sistemas de baixo custo podem competir
- ✅ Transformação homográfica melhora precisão
- ✅ Comunicação entre robôs é útil
- ✅ Múltiplas câmeras eliminam pontos cegos

**Seu projeto complementa isso ao**:
- ✅ Reduzir custos drasticamente
- ✅ Usar TinyML (mais moderno)
- ✅ Fornecer análise comparativa
- ✅ Criar módulo reutilizável
- ✅ Democratizar acesso à tecnologia

---

## 📝 Próximos Passos Sugeridos

1. **Adicionar ZG24Robotics às referências** do seu projeto
2. **Expandir seção de trabalhos relacionados** com análise comparativa
3. **Documentar transformação homográfica** como trabalho futuro
4. **Mencionar possibilidade de múltiplas câmeras** na conclusão
5. **Destacar redução de custo** como contribuição principal

---

**Última atualização**: Novembro 2025  
**Fonte**: Pôster técnico ZG24Robotics (RoboCup Junior)

