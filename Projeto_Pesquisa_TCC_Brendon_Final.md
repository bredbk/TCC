INSTITUTO FEDERAL DE EDUCAÇÃO, CIÊNCIA E TECNOLOGIA DA BAHIA  
CAMPUS VITÓRIA DA CONQUISTA  
BACHARELADO EM SISTEMAS DE INFORMAÇÃO

---

# MÓDULO DE VISÃO COMPUTACIONAL EMBARCADO PARA ROBÓTICA AUTÔNOMA: ANÁLISE COMPARATIVA DE PLATAFORMAS E DESENVOLVIMENTO DE PROTÓTIPO DE BAIXO CUSTO

**Brendon Sousa Lima**

Pré-projeto de pesquisa desenvolvido na linha de pesquisa de desenvolvimento de sistemas embarcados, sob orientação do Prof. Andrique Figueirêdo Amorim, como requisito de inscrição no componente curricular de Trabalho de Conclusão de Curso I, do Curso de Bacharelado em Sistemas de Informação, do Instituto Federal de Educação, Ciência e Tecnologia da Bahia, Campus Vitória da Conquista.

Vitória da Conquista, 2025

---

## SUMÁRIO

1. [INTRODUÇÃO](#1-introdução)
2. [JUSTIFICATIVA](#2-justificativa)
3. [OBJETIVOS](#3-objetivos)
   - 3.1. [Objetivo Geral](#31-objetivo-geral)
   - 3.2. [Objetivos Específicos](#32-objetivos-específicos)
4. [REFERENCIAL TEÓRICO](#4-referencial-teórico)
5. [METODOLOGIA](#5-metodologia)
6. [CRONOGRAMA](#6-cronograma)
7. [RECURSOS NECESSÁRIOS](#7-recursos-necessários)
8. [REFERÊNCIAS](#8-referências)
9. [APÊNDICES](#9-apêndices)

---

## 1. INTRODUÇÃO

### 1.1. Contextualização

A inteligência artificial tem se expandido para além dos servidores de alta potência e ambientes de nuvem, atingindo a fronteira dos dispositivos embarcados. Esse movimento, conhecido como Edge AI, tem sido impulsionado pela necessidade de processamento local de dados para aplicações que exigem baixa latência, alta privacidade e eficiência energética (WARDEN; SITUNAYAKE, 2019).

Nesse contexto, surge a disciplina do Tiny Machine Learning (TinyML), uma nova fronteira da inteligência artificial focada em implementar modelos de aprendizado de máquina em dispositivos diminutos, como microcontroladores (MCUs), que possuem apenas algumas centenas de kilobytes de memória. A ascensão do TinyML não é apenas um avanço tecnológico, mas uma resposta a um imperativo prático: com bilhões de dispositivos IoT gerando volumes massivos de dados, a dependência de servidores na nuvem para inferência se torna um gargalo de desempenho, latência e segurança (LIN et al., 2020).

A robótica autônoma, especialmente em ambientes dinâmicos e imprevisíveis como um campo de futebol, representa um desafio complexo e relevante no avanço da inteligência artificial e da mecatrônica. O desenvolvimento de sistemas de percepção visual é fundamental para permitir que robôs detectem, rastreiem e interajam com objetos em movimento em tempo real.

### 1.2. Problema de Pesquisa

A implementação de sistemas de visão computacional em robótica móvel autônoma tradicionalmente depende de uma de duas abordagens: sistemas de visão centralizados com alto poder computacional externo, ou sistemas embarcados em plataformas de alto custo (como placas com GPUs embarcadas, custando milhares de reais).

No contexto da RoboCup e competições similares de futebol de robôs, a categoria Small Size League utiliza um sistema de visão centralizado, onde câmeras externas capturam todo o campo e um computador central processa as imagens e envia comandos aos robôs via comunicação sem fio. Embora eficaz, essa abordagem:
- Requer infraestrutura complexa e cara
- Limita a portabilidade do sistema
- É menos realista do ponto de vista de autonomia genuína
- Não é escalável para aplicações além do ambiente controlado

Por outro lado, sistemas de visão embarcada em robôs móveis geralmente utilizam hardware especializado (como Jetson Nano, Raspberry Pi 4 com aceleradores, ou módulos Intel Movidius), que, embora mais poderosos, apresentam custos elevados (R$ 500 a R$ 2.000) e consumo energético significativo, inviáveis para robôs pequenos operados por bateria.

**Questão Central de Pesquisa:**

Qual plataforma de hardware oferece o melhor custo-benefício para implementação de um módulo de visão computacional embarcado baseado em TinyML, capaz de detectar objetos em tempo real e fornecer coordenadas (x, y) para integração com sistemas de controle de robótica autônoma, considerando restrições de custo, viabilidade técnica e redução de custos?

### 1.3. Delimitação do Tema

Este trabalho foca especificamente no **módulo de visão computacional embarcado**, que constitui a base fundamental para futuros desenvolvimentos em robótica autônoma. O módulo desenvolvido será responsável por capturar imagens do ambiente, processá-las localmente utilizando TinyML, e fornecer como saída as coordenadas (x, y) dos objetos detectados, que posteriormente serão utilizadas por um sistema de controle (Arduino ou similar) para comandar a movimentação do robô.

**Importante**: Este trabalho não inclui a montagem física completa do robô. O foco está no desenvolvimento, análise comparativa e validação do módulo de visão computacional como etapa inicial e fundamental da pesquisa em robótica autônoma.

O trabalho se concentra em:
- Desenvolvimento de sistema de visão embarcado (on-board)
- Análise comparativa de plataformas de hardware disponíveis no mercado
- Plataforma principal: Microcontrolador ESP32-S3
- Técnica: TinyML (Tiny Machine Learning)
- Aplicação: Robótica autônoma para futebol de robôs
- Restrições: Baixo custo (< R$ 200,00), tempo real (< 100ms)

---

## 2. JUSTIFICATIVA

### 2.1. Relevância Científica

Este trabalho contribui para o avanço do conhecimento em uma área emergente e de grande relevância: a interseção entre TinyML e visão computacional embarcada. A pesquisa em sistemas de visão que operam em dispositivos com recursos extremamente limitados é fundamental para o avanço da robótica autônoma e da Internet das Coisas (IoT).

O desenvolvimento de técnicas de otimização de modelos de machine learning para microcontroladores representa um desafio científico significativo, envolvendo conceitos de co-design de hardware e software, quantização de redes neurais, e otimização de arquiteturas computacionais (LIN et al., 2020).

### 2.2. Relevância Tecnológica

A implementação de visão computacional em dispositivos embarcados de baixo custo tem potencial para democratizar o acesso à tecnologia de robótica autônoma. Enquanto soluções baseadas em processamento na nuvem ou em hardware dedicado de alto custo (como GPUs) são eficazes, elas apresentam limitações significativas:

- **Latência**: A comunicação com servidores remotos introduz atrasos incompatíveis com aplicações de tempo real
- **Dependência de conectividade**: Sistemas na nuvem requerem conexão estável à internet
- **Privacidade**: O envio de dados para servidores externos levanta questões de segurança
- **Custo operacional**: Processamento na nuvem implica custos recorrentes
- **Escalabilidade**: Soluções baseadas em hardware dedicado têm custo proibitivo para escala

O desenvolvimento de soluções de visão embarcada em microcontroladores como o ESP32-S3 (custo aproximado de R$ 60,00) representa um avanço tecnológico que pode viabilizar aplicações antes inacessíveis.

### 2.3. Relevância Social e Educacional

A democratização da tecnologia de robótica tem impacto direto na educação e na formação de recursos humanos. Times de robótica educacionais, como os que participam de competições estudantis, frequentemente enfrentam restrições orçamentárias severas.

Soluções de baixo custo permitem que mais instituições de ensino, especialmente em regiões com menos recursos, tenham acesso a tecnologias de ponta, promovendo:
- Inclusão digital e tecnológica
- Formação de estudantes em áreas críticas (IA, robótica, sistemas embarcados)
- Incentivo à pesquisa e inovação
- Desenvolvimento de competências técnicas avançadas

### 2.4. Aplicabilidade Prática

O sistema desenvolvido neste trabalho terá aplicações diretas em:
- **Times de robótica educacionais**: Solução viável para competições estudantis
- **Pesquisa acadêmica**: Base para trabalhos futuros em visão embarcada
- **Projetos de extensão**: Tecnologia transferível para comunidade
- **Indústria 4.0**: Conceitos aplicáveis a outros domínios (inspeção, vigilância, automação)

Além disso, todo o código e documentação serão disponibilizados de forma aberta, permitindo replicação e extensão por outros pesquisadores e entusiastas.

---

## 3. OBJETIVOS

### 3.1. Objetivo Geral

Desenvolver, comparar e avaliar um módulo de visão computacional embarcado de baixo custo baseado em TinyML, realizando análise comparativa de diferentes plataformas de hardware disponíveis no mercado, com foco em viabilidade técnica e redução de custos, capaz de detectar objetos e fornecer coordenadas (x, y) para integração com sistemas de controle de robótica autônoma.

### 3.2. Objetivos Específicos

1. **Realizar revisão bibliográfica sistemática** sobre TinyML, Edge AI, visão computacional embarcada, arquiteturas de redes neurais eficientes e aplicações em robótica autônoma, identificando o estado da arte e lacunas na literatura.

2. **Realizar análise comparativa detalhada** de diferentes plataformas de hardware disponíveis no mercado para visão computacional embarcada, incluindo:
   - Microcontroladores (ESP32-S3, STM32, Raspberry Pi Pico)
   - Sistemas embarcados (Raspberry Pi, Jetson Nano, Coral Dev Board)
   - Critérios: custo, memória, processamento, interface de câmera, consumo energético, suporte a ML

3. **Avaliar viabilidade técnica e econômica** de cada plataforma para aplicação em robótica autônoma, considerando trade-offs entre desempenho e custo.

4. **Identificar estratégias de redução de custos** sem comprometer significativamente o desempenho, analisando alternativas de hardware, otimizações de software e técnicas de co-design.

5. **Coletar e anotar dataset customizado** de imagens representando visão de campo de futebol com objetos (bolas) em diferentes condições de iluminação, distância, ângulos e oclusões, adequado para treinamento de modelos de detecção.

6. **Treinar e otimizar modelo de machine learning** para detecção de objetos, aplicando técnicas de quantização, pruning e otimização de arquitetura para operação em plataformas de recursos limitados.

7. **Implementar módulo de visão computacional** na plataforma selecionada, incluindo:
   - Captura de imagem via câmera
   - Pré-processamento (redimensionamento, normalização)
   - Inferência do modelo TinyML
   - Pós-processamento e extração de coordenadas
   - Interface de comunicação (serial/UART) para envio de coordenadas (x, y)

8. **Desenvolver interface de saída padronizada** que forneça coordenadas (x, y) dos objetos detectados no campo de visão, formatadas para integração com Arduino ou outros sistemas de controle, representando a visão do campo com sistema de coordenadas definido.

9. **Avaliar desempenho quantitativo do módulo** através de métricas objetivas:
   - Precisão, recall e F1-score da detecção
   - Latência média, mínima e máxima do pipeline completo
   - Taxa de quadros por segundo (FPS)
   - Consumo de memória RAM e Flash
   - Precisão das coordenadas fornecidas (x, y)
   - Consumo energético

10. **Realizar testes qualitativos** avaliando robustez do módulo em diferentes cenários:
    - Variações de iluminação (ambiente interno, externo, diferentes intensidades)
    - Diferentes distâncias do objeto (0.5m a 3m)
    - Presença de oclusões e múltiplos objetos
    - Diferentes ângulos de visão

11. **Documentar solução de forma reproduzível**, incluindo código-fonte, datasets, modelos treinados, especificações de hardware e instruções detalhadas, permitindo replicação e extensão do trabalho por outros pesquisadores.

---

## 4. REFERENCIAL TEÓRICO

### 4.1. TinyML (Tiny Machine Learning)

TinyML refere-se à área de pesquisa e desenvolvimento focada na implementação de modelos de machine learning em dispositivos embarcados com recursos extremamente limitados, tipicamente microcontroladores (MCUs) com menos de 1 MB de memória e processadores de baixa potência (WARDEN; SITUNAYAKE, 2019).

**Características Fundamentais:**

Os sistemas TinyML são caracterizados por três restrições principais:
1. **Memória limitada**: Tipicamente 256 KB a 1 MB de RAM
2. **Processamento limitado**: Processadores de 10-240 MHz, sem unidade de ponto flutuante
3. **Energia limitada**: Operação com bateria, consumo em miliamperes

**Desafios Técnicos:**

A implementação de TinyML envolve desafios únicos que não existem em plataformas convencionais:

- **Restrição de memória de ativação**: Diferentemente do que se poderia imaginar, a principal limitação não é o número de parâmetros do modelo, mas sim a memória necessária para armazenar ativações intermediárias durante a inferência (LIN et al., 2020).

- **Ausência de ponto flutuante**: Microcontroladores geralmente não possuem unidades de ponto flutuante (FPU), tornando operações com números float32 extremamente lentas. A solução é a quantização para inteiros de 8 bits (int8).

- **Co-design necessário**: O sucesso de uma aplicação TinyML depende de um design conjunto otimizado do algoritmo e da arquitetura do sistema, considerando as capacidades específicas do hardware alvo.

**Frameworks e Ferramentas:**

- **TensorFlow Lite Micro**: Framework da Google para executar modelos TensorFlow Lite em microcontroladores
- **Edge Impulse**: Plataforma completa para desenvolvimento TinyML
- **Frameworks alternativos**: uTensor, ARM CMSIS-NN, NNoM

### 4.2. Edge AI

Edge AI refere-se ao paradigma de processamento de inteligência artificial localmente, no dispositivo final (edge device), em oposição ao processamento centralizado em servidores na nuvem (CHEN; RAN, 2019).

**Motivações para Edge AI:**

- **Latência**: Aplicações de tempo real como robótica não podem tolerar o atraso da comunicação com a nuvem (tipicamente > 100ms)
- **Privacidade**: Processar dados sensíveis localmente evita transmissão pela rede
- **Largura de banda**: Com bilhões de dispositivos IoT, enviar todos os dados para a nuvem é inviável
- **Confiabilidade**: Independência de conectividade permite operação mesmo sem acesso à internet
- **Custo**: Processamento local elimina custos recorrentes de serviços na nuvem

**Trade-offs:**

Edge AI envolve trade-offs fundamentais:
- Poder computacional vs Consumo energético
- Precisão do modelo vs Latência
- Autonomia vs Complexidade do algoritmo
- Custo vs Desempenho

### 4.3. Análise Comparativa de Plataformas de Hardware

Esta pesquisa realizará análise comparativa detalhada das principais plataformas de hardware disponíveis no mercado para implementação de visão computacional embarcada.

**Microcontroladores (MCUs):**

- **ESP32-S3**: Dual-core Xtensa LX7 @ 240 MHz, 512 KB SRAM, interface DVP dedicada, custo R$ 60-80
- **STM32F4**: ARM Cortex-M4 @ 168 MHz, 192 KB SRAM, interface DCMI, FPU, custo R$ 80-120
- **Raspberry Pi Pico**: Dual-core ARM Cortex-M0+ @ 133 MHz, 264 KB SRAM, sem interface de câmera dedicada, custo R$ 40-60

**Sistemas Embarcados (SBCs):**

- **Raspberry Pi 4**: Quad-core ARM Cortex-A72 @ 1.5 GHz, 2-8 GB RAM, interface CSI, custo R$ 500-600
- **NVIDIA Jetson Nano**: Quad-core ARM Cortex-A57 + GPU Maxwell, 4 GB RAM, custo R$ 1000-1500
- **Google Coral Dev Board**: Quad-core ARM Cortex-A53 + Edge TPU, 1 GB RAM, custo R$ 800-1200

**Critérios de comparação:**
- Custo total do sistema
- Memória disponível (RAM, Flash)
- Poder de processamento
- Interface de câmera (DVP, CSI, SPI/I2C)
- Consumo energético
- Suporte a frameworks de ML
- Viabilidade para aplicação em robótica autônoma

### 4.4. Visão Computacional Embarcada

Visão computacional embarcada refere-se à implementação de algoritmos de processamento e análise de imagens em sistemas com recursos limitados, geralmente para aplicações de tempo real (BONARDI et al., 2015).

**Pipeline Típico de Visão Computacional:**

1. **Captura de imagem**: Sensor de imagem (câmera) captura frame
2. **Pré-processamento**: Redimensionamento, conversão de espaço de cor, normalização
3. **Processamento principal**: Detecção de features, segmentação, detecção/reconhecimento de objetos
4. **Pós-processamento**: Filtros temporais, non-maximum suppression, extração de informação relevante
5. **Atuação**: Decisão baseada nos resultados

**Otimizações para Sistemas Embarcados:**

- **Quantização**: Redução de precisão de pesos e ativações (float32 → int8)
- **Pruning**: Remoção de pesos pouco importantes
- **Knowledge Distillation**: Treinar modelo pequeno para imitar modelo grande
- **Neural Architecture Search**: Busca automatizada pela arquitetura ideal para o hardware alvo

### 4.5. Interface de Saída e Representação do Campo de Visão

O módulo de visão desenvolvido fornece como saída as coordenadas (x, y) dos objetos detectados no campo de visão da câmera. A definição de um sistema de coordenadas consistente é fundamental para a integração com sistemas de controle subsequentes.

**Sistema de Coordenadas:**

- Coordenadas em pixels ou normalizadas
- Origem no centro da imagem ou canto superior esquerdo
- Mapeamento para coordenadas do campo real (se necessário)

**Protocolo de Comunicação:**

A interface de comunicação entre o módulo de visão e o sistema de controle utiliza comunicação serial (UART), com formato de mensagem padronizado:

```
OBJ,<x>,<y>,<confiança>,<largura>,<altura>\n
```

### 4.6. RoboCup e Futebol de Robôs

A RoboCup é uma competição científica internacional estabelecida em 1997 com o objetivo audacioso: até 2050, um time de robôs humanoides autônomos deve ser capaz de vencer o time campeão da Copa do Mundo de Futebol da FIFA (KITANO et al., 1997).

**Categorias Principais:**

- **Small Size League (SSL)**: Visão centralizada, câmeras externas, processamento off-board
- **Middle Size League (MSL)**: Visão embarcada, cada robô com sua própria câmera
- **Standard Platform League (SPL)**: Robôs humanoides idênticos (NAO), visão embarcada
- **Humanoid League**: Robôs bípedes, visão embarcada

**Visão Centralizada vs Embarcada:**

Este trabalho alinha-se com a filosofia de visão embarcada, buscando autonomia real e portabilidade do sistema.

### 4.7. Trabalhos Relacionados

**MCUNet: Tiny Deep Learning on IoT Devices (LIN et al., 2020):**

Lin et al. apresentam o MCUNet, um framework para design conjunto de redes neurais e sistema de inferência otimizado para microcontroladores. O trabalho demonstra que é possível executar classificação ImageNet em um MCU com apenas 320 KB de memória, alcançando 70.7% de acurácia top-1.

**MicroNets: Neural Network Architectures for Deploying TinyML Applications (BANBURY et al., 2021):**

Banbury et al. propõem uma família de arquiteturas de redes neurais especificamente projetadas para TinyML, considerando restrições de memória de ativação. Descoberta chave: a memória de ativação (não o número de parâmetros) é o principal gargalo em MCUs.

**Lacunas Identificadas:**

A revisão da literatura revela algumas lacunas que este trabalho pretende abordar:
1. Escassez de trabalhos com ESP32-S3 para visão
2. Falta de comparações sistemáticas entre plataformas em termos de custo-benefício
3. Poucos datasets públicos específicos para futebol de robôs com visão embarcada
4. Limitada documentação de trade-offs práticos em implementações reais

---

## 5. METODOLOGIA

### 5.1. Classificação da Pesquisa

Este trabalho caracteriza-se como:

- **Quanto à natureza**: Pesquisa Aplicada, pois visa gerar conhecimento para aplicação prática na solução de problemas específicos de robótica autônoma.

- **Quanto aos objetivos**: Pesquisa Exploratória e Experimental, pois explora a viabilidade de TinyML para visão embarcada e realiza experimentos controlados para validação.

- **Quanto à abordagem**: Pesquisa Quali-quantitativa, combinando análise quantitativa de métricas de desempenho com avaliação qualitativa do comportamento do sistema.

- **Quanto aos procedimentos técnicos**: 
  - Pesquisa Bibliográfica (revisão sistemática da literatura)
  - Pesquisa Experimental (desenvolvimento e testes do protótipo)
  - Estudo de Caso (aplicação no contexto de futebol de robôs autônomo)

### 5.2. Procedimentos Metodológicos

O desenvolvimento deste trabalho será dividido em seis etapas principais, distribuídas ao longo de dois semestres letivos:

#### Etapa 1: Revisão Bibliográfica Sistemática (Meses 1-3)

**Objetivo**: Fundamentar teoricamente o trabalho e identificar o estado da arte.

**Atividades**:
- Busca sistemática em bases de dados acadêmicas (IEEE Xplore, ACM Digital Library, Google Scholar, arXiv)
- Seleção de papers fundamentais sobre TinyML, Edge AI, visão computacional embarcada e RoboCup
- Leitura detalhada e fichamento de 15-20 trabalhos principais
- Análise de trabalhos relacionados e identificação de lacunas
- Redação dos capítulos teóricos da monografia

**Palavras-chave de busca**: "TinyML", "embedded vision", "ESP32 machine learning", "RoboCup autonomous", "edge AI microcontroller", "object detection MCU"

**Critérios de seleção**: Papers publicados nos últimos 5 anos (2020-2025), em conferências/journals relevantes, com alto número de citações.

**Produto**: Capítulo de fundamentação teórica e revisão de trabalhos relacionados.

#### Etapa 2: Especificação e Design do Sistema (Mês 4)

**Objetivo**: Definir arquitetura completa do sistema e requisitos.

**Atividades**:
- Levantamento de requisitos funcionais e não-funcionais
- Definição da arquitetura de hardware (componentes, conexões)
- Definição da arquitetura de software (módulos, interfaces)
- Criação de diagramas (blocos, fluxo de dados, casos de uso)
- Especificação de métricas de avaliação
- Planejamento detalhado de experimentos

**Requisitos principais**:
- Detecção de bola em tempo real (latência < 100ms)
- Operação em dispositivo de baixo custo (< R$ 200)
- Autonomia mínima de 30 minutos
- Precisão de detecção > 80%

**Produto**: Documento de especificação técnica com diagramas.

#### Etapa 3: Coleta e Preparação de Dados (Mês 5)

**Objetivo**: Criar dataset adequado para treinamento do modelo.

**Atividades**:
- Captura de 500-1000 imagens de bolas em diferentes cenários
- Variação sistemática de condições:
  - Iluminação (luz natural, artificial, diferentes intensidades)
  - Distância (0.5m a 3m)
  - Ângulos diversos
  - Com e sem oclusões
- Anotação manual de bounding boxes usando ferramentas como LabelImg ou Roboflow
- Organização do dataset (train/validation/test: 70%/15%/15%)
- Data augmentation (rotação, flip, ajuste de brilho/contraste)

**Ferramentas**: LabelImg, Roboflow, Python scripts

**Produto**: Dataset organizado e anotado.

#### Etapa 4: Desenvolvimento e Otimização do Modelo de ML (Meses 6-8)

**Objetivo**: Treinar e otimizar modelo de detecção para o ESP32-S3.

**Atividades**:

1. **Treinamento inicial** (Mês 6):
   - Seleção de arquitetura base (MobileNetV2, EfficientNet-Lite, ou modelo custom)
   - Treinamento no Google Colab usando TensorFlow/PyTorch
   - Avaliação de desempenho no dataset de validação
   - Iteração e ajuste de hiperparâmetros

2. **Otimização do modelo** (Mês 7):
   - Aplicação de quantização (int8)
   - Pruning de pesos menos relevantes
   - Redução de tamanho do modelo
   - Conversão para TensorFlow Lite
   - Verificação de acurácia pós-quantização

3. **Testes em simulação** (Mês 8):
   - Validação do modelo quantizado
   - Medição de tamanho final (deve caber em < 400 KB)
   - Estimativa de latência
   - Ajustes finais

**Ferramentas**: TensorFlow/PyTorch, TensorFlow Lite Converter, Google Colab

**Métricas**: Acurácia, precisão, recall, F1-score, tamanho do modelo, latência estimada

**Produto**: Modelo otimizado em formato .tflite

#### Etapa 5: Implementação do Módulo de Visão (Meses 9-10)

**Objetivo**: Implementar módulo completo de visão computacional no hardware embarcado com interface de saída padronizada.

**Atividades**:

1. **Setup de hardware** (Mês 9, semana 1):
   - Montagem do módulo (ESP32-S3 + câmera OV2640)
   - Configuração de pinos e interfaces
   - Testes de captura de imagem
   - Verificação de funcionamento básico
   - Calibração da câmera

2. **Desenvolvimento do firmware** (Mês 9, semanas 2-4):
   - Implementação do pipeline de visão:
     * Módulo de captura de imagem via interface DVP
     * Pré-processamento (redimensionamento, normalização, conversão de espaço de cor)
     * Inferência usando TFLite Micro
     * Pós-processamento (extração de bounding box, filtros de confiança)
   - Otimização de código para performance e memória
   - Debug e correções

3. **Desenvolvimento da interface de saída** (Mês 10):
   - Definição do sistema de coordenadas
   - Implementação do protocolo de comunicação serial/UART
   - Formato de mensagem padronizado
   - Testes de interface com Arduino simulado
   - Validação de precisão das coordenadas

**Ferramentas**: ESP-IDF ou Arduino IDE, PlatformIO, TensorFlow Lite Micro, Arduino IDE (para testes de interface)

**Produto**: Módulo de visão computacional completo com interface de saída padronizada para coordenadas (x, y)

#### Etapa 6: Testes, Avaliação e Documentação (Meses 11-12)

**Objetivo**: Validar sistema e documentar resultados.

**Atividades**:

1. **Testes sistemáticos** (Mês 11, semanas 1-2):
   - Experimentos controlados em laboratório
   - Coleta de dados quantitativos (métricas definidas)
   - Testes em diferentes cenários
   - Registro de vídeos e logs

2. **Análise de resultados** (Mês 11, semanas 3-4):
   - Processamento estatístico dos dados
   - Geração de gráficos e tabelas
   - Comparação com trabalhos relacionados
   - Identificação de limitações

3. **Redação da monografia** (Meses 11-12):
   - Escrita dos capítulos de desenvolvimento
   - Escrita dos capítulos de resultados e discussão
   - Escrita da conclusão e trabalhos futuros
   - Revisão completa do texto
   - Formatação segundo normas ABNT

4. **Preparação da defesa** (Mês 12):
   - Criação de slides
   - Preparação de demonstração ao vivo
   - Vídeo de demonstração (backup)
   - Ensaio da apresentação

**Produto**: Monografia completa e apresentação para defesa

### 5.3. Materiais e Recursos

#### Hardware Necessário

| Item | Descrição | Qtd | Valor Unit. | Valor Total |
|------|-----------|-----|-------------|-------------|
| ESP32-S3 DevKit | Microcontrolador principal | 2 | R$ 60,00 | R$ 120,00 |
| Câmera OV2640 | Módulo de câmera | 2 | R$ 25,00 | R$ 50,00 |
| Arduino Uno | Para testes de interface | 1 | R$ 80,00 | R$ 80,00 |
| Componentes diversos | Jumpers, protoboard, reguladores, conectores | - | - | R$ 30,00 |
| **TOTAL ESTIMADO** | | | | **R$ 280,00** |

**Nota**: A montagem física do robô não faz parte deste trabalho. O hardware listado é apenas para o módulo de visão e testes de interface.

#### Software (Gratuito)

- ESP-IDF ou Arduino IDE
- Python + TensorFlow
- Google Colab
- Visual Studio Code + PlatformIO
- OpenCV
- Zotero (gerenciador de referências)

#### Infraestrutura

- Laboratório de robótica do IFBA
- Computador pessoal para desenvolvimento
- Acesso à internet

### 5.4. Métodos de Avaliação

**Métricas Quantitativas:**
- Precisão, Recall, F1-Score da detecção
- Latência média, mínima e máxima do pipeline completo
- Taxa de quadros por segundo (FPS)
- Consumo de memória RAM e Flash
- Precisão das coordenadas fornecidas (x, y)
- Consumo energético

**Testes Qualitativos:**
- Robustez a diferentes iluminações
- Desempenho em diferentes distâncias (0.5m a 3m)
- Comportamento com oclusões
- Diferentes ângulos de visão

**Análise de Dados:**
- Estatística descritiva: Média, desvio padrão, mediana
- Visualização: Gráficos de desempenho, curvas ROC, matriz de confusão
- Comparação com trabalhos relacionados
- Análise qualitativa do comportamento do sistema

---

## 6. CRONOGRAMA

### Ano 2025 - TCC I e TCC II

| Atividades | Jan | Fev | Mar | Abr | Mai | Jun | Jul | Ago | Set | Out | Nov | Dez |
|-----------|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| **1. Levantar literatura** | X | X | X | | | | | | | | | |
| **2. Elaborar Projeto (TCC I)** | X | X | X | X | | | | | | | | |
| **3. Fundamentação teórica** | | X | X | X | | | | | | | | |
| **4. Especificar sistema** | | | | X | | | | | | | | |
| **5. Coletar dados (dataset)** | | | | | X | | | | | | | |
| **6. Treinar modelo ML** | | | | | X | X | | | | | | |
| **7. Otimizar modelo (TinyML)** | | | | | | X | X | | | | | |
| **8. Implementar no ESP32** | | | | | | X | X | X | | | | |
| **9. Desenvolver interface de saída** | | | | | | | | X | X | | | |
| **10. Realizar testes** | | | | | | | | | X | X | | |
| **11. Analisar resultados** | | | | | | | | | | X | | |
| **12. Elaborar monografia** | | | | | X | X | | | | X | X | |
| **13. Revisar texto** | | | | | | | | | | | X | X |
| **14. Preparar apresentação** | | | | | | | | | | | | X |
| **15. Entregar TCC I** | | | | | | **✓** | | | | | | |
| **16. Entregar TCC II** | | | | | | | | | | | **✓** | |
| **17. Defesa da monografia** | | | | | | | | | | | | **✓** |

**Marcos Críticos:**
- **30/Jun/2025**: Entrega do Projeto (TCC I)
- **30/Nov/2025**: Entrega da Monografia (TCC II)
- **15/Dez/2025**: Defesa da Monografia

---

## 7. RECURSOS NECESSÁRIOS

### 7.1. Recursos Humanos

- **Orientador**: Prof. Andrique Figueirêdo Amorim
- **Aluno pesquisador**: Brendon Sousa Lima
- **Colaboradores**: Possível suporte de técnicos de laboratório do IFBA

### 7.2. Recursos Materiais

Conforme tabela detalhada na Seção 5.3 (Materiais e Recursos)

**Custo total estimado**: R$ 280,00

**Fonte de financiamento**: Recursos próprios / Possível solicitação de bolsa ao IFBA

### 7.3. Recursos Computacionais

- Computador pessoal para desenvolvimento
- Google Colab (gratuito) para treinamento de modelos
- Laboratório de informática do IFBA (se necessário)

### 7.4. Infraestrutura

- Laboratório de robótica do IFBA para testes
- Acesso à biblioteca física e digital
- Acesso à internet para pesquisa e desenvolvimento
- Espaço para testes do módulo de visão

---

## 8. REFERÊNCIAS

BANBURY, C. R. et al. **MicroNets: Neural Network Architectures for Deploying TinyML Applications on Commodity Microcontrollers**. In: Proceedings of Machine Learning and Systems (MLSys), v. 3, p. 517-532, 2021.

BONARDI, F. et al. **Embedded Vision System for Real-Time Object Tracking Using an Asynchronous Transient Vision Sensor**. In: International Conference on Computer Vision Systems (ICVS), p. 125-135, 2015.

BROWNING, B. et al. **RoboCup Small Size League: Past, Present and Future**. In: RoboCup 2019: Robot World Cup XXIII. Springer, Cham, p. 611-623, 2019.

CHEN, J.; RAN, X. **Deep Learning with Edge Computing: A Review**. Proceedings of the IEEE, v. 107, n. 8, p. 1655-1674, ago. 2019.

ESPRESSIF SYSTEMS. **ESP32-S3 Series Datasheet**. Version 1.0. Shanghai: Espressif Systems, 2021. Disponível em: <https://www.espressif.com/sites/default/files/documentation/esp32-s3_datasheet_en.pdf>. Acesso em: 15 nov. 2024.

KITANO, H. et al. **RoboCup: The Robot World Cup Initiative**. In: Proceedings of the First International Conference on Autonomous Agents (AGENTS'97), p. 340-347, Marina del Rey, CA, USA, 1997. ACM Press.

LIN, J. et al. **MCUNet: Tiny Deep Learning on IoT Devices**. In: Advances in Neural Information Processing Systems (NeurIPS), v. 33, p. 11711-11722, 2020.

MÜHLENBROCK, D. et al. **Detecting and Tracking Robots in Real-Time Using RGB-D Data**. In: RoboCup 2018: Robot World Cup XXII. Springer, Cham, p. 147-158, 2018.

WARDEN, P.; SITUNAYAKE, D. **TinyML: Machine Learning with TensorFlow Lite on Arduino and Ultra-Low-Power Microcontrollers**. Sebastopol, CA: O'Reilly Media, 2019.

---

## 9. APÊNDICES

### Apêndice A - Termo de Aceite do Orientador

[Incluir cópia do Termo de Aceite assinado pelo orientador]

### Apêndice B - Especificações Técnicas Detalhadas

[Incluir quando disponível: diagramas de hardware, esquemáticos, especificações de componentes]

### Apêndice C - Cronograma Expandido

[Incluir se necessário: detalhamento semanal das atividades principais]

---

**Vitória da Conquista, BA**  
**Janeiro de 2025**

---

**_____________________________________**  
Brendon Sousa Lima  
Aluno

**_____________________________________**  
Prof. Andrique Figueirêdo Amorim  
Orientador

