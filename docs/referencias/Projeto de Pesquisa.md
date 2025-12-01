

**INSTITUTO FEDERAL DE EDUCAÇÃO, CIÊNCIA E TECNOLOGIA DA BAHIA \- IFBA**

BRENDON SOUSA LIMA

**TÍTULO PROVISÓRIO: DETECÇÃO E LOCALIZAÇÃO DE OBJETOS COM CÂMERA OV2640 E ESPELHO CONVEXO EM ROBÔS MÓVEIS AUTÔNOMOS**

Vitória da Conquista

2025

Projeto de Monografia apresentado como requisito parcial de avaliação da disciplina Trabalho de Conclusão de Curso I, do curso de Bacharelado em Sistemas de Informação do Instituto Federal de Educação, Ciência e Tecnologia da Bahia – IFBA, sob orientação do Prof. Andrique Figueirêdo Amorim.

 

Vitória da Conquista

2025

Sumário  
[1\.	INTRODUÇÃO	4](#introdução)

[1.1	Justificativa	4](#justificativa)

[1.2	Problema	4](#problema)

[1.3	Objetivos	4](#objetivos)

[1.3.1	Geral	4](#geral)

[1.3.2	Específicos	4](#específicos)

[1.4	Metodologia	4](#heading=h.yfwd0x9ju8iv)

[2	CONCEITOS TEÓRICOS / TRABALHOS RELACIONADOS	5](#conceitos-teóricos-\(quantas-seções-forem-necessárias\)/-trabalhos-relacionados)

[3	CRONOGRAMA	6](#cronograma)

[4	REFERÊNCIAS	7](#referências)

[APÊNDICES	8](#apêndices)

## 1. **INTRODUÇÃO** {#introdução}

A robótica móvel autônoma representa um desafio tecnológico relevante, especialmente em ambientes dinâmicos como campos de futebol de robôs. Nesses cenários, sistemas precisam perceber o ambiente, localizar objetos e tomar decisões em tempo real, com latência mínima e baixo custo. Um exemplo emblemático são as competições da RoboCup, nas quais robôs devem identificar e acompanhar uma bola em movimento enquanto executam ações de locomoção e estratégia.

Tradicionalmente, competições utilizam visão centralizada: câmeras suspensas sobre o campo detectam a bola e transmitem coordenadas para os robôs via comunicação sem fio. Entretanto, este modelo não representa cenários reais de autonomia, além de exigir infraestrutura complexa e cara. A proposta deste trabalho se diferencia ao adotar visão embarcada, utilizando uma câmera OV2640 apontada para um espelho convexo, que amplia o campo de visão e permite ao robô localizar objetos ao seu redor com custo reduzido.

O presente projeto visa desenvolver um sistema embarcado de visão computacional que detecte a bola laranja no campo de jogo utilizando técnicas de segmentação por cor no espaço HSV (Hue, Saturation, Value), calcule sua posição relativa ao robô e envie as coordenadas para o sistema de controle de movimento. O dispositivo será baseado no microcontrolador ESP32-S3, que permite processamento local eficiente e comunicação com a placa de locomoção, resultando em um robô realmente autônomo com baixo custo e alta responsividade.

### 1.1 **Justificativa** {#justificativa}

A crescente popularização da robótica educacional e da robótica de baixo custo evidencia a necessidade de soluções eficientes e acessíveis. Sensores profissionais, câmeras industriais e placas de alto desempenho possuem custo elevado e complexidade de uso, tornando inviável sua adoção em plataformas acadêmicas e amadoras.

O uso de visão embarcada com câmera OV2640, espelho convexo e ESP32-S3, utilizando técnicas de segmentação por cor (HSV), apresenta um conjunto de vantagens significativas: baixo custo (custo total do módulo < R$ 100), baixo consumo energético, independência de internet, processamento em tempo real com latência muito baixa (15-25 ms) e simplicidade de implementação. Esta abordagem é particularmente adequada para detecção de objetos com características de cor distintivas, como a bola laranja utilizada em competições de futebol de robôs, oferecendo um excelente custo-benefício quando comparada a soluções baseadas em machine learning que requerem treinamento de modelos e maior capacidade computacional.

### 1.2 **Problema** {#problema}

Como permitir que um robô móvel autônomo detecte e estime, em tempo real, a posição relativa de uma bola laranja em um campo de futebol, utilizando apenas visão embarcada, baixo custo e capacidade computacional limitada?

### 1.3 **Objetivos** {#objetivos}

#### 1.3.1 **Geral** {#geral}

Desenvolver um sistema embarcado de visão computacional capaz de detectar e localizar uma bola laranja em tempo real utilizando técnicas de segmentação por cor (HSV), com uma câmera OV2640 acoplada a um espelho convexo, processando os dados diretamente no microcontrolador ESP32-S3.

#### 1.3.2 **Específicos** {#específicos}

1. Capturar imagens através da OV2640 com espelho convexo, obtendo visão panorâmica do ambiente.

2. Implementar algoritmo de segmentação por cor no espaço HSV para identificar a bola laranja no campo, utilizando thresholding adaptativo.

3. Calcular o centroide da bola detectada e converter sua posição em coordenadas cartesianas relativas ao robô (sistema de coordenadas normalizado).

4. Desenvolver sistema de calibração para transformar distâncias em pixels para distância real no chão, considerando a geometria do espelho convexo.

5. Implementar interface de comunicação (UART/Serial) para envio das coordenadas (x, y) para a placa controladora de movimento.

6. Avaliar precisão, tempo de resposta (latência), taxa de quadros (FPS) e robustez do sistema em diferentes condições de iluminação e distâncias.

7. Implementar sistema de medição de tempo de resposta em cada etapa do pipeline para análise comparativa.

8. Realizar validação incremental: inicialmente com fotos de cima (bola isolada, depois bola e gols), e posteriormente com espelho convexo simulando visão do robô, medindo tempo de detecção em cada passo para comparação e busca do equilíbrio entre desempenho e acurácia.

### 1.4 **Metodologia** {#metodologia}

#### **1.4.1 Classificação da Pesquisa**

* **Quanto à natureza:** aplicada, pois visa solucionar um problema real com fins práticos na área de robótica autônoma.

* **Quanto aos objetivos:** experimental e exploratória, pois desenvolve e testa um protótipo funcional.

* **Quanto aos procedimentos técnicos:** pesquisa bibliográfica, desenvolvimento de protótipo funcional e testes experimentais com coleta de dados quantitativos.

#### **1.4.2 Procedimentos Metodológicos**

**Fase 1: Revisão Bibliográfica e Fundamentação Teórica**
1. Estudo teórico sobre visão computacional embarcada, espelhos catadióptricos (convexos) e técnicas de segmentação por cor no espaço HSV.
2. Análise de trabalhos relacionados sobre detecção de objetos em robótica, especialmente em competições RoboCup.
3. Estudo de otimizações para processamento de imagens em microcontroladores.

**Fase 2: Montagem e Configuração do Hardware**
4. Montagem do conjunto câmera OV2640 + espelho convexo + ESP32-S3.
5. Configuração da interface DVP (Digital Video Port) do ESP32-S3 para captura de imagens.
6. Calibração inicial da câmera (ajuste de exposição, white balance).

**Fase 3: Desenvolvimento do Algoritmo de Detecção**
7. Implementação do pipeline de processamento de imagens:
   * Captura de frames em resolução otimizada (QQVGA 160x120 ou QVGA 320x240)
   * Conversão RGB → HSV otimizada (sem ponto flutuante quando possível)
   * Segmentação da cor laranja através de thresholding binário no espaço HSV
   * Operações morfológicas (opcional: erosão/dilatação para remover ruído)
   * Identificação do maior blob (região conectada) como a bola
   * Cálculo do centroide (centro de massa) da região detectada

8. Implementação do sistema de coordenadas:
   * Conversão da posição em pixels para coordenadas normalizadas (x, y) relativas ao robô
   * Calibração para transformar distâncias em pixels para distância real no chão
   * Consideração da geometria do espelho convexo na transformação de coordenadas

**Fase 4: Interface de Comunicação**
9. Implementação do protocolo de comunicação serial (UART) para envio das coordenadas:
   * Formato padronizado: `OBJ,x,y,confiança\n`
   * Taxa de transmissão: 115200 baud
   * Tratamento de casos sem detecção

**Fase 5: Validação Incremental e Testes**

10. **Implementação do sistema de medição de tempo de resposta:**
    * Timestamp no início da captura de imagem
    * Timestamp após cada etapa do pipeline (captura, pré-processamento, segmentação, cálculo de coordenadas)
    * Cálculo de tempo de resposta total e por etapa
    * Logging de métricas de desempenho para análise comparativa

11. **Validação Incremental - Fase 5.1: Testes Iniciais com Fotos de Cima (Bola Isolada)**
    * Captura de fotos utilizando ESP32-S3 posicionado acima do campo (vista superior)
    * Cenário: Bola laranja isolada no campo
    * Quantidade: 50-100 fotos em diferentes posições e condições de iluminação
    * Validação:
      - Taxa de detecção positiva da bola
      - Precisão das coordenadas (x, y) detectadas
      - Tempo de resposta médio, mínimo e máximo
      - Taxa de falsos positivos
    * Critério de sucesso: Taxa de detecção > 90%, latência < 100ms
    * Objetivo: Validar reconhecimento básico e detecção de pontos antes de avançar para cenários mais complexos

12. **Validação Incremental - Fase 5.2: Testes com Fotos de Cima (Bola e Gols)**
    * Captura de fotos utilizando ESP32-S3 posicionado acima do campo
    * Cenário: Bola laranja + gols do time e do oponente visíveis simultaneamente
    * Quantidade: 50-100 fotos variando posições relativas dos objetos
    * Validação:
      - Detecção simultânea de bola e gols
      - Precisão das coordenadas de cada objeto detectado
      - Distinção correta entre gol do time e gol oponente
      - Tempo de resposta para detecção múltipla
      - Taxa de detecção de cada classe (bola, gol_time, gol_oponente)
    * Critério de sucesso: Taxa de detecção > 85% para todos os objetos, latência < 150ms
    * Objetivo: Validar capacidade de detecção múltipla e distinção de objetos

13. **Validação Incremental - Fase 5.3: Testes com Espelho Convexo (Visão do Robô)**
    * Após validação positiva das fases anteriores, transição para visão real do robô
    * Captura de fotos utilizando ESP32-S3 com espelho convexo
    * Simulação da perspectiva do robô em campo
    * Quantidade: 100-200 fotos em diferentes posições do robô
    * Variações:
      - Diferentes alturas do espelho
      - Diferentes ângulos de inclinação do espelho
      - Diferentes posições do robô no campo
      - Diferentes condições de iluminação
    * Validação:
      - Taxa de detecção em perspectiva de campo
      - Precisão das coordenadas com distorção do espelho convexo
      - Tempo de resposta comparado com fases anteriores
      - Robustez a variações de perspectiva
      - Análise de trade-off desempenho vs acurácia
    * Critério de sucesso: Taxa de detecção > 80%, latência < 200ms, acurácia de coordenadas aceitável
    * Objetivo: Validar sistema em condições reais de operação do robô

14. **Coleta de métricas quantitativas em todas as fases:**
    * Tempo de captura de imagem
    * Tempo de pré-processamento (conversão RGB → HSV)
    * Tempo de segmentação e detecção
    * Tempo de cálculo de coordenadas
    * Tempo total de resposta (end-to-end)
    * Taxa de quadros por segundo (FPS)
    * Precisão da detecção (taxa de acerto)
    * Precisão das coordenadas fornecidas (erro em cm)
    * Consumo de memória durante processamento
    * Comparação de desempenho entre diferentes perspectivas de visão

15. **Otimização de Desempenho vs Acurácia:**
    * Análise dos dados coletados nas 3 fases de validação
    * Identificação de gargalos de performance
    * Ajuste fino de parâmetros para equilíbrio:
      - Resolução de imagem vs latência
      - Complexidade do algoritmo vs acurácia
      - Técnicas de otimização (downsampling, ROI) vs precisão
    * Validação final do equilíbrio alcançado entre desempenho e acurácia
    * Documentação das trade-offs identificadas
    * Este projeto visa ter o equilíbrio entre desempenho e acurácia

16. **Testes adicionais em campo real:**
    * Diferentes distâncias (0.5m a 3m)
    * Diferentes ângulos de visão
    * Diferentes condições de iluminação (ambiente interno, externo, variações)
    * Presença de objetos laranjas similares (teste de falsos positivos)
    * Comportamento com oclusões parciais

**Fase 6: Documentação**
17. Redação da monografia com resultados, discussões e conclusões.  
 


## 2. **CONCEITOS TEÓRICOS / TRABALHOS RELACIONADOS** {#conceitos-teóricos-trabalhos-relacionados}

### 2.1 Visão Computacional Embarcada

Visão computacional embarcada refere-se ao processamento de imagens realizado diretamente em dispositivos com recursos limitados, sem dependência de servidores externos ou processamento na nuvem. Esta abordagem oferece vantagens significativas em aplicações de robótica: baixa latência, independência de conectividade, privacidade e eficiência energética.

### 2.2 Segmentação por Cor no Espaço HSV

O espaço de cores HSV (Hue, Saturation, Value) é particularmente adequado para segmentação de objetos por cor, pois separa a informação de cor (matiz) da intensidade luminosa. Esta característica torna a detecção mais robusta a variações de iluminação quando comparada ao espaço RGB tradicional.

**Componentes do HSV:**
- **Hue (Matiz)**: Representa a cor pura (0-360° ou 0-180 em implementações de 8 bits)
- **Saturation (Saturação)**: Intensidade da cor (0-255)
- **Value (Valor)**: Brilho/luminosidade (0-255)

**Vantagens para detecção de bola laranja:**
- Laranja possui faixa de matiz bem definida (aproximadamente 10-25°)
- Permite thresholding binário eficiente
- Menos sensível a variações de iluminação que RGB

### 2.3 Espelhos Catadióptricos para Visão Panorâmica

Espelhos convexos (catadióptricos) permitem ampliar significativamente o campo de visão de uma câmera, criando uma visão panorâmica ou até 360° quando combinados adequadamente. Esta técnica é amplamente utilizada em robótica para permitir que robôs "vejam" ao redor sem necessidade de múltiplas câmeras ou sistemas rotativos.

### 2.4 Processamento de Imagens em Microcontroladores

O processamento de imagens em microcontroladores requer otimizações específicas devido às limitações de memória e processamento. Técnicas comuns incluem:
- Redução de resolução (downsampling)
- Processamento de ROI (Region of Interest)
- Uso de operações inteiras em vez de ponto flutuante
- Otimizações SIMD quando disponíveis

### 2.5 Trabalhos Relacionados

* Abordagens de visão embarcada em competições RoboCup (Small Size League, RoboCup Junior)
* Trabalhos utilizando ESP32/ESP32-S3 em visão computacional
* Sistemas de detecção de objetos por cor em robótica móvel
* Técnicas de calibração de câmeras e transformação de coordenadas

## 3. **CRONOGRAMA** {#cronograma}

Cronograma de atividades para desenvolvimento do trabalho monográfico, incluindo o projeto (TCC I - 1º semestre) e a monografia (TCC II - 2º semestre) do ano letivo de 2025.

*Nota: As referências "(Met. item X)" indicam a correspondência com os itens numerados da seção de Metodologia (1.4.2), facilitando o rastreamento entre o cronograma e os procedimentos metodológicos detalhados.*

| Atividades | Jan | Fev | Mar | Abr | Mai | Jun | Jul | Ago | Set | Out | Nov | Dez |
|-----------|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| **1. Levantar literatura** | X | X | X | | | | | | | | | |
| **2. Elaborar Projeto (TCC I)** | | X | X | X | X | | | | | | | |
| **3. Fundamentação teórica** | | | X | X | | | | | | | | |
| **4. Montagem do hardware** | | | | | X | | | | | | | |
| **5. Desenvolvimento do algoritmo** | | | | | | X | X | | | | | |
| **6. Implementação da interface** | | | | | | | X | | | | | |
| **7. Testes e calibração** | | | | | | | | X | X | | | |
| **8. Sistema de medição de tempo (Met. item 10)** | | | | | | | | X | | | | | |
| **9. Validação incremental Fase 5.1 - Bola isolada (Met. item 11)** | | | | | | | | | X | | | | |
| **10. Validação incremental Fase 5.2 - Bola e gols (Met. item 12)** | | | | | | | | | X | | | | |
| **11. Validação incremental Fase 5.3 - Espelho convexo (Met. item 13)** | | | | | | | | | X | | | | |
| **12. Coleta de métricas e otimização (Met. itens 14-15)** | | | | | | | | | X | X | | | |
| **13. Testes adicionais em campo real (Met. item 16)** | | | | | | | | | | X | | | |
| **14. Análise de resultados** | | | | | | | | | | X | | |
| **15. Elaborar monografia (TCC II)** | | | | | | | | | | X | X | |
| **16. Revisar texto** | | | | | | | | | | | X | |
| **17. Preparar apresentação** | | | | | | | | | | | X | |
| **18. Entregar TCC I** | | | | | | **✓** | | | | | | |
| **19. Entregar TCC II** | | | | | | | | | | | **✓** | |
| **20. Defesa da monografia** | | | | | | | | | | | | **✓** |

**Marcos Críticos:**
- **30/Nov/2025**: Entrega do Projeto (TCC I)
- **30/Jun/2026**: Entrega da Monografia (TCC II)
- **15/Jul/2026**: Defesa da Monografia

## 4. **REFERÊNCIAS** {#referências}

*Nota: As referências devem ser formatadas segundo normas ABNT. Abaixo estão listadas fontes relevantes que devem ser consultadas e referenciadas adequadamente.*

**Documentação Técnica:**
- ESPRESSIF SYSTEMS. ESP32-S3 Series Datasheet. Disponível em: <https://www.espressif.com/sites/default/files/documentation/esp32-s3_datasheet_en.pdf>
- ESPRESSIF SYSTEMS. ESP32-S3 Camera API Documentation. Disponível em: <https://docs.espressif.com/projects/esp-idf/en/latest/esp32s3/api-reference/peripherals/camera.html>

**Visão Computacional e Segmentação por Cor:**
- BRADSKI, G.; KAEHLER, A. Learning OpenCV: Computer Vision with the OpenCV Library. O'Reilly Media, 2008.
- GONZALEZ, R. C.; WOODS, R. E. Digital Image Processing. 4ª ed. Pearson, 2018.

**RoboCup e Robótica Autônoma:**
- KITANO, H. et al. RoboCup: The Robot World Cup Initiative. In: Proceedings of the First International Conference on Autonomous Agents, 1997.
- SSL RoboCup. Small Size League Official Website. Disponível em: <https://ssl.robocup.org/>

**Visão Embarcada e ESP32:**
- Artigos e tutoriais sobre ESP32-CAM e processamento de imagens embarcado
- Documentação de projetos open-source de robótica com ESP32

*Nota: Esta lista será expandida durante a pesquisa bibliográfica sistemática, com todas as referências formatadas segundo normas ABNT.*

## **APÊNDICES** {#apêndices}

### Apêndice A - Termo de Aceite do Orientador

[Incluir cópia do Termo de Aceite assinado pelo orientador]

### Apêndice B - Especificações Técnicas do Hardware

[Incluir quando disponível: especificações detalhadas dos componentes, diagramas de conexão]

### Apêndice C - Código-Fonte do Algoritmo

[Incluir código-fonte principal do algoritmo de detecção, se aplicável]

### Apêndice D - Resultados Experimentais Detalhados

[Incluir tabelas e gráficos detalhados dos testes realizados]