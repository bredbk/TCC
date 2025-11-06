# TEMPLATE - PROJETO DE PESQUISA
## Conforme Modelo IFBA

---

**INSTITUTO FEDERAL DE EDUCAÇÃO, CIÊNCIA E TECNOLOGIA DA BAHIA**  
**CAMPUS VITÓRIA DA CONQUISTA**  
**BACHARELADO EM SISTEMAS DE INFORMAÇÃO**

---

# SISTEMA DE VISÃO COMPUTACIONAL EMBARCADO PARA ROBÓTICA AUTÔNOMA DE BAIXO CUSTO

**Brendon Sousa Lima**

Pré-projeto de pesquisa desenvolvido na linha de pesquisa de desenvolvimento de sistemas embarcados, sob orientação do(a) Prof(ª). Andrique Figueirêdo Amorim, como requisito de inscrição no componente curricular de Trabalho de Conclusão de Curso I, do Curso de Bacharelado em Sistemas de Informação, do Instituto Federal de Educação, Ciência e Tecnologia da Bahia, Campus Vitória da Conquista.

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

---

## 1. INTRODUÇÃO

### 1.1. Contextualização

A inteligência artificial tem se expandido para além dos servidores de alta potência e ambientes de nuvem, atingindo a fronteira dos dispositivos. Esse movimento é conhecido como Edge AI e tem sido impulsionado pela necessidade de processamento local de dados para aplicações que exigem baixa latência, alta privacidade e eficiência energética (WARDEN; SITUNAYAKE, 2019).

Nesse contexto, a disciplina do Tiny Machine Learning (TinyML) surge como uma nova fronteira, focada em implementar modelos de aprendizado de máquina em dispositivos diminutos, como microcontroladores (MCUs), que possuem apenas algumas centenas de kilobytes de memória (LIN et al., 2020).

### 1.2. Problema de Pesquisa

A robótica autônoma, especialmente em ambientes dinâmicos e imprevisíveis como um campo de futebol, representa um desafio complexo e relevante no avanço da inteligência artificial. Uma distinção fundamental na pesquisa em robótica de futebol é a arquitetura do sistema de visão: centralizada versus embarcada.

Ligas tradicionais como a RoboCup SSL utilizam frequentemente um sistema de visão centralizado, externo ao campo. Em contraste, a visão embarcada, onde o próprio robô é responsável por sua percepção, enfrenta desafios mais significativos: campo de visão limitado, movimentos bruscos, tremores e iluminação variável.

**Questão de Pesquisa**: Como desenvolver um sistema de visão computacional embarcado de baixo custo, utilizando TinyML em microcontroladores ESP32-S3, capaz de operar em tempo real para aplicações de robótica autônoma?

### 1.3. Delimitação do Tema

Este trabalho se concentra em:
- Desenvolvimento de sistema de visão embarcado (on-board)
- Plataforma: Microcontrolador ESP32-S3
- Técnica: TinyML (Tiny Machine Learning)
- Aplicação: Robótica autônoma para futebol de robôs
- Restrições: Baixo custo (< R$ 200,00), tempo real (< 100ms)

---

## 2. JUSTIFICATIVA

### 2.1. Relevância Científica

O trabalho contribui para o avanço do conhecimento em TinyML aplicado à visão computacional embarcada, uma área em crescimento. A pesquisa em sistemas de baixo custo e alta eficiência é fundamental para democratizar a robótica autônoma.

### 2.2. Relevância Tecnológica

O desenvolvimento de soluções de visão embarcada em dispositivos de recursos limitados representa um avanço tecnológico significativo, permitindo:
- Independência de infraestrutura externa
- Redução de latência
- Aumento da privacidade dos dados
- Operação offline

### 2.3. Relevância Social e Educacional

Soluções de baixo custo são essenciais para:
- Acesso de instituições de ensino à tecnologia de ponta
- Formação de estudantes em robótica e IA
- Democratização do conhecimento
- Incentivo à pesquisa e inovação

### 2.4. Aplicabilidade

O sistema desenvolvido poderá ser aplicado em:
- Times de robótica educacionais
- Competições de futebol de robôs
- Pesquisas futuras em visão embarcada
- Base para outros projetos de robótica autônoma

---

## 3. OBJETIVOS

### 3.1. Objetivo Geral

Desenvolver um sistema de visão computacional embarcado de baixo custo para robótica autônoma, utilizando TinyML no microcontrolador ESP32-S3, aplicado ao contexto de futebol de robôs.

### 3.2. Objetivos Específicos

1. **Realizar revisão bibliográfica** abrangente sobre TinyML, Edge AI, visão computacional embarcada e robótica autônoma

2. **Implementar modelo de machine learning otimizado** para detecção de objetos (bola) em microcontroladores com recursos limitados

3. **Desenvolver pipeline de visão computacional** eficiente, incluindo captura, pré-processamento, inferência e pós-processamento de imagens

4. **Integrar sistema de visão com controle de movimento** do robô, permitindo navegação autônoma baseada em visão

5. **Avaliar desempenho do sistema** em termos de:
   - Precisão de detecção
   - Latência de processamento
   - Taxa de quadros por segundo (FPS)
   - Consumo energético
   - Robustez em diferentes condições

6. **Comparar abordagem embarcada com sistemas centralizados**, identificando vantagens, desvantagens e trade-offs

7. **Documentar solução** de forma a permitir replicação e extensão por outros pesquisadores

---

## 4. REFERENCIAL TEÓRICO

### 4.1. TinyML (Tiny Machine Learning)

TinyML refere-se à implementação de modelos de machine learning em dispositivos embarcados com recursos extremamente limitados, tipicamente microcontroladores com menos de 1 MB de memória (WARDEN; SITUNAYAKE, 2019).

**Características principais:**
- Modelos com poucos kilobytes
- Inferência em milissegundos
- Consumo energético mínimo
- Processamento local (edge)

**Frameworks principais:**
- TensorFlow Lite Micro
- Edge Impulse
- Arduino TinyML

### 4.2. Edge AI

Edge AI refere-se ao processamento de algoritmos de inteligência artificial localmente, no dispositivo, sem necessidade de conexão com servidores remotos (CHEN; RAN, 2019).

**Vantagens:**
- Baixa latência
- Privacidade dos dados
- Independência de conectividade
- Redução de custos de banda

### 4.3. ESP32-S3

O ESP32-S3 é um microcontrolador da Espressif Systems com suporte específico para aplicações de IA (ESPRESSIF, 2021).

**Especificações relevantes:**
- Dual-core Xtensa LX7 @ 240 MHz
- 512 KB SRAM
- Interface para câmera
- Aceleradores de hardware para processamento de imagem
- WiFi e Bluetooth integrados

### 4.4. Visão Computacional Embarcada

Visão computacional em sistemas embarcados enfrenta desafios únicos devido às restrições de recursos (BONARDI et al., 2015).

**Técnicas comuns:**
- Detecção baseada em cor (HSV)
- Redes neurais convolucionais leves (MobileNet, EfficientNet)
- Quantização de modelos
- Otimização de pipeline

### 4.5. RoboCup e Futebol de Robôs

A RoboCup é uma competição internacional que serve como benchmark para pesquisa em robótica e inteligência artificial (KITANO et al., 1997).

**Categorias principais:**
- Small Size League (SSL) - visão centralizada
- Middle Size League (MSL) - visão embarcada
- Humanoid League

### 4.6. Trabalhos Relacionados

**Modelo MCUNet (LIN et al., 2020):**
- Estado da arte em TinyML
- Co-design de modelo e hardware
- Resultados em ImageNet com MCUs

**Sistemas de Visão para RoboCup (BROWNING et al., 2019):**
- Revisão de arquiteturas
- Comparação centralizada vs embarcada
- Desafios de tempo real

**[Adicionar mais trabalhos conforme revisão bibliográfica]**

---

## 5. METODOLOGIA

### 5.1. Tipo de Pesquisa

Esta pesquisa caracteriza-se como:
- **Quanto à natureza**: Aplicada
- **Quanto aos objetivos**: Exploratória e Experimental
- **Quanto à abordagem**: Quali-quantitativa
- **Quanto aos procedimentos**: Experimental, Bibliográfica e Documental

### 5.2. Etapas da Pesquisa

#### Etapa 1: Revisão Bibliográfica (Meses 1-3)
- Busca sistemática em bases de dados (IEEE, ACM, Google Scholar)
- Fichamento de papers fundamentais
- Identificação do estado da arte
- Análise de trabalhos relacionados

**Produtos**: Capítulo de fundamentação teórica

#### Etapa 2: Especificação do Sistema (Mês 4)
- Definição da arquitetura do sistema
- Especificação de requisitos funcionais e não-funcionais
- Seleção de componentes de hardware
- Planejamento de experimentos

**Produtos**: Documento de especificação, diagramas

#### Etapa 3: Desenvolvimento do Modelo de ML (Meses 5-7)
1. **Coleta de dados**:
   - Captura de 500-1000 imagens de bolas em diferentes condições
   - Anotação de imagens (bounding boxes)
   - Divisão em train/val/test (70/15/15)

2. **Treinamento**:
   - Arquitetura base: MobileNetV2 ou modelo custom
   - Treinamento no Google Colab
   - Data augmentation
   - Validação cruzada

3. **Otimização**:
   - Quantização post-training
   - Conversão para TensorFlow Lite
   - Otimização de memória de ativação

**Produtos**: Modelo treinado e otimizado (.tflite)

#### Etapa 4: Implementação no ESP32-S3 (Meses 8-9)
1. **Configuração do hardware**:
   - Montagem do circuito
   - Instalação de câmera
   - Testes de captura

2. **Implementação do software**:
   - Pipeline de visão (captura → pré-proc → inferência → pós-proc)
   - Integração com TFLite Micro
   - Otimização de código

3. **Integração com robô**:
   - Controle de motores
   - Lógica de navegação
   - Sistema completo funcionando

**Produtos**: Sistema embarcado funcional

#### Etapa 5: Testes e Avaliação (Mês 10)
**Métricas quantitativas**:
- Precisão, Recall, F1-Score
- Latência média, máxima, mínima
- FPS (frames per second)
- Consumo de memória (RAM, Flash)
- Consumo energético (mAh)

**Testes qualitativos**:
- Robustez a diferentes iluminações
- Desempenho com oclusões
- Comportamento em movimento

**Cenários de teste**:
1. Ambiente controlado
2. Iluminação variável
3. Movimento do robô
4. Múltiplos objetos

**Produtos**: Dados de experimentos, análises estatísticas

#### Etapa 6: Documentação e Escrita (Meses 11-12)
- Escrita do TCC final
- Análise de resultados
- Comparação com trabalhos relacionados
- Conclusões e trabalhos futuros
- Preparação da apresentação

**Produtos**: TCC completo, apresentação

### 5.3. Materiais e Equipamentos

#### Hardware
| Item | Descrição | Qtd | Valor Unit. | Valor Total |
|------|-----------|-----|-------------|-------------|
| ESP32-S3 DevKit | Microcontrolador principal | 2 | R$ 60,00 | R$ 120,00 |
| Câmera OV2640 | Módulo de câmera | 2 | R$ 25,00 | R$ 50,00 |
| Chassis robótico | Base, rodas, estrutura | 1 | R$ 80,00 | R$ 80,00 |
| Motores DC | Com encoders | 2 | R$ 20,00 | R$ 40,00 |
| Driver L298N | Controle de motores | 1 | R$ 15,00 | R$ 15,00 |
| Bateria LiPo | 7.4V 2200mAh | 1 | R$ 50,00 | R$ 50,00 |
| Componentes diversos | Jumpers, protoboard, etc | - | - | R$ 45,00 |
| **TOTAL** | | | | **R$ 400,00** |

#### Software (Gratuito)
- ESP-IDF / Arduino IDE
- Python + TensorFlow
- Google Colab
- Visual Studio Code + PlatformIO
- OpenCV
- Zotero

#### Infraestrutura
- Laboratório de robótica (IFBA)
- Computador para desenvolvimento
- Espaço para testes

### 5.4. Análise de Dados

Os dados coletados serão analisados utilizando:
- **Estatística descritiva**: Média, desvio padrão, mediana
- **Visualização**: Gráficos de desempenho, curvas ROC, matriz de confusão
- **Comparação**: Testes estatísticos (t-test) quando aplicável
- **Análise qualitativa**: Observação do comportamento do robô

---

## 6. CRONOGRAMA

### Ano 2025 - TCC I e TCC II

| Atividade | Jan | Fev | Mar | Abr | Mai | Jun | Jul | Ago | Set | Out | Nov | Dez |
|-----------|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| 1. Revisão bibliográfica | ✓ | ✓ | ✓ | | | | | | | | | |
| 2. Fundamentação teórica | | ✓ | ✓ | ✓ | | | | | | | | |
| 3. Especificação do sistema | | | | ✓ | | | | | | | | |
| 4. Coleta de dados | | | | | ✓ | | | | | | | |
| 5. Treinamento do modelo | | | | | ✓ | ✓ | ✓ | | | | | |
| 6. Implementação ESP32 | | | | | | ✓ | ✓ | ✓ | | | | |
| 7. Integração com robô | | | | | | | | ✓ | ✓ | | | |
| 8. Testes e avaliação | | | | | | | | | ✓ | ✓ | | |
| 9. Análise de resultados | | | | | | | | | | ✓ | ✓ | |
| 10. Escrita do TCC | | | | | ✓ | ✓ | | | | ✓ | ✓ | ✓ |
| 11. Entrega TCC I | | | | | | ✓ | | | | | | |
| 12. Revisão final | | | | | | | | | | | ✓ | |
| 13. Entrega TCC II | | | | | | | | | | | ✓ | |
| 14. Defesa | | | | | | | | | | | | ✓ |

**Marcos importantes:**
- **Junho/2025**: Entrega do TCC I
- **Novembro/2025**: Entrega do TCC II
- **Dezembro/2025**: Defesa do TCC

---

## 7. RECURSOS NECESSÁRIOS

### 7.1. Recursos Humanos
- Orientador: Prof. Andrique Figueirêdo Amorim
- Aluno pesquisador: Brendon Sousa Lima
- Colaboradores: Possível suporte de técnicos de laboratório

### 7.2. Recursos Materiais
Conforme tabela na seção 5.3 (Materiais e Equipamentos)

**Total estimado**: R$ 400,00

**Fonte de financiamento**: Recursos próprios / Possível solicitação ao IFBA

### 7.3. Recursos Computacionais
- Computador pessoal para desenvolvimento
- Google Colab (gratuito) para treinamento de modelos
- Laboratório de informática do IFBA

### 7.4. Infraestrutura
- Laboratório de robótica (IFBA)
- Acesso à biblioteca (física e digital)
- Acesso à internet
- Espaço para testes do robô

---

## 8. REFERÊNCIAS

BROWNING, B. et al. **RoboCup Small Size League: Past, Present and Future**. In: RoboCup Symposium, 2019.

CHEN, J.; RAN, X. **Deep Learning with Edge Computing: A Review**. Proceedings of the IEEE, v. 107, n. 8, p. 1655-1674, 2019.

ESPRESSIF SYSTEMS. **ESP32-S3 Technical Reference Manual**. Version 1.0. Shanghai: Espressif Systems, 2021.

KITANO, H. et al. **RoboCup: The Robot World Cup Initiative**. In: Proceedings of the First International Conference on Autonomous Agents, p. 340-347, 1997.

LIN, J. et al. **MCUNet: Tiny Deep Learning on IoT Devices**. In: Conference on Neural Information Processing Systems (NeurIPS), 2020.

WARDEN, P.; SITUNAYAKE, D. **TinyML: Machine Learning with TensorFlow Lite on Arduino and Ultra-Low-Power Microcontrollers**. O'Reilly Media, 2019.

**[Adicionar mais referências conforme desenvolvimento da revisão bibliográfica]**

---

## APÊNDICES

### Apêndice A - Termo de Aceite do Orientador
[Incluir termo assinado]

### Apêndice B - Cronograma Detalhado
[Incluir cronograma expandido se necessário]

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

