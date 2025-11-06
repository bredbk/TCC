# 🚀 COMECE AQUI - Primeiros Passos

**Bem-vindo ao seu projeto de TCC!**

Este documento contém as **primeiras ações** que você deve tomar **AGORA** para começar seu TCC da melhor forma.

---

## ✅ Checklist Imediato (Hoje/Esta Semana)

### 📚 Passo 1: Ler a Documentação (2-3 horas)

Leia na ordem:

1. **[README.md](README.md)** (10 min)
   - Visão geral do projeto
   
2. **[conceitos_tecnicos_explicados.md](conceitos_tecnicos_explicados.md)** (60 min)
   - Entenda os conceitos técnicos
   - Não precisa memorizar tudo, apenas ter uma noção
   
3. **[guia_pesquisa_tcc.md](guia_pesquisa_tcc.md)** (45 min)
   - Veja as áreas que precisa pesquisar
   - Marque os tópicos que você já conhece vs precisa aprender
   
4. **[cronograma_tcc.md](cronograma_tcc.md)** (30 min)
   - Entenda o cronograma completo
   - Adapte para sua realidade

**✓ Resultado esperado**: Você terá uma visão completa do que vem pela frente

---

### 🔧 Passo 2: Configurar Ferramentas (2-3 horas)

#### A. Git e GitHub
```bash
# 1. Criar repositório privado no GitHub
# Nome sugerido: tcc-visao-embarcada-robotica

# 2. Clonar este repositório
git clone [URL_DO_SEU_REPO]

# 3. Fazer primeiro commit
git add .
git commit -m "Estrutura inicial do TCC"
git push
```

#### B. Gerenciador de Referências
- [ ] Instalar **Zotero** (recomendado) ou **Mendeley**
- [ ] Criar coleção "TCC - Visão Embarcada"
- [ ] Instalar extensão do navegador para salvar papers

**Download**: https://www.zotero.org/download/

#### C. Editor de Texto
- [ ] Instalar **VS Code** ou editor preferido
- [ ] Instalar extensões:
  - Markdown Preview
  - LaTeX (se for usar)
  - Git Lens

#### D. Conta Google (para Colab)
- [ ] Ter conta Google ativa (para treinar modelos no Google Colab)

**✓ Resultado esperado**: Ambiente de trabalho pronto

---

### 📖 Passo 3: Começar Pesquisa Bibliográfica (3-4 horas)

#### A. Cadastrar em Bases de Dados

1. **Google Scholar** (gratuito)
   - Acesse: https://scholar.google.com
   - Crie perfil acadêmico
   - Configure alertas para temas do seu TCC

2. **IEEE Xplore** (ver se IFBA tem acesso institucional)
   - Acesse: https://ieeexplore.ieee.org
   - Procure por "institutional access"
   - Entre via CAPES/IFBA se disponível

3. **arXiv.org** (gratuito)
   - Acesse: https://arxiv.org
   - Busque em: cs.RO, cs.CV, cs.LG

#### B. Primeiras Buscas

Use estas palavras-chave no Google Scholar:

```
1. "TinyML" + "computer vision"
2. "ESP32" + "machine learning"
3. "RoboCup" + "embedded vision"
4. "autonomous robot" + "ball detection"
5. "edge AI" + "microcontroller"
```

**Meta de hoje**: Encontrar **5-10 papers interessantes**

#### C. Salvar Papers Encontrados

Para cada paper:
1. Salvar no Zotero
2. Baixar PDF
3. Ler abstract e conclusão
4. Marcar os mais relevantes

**✓ Resultado esperado**: 5-10 papers salvos e catalogados

---

### 📝 Passo 4: Criar Estrutura de Pastas (15 min)

Organize seu projeto:

```
TCC/
├── docs/
│   ├── revisao_bibliografica/
│   │   ├── fichamentos/          # Criar hoje
│   │   └── papers/                # Criar hoje
│   ├── relatorios/
│   └── apresentacoes/
├── code/                          # Criar hoje
│   ├── esp32/
│   ├── training/
│   └── experiments/
├── datasets/                      # Criar hoje
├── models/
└── notas/                         # Criar hoje
    ├── ideias.md
    ├── duvidas.md
    └── progresso_semanal.md
```

**Comando rápido**:
```bash
mkdir -p docs/revisao_bibliografica/{fichamentos,papers}
mkdir -p code/{esp32,training,experiments}
mkdir -p {datasets,models,notas}
touch notas/{ideias.md,duvidas.md,progresso_semanal.md}
```

**✓ Resultado esperado**: Estrutura organizada pronta

---

### 💬 Passo 5: Reunião com Orientador (1 hora)

Agende uma reunião e prepare:

#### Pauta Sugerida:
1. **Apresentar estrutura do projeto** (mostrar este repositório)
2. **Validar escopo**:
   - Visão embarcada está OK?
   - ESP32-S3 é viável?
   - Futebol de robôs é o melhor cenário?
3. **Definir frequência de reuniões**:
   - Sugestão: Quinzenal no TCC I, Semanal no TCC II
4. **Esclarecer dúvidas** (anote antes!)
5. **Próximos passos**

#### Perguntas para Fazer:
- [ ] Há algum hardware disponível no IFBA?
- [ ] Há laboratório/espaço para testes?
- [ ] Há outros alunos fazendo TCC similar? (Possível colaboração)
- [ ] Orientador tem preferência de metodologia?
- [ ] Há grupos de pesquisa relacionados?

**✓ Resultado esperado**: Alinhamento com orientador

---

## 📅 Próximas 2 Semanas

### Semana 1: Imersão Teórica

**Objetivo**: Entender profundamente os conceitos

- [ ] **Dia 1-2**: Ler 3 papers sobre TinyML
  - MCUNet
  - MicroNets  
  - Um survey sobre TinyML
  
- [ ] **Dia 3-4**: Estudar ESP32-S3
  - Ler datasheet (principais seções)
  - Ver exemplos de código
  - Assistir tutoriais no YouTube
  
- [ ] **Dia 5-6**: Estudar RoboCup
  - Assistir vídeos de competições
  - Ler Team Description Papers (2-3)
  - Entender regras básicas
  
- [ ] **Dia 7**: Resumir tudo
  - Criar documento "O que aprendi esta semana"
  - Anotar dúvidas para o orientador

**Entregável**: Documento com resumo dos aprendizados + 3 fichamentos

---

### Semana 2: Hands-On Inicial

**Objetivo**: Ter contato com as tecnologias

- [ ] **Dia 1-2**: Configurar ESP-IDF ou Arduino
  - Instalar ferramentas
  - Fazer blink LED
  - Testar comunicação serial
  
- [ ] **Dia 3-4**: Experimento com Python
  - Detecção de objetos com OpenCV
  - Usar webcam do computador
  - Detectar objeto colorido (ex: bola laranja)
  
- [ ] **Dia 5-6**: Google Colab - ML Básico
  - Tutorial de TensorFlow
  - Treinar modelo simples (MNIST ou similar)
  - Entender pipeline de treinamento
  
- [ ] **Dia 7**: Documentar
  - "O que aprendi - Semana 2"
  - Reunião com orientador
  - Planejar próximas semanas

**Entregável**: Código funcionando + documentação

---

## 📊 Métricas de Sucesso (Primeiras 2 Semanas)

### Indicadores
- ✅ **5-10 papers** encontrados e salvos
- ✅ **3 papers** lidos e fichados
- ✅ **Ambiente** de desenvolvimento configurado
- ✅ **Repositório** organizado
- ✅ **1 reunião** com orientador realizada
- ✅ **Experimento básico** funcionando (blink ou webcam)

### Se você atingir isso, está no caminho certo! 🎯

---

## 🆘 Se Você Está Travado

### Problema: "Não entendi os conceitos"
**Solução**:
- Leia [conceitos_tecnicos_explicados.md](conceitos_tecnicos_explicados.md) novamente
- Assista vídeos no YouTube sobre TinyML
- Comece pelos conceitos mais simples

### Problema: "Não consigo encontrar papers"
**Solução**:
- Use as palavras-chave exatas de [papers_recomendados.md](papers_recomendados.md)
- Comece pelo Google Scholar (mais fácil)
- Leia apenas abstract inicialmente

### Problema: "Não sei programar ESP32"
**Solução**:
- Comece pelo Arduino (mais simples)
- Faça tutoriais básicos primeiro
- RandomNerdTutorials.com é excelente

### Problema: "Não tenho hardware ainda"
**Solução**:
- Comece pela parte teórica (revisão bibliográfica)
- Faça experimentos com Python no PC
- Use simuladores (Wokwi, TinkerCAD)
- Hardware pode vir depois (mês 3-4)

---

## 💡 Dicas de Ouro

### 1. **Não tente fazer tudo de uma vez**
Vá passo a passo. TCC é maratona, não sprint.

### 2. **Documente TUDO desde o início**
- Cada experimento
- Cada decisão
- Cada problema encontrado

Isso vira conteúdo do TCC!

### 3. **Mantenha contato com orientador**
Mesmo que seja só um email semanal com "Fiz X, Y, Z esta semana"

### 4. **Participe de comunidades**
- Reddit r/tinyml
- Discord de ESP32
- Fóruns

Muita gente passa pelos mesmos problemas!

### 5. **Celebre pequenas vitórias**
- Primeiro LED piscando? 🎉
- Primeiro paper fichado? 🎉
- Primeira imagem capturada? 🎉

Tudo é progresso!

---

## 📞 Lista de Recursos Quick

### Documentação Essencial
- [ESP32-S3 Getting Started](https://docs.espressif.com/projects/esp-idf/en/latest/esp32s3/get-started/)
- [TensorFlow Lite Micro Docs](https://www.tensorflow.org/lite/microcontrollers)
- [RoboCup Official Site](https://www.robocup.org/)

### Tutoriais Recomendados
- [RandomNerdTutorials - ESP32](https://randomnerdtutorials.com/projects-esp32/)
- [Harvard TinyML Course](https://www.edx.org/course/fundamentals-of-tinyml)
- [Edge Impulse Tutorials](https://docs.edgeimpulse.com/docs)

### Comunidades
- Reddit: r/tinyml, r/esp32, r/robotics
- Discord: TinyML, ESP32 Community
- Fórum: esp32.com

### Canais YouTube
- "Andreas Spiess" - ESP32 projects
- "Shawn Hymel" - TinyML
- "DroneBot Workshop" - Robotics

---

## ✅ Checklist Final - Semana 1

Ao final da primeira semana, você deve ter:

- [ ] Lido toda a documentação deste repositório
- [ ] Configurado Git + Zotero + VS Code
- [ ] Criado estrutura de pastas
- [ ] Encontrado 5-10 papers
- [ ] Lido 2-3 papers (abstract completo)
- [ ] Feito 1 fichamento completo
- [ ] Agendado/realizado reunião com orientador
- [ ] Instalado ferramentas de desenvolvimento (ESP-IDF ou Arduino)
- [ ] Feito experimento básico (blink LED ou similar)
- [ ] Criado documento de progresso semanal

### Se você completou isso, parabéns! 🎉

**Você está pronto para a jornada do TCC!**

---

## 🎯 Próximo Documento

Depois de completar estas tarefas, volte ao **[cronograma_tcc.md](cronograma_tcc.md)** e comece a seguir o planejamento mês a mês.

---

## 📝 Template: Progresso Semanal

Use este template no arquivo `notas/progresso_semanal.md`:

```markdown
# Progresso Semanal

## Semana 1 (DD/MM - DD/MM)

### O que fiz
- Item 1
- Item 2

### O que aprendi
- Conceito 1
- Conceito 2

### Dificuldades encontradas
- Problema 1
- Problema 2

### Próxima semana
- [ ] Tarefa 1
- [ ] Tarefa 2

### Observações
(Qualquer outra coisa relevante)
```

---

**Lembre-se**: Todo grande projeto começa com pequenos passos!

🚀 **Vamos começar? Boa sorte!** 🚀

