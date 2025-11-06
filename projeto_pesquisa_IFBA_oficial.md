INSTITUTO FEDERAL DE EDUCAÇÃO, CIÊNCIA E TECNOLOGIA DA BAHIA - IFBA




BRENDON SOUSA LIMA




MÓDULO DE VISÃO COMPUTACIONAL EMBARCADO PARA ROBÓTICA AUTÔNOMA: ANÁLISE COMPARATIVA DE PLATAFORMAS E DESENVOLVIMENTO DE PROTÓTIPO DE BAIXO CUSTO






Vitória da Conquista
2025

---

BRENDON SOUSA LIMA







MÓDULO DE VISÃO COMPUTACIONAL EMBARCADO PARA ROBÓTICA AUTÔNOMA: ANÁLISE COMPARATIVA DE PLATAFORMAS E DESENVOLVIMENTO DE PROTÓTIPO DE BAIXO CUSTO




Projeto de Monografia apresentado como requisito parcial de avaliação da disciplina Trabalho de Conclusão de Curso I, do curso de Sistemas de Informação do Instituto Federal de Educação, Ciência e Tecnologia da Bahia – IFBA, sob orientação do Prof. Andrique Figueirêdo Amorim.

 



Vitória da Conquista
2025

---

# Sumário

1. [INTRODUÇÃO](#1-introdução) .......... 4
   - 1.1 [Justificativa](#11-justificativa) .......... 5
   - 1.2 [Problema](#12-problema) .......... 7
   - 1.3 [Objetivos](#13-objetivos) .......... 8
     - 1.3.1 [Geral](#131-geral) .......... 8
     - 1.3.2 [Específicos](#132-específicos) .......... 8
   - 1.4 [Metodologia](#14-metodologia) .......... 9
2. [CONCEITOS TEÓRICOS / TRABALHOS RELACIONADOS](#2-conceitos-teóricos--trabalhos-relacionados) .......... 12
   - 2.1 [TinyML (Tiny Machine Learning)](#21-tinyml-tiny-machine-learning) .......... 12
   - 2.2 [Edge AI](#22-edge-ai) .......... 13
   - 2.3 [Análise Comparativa de Plataformas de Hardware](#23-análise-comparativa-de-plataformas-de-hardware) .......... 14
   - 2.4 [Interface de Saída e Representação do Campo de Visão](#24-interface-de-saída-e-representação-do-campo-de-visão) .......... 18
   - 2.5 [Visão Computacional Embarcada](#25-visão-computacional-embarcada) .......... 19
   - 2.6 [RoboCup e Futebol de Robôs](#26-robocup-e-futebol-de-robôs) .......... 20
   - 2.7 [Trabalhos Relacionados](#27-trabalhos-relacionados) .......... 21
3. [CRONOGRAMA](#3-cronograma) .......... 19
4. [REFERÊNCIAS](#4-referências) .......... 20
[APÊNDICES](#apêndices) .......... 21

---

# 1. INTRODUÇÃO

A inteligência artificial tem se expandido para além dos servidores de alta potência e ambientes de nuvem, atingindo a fronteira dos dispositivos embarcados. Esse movimento, conhecido como Edge AI, tem sido impulsionado pela necessidade de processamento local de dados para aplicações que exigem baixa latência, alta privacidade e eficiência energética (WARDEN; SITUNAYAKE, 2019).

Nesse contexto, surge a disciplina do Tiny Machine Learning (TinyML), uma nova fronteira da inteligência artificial focada em implementar modelos de aprendizado de máquina em dispositivos diminutos, como microcontroladores (MCUs), que possuem apenas algumas centenas de kilobytes de memória. A ascensão do TinyML não é apenas um avanço tecnológico, mas uma resposta a um imperativo prático: com bilhões de dispositivos IoT gerando volumes massivos de dados, a dependência de servidores na nuvem para inferência se torna um gargalo de desempenho, latência e segurança (LIN et al., 2020).

A robótica autônoma, especialmente em ambientes dinâmicos e imprevisíveis como um campo de futebol, representa um desafio complexo e relevante no avanço da inteligência artificial e da mecatrônica. O desenvolvimento de sistemas de percepção visual é fundamental para permitir que robôs detectem, rastreiem e interajam com objetos em movimento em tempo real.

Este trabalho foca especificamente no **módulo de visão computacional embarcado**, que constitui a base fundamental para futuros desenvolvimentos em robótica autônoma. O módulo desenvolvido será responsável por capturar imagens do ambiente, processá-las localmente utilizando TinyML, e fornecer como saída as coordenadas (x, y) dos objetos detectados, que posteriormente serão utilizadas por um sistema de controle (Arduino ou similar) para comandar a movimentação do robô.

**Importante**: Este trabalho não inclui a montagem física completa do robô. O foco está no desenvolvimento, análise comparativa e validação do módulo de visão computacional como etapa inicial e fundamental da pesquisa em robótica autônoma.

## 1.1 Justificativa

### Relevância Científica

Este trabalho contribui para o avanço do conhecimento em uma área emergente e de grande relevância: a interseção entre TinyML e visão computacional embarcada. A pesquisa em sistemas de visão que operam em dispositivos com recursos extremamente limitados é fundamental para o avanço da robótica autônoma e da Internet das Coisas (IoT). 

O desenvolvimento de técnicas de otimização de modelos de machine learning para microcontroladores representa um desafio científico significativo, envolvendo conceitos de co-design de hardware e software, quantização de redes neurais, e otimização de arquiteturas computacionais (LIN et al., 2020).

### Relevância Tecnológica

A implementação de visão computacional em dispositivos embarcados de baixo custo tem potencial para democratizar o acesso à tecnologia de robótica autônoma. Enquanto soluções baseadas em processamento na nuvem ou em hardware dedicado de alto custo (como GPUs) são eficazes, elas apresentam limitações significativas:

- **Latência**: A comunicação com servidores remotos introduz atrasos incompatíveis com aplicações de tempo real
- **Dependência de conectividade**: Sistemas na nuvem requerem conexão estável à internet
- **Privacidade**: O envio de dados para servidores externos levanta questões de segurança
- **Custo operacional**: Processamento na nuvem implica custos recorrentes
- **Escalabilidade**: Soluções baseadas em hardware dedicado têm custo proibitivo para escala

O desenvolvimento de soluções de visão embarcada em microcontroladores como o ESP32-S3 (custo aproximado de R$ 60,00) representa um avanço tecnológico que pode viabilizar aplicações antes inacessíveis.

### Relevância Social e Educacional

A democratização da tecnologia de robótica tem impacto direto na educação e na formação de recursos humanos. Times de robótica educacionais, como os que participam de competições estudantis, frequentemente enfrentam restrições orçamentárias severas. 

Soluções de baixo custo permitem que mais instituições de ensino, especialmente em regiões com menos recursos, tenham acesso a tecnologias de ponta, promovendo:
- Inclusão digital e tecnológica
- Formação de estudantes em áreas críticas (IA, robótica, sistemas embarcados)
- Incentivo à pesquisa e inovação
- Desenvolvimento de competências técnicas avançadas

### Aplicabilidade Prática

O sistema desenvolvido neste trabalho terá aplicações diretas em:
- **Times de robótica educacionais**: Solução viável para competições estudantis
- **Pesquisa acadêmica**: Base para trabalhos futuros em visão embarcada
- **Projetos de extensão**: Tecnologia transferível para comunidade
- **Indústria 4.0**: Conceitos aplicáveis a outros domínios (inspeção, vigilância, automação)

Além disso, todo o código e documentação serão disponibilizados de forma aberta, permitindo replicação e extensão por outros pesquisadores e entusiastas.

## 1.2 Problema

A implementação de sistemas de visão computacional em robótica móvel autônoma tradicionalmente depende de uma de duas abordagens: sistemas de visão centralizados com alto poder computacional externo, ou sistemas embarcados em plataformas de alto custo (como placas com GPUs embarcadas, custando milhares de reais).

No contexto da RoboCup e competições similares de futebol de robôs, a categoria Small Size League utiliza um sistema de visão centralizado, onde câmeras externas capturam todo o campo e um computador central processa as imagens e envia comandos aos robôs via comunicação sem fio. Embora eficaz, essa abordagem:
- Requer infraestrutura complexa e cara
- Limita a portabilidade do sistema
- É menos realista do ponto de vista de autonomia genuína
- Não é escalável para aplicações além do ambiente controlado

Por outro lado, sistemas de visão embarcada em robôs móveis geralmente utilizam hardware especializado (como Jetson Nano, Raspberry Pi 4 com aceleradores, ou módulos Intel Movidius), que, embora mais poderosos, apresentam custos elevados (R$ 500 a R$ 2.000) e consumo energético significativo, inviáveis para robôs pequenos operados por bateria.

**Questão Central de Pesquisa:**

Qual plataforma de hardware oferece o melhor custo-benefício para implementação de um módulo de visão computacional embarcado baseado em TinyML, capaz de detectar objetos em tempo real e fornecer coordenadas (x, y) para integração com sistemas de controle de robótica autônoma, considerando restrições de custo, viabilidade técnica e redução de custos?

**Questões Secundárias:**

1. Quais são as plataformas de hardware disponíveis no mercado adequadas para visão computacional embarcada e como elas se comparam em termos de custo, desempenho e viabilidade técnica?

2. Como otimizar modelos de deep learning para operar dentro das restrições de memória e processamento de microcontroladores de baixo custo, mantendo acurácia aceitável?

3. Quais técnicas de quantização, pruning e co-design são mais eficazes para reduzir custos sem comprometer significativamente o desempenho?

4. Como projetar uma interface de saída padronizada que forneça coordenadas (x, y) dos objetos detectados de forma eficiente para integração com sistemas de controle (Arduino)?

5. Qual o trade-off entre complexidade do modelo, acurácia, latência e consumo energético em diferentes plataformas de hardware?

6. Como treinar e otimizar modelos de detecção de objetos especificamente para operação em dispositivos embarcados de recursos limitados?

## 1.3 Objetivos

### 1.3.1 Geral

Desenvolver, comparar e avaliar um módulo de visão computacional embarcado de baixo custo baseado em TinyML, realizando análise comparativa de diferentes plataformas de hardware disponíveis no mercado, com foco em viabilidade técnica e redução de custos, capaz de detectar objetos e fornecer coordenadas (x, y) para integração com sistemas de controle de robótica autônoma.

### 1.3.2 Específicos

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

## 1.4 Metodologia

### Classificação da Pesquisa

Este trabalho caracteriza-se como:

- **Quanto à natureza**: Pesquisa Aplicada, pois visa gerar conhecimento para aplicação prática na solução de problemas específicos de robótica autônoma.

- **Quanto aos objetivos**: Pesquisa Exploratória e Experimental, pois explora a viabilidade de TinyML para visão embarcada e realiza experimentos controlados para validação.

- **Quanto à abordagem**: Pesquisa Quali-quantitativa, combinando análise quantitativa de métricas de desempenho com avaliação qualitativa do comportamento do sistema.

- **Quanto aos procedimentos técnicos**: 
  - Pesquisa Bibliográfica (revisão sistemática da literatura)
  - Pesquisa Experimental (desenvolvimento e testes do protótipo)
  - Estudo de Caso (aplicação no contexto de futebol de robôs)

### Procedimentos Metodológicos

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
   - Calibração da câmera (correção de distorção, ajuste de exposição)

2. **Desenvolvimento do firmware** (Mês 9, semanas 2-4):
   - Implementação do pipeline de visão:
     * Módulo de captura de imagem via interface DVP
     * Pré-processamento (redimensionamento, normalização, conversão de espaço de cor)
     * Inferência usando TFLite Micro
     * Pós-processamento (extração de bounding box, filtros de confiança, non-maximum suppression)
   - Otimização de código para performance e memória
   - Debug e correções

3. **Desenvolvimento da interface de saída** (Mês 10):
   - **Definição do sistema de coordenadas**: 
     * Origem no centro da imagem ou canto superior esquerdo
     * Eixos X (horizontal) e Y (vertical) normalizados ou em pixels
     * Sistema de coordenadas relativo ao campo de visão da câmera
   
   - **Implementação do protocolo de comunicação**:
     * Interface serial/UART para comunicação com Arduino ou sistema de controle
     * Formato de mensagem padronizado: `OBJ,x,y,confiança\n` ou JSON
     * Taxa de transmissão configurável (ex: 115200 baud)
     * Tratamento de múltiplos objetos detectados
   
   - **Representação da visão do campo**:
     * Mapeamento da imagem capturada para coordenadas do campo
     * Calibração de perspectiva (se necessário)
     * Fornecimento de coordenadas (x, y) dos objetos detectados
     * Informações adicionais: confiança, tamanho do objeto, timestamp
   
   - **Testes de interface**:
     * Comunicação com Arduino simulado
     * Validação do formato de dados
     * Testes de latência de transmissão
     * Verificação de precisão das coordenadas

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

### Materiais e Recursos

**Hardware necessário** (custo total estimado: R$ 150,00):
- ESP32-S3 DevKit (2 unidades para testes): R$ 120,00
- Câmera OV2640 (2 unidades): R$ 50,00
- Componentes diversos (jumpers, protoboard, reguladores, conectores): R$ 30,00
- Arduino Uno ou similar (para testes de interface de comunicação): R$ 80,00 (opcional, pode usar simulador)

**Nota**: A montagem física do robô não faz parte deste trabalho. O hardware listado é apenas para o módulo de visão e testes de interface.

**Software** (gratuito):
- ESP-IDF ou Arduino IDE
- Python + TensorFlow
- Google Colab
- Visual Studio Code + PlatformIO
- OpenCV
- Zotero (gerenciador de referências)

**Infraestrutura**:
- Laboratório de robótica do IFBA
- Computador pessoal para desenvolvimento
- Acesso à internet

---

# 2. CONCEITOS TEÓRICOS / TRABALHOS RELACIONADOS

## 2.1 TinyML (Tiny Machine Learning)

TinyML refere-se à área de pesquisa e desenvolvimento focada na implementação de modelos de machine learning em dispositivos embarcados com recursos extremamente limitados, tipicamente microcontroladores (MCUs) com menos de 1 MB de memória e processadores de baixa potência (WARDEN; SITUNAYAKE, 2019).

### Características Fundamentais

Os sistemas TinyML são caracterizados por três restrições principais:
1. **Memória limitada**: Tipicamente 256 KB a 1 MB de RAM
2. **Processamento limitado**: Processadores de 10-240 MHz, sem unidade de ponto flutuante
3. **Energia limitada**: Operação com bateria, consumo em miliamperes

### Desafios Técnicos

A implementação de TinyML envolve desafios únicos que não existem em plataformas convencionais:

**Restrição de memória de ativação**: Diferentemente do que se poderia imaginar, a principal limitação não é o número de parâmetros do modelo, mas sim a memória necessária para armazenar ativações intermediárias durante a inferência. Isso significa que arquiteturas como ResNet, que funcionam bem em mobile, são inviáveis em MCUs (LIN et al., 2020).

**Ausência de ponto flutuante**: Microcontroladores geralmente não possuem unidades de ponto flutuante (FPU), tornando operações com números float32 extremamente lentas. A solução é a quantização para inteiros de 8 bits (int8).

**Co-design necessário**: O sucesso de uma aplicação TinyML depende de um design conjunto otimizado do algoritmo e da arquitetura do sistema, considerando as capacidades específicas do hardware alvo.

### Frameworks e Ferramentas

**TensorFlow Lite Micro**: Framework da Google para executar modelos TensorFlow Lite em microcontroladores. Suporta quantização int8 e possui footprint de apenas ~20 KB.

**Edge Impulse**: Plataforma completa para desenvolvimento TinyML, incluindo coleta de dados, treinamento e deployment.

**Frameworks alternativos**: uTensor, ARM CMSIS-NN, NNoM.

### Aplicações Típicas

- Reconhecimento de palavras-chave (keyword spotting)
- Detecção de anomalias em sensores
- Visão computacional básica (gestos, objetos simples)
- Manutenção preditiva
- Wearables inteligentes

## 2.2 Edge AI

Edge AI refere-se ao paradigma de processamento de inteligência artificial localmente, no dispositivo final (edge device), em oposição ao processamento centralizado em servidores na nuvem (CHEN; RAN, 2019).

### Motivações para Edge AI

**Latência**: Aplicações de tempo real como robótica, veículos autônomos e realidade aumentada não podem tolerar o atraso da comunicação com a nuvem (tipicamente > 100ms).

**Privacidade**: Processar dados sensíveis localmente evita transmissão pela rede, reduzindo riscos de segurança.

**Largura de banda**: Com bilhões de dispositivos IoT, enviar todos os dados para a nuvem é inviável do ponto de vista de infraestrutura de rede.

**Confiabilidade**: Independência de conectividade permite operação mesmo sem acesso à internet.

**Custo**: Processamento local elimina custos recorrentes de serviços na nuvem.

### Espectro de Edge AI

Edge AI não é um conceito binário, mas um espectro:
- **Tiny Edge**: Microcontroladores (TinyML) - µW a mW
- **Small Edge**: Dispositivos mobile (smartphones) - Watts
- **Medium Edge**: Placas embarcadas (Raspberry Pi, Jetson) - dezenas de Watts
- **Large Edge**: Servidores locais (edge servers) - centenas de Watts

Este trabalho foca no extremo inferior do espectro (Tiny Edge).

### Trade-offs

Edge AI envolve trade-offs fundamentais:
- **Poder computacional vs Consumo energético**
- **Precisão do modelo vs Latência**
- **Autonomia vs Complexidade do algoritmo**
- **Custo vs Desempenho**

## 2.3 Análise Comparativa de Plataformas de Hardware

Esta seção apresenta uma análise comparativa detalhada das principais plataformas de hardware disponíveis no mercado para implementação de visão computacional embarcada, considerando critérios de custo, desempenho, viabilidade técnica e adequação para aplicações de robótica autônoma.

### 2.3.1 Microcontroladores (MCUs)

#### ESP32-S3

**Fabricante**: Espressif Systems  
**Custo aproximado**: R$ 60,00 - R$ 80,00  
**Processador**: Dual-core Xtensa LX7 @ 240 MHz  
**Memória RAM**: 512 KB SRAM interna + suporte a PSRAM externa (até 8 MB)  
**Memória Flash**: 4-16 MB (externa)  
**Interface de Câmera**: DVP (Digital Video Port) dedicada, 8/16 bits, até 40 MHz  
**Unidade de Ponto Flutuante**: Não (operações float são lentas)  
**Conectividade**: WiFi 802.11 b/g/n, Bluetooth 5.0 LE  
**Consumo energético**: ~80-240 mA (ativo), ~10 µA (deep sleep)  
**Frameworks ML**: TensorFlow Lite Micro, Edge Impulse  
**Vantagens**:
- Interface de câmera dedicada (DVP) - raro em MCUs
- Custo muito baixo
- Boa comunidade e documentação
- WiFi integrado para debug/monitoramento
- Aceleradores de hardware para processamento de imagem

**Desvantagens**:
- Memória RAM limitada (512 KB)
- Sem FPU (float32 muito lento)
- Processamento limitado para modelos complexos

**Viabilidade para visão embarcada**: ⭐⭐⭐⭐ (4/5) - Excelente custo-benefício

#### STM32F4 Series (ex: STM32F407)

**Fabricante**: STMicroelectronics  
**Custo aproximado**: R$ 80,00 - R$ 120,00  
**Processador**: ARM Cortex-M4 @ 168 MHz  
**Memória RAM**: 192 KB SRAM  
**Memória Flash**: 1-2 MB  
**Interface de Câmera**: DCMI (Digital Camera Interface) dedicada  
**Unidade de Ponto Flutuante**: Sim (FPU single precision)  
**Conectividade**: Requer módulos externos  
**Consumo energético**: ~100-200 mA (ativo)  
**Frameworks ML**: TensorFlow Lite Micro, STM32Cube.AI  
**Vantagens**:
- FPU nativa (float32 rápido)
- Interface de câmera dedicada (DCMI)
- Boa performance para operações matemáticas
- STM32Cube.AI otimizado para STM32

**Desvantagens**:
- Custo maior que ESP32-S3
- Menos memória RAM que ESP32-S3
- Comunidade menor para ML
- Requer módulos externos para WiFi

**Viabilidade para visão embarcada**: ⭐⭐⭐ (3/5) - Boa, mas mais cara

#### Raspberry Pi Pico / RP2040

**Fabricante**: Raspberry Pi Foundation  
**Custo aproximado**: R$ 40,00 - R$ 60,00  
**Processador**: Dual-core ARM Cortex-M0+ @ 133 MHz  
**Memória RAM**: 264 KB SRAM  
**Memória Flash**: 2-16 MB (externa)  
**Interface de Câmera**: Não (requer comunicação SPI/I2C)  
**Unidade de Ponto Flutuante**: Não  
**Conectividade**: Requer módulos externos  
**Consumo energético**: ~50-100 mA (ativo)  
**Frameworks ML**: TensorFlow Lite Micro (suporte limitado)  
**Vantagens**:
- Custo muito baixo
- Boa documentação
- Comunidade ativa

**Desvantagens**:
- Sem interface de câmera dedicada (SPI/I2C muito lento)
- Memória RAM muito limitada
- Sem FPU
- Suporte ML limitado

**Viabilidade para visão embarcada**: ⭐⭐ (2/5) - Limitada pela falta de interface de câmera

### 2.3.2 Sistemas Embarcados (SBCs - Single Board Computers)

#### Raspberry Pi 4 Model B

**Fabricante**: Raspberry Pi Foundation  
**Custo aproximado**: R$ 500,00 - R$ 600,00  
**Processador**: Quad-core ARM Cortex-A72 @ 1.5 GHz  
**Memória RAM**: 2-8 GB LPDDR4  
**Memória Flash**: MicroSD (externa)  
**Interface de Câmera**: CSI (Camera Serial Interface) dedicada  
**Unidade de Ponto Flutuante**: Sim (NEON SIMD)  
**Conectividade**: WiFi 802.11ac, Bluetooth 5.0, Gigabit Ethernet  
**Consumo energético**: ~2-5 W (1-2.5 A @ 5V)  
**Frameworks ML**: TensorFlow Lite, PyTorch, OpenCV  
**Vantagens**:
- Muito mais poder de processamento
- Grande quantidade de RAM
- Suporte completo a frameworks ML
- Comunidade enorme
- GPU VideoCore VI para aceleração

**Desvantagens**:
- Custo 8-10x maior que ESP32-S3
- Consumo energético alto (requer fonte dedicada)
- Não é um MCU (sistema operacional Linux)
- Overhead do sistema operacional

**Viabilidade para visão embarcada**: ⭐⭐⭐⭐⭐ (5/5) - Excelente, mas caro e consome muita energia

#### NVIDIA Jetson Nano

**Fabricante**: NVIDIA  
**Custo aproximado**: R$ 1.000,00 - R$ 1.500,00  
**Processador**: Quad-core ARM Cortex-A57 @ 1.43 GHz + GPU NVIDIA Maxwell (128 CUDA cores)  
**Memória RAM**: 4 GB LPDDR4  
**Memória Flash**: MicroSD (externa)  
**Interface de Câmera**: CSI dedicada  
**Unidade de Ponto Flutuante**: Sim + GPU para aceleração  
**Conectividade**: WiFi 802.11ac, Bluetooth 4.2, Gigabit Ethernet  
**Consumo energético**: ~5-10 W (1-2 A @ 5V)  
**Frameworks ML**: TensorFlow, PyTorch, TensorRT (otimizado para NVIDIA)  
**Vantagens**:
- GPU dedicada para ML (muito rápido)
- TensorRT para otimização
- Suporte completo a deep learning
- Performance excepcional

**Desvantagens**:
- Custo muito alto (20x ESP32-S3)
- Consumo energético muito alto
- Requer fonte dedicada robusta
- Overkill para aplicações simples

**Viabilidade para visão embarcada**: ⭐⭐⭐⭐⭐ (5/5) - Excelente para aplicações complexas, mas proibitivo em custo

#### Google Coral Dev Board / Edge TPU

**Fabricante**: Google  
**Custo aproximado**: R$ 800,00 - R$ 1.200,00  
**Processador**: Quad-core ARM Cortex-A53 + Edge TPU (ASIC para ML)  
**Memória RAM**: 1 GB LPDDR4  
**Memória Flash**: 8 GB eMMC  
**Interface de Câmera**: CSI dedicada  
**Unidade de Ponto Flutuante**: Sim + Edge TPU  
**Conectividade**: WiFi 802.11ac, Bluetooth 4.2, Gigabit Ethernet  
**Consumo energético**: ~2-5 W  
**Frameworks ML**: TensorFlow Lite (otimizado para Edge TPU)  
**Vantagens**:
- Edge TPU: ASIC dedicado para inferência ML (muito rápido)
- Baixo consumo para o desempenho
- Otimizado especificamente para ML

**Desvantagens**:
- Custo alto
- Requer modelos quantizados específicos
- Menos flexível que soluções genéricas

**Viabilidade para visão embarcada**: ⭐⭐⭐⭐ (4/5) - Excelente para ML, mas caro

### 2.3.3 Tabela Comparativa Resumida

| Plataforma | Custo (R$) | RAM | Clock | Interface Câmera | FPU | Consumo | ML Support | Score |
|------------|-----------|-----|-------|-----------------|-----|---------|------------|-------|
| **ESP32-S3** | 60-80 | 512 KB | 240 MHz | DVP (dedicada) | Não | ~80-240 mA | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ |
| **STM32F4** | 80-120 | 192 KB | 168 MHz | DCMI (dedicada) | Sim | ~100-200 mA | ⭐⭐⭐ | ⭐⭐⭐ |
| **RPi Pico** | 40-60 | 264 KB | 133 MHz | Não | Não | ~50-100 mA | ⭐⭐ | ⭐⭐ |
| **RPi 4** | 500-600 | 2-8 GB | 1.5 GHz | CSI (dedicada) | Sim | ~2-5 W | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| **Jetson Nano** | 1000-1500 | 4 GB | 1.43 GHz | CSI (dedicada) | Sim+GPU | ~5-10 W | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| **Coral Dev** | 800-1200 | 1 GB | + Edge TPU | CSI (dedicada) | Sim+TPU | ~2-5 W | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ |

### 2.3.4 Análise de Viabilidade e Trade-offs

#### Para Aplicação em Robótica Autônoma de Baixo Custo

**Critérios de seleção prioritários**:
1. **Custo** (< R$ 200 para módulo completo)
2. **Interface de câmera dedicada** (essencial para performance)
3. **Consumo energético** (bateria deve durar > 30 min)
4. **Suporte a ML** (frameworks disponíveis)
5. **Memória suficiente** (para modelo + imagem)

**Análise por categoria**:

**Categoria 1: Microcontroladores de Baixo Custo**
- **ESP32-S3**: ⭐⭐⭐⭐ Melhor opção - Interface DVP, custo baixo, boa comunidade
- **STM32F4**: ⭐⭐⭐ Boa opção, mas mais cara e menos memória
- **RPi Pico**: ⭐⭐ Não recomendado - falta interface de câmera dedicada

**Categoria 2: Sistemas Embarcados**
- **RPi 4**: ⭐⭐⭐⭐ Excelente desempenho, mas custo e consumo altos
- **Jetson Nano**: ⭐⭐⭐ Overkill e muito caro para este projeto
- **Coral Dev**: ⭐⭐⭐ Boa para ML, mas custo alto

**Recomendação**: **ESP32-S3** oferece o melhor custo-benefício para este projeto, com interface de câmera dedicada e custo acessível.

### 2.3.5 Estratégias de Redução de Custos

1. **Seleção de hardware**: ESP32-S3 oferece melhor custo-benefício
2. **Otimização de software**: Modelos menores = menos memória necessária
3. **Quantização**: Reduz tamanho do modelo em 4x
4. **Co-design**: Otimizar modelo para hardware específico
5. **Alternativas de câmera**: Câmeras OV2640 são baratas (~R$ 25)
6. **Produção em escala**: Custos podem cair 30-50% em volumes maiores

**Custo total estimado do módulo**:
- ESP32-S3: R$ 60
- Câmera OV2640: R$ 25
- Componentes (reguladores, conectores): R$ 15
- **Total: R$ 100** (50% do orçamento de R$ 200)

## 2.4 ESP32-S3 (Plataforma Selecionada)

O ESP32-S3 foi selecionado como plataforma principal após análise comparativa, oferecendo o melhor equilíbrio entre custo, recursos e viabilidade técnica para este projeto.

### Especificações Técnicas Relevantes

**Processador**:
- Dual-core Xtensa LX7 @ até 240 MHz
- Suporte a instruções vetoriais (SIMD)
- Sem unidade de ponto flutuante dedicada

**Memória**:
- 512 KB SRAM interna
- 384 KB ROM
- Suporte a Flash externa (4 MB típico, até 16 MB)
- Suporte a PSRAM externa (até 8 MB)

**Interfaces**:
- Interface dedicada para câmera (DVP - 8/16 bits)
- WiFi 802.11 b/g/n
- Bluetooth 5.0 LE
- 45 GPIOs programáveis
- SPI, I2C, UART, I2S

**Aceleradores**:
- Acelerador de hardware para operações de processamento de imagem
- Suporte a instruções SIMD para aceleração de operações matemáticas

### Vantagens para Visão Computacional

**Interface de câmera dedicada**: Ao contrário de outros MCUs que requerem comunicação SPI/I2C lenta com módulos de câmera, o ESP32-S3 possui interface DVP que permite captura direta de imagens de sensores, com taxas de até 40 MHz.

**Memória adequada**: Os 512 KB de SRAM são suficientes para armazenar um frame de imagem de baixa resolução e executar inferência de modelos TinyML.

**Conectividade WiFi**: Permite debug remoto, visualização de resultados em tempo real e eventual comunicação entre robôs.

### Comparação com Alternativas

| Plataforma | RAM | Clock | Custo | FPU | Interface Câmera |
|------------|-----|-------|-------|-----|------------------|
| ESP32-S3 | 512 KB | 240 MHz | R$ 60 | Não | Sim (DVP) |
| Arduino Uno | 2 KB | 16 MHz | R$ 80 | Não | Não |
| STM32F4 | 192 KB | 168 MHz | R$ 100 | Sim | Não |
| Raspberry Pi Pico | 264 KB | 133 MHz | R$ 40 | Não | Não |
| Raspberry Pi 4 | 4 GB | 1.5 GHz | R$ 500 | Sim | Sim (CSI) |

O ESP32-S3 oferece o melhor compromisso custo-benefício para aplicações de visão computacional embarcada.

## 2.4 Interface de Saída e Representação do Campo de Visão

### 2.4.1 Sistema de Coordenadas

O módulo de visão desenvolvido fornece como saída as coordenadas (x, y) dos objetos detectados no campo de visão da câmera. A definição de um sistema de coordenadas consistente é fundamental para a integração com sistemas de controle subsequentes.

**Opções de sistema de coordenadas**:

1. **Coordenadas em pixels**:
   - Origem no canto superior esquerdo (0, 0)
   - Eixo X: horizontal, de 0 a largura_da_imagem
   - Eixo Y: vertical, de 0 a altura_da_imagem
   - Vantagem: Direto, sem conversão
   - Desvantagem: Depende da resolução da câmera

2. **Coordenadas normalizadas**:
   - Origem no centro da imagem (0, 0)
   - Eixos X e Y de -1 a +1 (ou 0 a 1)
   - Vantagem: Independente da resolução
   - Desvantagem: Requer conversão para uso prático

3. **Coordenadas relativas ao campo**:
   - Mapeamento da imagem para coordenadas do campo de futebol
   - Requer calibração de perspectiva
   - Vantagem: Diretamente utilizável para navegação
   - Desvantagem: Mais complexo, requer calibração

**Recomendação para este trabalho**: Sistema híbrido - coordenadas em pixels com origem no centro da imagem, permitindo fácil conversão para qualquer sistema desejado.

### 2.4.2 Protocolo de Comunicação

A interface de comunicação entre o módulo de visão e o sistema de controle (Arduino ou similar) utiliza comunicação serial (UART) padrão, permitindo integração simples e universal.

**Formato de mensagem proposto**:

```
OBJ,<x>,<y>,<confiança>,<largura>,<altura>\n
```

Onde:
- `OBJ`: Identificador do objeto (ex: "BALL" para bola)
- `<x>`: Coordenada X (pixels ou normalizada)
- `<y>`: Coordenada Y (pixels ou normalizada)
- `<confiança>`: Confiança da detecção (0.0 a 1.0)
- `<largura>`: Largura do bounding box (opcional)
- `<altura>`: Altura do bounding box (opcional)

**Exemplo de mensagem**:
```
BALL,160,120,0.95,30,30\n
```

**Alternativa JSON** (mais flexível, mas maior overhead):
```json
{"objects": [{"type": "ball", "x": 160, "y": 120, "confidence": 0.95, "width": 30, "height": 30}]}
```

### 2.4.3 Representação da Visão do Campo

O módulo fornece uma "visão" do campo através das coordenadas dos objetos detectados. Esta representação permite que o sistema de controle:

1. **Localizar objetos**: Saber onde está a bola no campo de visão
2. **Calcular direção**: Determinar para onde o robô deve se mover
3. **Estimar distância**: Usar tamanho do objeto para estimar distância (se calibrado)
4. **Rastrear movimento**: Comparar coordenadas entre frames para rastreamento

**Informações fornecidas**:
- Posição do objeto (x, y)
- Confiança da detecção
- Tamanho do objeto (se disponível)
- Timestamp (opcional, para sincronização)

**Integração com Arduino**:
O Arduino recebe as coordenadas via Serial e pode:
- Calcular ângulo de movimento necessário
- Decidir velocidade e direção dos motores
- Implementar lógica de navegação
- Executar estratégias de jogo

### 2.4.4 Calibração e Mapeamento

Para aplicações futuras mais avançadas, o módulo pode incluir:
- **Calibração de perspectiva**: Mapear coordenadas da imagem para coordenadas do campo real
- **Correção de distorção**: Compensar distorção da lente da câmera
- **Estimativa de distância**: Usar tamanho aparente do objeto para estimar distância real

Estas funcionalidades avançadas podem ser implementadas em trabalhos futuros, após a validação do módulo básico.

## 2.5 Visão Computacional Embarcada

Visão computacional embarcada refere-se à implementação de algoritmos de processamento e análise de imagens em sistemas com recursos limitados, geralmente para aplicações de tempo real (BONARDI et al., 2015).

### Pipeline Típico de Visão Computacional

Um sistema de visão embarcado típico consiste em:

1. **Captura de imagem**: Sensor de imagem (câmera) captura frame
2. **Pré-processamento**: 
   - Redimensionamento
   - Conversão de espaço de cor
   - Normalização
   - Correção de distorção
3. **Processamento principal**:
   - Detecção de features
   - Segmentação
   - Detecção/reconhecimento de objetos
4. **Pós-processamento**:
   - Filtros temporais
   - Non-maximum suppression
   - Extração de informação relevante
5. **Atuação**: Decisão baseada nos resultados

### Técnicas Clássicas vs Deep Learning

**Abordagens clássicas**:
- Detecção baseada em cor (thresholding em HSV)
- Detecção de bordas (Canny, Sobel)
- Transformada de Hough (detecção de círculos/linhas)
- Template matching

Vantagens: Leves, rápidas, determinísticas
Desvantagens: Sensíveis a variações, pouco robustas

**Abordagens de Deep Learning**:
- Redes Neurais Convolucionais (CNNs)
- Arquiteturas modernas: YOLO, SSD, MobileNet

Vantagens: Robustas, aprendem features automaticamente
Desvantagens: Computacionalmente intensivas

### Otimizações para Sistemas Embarcados

**Quantização**: Redução de precisão de pesos e ativações (float32 → int8)
- Reduz tamanho do modelo em ~4x
- Acelera inferência em ~4x
- Perda mínima de acurácia (< 1% tipicamente)

**Pruning**: Remoção de pesos pouco importantes
- Pode reduzir modelo em 50-90%
- Requer fine-tuning pós-pruning

**Knowledge Distillation**: Treinar modelo pequeno (student) para imitar modelo grande (teacher)

**Neural Architecture Search**: Busca automatizada pela arquitetura ideal para o hardware alvo

## 2.6 RoboCup e Futebol de Robôs

A RoboCup é uma competição científica internacional estabelecida em 1997 com o objetivo audacioso: até 2050, um time de robôs humanoides autônomos deve ser capaz de vencer o time campeão da Copa do Mundo de Futebol da FIFA (KITANO et al., 1997).

### Categorias Principais

**Small Size League (SSL)**:
- Robôs pequenos (~15 cm diâmetro)
- **Visão centralizada**: Câmeras externas, processamento off-board
- Comunicação via rádio
- Jogo extremamente rápido e preciso

**Middle Size League (MSL)**:
- Robôs médios (~50 cm altura)
- **Visão embarcada**: Cada robô tem sua própria câmera
- Completamente autônomos
- Mais desafiador tecnicamente

**Standard Platform League (SPL)**:
- Robôs humanoides idênticos (NAO)
- Visão embarcada
- Foco em software

**Humanoid League**:
- Robôs bípedes de diferentes tamanhos
- Visão embarcada
- Estado da arte em locomoção e controle

### Visão Centralizada vs Embarcada

| Aspecto | Centralizada (SSL) | Embarcada (MSL/SPL) |
|---------|-------------------|---------------------|
| Processamento | Computador externo | No próprio robô |
| Visão | Global (todo campo) | Local (limitada) |
| Comunicação | Essencial | Opcional |
| Autonomia | Parcial | Total |
| Latência | ~10-20 ms | ~20-100 ms |
| Custo | Alto (infraestrutura) | Moderado |
| Portabilidade | Baixa | Alta |
| Realismo | Menor | Maior |

Este trabalho alinha-se com a filosofia de visão embarcada, buscando autonomia real.

### Desafios Técnicos

**Ambiente dinâmico**: Bola e robôs se movem rapidamente, exigindo reação em tempo real.

**Iluminação variável**: Condições de luz mudam durante o jogo (sombras, reflexos).

**Oclusões**: Outros robôs podem bloquear a visão da bola.

**Vibração**: Movimento do robô causa trepidação na câmera (motion blur).

**Campo de visão limitado**: Câmera embarcada vê apenas uma fração do campo.

## 2.7 Trabalhos Relacionados

### MCUNet: Tiny Deep Learning on IoT Devices (LIN et al., 2020)

Lin et al. apresentam o MCUNet, um framework para design conjunto de redes neurais e sistema de inferência otimizado para microcontroladores. O trabalho demonstra que é possível executar classificação ImageNet em um MCU com apenas 320 KB de memória, alcançando 70.7% de acurácia top-1.

**Contribuições principais**:
- TinyNAS: Neural Architecture Search para MCUs
- TinyEngine: Sistema de inferência otimizado
- Demonstração de viabilidade de CNNs profundas em MCUs

**Relevância para este trabalho**: Valida a viabilidade técnica de visão computacional em microcontroladores e fornece diretrizes para otimização.

### MicroNets: Neural Network Architectures for Deploying TinyML Applications (BANBURY et al., 2021)

Banbury et al. propõem uma família de arquiteturas de redes neurais especificamente projetadas para TinyML, considerando restrições de memória de ativação.

**Descoberta chave**: A memória de ativação (não o número de parâmetros) é o principal gargalo em MCUs.

**Relevância**: Informa o design do modelo de detecção para o ESP32-S3.

### Visão Embarcada em Futebol de Robôs

**CMDragons (CMU)**: Time da Small Size League que pioneirou algoritmos de coordenação multi-agentes. Embora use visão centralizada, suas técnicas de planejamento são relevantes.

**B-Human (SPL)**: Time campeão múltiplo da Standard Platform League, com sistema de visão embarcado robusto. Seu trabalho em detecção de bola usando CNNs leves é particularmente relevante (MÜHLENBROCK et al., 2018).

**RobôCIn (UFPE)**: Time brasileiro com contribuições em visão computacional para robótica.

### Lacunas Identificadas

A revisão da literatura revela algumas lacunas que este trabalho pretende abordar:

1. **Escassez de trabalhos com ESP32-S3 para visão**: Maioria usa plataformas mais poderosas
2. **Falta de comparações sistemáticas** entre visão embarcada e centralizada em termos de custo-benefício
3. **Poucos datasets públicos** específicos para futebol de robôs com visão embarcada
4. **Limitada documentação de trade-offs** práticos em implementações reais

---

# 3. CRONOGRAMA

Cronograma de atividades para desenvolvimento do trabalho monográfico, incluindo o projeto (TCC I - 1º semestre) e a monografia (TCC II - 2º semestre) do ano letivo de 2025.

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
| **9. Integrar com robô** | | | | | | | | X | X | | | |
| **10. Realizar testes** | | | | | | | | | X | X | | |
| **11. Analisar resultados** | | | | | | | | | | X | | |
| **12. Elaborar monografia** | | | | | X | X | | | | X | X | |
| **13. Revisar texto** | | | | | | | | | | | X | X |
| **14. Preparar apresentação** | | | | | | | | | | | | X |
| **15. Entregar TCC I** | | | | | | **✓** | | | | | | |
| **16. Entregar TCC II** | | | | | | | | | | | **✓** | |
| **17. Defesa da monografia** | | | | | | | | | | | | **✓** |

**Marcos Críticos**:
- **30/Jun/2025**: Entrega do Projeto (TCC I)
- **30/Nov/2025**: Entrega da Monografia (TCC II)
- **15/Dez/2025**: Defesa da Monografia

---

# 4. REFERÊNCIAS

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

# APÊNDICES

## Apêndice A - Termo de Aceite do Orientador

[Incluir cópia do Termo de Aceite assinado pelo orientador]

## Apêndice B - Especificações Técnicas Detalhadas

[Incluir quando disponível: diagramas de hardware, esquemáticos, especificações de componentes]

## Apêndice C - Cronograma Expandido

[Incluir se necessário: detalhamento semanal das atividades principais]

