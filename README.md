# TCC - Sistema de Visão Computacional Embarcado para Robótica Autônoma

**Aluno**: Brendon Sousa Lima  
**Orientador**: Prof. Andrique Figueirêdo Amorim  
**Instituição**: IFBA - Campus Vitória da Conquista  
**Curso**: Bacharelado em Sistemas de Informação  
**Ano**: 2025

---

## 🚀 NOVO NO PROJETO? 

**👉 Comece por aqui: [docs/guia/COMECE_AQUI.md](docs/guia/COMECE_AQUI.md)**

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

### 📄 **Documento Principal da Monografia**

#### **[Projeto_Pesquisa_TCC_Brendon_Final.md](Projeto_Pesquisa_TCC_Brendon_Final.md)** 📖
**Este é o arquivo principal da monografia do TCC**, contendo:
- Introdução e justificativa
- Objetivos gerais e específicos
- Metodologia completa
- Referencial teórico
- Cronograma
- Referências bibliográficas

---

### 📂 **Estrutura Organizada do Projeto**

O projeto está organizado em pastas para facilitar a navegação:

#### 📁 **docs/guia/** - Guias e Orientações
- **[COMECE_AQUI.md](docs/guia/COMECE_AQUI.md)** ⭐ - **Comece por aqui!** Primeiros passos do TCC
- **[guia_pesquisa_tcc.md](docs/guia/guia_pesquisa_tcc.md)** - Guia completo de pesquisa
- **[cronograma_tcc.md](docs/guia/cronograma_tcc.md)** 📅 - Cronograma detalhado mês a mês
- **[conceitos_tecnicos_explicados.md](docs/guia/conceitos_tecnicos_explicados.md)** 💡 - Explicações didáticas dos conceitos

#### 📁 **docs/analises/** - Análises Técnicas
- **[analise_arquiteturas_robocup/](docs/analises/analise_arquiteturas_robocup/)** 🏗️ ⭐
  - 6 análises completas de times de competição RoboCup
  - Comparação de arquiteturas (distribuída vs centralizada)
  - Prova real de uso de ESP32 (Munako Aegis)
  - Análise de custos (economia de 80-90%)
- **[analise_viabilidade_haar_cascade_esp32s3.md](docs/analises/analise_viabilidade_haar_cascade_esp32s3.md)** 🔍
  - Comparação: Detecção de cores vs Haar Cascade
  - Benchmarks de performance
  - Recomendações técnicas
- **[analise_pytorch_vs_tensorflow_esp32.md](docs/analises/analise_pytorch_vs_tensorflow_esp32.md)** 🤖
  - Comparação de frameworks de ML
  - Recomendação: TensorFlow Lite Micro
- **[analise_zg24robotics.md](docs/analises/analise_zg24robotics.md)** - Análise adicional

#### 📁 **docs/referencias/** - Documentos de Referência
- **[papers_recomendados.md](docs/referencias/papers_recomendados.md)** - Lista curada de papers
- **[sumula.md](docs/referencias/sumula.md)** - Súmula oficial do projeto
- **[PONTOS_DE_MELHORIA_TCC.md](docs/referencias/PONTOS_DE_MELHORIA_TCC.md)** - Análise de melhorias
- **[template_projeto_pesquisa_IFBA.md](docs/referencias/template_projeto_pesquisa_IFBA.md)** - Template
- Versões anteriores do projeto (para referência)

#### 📁 **docs/formais/** - Documentos Formais
- Termo de Aceite do Orientador (PDF)
- Súmula oficial (PDF)
- Modelo de Projeto de Pesquisa (DOCX)

#### 📁 **referencias para estudo/** - Materiais de Estudo
- Posters de times RoboCup
- PDFs de referência (TinyML, etc.)
- Imagens e diagramas
- Arquivos RAR com materiais adicionais

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
├── README.md                                    # Este arquivo
├── Projeto_Pesquisa_TCC_Brendon_Final.md        # 📖 MONOGRAFIA PRINCIPAL
│
├── docs/                                        # Documentação organizada
│   ├── guia/                                   # Guias e orientações
│   │   ├── COMECE_AQUI.md                     # ⭐ Comece por aqui!
│   │   ├── guia_pesquisa_tcc.md               # Guia completo de pesquisa
│   │   ├── cronograma_tcc.md                  # Cronograma detalhado
│   │   └── conceitos_tecnicos_explicados.md   # Conceitos técnicos
│   │
│   ├── analises/                               # Análises técnicas
│   │   ├── analise_arquiteturas_robocup/      # Análises de arquiteturas
│   │   ├── analise_viabilidade_haar_cascade_esp32s3.md
│   │   ├── analise_pytorch_vs_tensorflow_esp32.md
│   │   └── analise_zg24robotics.md
│   │
│   ├── referencias/                            # Documentos de referência
│   │   ├── papers_recomendados.md             # Lista de papers
│   │   ├── sumula.md                          # Súmula oficial
│   │   ├── PONTOS_DE_MELHORIA_TCC.md          # Análise de melhorias
│   │   ├── template_projeto_pesquisa_IFBA.md  # Template
│   │   └── [versões anteriores do projeto]
│   │
│   └── formais/                                # Documentos formais
│       ├── Termo de Aceite (PDF)
│       ├── Súmula oficial (PDF)
│       └── Modelo de Projeto (DOCX)
│
└── referencias para estudo/                    # Materiais de estudo
    ├── Posters RoboCup (PDFs)
    ├── Papers e livros (PDFs)
    └── Imagens e diagramas
```

---

## 🚀 Como Começar

### Semana 1-2: Setup Inicial
1. ✅ Ler todos os documentos de orientação deste repositório
2. ✅ Configurar ambiente de desenvolvimento
3. ✅ Fazer cadastro em bases acadêmicas (IEEE Xplore, Google Scholar)
4. ✅ Começar busca por papers fundamentais

### Próximos Passos
Siga o [docs/guia/cronograma_tcc.md](docs/guia/cronograma_tcc.md) para as próximas etapas!

---

## 📖 Leitura Recomendada (Ordem)

1. **[docs/guia/COMECE_AQUI.md](docs/guia/COMECE_AQUI.md)** ⭐ - **Comece por aqui!** Primeiros passos
2. **[docs/guia/conceitos_tecnicos_explicados.md](docs/guia/conceitos_tecnicos_explicados.md)** - Para entender os conceitos básicos
3. **[docs/guia/guia_pesquisa_tcc.md](docs/guia/guia_pesquisa_tcc.md)** - Para saber o que pesquisar
4. **[docs/analises/analise_arquiteturas_robocup/README.md](docs/analises/analise_arquiteturas_robocup/README.md)** ⭐ - Para entender arquiteturas e validar escolha do ESP32
5. **[docs/referencias/papers_recomendados.md](docs/referencias/papers_recomendados.md)** - Para encontrar referências
6. **[docs/guia/cronograma_tcc.md](docs/guia/cronograma_tcc.md)** - Para se organizar no tempo
7. **[Projeto_Pesquisa_TCC_Brendon_Final.md](Projeto_Pesquisa_TCC_Brendon_Final.md)** 📖 - Monografia principal

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
- **Janeiro 2025**: Reorganização da estrutura em pastas para melhor organização
- **Junho 2025**: Conclusão do TCC I (previsto)
- **Dezembro 2025**: Defesa do TCC II (previsto)

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