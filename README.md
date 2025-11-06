# TCC - Sistema de Visão Computacional Embarcado para Robótica Autônoma

**Aluno**: Brendon Sousa Lima  
**Orientador**: Prof. Andrique Figueirêdo Amorim  
**Instituição**: IFBA - Campus Vitória da Conquista  
**Curso**: Bacharelado em Sistemas de Informação  
**Ano**: 2025

---

## 🚀 NOVO NO PROJETO? 

**👉 Comece por aqui: [COMECE_AQUI.md](COMECE_AQUI.md)**

Este documento contém todas as primeiras ações que você deve tomar para começar seu TCC da forma correta!

---

## 📋 Sobre o Projeto

Este repositório contém todos os materiais relacionados ao desenvolvimento do Trabalho de Conclusão de Curso focado em **visão computacional embarcada** utilizando **TinyML** para **robótica autônoma de baixo custo** aplicada ao futebol de robôs.

### Tema
**Sistema de Visão Computacional Embarcado para Robótica Autônoma de Baixo Custo**

### Resumo
O projeto visa desenvolver um sistema de visão computacional que opera diretamente em microcontroladores (ESP32-S3), permitindo que robôs autônomos detectem e rastreiem objetos em tempo real sem depender de processamento em nuvem ou sistemas externos. A aplicação prática é o futebol de robôs, onde o robô precisa identificar e seguir uma bola de forma autônoma.

---

## 🎯 Objetivos

### Objetivo Geral
Desenvolver um sistema de visão computacional embarcado de baixo custo para robótica autônoma aplicada ao futebol de robôs, utilizando TinyML no microcontrolador ESP32-S3.

### Objetivos Específicos
1. Implementar um modelo de machine learning otimizado para detecção de objetos em microcontroladores
2. Otimizar o pipeline de visão computacional para operação em tempo real com recursos limitados
3. Integrar o sistema de visão com o controle de movimento do robô
4. Avaliar o desempenho do sistema em termos de precisão, latência e consumo energético
5. Comparar visão embarcada vs centralizada no contexto da RoboCup

---

## 📚 Documentação do Projeto

### 📖 Documentos Principais

#### 1. **[sumula.md](sumula.md)**
Súmula oficial do projeto de pesquisa com:
- Introdução e contextualização
- Fundamentação teórica inicial
- Descrição do problema de pesquisa

#### 2. **[guia_pesquisa_tcc.md](guia_pesquisa_tcc.md)** ⭐
Guia completo de pesquisa contendo:
- Áreas principais de estudo (TinyML, Edge AI, Visão Computacional)
- Recursos recomendados
- Metodologia sugerida
- Estrutura do TCC
- Checklist de ações

#### 3. **[papers_recomendados.md](papers_recomendados.md)**
Lista curada de papers e referências:
- Papers fundamentais sobre TinyML
- Visão computacional embarcada
- RoboCup e futebol de robôs
- ESP32 e hardware
- Tutoriais e cursos online

#### 4. **[cronograma_tcc.md](cronograma_tcc.md)** 📅
Cronograma detalhado mês a mês:
- TCC I (Janeiro-Junho 2025)
- TCC II (Julho-Dezembro 2025)
- Marcos críticos
- Checklist semanal

#### 5. **[conceitos_tecnicos_explicados.md](conceitos_tecnicos_explicados.md)** 💡
Explicações didáticas dos conceitos técnicos:
- TinyML e Quantização
- Edge AI vs Cloud AI
- Visão Computacional
- ESP32-S3
- RoboCup
- Métricas de avaliação

#### 6. **[analise_arquiteturas_robocup/](analise_arquiteturas_robocup/)** 🏗️ ⭐ **NOVO!**
Análises detalhadas de arquiteturas de robôs de competições RoboCup:
- **6 análises completas** de times reais de competição
- **Comparação de arquiteturas** (distribuída vs centralizada)
- **Análise de viabilidade** do ESP32 como alternativa de baixo custo
- **Prova real** de uso de ESP32 em robótica (Munako Aegis)
- **Recomendações específicas** para seu TCC
- **Análise de custos** detalhada (economia de 80-90%)

**Arquivos principais**:
- `README.md` - Índice completo e resumo executivo
- `05_analise_munako_aegis.md` - ⭐ **MUITO RELEVANTE**: Prova real de ESP32
- `03_analise_arquitetura_distribuida.md` - Análise de arquiteturas
- Outras 4 análises de times de competição

#### 7. **[analise_viabilidade_haar_cascade_esp32s3.md](analise_viabilidade_haar_cascade_esp32s3.md)** 🔍 ⭐ **NOVO!**
Análise crítica de viabilidade técnica:
- **Comparação**: Detecção de cores vs Haar Cascade no ESP32-S3
- **Análise do artigo**: "Color Detection & Tracking with ESP32-CAM & OpenCV"
- **Benchmarks de performance**: Latência, consumo de memória, FPS
- **Recomendação técnica**: Detecção de cores otimizada é mais eficiente
- **Código de exemplo**: Implementação otimizada para ESP32-S3
- **Trade-offs detalhados**: Quando usar cada abordagem

**Conclusão principal**: Para detecção de bola laranja, **detecção de cores é 5-10x mais rápida** que Haar Cascade, com consumo 4-8x menor de memória.

#### 8. **[analise_pytorch_vs_tensorflow_esp32.md](analise_pytorch_vs_tensorflow_esp32.md)** 🤖 ⭐ **NOVO!**
Análise comparativa de frameworks de ML:
- **Comparação**: PyTorch vs TensorFlow Lite Micro para ESP32-S3
- **Viabilidade técnica**: Suporte nativo, otimizações, ecossistema
- **Rota alternativa**: ESP-DL com conversão PyTorch → ONNX → ESP-DL
- **Recomendação técnica**: TensorFlow Lite Micro é a escolha clara
- **Workflow recomendado**: Treinar → Converter → Deploy
- **Alternativas**: Edge Impulse como plataforma integrada

**Conclusão principal**: **TensorFlow Lite Micro vence em todos os aspectos** - suporte oficial, facilidade, documentação, ecossistema e performance. PyTorch não tem suporte nativo para microcontroladores.

---

## 🔑 Conceitos-Chave

### TinyML (Tiny Machine Learning)
Machine Learning em dispositivos minúsculos (microcontroladores) com recursos limitados.

### Edge AI
Processamento de inteligência artificial localmente no dispositivo, sem depender da nuvem.

### ESP32-S3
Microcontrolador da Espressif com suporte a IA e interface para câmera, ideal para TinyML.

### Visão Embarcada
Sistema de visão onde a câmera e o processamento estão no próprio robô, não em sistema externo.

### RoboCup
Competição mundial de futebol de robôs, servindo como benchmark para pesquisa em robótica.

---

## 🛠️ Tecnologias e Ferramentas

### Hardware
- **ESP32-S3**: Microcontrolador principal
- **Câmera OV2640** ou similar
- **Chassis robótico**: Motores, rodas, estrutura
- **Bateria**: LiPo 7.4V ou similar
- **Driver de motores**: L298N ou similar

### Software e Frameworks
- **ESP-IDF**: Framework de desenvolvimento do ESP32
- **TensorFlow Lite Micro**: Para inferência de ML
- **Arduino IDE**: Alternativa para prototipagem
- **Edge Impulse**: Plataforma para treinar modelos TinyML
- **Python + TensorFlow**: Para treinar modelos
- **OpenCV**: Para processamento de imagens

### Ferramentas de Desenvolvimento
- **VS Code + PlatformIO**: IDE
- **Google Colab**: Para treinar modelos
- **Git/GitHub**: Versionamento
- **Zotero/Mendeley**: Gerenciador de referências

---

## 📂 Estrutura do Repositório

```
TCC/
├── README.md                           # Este arquivo
├── sumula.md                           # Súmula do projeto
├── guia_pesquisa_tcc.md               # Guia de pesquisa completo
├── papers_recomendados.md             # Lista de papers
├── cronograma_tcc.md                  # Cronograma detalhado
├── conceitos_tecnicos_explicados.md   # Conceitos técnicos
├── docs/                              # Documentação adicional
│   ├── revisao_bibliografica/        # Fichamentos de papers
│   ├── relatorios/                   # Relatórios de progresso
│   └── apresentacoes/                # Slides
├── code/                             # Código do projeto
│   ├── esp32/                        # Código do ESP32
│   ├── training/                     # Scripts de treinamento
│   └── tests/                        # Testes
├── datasets/                         # Datasets de imagens
├── models/                           # Modelos treinados
└── hardware/                         # Esquemáticos, CAD
```

---

## 🚀 Como Começar

### Semana 1-2: Setup Inicial
1. ✅ Ler todos os documentos de orientação deste repositório
2. ✅ Configurar ambiente de desenvolvimento
3. ✅ Fazer cadastro em bases acadêmicas (IEEE Xplore, Google Scholar)
4. ✅ Começar busca por papers fundamentais

### Próximos Passos
Siga o [cronograma_tcc.md](cronograma_tcc.md) para as próximas etapas!

---

## 📖 Leitura Recomendada (Ordem)

1. **[conceitos_tecnicos_explicados.md](conceitos_tecnicos_explicados.md)** - Para entender os conceitos básicos
2. **[guia_pesquisa_tcc.md](guia_pesquisa_tcc.md)** - Para saber o que pesquisar
3. **[analise_arquiteturas_robocup/README.md](analise_arquiteturas_robocup/README.md)** ⭐ **NOVO!** - Para entender arquiteturas e validar escolha do ESP32
4. **[papers_recomendados.md](papers_recomendados.md)** - Para encontrar referências
5. **[cronograma_tcc.md](cronograma_tcc.md)** - Para se organizar no tempo

---

## 📊 Metas e Indicadores

### TCC I (Junho/2025)
- [ ] 15-20 papers lidos e fichados
- [ ] Capítulos teóricos escritos
- [ ] Protótipo básico funcionando
- [ ] Relatório TCC I completo

### TCC II (Dezembro/2025)
- [ ] Sistema completo implementado
- [ ] Experimentos realizados
- [ ] TCC final escrito
- [ ] Defesa bem-sucedida

---

## 🔗 Links Úteis

### Documentação Oficial
- [ESP32-S3 Datasheet](https://www.espressif.com/sites/default/files/documentation/esp32-s3_datasheet_en.pdf)
- [ESP-IDF Programming Guide](https://docs.espressif.com/projects/esp-idf/en/latest/esp32s3/)
- [TensorFlow Lite Micro](https://www.tensorflow.org/lite/microcontrollers)

### Comunidades
- [TinyML Foundation](https://www.tinyml.org/)
- [RoboCup Official](https://www.robocup.org/)
- [ESP32 Forum](https://esp32.com/)
- Reddit: [r/tinyml](https://reddit.com/r/tinyml), [r/esp32](https://reddit.com/r/esp32)

### Cursos Online
- [Harvard CS249r: TinyML](https://www.edx.org/course/fundamentals-of-tinyml)
- [Coursera: Embedded ML](https://www.coursera.org/specializations/embedded-machine-learning)
- [Edge Impulse University](https://www.edgeimpulse.com/university)

---

## 📞 Contato

**Aluno**: Brendon Sousa Lima  
**Email**: [Seu email]  
**GitHub**: [Seu GitHub]  
**LinkedIn**: [Seu LinkedIn]

**Orientador**: Prof. Andrique Figueirêdo Amorim  
**IFBA - Campus Vitória da Conquista**

---

## 📝 Notas

### Atualizações
- **Novembro 2024**: Criação da estrutura inicial do projeto
- **Novembro 2024**: Adição de 6 análises detalhadas de arquiteturas RoboCup
- **Janeiro 2025**: Início do TCC I
- **Junho 2025**: Conclusão do TCC I
- **Dezembro 2025**: Defesa do TCC II

### Status Atual
🚧 **Em Planejamento** - Fase de organização e revisão bibliográfica inicial

---

## 🎓 Agradecimentos

- Prof. Andrique Figueirêdo Amorim - Orientação
- IFBA - Campus Vitória da Conquista
- Comunidade TinyML
- Espressif Systems
- Todos que contribuírem para o projeto

---

## 📄 Licença

Este projeto acadêmico está sendo desenvolvido para fins educacionais no IFBA.

O código-fonte será disponibilizado sob licença MIT após a conclusão.

---

## 🎯 Citação

Se você utilizar este trabalho, por favor cite:

```bibtex
@mastersthesis{lima2025visao,
  author  = {Brendon Sousa Lima},
  title   = {Sistema de Visão Computacional Embarcado para Robótica Autônoma de Baixo Custo},
  school  = {Instituto Federal da Bahia},
  year    = {2025},
  address = {Vitória da Conquista, BA},
  type    = {Trabalho de Conclusão de Curso}
}
```

---

**Última atualização**: Novembro de 2025  
**Versão**: 1.0

🤖 **Boa sorte no desenvolvimento do seu TCC!** 🚀
