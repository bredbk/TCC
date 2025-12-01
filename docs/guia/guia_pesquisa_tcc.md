# Guia de Pesquisa - TCC
## Sistema de Visão Computacional Embarcado para Robótica Autônoma de Baixo Custo

---

## 📋 Resumo do Projeto

**Aluno**: Brendon Sousa Lima  
**Orientador**: Prof. Andrique Figueirêdo Amorim  
**Instituição**: IFBA - Campus Vitória da Conquista  
**Curso**: Bacharelado em Sistemas de Informação  
**Ano**: 2025

**Tema Central**: Desenvolvimento de um sistema de visão computacional embarcado utilizando ESP32-S3 para robótica autônoma aplicada ao futebol de robôs, com foco em TinyML e Edge AI.

---

## 🎯 Áreas Principais de Pesquisa

### 1. TinyML (Tiny Machine Learning)

#### O que é?
- **TinyML** é a área que trabalha com implementação de modelos de Machine Learning em dispositivos minúsculos com recursos limitados (microcontroladores)
- Foca em "espremer" modelos para operar em dispositivos com centenas de KB de memória
- Permite IA em dispositivos IoT sem dependência da nuvem

#### Conceitos-chave para pesquisar:
- [ ] Quantização de modelos
- [ ] Otimização de memória de ativação
- [ ] TensorFlow Lite for Microcontrollers
- [ ] Edge Impulse
- [ ] Frameworks: TensorFlow Lite Micro, TinyML Kit
- [ ] Comparação: MobileNets vs modelos otimizados para MCU
- [ ] Co-design: hardware + software

#### Perguntas de pesquisa:
1. Quais são as principais restrições ao executar ML em microcontroladores?
2. Como a memória de ativação impacta mais que o número de parâmetros?
3. Quais técnicas de quantização são mais eficientes para o ESP32-S3?
4. Como medir o desempenho (latência, precisão, consumo energético)?

#### Referências para buscar:
- TinyML Foundation
- Papers sobre TinyML em conferências (MLSys, NeurIPS, ICML)
- Livro: "TinyML: Machine Learning with TensorFlow Lite"
- Exemplos de projetos TinyML no GitHub

---

### 2. Edge AI (Inteligência Artificial na Borda)

#### O que é?
- Processamento de IA localmente no dispositivo, não na nuvem
- Vantagens: baixa latência, privacidade, independência de conectividade
- Essencial para aplicações em tempo real

#### Conceitos-chave para pesquisar:
- [ ] Edge Computing vs Cloud Computing
- [ ] Inferência local vs remota
- [ ] Benefícios: latência, privacidade, largura de banda
- [ ] Casos de uso: veículos autônomos, robótica, IoT
- [ ] Hardware accelerators (Neural Network Accelerators)

#### Perguntas de pesquisa:
1. Quais são os trade-offs entre Edge AI e Cloud AI?
2. Como medir a latência em sistemas de tempo real?
3. Quais métricas são importantes para Edge AI?
4. Comparação de consumo energético: local vs nuvem

---

### 3. ESP32-S3

#### O que é?
- Microcontrolador da Espressif com suporte a IA
- Possui aceleradores de hardware para processamento de imagens
- Ideal para aplicações de visão computacional embarcada

#### Especificações para pesquisar:
- [ ] Arquitetura do ESP32-S3
- [ ] Memória disponível (RAM, Flash)
- [ ] Clock speed e capacidade de processamento
- [ ] Suporte a câmera (interface, resoluções)
- [ ] Bibliotecas disponíveis (ESP-IDF, Arduino)
- [ ] Frameworks de IA suportados
- [ ] Comparação com outros MCUs (STM32, Arduino, Raspberry Pi Pico)

#### Projetos de referência:
- [ ] ESP32-CAM projects
- [ ] ESP-WHO (framework de reconhecimento facial)
- [ ] ESP-DL (Deep Learning library)
- [ ] Projetos de detecção de objetos com ESP32

---

### 4. Visão Computacional Embarcada

#### O que é?
- Processamento de imagens e vídeo diretamente no dispositivo
- Desafios: recursos limitados, tempo real, iluminação variável
- Aplicações: detecção de objetos, rastreamento, reconhecimento

#### Conceitos-chave para pesquisar:
- [ ] Detecção de objetos (YOLO, SSD, MobileNet-SSD)
- [ ] Rastreamento de objetos (tracking algorithms)
- [ ] Processamento de imagem em tempo real
- [ ] Técnicas de otimização (downsampling, ROI)
- [ ] Algoritmos de visão computacional leves
- [ ] Color space (RGB, HSV) para detecção

#### Técnicas específicas para futebol de robôs:
- [ ] Detecção de bola colorida
- [ ] Estimativa de distância
- [ ] Correção de perspectiva
- [ ] Lidar com movimento rápido (motion blur)
- [ ] Iluminação variável

#### Perguntas de pesquisa:
1. Qual algoritmo de detecção é mais adequado para ESP32-S3?
2. Como otimizar o pipeline de visão para tempo real?
3. Quais técnicas de pré-processamento reduzem a carga computacional?
4. Como lidar com oclusões e reflexos?

---

### 5. Robótica Autônoma

#### O que é?
- Robôs capazes de operar sem controle humano
- Tomam decisões baseadas em sensores e algoritmos
- Aplicação: futebol de robôs

#### Conceitos-chave para pesquisar:
- [ ] Arquitetura de controle de robôs
- [ ] Sensoriamento e atuação
- [ ] Planejamento de trajetória
- [ ] Controle de movimento (motores, encoders)
- [ ] Fusão de sensores (sensor fusion)
- [ ] Closed-loop control

#### Componentes do sistema:
1. **Percepção** (visão computacional)
2. **Planejamento** (algoritmos de decisão)
3. **Atuação** (controle de motores)

---

### 6. RoboCup e Futebol de Robôs

#### O que é?
- Competição internacional de robótica
- Diferentes categorias (Small Size, Middle Size, Humanoid)
- Benchmark para pesquisa em IA e robótica

#### Tópicos para pesquisar:
- [ ] RoboCup Small Size League (SSL)
- [ ] Diferença entre visão centralizada vs embarcada
- [ ] Regras e desafios técnicos
- [ ] Papers de times participantes
- [ ] Arquiteturas de sistema utilizadas
- [ ] Estratégias de controle e navegação

#### Visão Embarcada vs Centralizada:
- **Centralizada**: Câmera externa, visão global, processamento externo
- **Embarcada**: Câmera no robô, visão local, autonomia completa

#### Perguntas de pesquisa:
1. Quais são as vantagens da visão embarcada?
2. Quais são os desafios específicos?
3. Como times da RoboCup resolvem o problema de detecção?
4. Qual a latência aceitável para controle em tempo real?

---

## 📚 Recursos de Pesquisa Recomendados

### Bases de Dados Acadêmicas
- [ ] IEEE Xplore
- [ ] Google Scholar
- [ ] ACM Digital Library
- [ ] arXiv (especialmente cs.RO, cs.CV)
- [ ] ScienceDirect

### Palavras-chave para busca:
```
- "TinyML microcontroller vision"
- "Edge AI embedded systems"
- "ESP32 computer vision"
- "RoboCup vision system"
- "autonomous robot soccer"
- "embedded object detection"
- "real-time vision MCU"
- "TensorFlow Lite Micro"
- "mobile robot vision"
- "low-cost robot vision"
```

### Conferências Relevantes
- [ ] RoboCup Symposium
- [ ] IROS (International Conference on Intelligent Robots and Systems)
- [ ] ICRA (International Conference on Robotics and Automation)
- [ ] CVPR (Computer Vision and Pattern Recognition)
- [ ] MLSys (Machine Learning and Systems)
- [ ] TinyML Summit

### Journals
- [ ] IEEE Transactions on Robotics
- [ ] Robotics and Autonomous Systems
- [ ] Journal of Intelligent & Robotic Systems
- [ ] IEEE Transactions on Industrial Electronics

---

## 🛠️ Ferramentas e Plataformas

### Desenvolvimento
- [ ] **ESP-IDF**: Framework oficial do ESP32
- [ ] **Arduino IDE**: Para prototipagem rápida
- [ ] **PlatformIO**: IDE avançada para embedded

### Machine Learning
- [ ] **TensorFlow Lite Micro**: Para inferência em MCU
- [ ] **Edge Impulse**: Plataforma TinyML
- [ ] **Google Colab**: Para treinar modelos
- [ ] **PyTorch**: Framework ML alternativo

### Visão Computacional
- [ ] **OpenCV**: Biblioteca de visão computacional
- [ ] **OpenMV**: Câmera e IDE para visão embarcada
- [ ] **ESP-WHO**: Framework de visão da Espressif

### Simulação
- [ ] **Webots**: Simulador de robótica
- [ ] **Gazebo**: Simulador 3D
- [ ] **V-REP/CoppeliaSim**: Simulador robótico

---

## 📊 Metodologia Sugerida

### Fase 1: Revisão Bibliográfica (4-6 semanas)
- [ ] Ler papers fundamentais sobre TinyML
- [ ] Estudar arquitetura do ESP32-S3
- [ ] Analisar trabalhos sobre RoboCup
- [ ] Revisar técnicas de visão computacional embarcada

### Fase 2: Experimentação Inicial (4-6 semanas)
- [ ] Configurar ambiente de desenvolvimento
- [ ] Testar exemplos básicos com ESP32-S3
- [ ] Implementar detecção simples de objetos
- [ ] Medir métricas de desempenho

### Fase 3: Desenvolvimento do Sistema (8-10 semanas)
- [ ] Treinar modelo de detecção de bola
- [ ] Otimizar modelo para ESP32-S3
- [ ] Integrar com sistema de controle do robô
- [ ] Testes em ambiente real

### Fase 4: Análise e Documentação (4-6 semanas)
- [ ] Avaliar resultados
- [ ] Comparar com trabalhos relacionados
- [ ] Escrever TCC
- [ ] Preparar apresentação

---

## 🎯 Objetivos do TCC (baseado na súmula)

### Objetivo Geral
Desenvolver um sistema de visão computacional embarcado de baixo custo para robótica autônoma aplicada ao futebol de robôs.

### Objetivos Específicos (possíveis)
1. Implementar modelo TinyML para detecção de objetos no ESP32-S3
2. Otimizar o pipeline de visão para tempo real (baixa latência)
3. Integrar o sistema de visão com controle do robô
4. Avaliar desempenho (precisão, latência, consumo energético)
5. Comparar visão embarcada vs centralizada no contexto da RoboCup

---

## 💡 Contribuições Esperadas

1. **Técnica**: Sistema funcional de visão embarcada para robótica de baixo custo
2. **Científica**: Análise comparativa de técnicas TinyML para visão em MCU
3. **Prática**: Solução acessível para times de robótica educacional
4. **Metodológica**: Framework para desenvolvimento de sistemas similares

---

## 📝 Estrutura Sugerida do TCC

### 1. Introdução
- Contextualização (Edge AI, TinyML, Robótica)
- Problema de pesquisa
- Justificativa
- Objetivos
- Estrutura do trabalho

### 2. Fundamentação Teórica
- 2.1 TinyML e Edge AI
- 2.2 Visão Computacional Embarcada
- 2.3 Arquitetura ESP32-S3
- 2.4 Robótica Autônoma e Futebol de Robôs
- 2.5 Trabalhos Relacionados

### 3. Metodologia
- 3.1 Arquitetura do Sistema
- 3.2 Hardware Utilizado
- 3.3 Treinamento do Modelo
- 3.4 Otimização para ESP32-S3
- 3.5 Métricas de Avaliação

### 4. Desenvolvimento
- 4.1 Implementação do Sistema de Visão
- 4.2 Integração com Robô
- 4.3 Testes e Ajustes

### 5. Resultados e Discussão
- 5.1 Análise de Desempenho
- 5.2 Comparação com Trabalhos Relacionados
- 5.3 Limitações

### 6. Conclusão
- Síntese dos resultados
- Contribuições
- Trabalhos futuros

### Referências

### Apêndices
- Código-fonte
- Diagramas
- Dados dos experimentos

---

## ✅ Checklist de Ações Imediatas

### Esta Semana
- [ ] Fazer cadastro no IEEE Xplore e Google Scholar
- [ ] Buscar 10-15 papers fundamentais sobre TinyML
- [ ] Ler documentação oficial do ESP32-S3
- [ ] Assistir tutoriais sobre TensorFlow Lite Micro
- [ ] Configurar ambiente de desenvolvimento (ESP-IDF ou Arduino)

### Próximas 2 Semanas
- [ ] Ler e fichamentar os papers encontrados
- [ ] Testar exemplos básicos de visão com ESP32-CAM
- [ ] Criar documento com revisão bibliográfica inicial
- [ ] Definir especificações técnicas do robô
- [ ] Reunião com orientador para validar escopo

### Próximo Mês
- [ ] Finalizar revisão bibliográfica
- [ ] Adquirir componentes necessários (ESP32-S3, câmera, chassis)
- [ ] Implementar primeiro protótipo de detecção
- [ ] Documentar arquitetura do sistema
- [ ] Preparar apresentação de andamento

---

## 📞 Contatos Úteis

### Comunidades Online
- **Reddit**: r/tinyml, r/esp32, r/robotics
- **Discord**: TinyML Discord, ESP32 Community
- **Fóruns**: ESP32 Forum, RoboCup Forums
- **GitHub**: Procurar repositórios relevantes

### Grupos de Pesquisa
- Buscar grupos de robótica no IFBA
- Contatar times brasileiros da RoboCup
- Participar de eventos de robótica regional

---

## 🎓 Dicas Finais

1. **Organize suas referências desde o início** (use Zotero ou Mendeley)
2. **Faça anotações detalhadas** de cada paper lido
3. **Documente todos os experimentos** (caderno de laboratório)
4. **Mantenha código no GitHub** (versionamento)
5. **Reuniões regulares com orientador** (quinzenais recomendado)
6. **Participe de grupos de estudo** de TCC
7. **Comece a escrever cedo** (não deixe para o final)
8. **Teste frequentemente** (desenvolvimento incremental)

---

**Última atualização**: Novembro de 2024  
**Próxima revisão**: Adicionar referências específicas encontradas

