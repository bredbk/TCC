INSTITUTO FEDERAL DE EDUCAÇÃO, CIÊNCIA E TECNOLOGIA DA BAHIA  
CAMPUS VITÓRIA DA CONQUISTA  
BACHARELADO EM SISTEMAS DE INFORMAÇÃO

---

# MÓDULO DE VISÃO COMPUTACIONAL EMBARCADO PARA ROBÓTICA AUTÔNOMA: ANÁLISE COMPARATIVA DE PLATAFORMAS E DESENVOLVIMENTO DE PROTÓTIPO DE BAIXO CUSTO

**Brendon Sousa Lima**

Pré-projeto de pesquisa desenvolvido na linha de pesquisa de desenvolvimento de sistemas embarcados, sob orientação do Prof. Andrique Figueirêdo Amorim, como requisito de inscrição no componente curricular de Trabalho de Conclusão de Curso I, do Curso de Bacharelado em Sistemas de Informação, do Instituto Federal de Educação, Ciência e Tecnologia da Bahia, Campus Vitória da Conquista.

Vitória da Conquista, 2025

---

## ABSTRACT

This work proposes the development of a low-cost embedded computer vision module for autonomous robotics based on Tiny Machine Learning (TinyML). The research addresses the challenge of implementing real-time object detection systems in resource-constrained microcontrollers, focusing on the ESP32-S3 platform as a cost-effective alternative to high-end embedded systems. The proposed module will capture images through a camera, process them locally using optimized TinyML models, and provide object coordinates (x, y) for integration with autonomous robot control systems. The application context is autonomous robot soccer, where the system must detect and track objects such as balls and goals in real-time. The methodology includes a comparative analysis of different hardware platforms, development and optimization of machine learning models for microcontrollers, and incremental validation through three phases: initial tests with top-view images (isolated ball, then ball and goals), followed by tests with a convex mirror simulating the robot's field perspective. Performance metrics such as detection accuracy, latency, frames per second (FPS), and energy consumption will be evaluated, with the goal of achieving a balance between performance and accuracy. The expected contribution is to democratize access to autonomous robotics technology by providing a solution with a total cost of less than R$ 200, representing a 80-90% cost reduction compared to traditional solutions, while maintaining acceptable performance for educational and research applications in autonomous robotics.

**Keywords**: Computer Vision, TinyML, Embedded Systems, Autonomous Robotics, ESP32-S3, Edge AI, RoboCup

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

Este projeto propõe o desenvolvimento de um módulo de visão embarcada utilizando o microcontrolador ESP32-S3 e uma câmera OV2640. O diferencial inovador desta proposta reside na integração de um sistema óptico catadióptrico (uso de espelho convexo), que visa ampliar o campo de visão do robô para 360 graus (omnidirecional) com um único sensor, eliminando partes móveis e mantendo o custo do sistema reduzido.

### 1.2. Problema de Pesquisa

A implementação de sistemas de visão computacional em robótica móvel autônoma tradicionalmente depende de uma de duas abordagens: sistemas de visão centralizados com alto poder computacional externo, ou sistemas embarcados em plataformas de alto custo (como placas com GPUs embarcadas, custando milhares de reais).

No contexto da RoboCup e competições similares de futebol de robôs, a categoria Small Size League utiliza um sistema de visão centralizado, onde câmeras externas capturam todo o campo e um computador central processa as imagens e envia comandos aos robôs via comunicação sem fio. Embora eficaz, essa abordagem:
- Requer infraestrutura complexa e cara
- Limita a portabilidade do sistema
- É menos realista do ponto de vista de autonomia genuína
- Não é escalável para aplicações além do ambiente controlado

Por outro lado, sistemas de visão embarcada em robôs móveis geralmente utilizam hardware especializado (como Jetson Nano, Raspberry Pi 4 com aceleradores, ou módulos Intel Movidius), que, embora mais poderosos, apresentam custos elevados (R$ 500 a R$ 2.000) e consumo energético significativo, inviáveis para robôs pequenos operados por bateria.

Além disso, câmeras convencionais possuem campo de visão limitado (aproximadamente 60°), obrigando o robô a girar constantemente para encontrar a bola, o que reduz sua eficiência em jogo e aumenta o consumo energético.

**Questão Central de Pesquisa:**

Qual a viabilidade técnica e o desempenho de um módulo de visão computacional embarcado de baixo custo (baseado em ESP32-S3 e óptica catadióptrica) para a detecção de objetos em tempo real em robôs móveis autônomos, considerando a comparação entre abordagens baseadas em segmentação de cor (HSV) e Machine Learning (TinyML)?

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

### 2.4. Inovação em Design

A utilização de um espelho convexo (catadióptrico) para obter visão panorâmica em um sistema de baixo custo é uma alternativa criativa aos caros sensores LIDAR ou arranjos de múltiplas câmeras, reduzindo a complexidade mecânica e eletrônica do robô. Esta abordagem permite que o robô "veja" o gol adversário e a bola simultaneamente sem precisar girar o chassi, aumentando significativamente a eficiência operacional.

### 2.5. Aplicabilidade Prática

O sistema desenvolvido neste trabalho terá aplicações diretas em:
- **Times de robótica educacionais**: Solução viável para competições estudantis
- **Pesquisa acadêmica**: Base para trabalhos futuros em visão embarcada
- **Projetos de extensão**: Tecnologia transferível para comunidade
- **Indústria 4.0**: Conceitos aplicáveis a outros domínios (inspeção, vigilância, automação)

Além disso, todo o código e documentação serão disponibilizados de forma aberta, permitindo replicação e extensão por outros pesquisadores e entusiastas.

---

## 3. OBJETIVOS

### 3.1. Objetivo Geral

Desenvolver um protótipo funcional de módulo de visão computacional embarcado utilizando o microcontrolador ESP32-S3 e óptica catadióptrica, realizando análise comparativa de diferentes plataformas de hardware disponíveis no mercado e comparando abordagens de detecção (segmentação por cor HSV e Machine Learning), capaz de detectar uma bola laranja em tempo real e fornecer suas coordenadas relativas para o controle de navegação de um robô autônomo.

### 3.2. Objetivos Específicos

1. **Realizar revisão bibliográfica sistemática** sobre TinyML, Edge AI, visão computacional embarcada, arquiteturas de redes neurais eficientes e aplicações em robótica autônoma, identificando o estado da arte e lacunas na literatura.

2. **Realizar análise comparativa detalhada** de diferentes plataformas de hardware disponíveis no mercado para visão computacional embarcada, incluindo:
   - Microcontroladores (ESP32-S3, STM32, Raspberry Pi Pico)
   - Sistemas embarcados (Raspberry Pi, Jetson Nano, Coral Dev Board)
   - Critérios: custo, memória, processamento, interface de câmera, consumo energético, suporte a ML

3. **Avaliar viabilidade técnica e econômica** de cada plataforma para aplicação em robótica autônoma, considerando trade-offs entre desempenho e custo.

4. **Identificar estratégias de redução de custos** sem comprometer significativamente o desempenho, analisando alternativas de hardware, otimizações de software e técnicas de co-design.

5. **Coletar e anotar dataset customizado** de imagens representando visão de campo de futebol com objetos (bolas) em diferentes condições de iluminação, distância, ângulos e oclusões, adequado para treinamento de modelos de detecção.

6. **Implementar e comparar algoritmos de detecção de objetos** baseados em cor (espaço HSV) e Machine Learning (TensorFlow Lite Micro), avaliando latência e acurácia de cada abordagem para determinar a mais adequada ao contexto de aplicação.

7. **Treinar e otimizar modelo de machine learning** para detecção de objetos, aplicando técnicas de quantização, pruning e otimização de arquitetura para operação em plataformas de recursos limitados.

8. **Desenvolver suporte físico para acoplamento** da câmera OV2640 e do espelho convexo, garantindo alinhamento adequado do eixo óptico e estabilidade mecânica do sistema.

9. **Criar algoritmo de mapeamento** para converter a imagem distorcida do espelho convexo em coordenadas cartesianas (X, Y) úteis para o robô, considerando as distorções radiais características de sistemas catadióptricos.

10. **Implementar módulo de visão computacional** na plataforma selecionada, incluindo:
   - Captura de imagem via câmera
   - Pré-processamento (redimensionamento, normalização)
   - Inferência do modelo TinyML ou processamento HSV
   - Pós-processamento e extração de coordenadas
   - Interface de comunicação (serial/UART) para envio de coordenadas (x, y)

11. **Desenvolver interface de saída padronizada** que forneça coordenadas (x, y) dos objetos detectados no campo de visão, formatadas para integração com Arduino ou outros sistemas de controle, representando a visão do campo com sistema de coordenadas definido.

12. **Avaliar desempenho quantitativo do módulo** através de métricas objetivas:
   - Precisão, recall e F1-score da detecção
   - Latência média, mínima e máxima do pipeline completo
   - Taxa de quadros por segundo (FPS)
   - Consumo de memória RAM e Flash
   - Precisão das coordenadas fornecidas (x, y)
   - Consumo energético

13. **Validar o sistema em etapas incrementais**:
    - Visão estática superior (Bird's Eye View): testes com câmera apontada diretamente para baixo (sem espelho), validando algoritmo de detecção sem distorção óptica
    - Visão catadióptrica (com espelho): testes com espelho convexo acoplado, validando algoritmo de mapeamento e detecção com distorção radial
    - Testes qualitativos em diferentes cenários: variações de iluminação, distâncias (0.5m a 3m), oclusões e múltiplos objetos

14. **Documentar solução de forma reproduzível**, incluindo código-fonte, datasets, modelos treinados, especificações de hardware e instruções detalhadas, permitindo replicação e extensão do trabalho por outros pesquisadores.

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

### 4.5. Segmentação por Cor no Espaço HSV

Para aplicações de alta velocidade como o futebol de robôs, redes neurais profundas podem ser lentas em microcontroladores. A segmentação por cor no espaço HSV (Hue, Saturation, Value) é uma técnica eficiente que separa a cromaticidade (cor) da luminosidade (brilho), sendo mais robusta a variações de iluminação que o espaço RGB.

**Vantagens do Espaço HSV:**

- **Robustez à iluminação**: O componente de valor (V) separa a informação de brilho da cor, permitindo detecção consistente mesmo com variações de iluminação
- **Baixo custo computacional**: Operações de thresholding em HSV são extremamente rápidas, adequadas para processamento em tempo real em microcontroladores
- **Eficiência para objetos coloridos**: Como a bola oficial de competições possui uma cor laranja padronizada, esta técnica permite uma detecção rápida e robusta com baixo custo computacional

**Aplicação no Contexto:**

A segmentação HSV será implementada como alternativa ou complemento ao modelo de machine learning, permitindo comparação direta entre abordagens baseadas em cor e baseadas em ML quanto à latência e acurácia.

### 4.6. Sistemas de Visão Omnidirecional (Catadióptricos)

Sistemas catadióptricos combinam lentes (dióptricos) e espelhos (catóptricos). O uso de um espelho convexo alinhado ao eixo óptico da câmera permite capturar uma imagem de 360 graus em um único frame, eliminando a necessidade de partes móveis ou múltiplas câmeras.

**Características:**

- **Campo de visão ampliado**: Visão panorâmica completa do entorno do robô
- **Eficiência operacional**: Permite que o robô "veja" o gol adversário e a bola simultaneamente sem precisar girar o chassi
- **Custo reduzido**: Alternativa criativa aos caros sensores LIDAR ou arranjos de múltiplas câmeras
- **Distorções radiais**: A imagem resultante sofre distorções características que requerem algoritmos de mapeamento para conversão em coordenadas cartesianas úteis

**Desafios Técnicos:**

- Calibração do sistema óptico
- Algoritmos de correção de distorção radial
- Mapeamento de coordenadas da imagem distorcida para coordenadas do campo real
- Compensação de reflexões e artefatos ópticos

### 4.7. Interface de Saída e Representação do Campo de Visão

O módulo de visão desenvolvido fornece como saída as coordenadas (x, y) dos objetos detectados no campo de visão da câmera. A definição de um sistema de coordenadas consistente é fundamental para a integração com sistemas de controle subsequentes.

**Sistema de Coordenadas:**

- Coordenadas em pixels ou normalizadas
- Origem no centro da imagem ou canto superior esquerdo
- Mapeamento para coordenadas do campo real (se necessário)
- Para sistemas catadióptricos: conversão de coordenadas distorcidas para coordenadas cartesianas

**Protocolo de Comunicação:**

A interface de comunicação entre o módulo de visão e o sistema de controle utiliza comunicação serial (UART), com formato de mensagem padronizado:

```
OBJ,<x>,<y>,<confiança>,<largura>,<altura>\n
```

### 4.8. RoboCup e Futebol de Robôs

A RoboCup é uma competição científica internacional estabelecida em 1997 com o objetivo audacioso: até 2050, um time de robôs humanoides autônomos deve ser capaz de vencer o time campeão da Copa do Mundo de Futebol da FIFA (KITANO et al., 1997).

**Categorias Principais:**

- **Small Size League (SSL)**: Visão centralizada, câmeras externas, processamento off-board
- **Middle Size League (MSL)**: Visão embarcada, cada robô com sua própria câmera
- **Standard Platform League (SPL)**: Robôs humanoides idênticos (NAO), visão embarcada
- **Humanoid League**: Robôs bípedes, visão embarcada

**Visão Centralizada vs Embarcada:**

Este trabalho alinha-se com a filosofia de visão embarcada, buscando autonomia real e portabilidade do sistema.

### 4.9. Trabalhos Relacionados

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

O desenvolvimento deste trabalho seguirá um processo incremental para isolar variáveis e garantir a robustez do sistema. O projeto será executado em três fases principais, além das etapas de preparação e documentação:

**Estrutura Geral em Três Fases:**

- **Fase 1: Configuração e Algoritmo Base (Ambiente Controlado)**: Implementação e comparação de algoritmos de detecção (HSV e TinyML)
- **Fase 2: Validação Incremental**: Testes progressivos com visão superior e visão catadióptrica
- **Fase 3: Coleta de Métricas e Otimização**: Avaliação quantitativa e qualitativa do desempenho

O desenvolvimento completo será dividido em seis etapas principais, distribuídas ao longo de dois semestres letivos:

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

#### Etapa 4: Desenvolvimento e Otimização do Modelo de ML e Implementação HSV (Meses 6-8) - **Fase 1**

**Objetivo**: Implementar e comparar algoritmos de detecção baseados em cor (HSV) e Machine Learning (TensorFlow Lite Micro).

**Atividades**:

1. **Implementação de segmentação HSV** (Mês 6, semanas 1-2):
   - Configuração do firmware no ESP32-S3 para captura de imagens em resolução reduzida (QVGA ou QQVGA) para otimizar FPS
   - Implementação de filtros de segmentação no espaço de cor HSV (Hue, Saturation, Value)
   - Calibração de thresholds para detecção da cor laranja da bola
   - Otimização para processamento em tempo real

2. **Treinamento e otimização do modelo ML** (Mês 6-7):
   - Seleção de arquitetura base (MobileNetV2, EfficientNet-Lite, ou modelo custom)
   - Treinamento no Google Colab usando TensorFlow/PyTorch
   - Avaliação de desempenho no dataset de validação
   - Aplicação de quantização (int8)
   - Pruning de pesos menos relevantes
   - Conversão para TensorFlow Lite Micro
   - Verificação de acurácia pós-quantização

3. **Comparação de abordagens** (Mês 7-8):
   - Implementação de ambos os algoritmos no ESP32-S3
   - Comparação direta quanto à latência e acurácia
   - Análise de trade-offs entre as abordagens
   - Seleção da abordagem mais adequada ou combinação híbrida

**Ferramentas**: ESP-IDF/Arduino IDE, TensorFlow/PyTorch, TensorFlow Lite Micro, Google Colab

**Métricas**: Acurácia, precisão, recall, F1-score, latência, FPS, consumo de memória

**Produto**: Modelo otimizado em formato .tflite e algoritmo HSV implementado, com análise comparativa

#### Etapa 5: Implementação do Módulo de Visão e Validação Incremental (Meses 9-10) - **Fase 2**

**Objetivo**: Implementar módulo completo de visão computacional no hardware embarcado e validar em etapas incrementais.

**Atividades**:

1. **Setup de hardware e desenvolvimento do suporte físico** (Mês 9, semana 1):
   - Montagem do módulo (ESP32-S3 + câmera OV2640)
   - Desenvolvimento do suporte físico para acoplamento da câmera OV2640 e do espelho convexo
   - Garantia de alinhamento adequado do eixo óptico e estabilidade mecânica
   - Configuração de pinos e interfaces
   - Testes de captura de imagem
   - Verificação de funcionamento básico
   - Calibração da câmera

2. **Desenvolvimento do firmware** (Mês 9, semanas 2-4):
   - Implementação do pipeline de visão:
     * Módulo de captura de imagem via interface DVP
     * Pré-processamento (redimensionamento, normalização, conversão de espaço de cor)
     * Inferência usando TFLite Micro ou processamento HSV
     * Pós-processamento (extração de bounding box, filtros de confiança)
   - Otimização de código para performance e memória
   - Debug e correções

3. **Validação Incremental - Visão Superior (Bird's Eye View)** (Mês 10, semanas 1-2):
   - Testes com câmera apontada diretamente para baixo (sem espelho)
   - Captura da bola em fundo contrastante
   - Validação do algoritmo de detecção (HSV ou ML)
   - Medição do tempo de resposta (latência) sem distorção óptica
   - Coleta de métricas iniciais

4. **Validação Incremental - Visão Catadióptrica (Com Espelho)** (Mês 10, semanas 3-4):
   - Acoplamento da câmera ao espelho convexo
   - Adaptação do algoritmo para identificar o "blob" (mancha) laranja na imagem refletida
   - Desenvolvimento de algoritmo de mapeamento para converter a imagem distorcida do espelho em coordenadas cartesianas (X, Y) úteis para o robô
   - Cálculo de ângulo e distância relativos ao centro da imagem (posição do robô)
   - Validação do sistema completo

5. **Desenvolvimento da interface de saída** (Mês 10):
   - Definição do sistema de coordenadas
   - Implementação do protocolo de comunicação serial/UART
   - Formato de mensagem padronizado
   - Testes de interface com Arduino simulado
   - Validação de precisão das coordenadas

**Ferramentas**: ESP-IDF ou Arduino IDE, PlatformIO, TensorFlow Lite Micro, Arduino IDE (para testes de interface)

**Produto**: Módulo de visão computacional completo com interface de saída padronizada para coordenadas (x, y), validado em ambas as configurações (superior e catadióptrica)

#### Etapa 6: Testes, Avaliação e Documentação (Meses 11-12) - **Fase 3**

**Objetivo**: Coletar métricas, otimizar e documentar resultados.

**Atividades**:

1. **Coleta de Métricas e Otimização** (Mês 11, semanas 1-2):
   - Experimentos práticos medindo:
     * **Latência (ms)**: Tempo entre captura e saída da coordenada
     * **Taxa de Acerto (%)**: Eficácia da detecção em diferentes distâncias (0.5m a 2.0m)
     * **FPS**: Fluidez do processamento de vídeo
     * **Consumo de memória**: RAM e Flash utilizados
     * **Consumo energético**: Corrente e potência
   - Objetivo: encontrar o equilíbrio ideal entre resolução da imagem e velocidade de processamento
   - Otimização de parâmetros baseada nos resultados

2. **Testes sistemáticos** (Mês 11, semanas 2-3):
   - Experimentos controlados em laboratório
   - Coleta de dados quantitativos (métricas definidas)
   - Testes em diferentes cenários (iluminação, distância, oclusões)
   - Registro de vídeos e logs

3. **Análise de resultados** (Mês 11, semanas 3-4):
   - Processamento estatístico dos dados
   - Geração de gráficos e tabelas
   - Comparação entre abordagens HSV e ML
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

BANBURY, C. R. et al. **MicroNets: Neural Network Architectures for Deploying TinyML Applications on Commodity Microcontrollers**. In: Proceedings of Machine Learning and Systems (MLSys), v. 3, p. 517-532, 2021. Disponível em: <https://arxiv.org/pdf/2010.11267>. Acesso em: 15 nov. 2025.

BONARDI, F. et al. **Embedded Vision System for Real-Time Object Tracking Using an Asynchronous Transient Vision Sensor**. In: International Conference on Computer Vision Systems (ICVS), p. 125-135, 2015. Disponível em: <http://www.belbachir.info/PDF/dsp2006.pdf>. Acesso em: 15 nov. 2025.

BROWNING, B. et al. **RoboCup Small Size League: Past, Present and Future**. In: RoboCup 2019: Robot World Cup XXIII. Springer, Cham, p. 611-623, 2019.

CHEN, J.; RAN, X. **Deep Learning with Edge Computing: A Review**. Proceedings of the IEEE, v. 107, n. 8, p. 1655-1674, ago. 2019. Disponível em: <https://ieeexplore.ieee.org/document/8763885>. Acesso em: 15 nov. 2025.

ESPRESSIF SYSTEMS. **ESP32-S3 Series Datasheet**. Version 1.0. Shanghai: Espressif Systems, 2021. Disponível em: <https://www.espressif.com/sites/default/files/documentation/esp32-s3_datasheet_en.pdf>. Acesso em: 15 nov. 2025.

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

