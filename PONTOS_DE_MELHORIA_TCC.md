# 📋 Pontos de Melhoria - Projeto de TCC
## Detecção e Localização de Objetos com Câmera OV2640 e Espelho Convexo

**Aluno**: Brendon Sousa Lima  
**Data da Análise**: Janeiro 2025

---

## 📊 Resumo Executivo

**Avaliação Geral**: ⭐⭐⭐⭐ (4/5) - **Muito Bom**

O projeto está bem estruturado e fundamentado, mas há oportunidades de melhoria em várias áreas para elevar a qualidade acadêmica e técnica do trabalho.

---

## 🔴 MELHORIAS CRÍTICAS (Alta Prioridade)

### 1. **Referências Bibliográficas**

**Problema Identificado**:
- Referências incompletas e não formatadas segundo ABNT
- Falta de citações de papers científicos recentes
- Ausência de trabalhos relacionados específicos sobre ESP32-S3 + espelho convexo
- Referências genéricas ("Artigos e tutoriais sobre...")

**Recomendações**:
- ✅ Expandir busca em bases acadêmicas (IEEE Xplore, ACM Digital Library, Google Scholar)
- ✅ Incluir papers sobre:
  - Visão embarcada com ESP32/ESP32-S3
  - Espelhos catadióptricos em robótica
  - Segmentação por cor HSV em microcontroladores
  - RoboCup e sistemas de visão embarcada
- ✅ Formatar todas as referências segundo ABNT NBR 6023
- ✅ Adicionar citações no texto (ex: "Segundo BRADSKI e KAEHLER (2008)...")
- ✅ Incluir trabalhos de 2020-2025 (estado da arte recente)

**Exemplo de Referência Correta (ABNT)**:
```
BRADSKI, G.; KAEHLER, A. Learning OpenCV: Computer Vision with the OpenCV Library. 
Sebastopol: O'Reilly Media, 2008. 580 p.
```

### 2. **Seção de Trabalhos Relacionados**

**Problema Identificado**:
- Seção muito genérica (apenas lista de tópicos)
- Falta análise comparativa com trabalhos similares
- Ausência de tabela comparativa
- Não posiciona o trabalho em relação ao estado da arte

**Recomendações**:
- ✅ Expandir para 2-3 páginas com análise detalhada
- ✅ Incluir 5-8 trabalhos relacionados com:
  - Resumo do trabalho
  - Metodologia utilizada
  - Resultados obtidos
  - Comparação com sua proposta
- ✅ Criar tabela comparativa:
  | Trabalho | Plataforma | Método | Latência | Custo | Limitações |
  |----------|-----------|--------|----------|-------|------------|
  | Seu trabalho | ESP32-S3 | HSV | <100ms | <R$100 | ... |
- ✅ Identificar lacunas na literatura que seu trabalho preenche

### 3. **Delimitação do Escopo**

**Problema Identificado**:
- Objetivo 8 menciona detecção de "gols" mas não está claro como serão detectados
- Falta especificação de como distinguir gol do time vs gol oponente
- Não está claro se gols serão detectados por cor, forma, ou outra característica

**Recomendações**:
- ✅ Especificar claramente:
  - Como os gols serão detectados (cor? forma? posição fixa?)
  - Características distintivas entre gol do time e oponente
  - Se gols fazem parte do escopo principal ou são apenas validação
- ✅ Considerar adicionar subseção "Delimitação do Escopo" na introdução
- ✅ Definir o que está incluído e o que está excluído do trabalho

### 4. **Metodologia - Numeração Inconsistente**

**Problema Identificado**:
- Fase 6 tem item "13" mas deveria ser "18" (sequência quebrada)
- Numeração não está sequencial após adicionar novas fases

**Recomendações**:
- ✅ Corrigir numeração sequencial (1-18)
- ✅ Revisar toda a numeração do documento

---

## 🟡 MELHORIAS IMPORTANTES (Média Prioridade)

### 5. **Introdução - Contextualização**

**Problema Identificado**:
- Introdução poderia ser mais robusta
- Falta mencionar trabalhos anteriores na área
- Não contextualiza o problema dentro de um panorama maior

**Recomendações**:
- ✅ Adicionar parágrafo sobre evolução da visão embarcada
- ✅ Mencionar desafios técnicos específicos (memória, processamento, latência)
- ✅ Contextualizar dentro do cenário brasileiro/latino-americano (se relevante)
- ✅ Adicionar estatísticas ou dados sobre robótica educacional (se disponível)

### 6. **Justificativa - Dados Quantitativos**

**Problema Identificado**:
- Menciona "latência muito baixa (15-25 ms)" mas não cita fonte
- Falta comparação quantitativa com outras soluções
- Não apresenta dados de mercado ou custos comparativos

**Recomendações**:
- ✅ Adicionar tabela comparativa de custos:
  | Solução | Custo | Latência | Complexidade |
  |---------|-------|----------|--------------|
  | Solução proposta | <R$100 | 15-25ms | Baixa |
  | Jetson Nano | R$1000+ | 50-100ms | Alta |
  | Raspberry Pi + ML | R$500+ | 100-200ms | Média |
- ✅ Incluir referências para os valores mencionados
- ✅ Adicionar dados sobre consumo energético comparativo

### 7. **Metodologia - Detalhamento Técnico**

**Problema Identificado**:
- Fase 3 menciona "thresholding adaptativo" mas não explica como será implementado
- Falta especificar algoritmo de detecção de blobs
- Não detalha transformação de coordenadas do espelho convexo

**Recomendações**:
- ✅ Adicionar subseção técnica detalhando:
  - Algoritmo de thresholding adaptativo (como calcular thresholds?)
  - Algoritmo de detecção de blobs (connected components? contour detection?)
  - Modelo matemático da transformação de coordenadas do espelho
- ✅ Incluir pseudocódigo ou diagrama de fluxo do algoritmo
- ✅ Especificar valores de threshold HSV para laranja

### 8. **Cronograma - Detalhamento**

**Problema Identificado**:
- Cronograma muito genérico (apenas meses)
- Falta distribuição semanal das atividades
- Não especifica dependências entre atividades

**Recomendações**:
- ✅ Adicionar cronograma detalhado por semanas (pelo menos para TCC II)
- ✅ Indicar dependências (ex: "Validação incremental depende de algoritmo implementado")
- ✅ Incluir marcos intermediários (milestones)
- ✅ Adicionar buffer de tempo para imprevistos (20% adicional)

### 9. **Métricas de Avaliação**

**Problema Identificado**:
- Critérios de sucesso mencionados mas não justificados
- Falta especificar como será calculado "erro em cm"
- Não menciona análise estatística dos dados

**Recomendações**:
- ✅ Adicionar seção "Critérios de Avaliação" detalhando:
  - Como calcular precisão de coordenadas (ground truth vs detectado)
  - Métodos estatísticos (média, desvio padrão, intervalo de confiança)
  - Tamanho mínimo de amostra para validade estatística
- ✅ Justificar critérios de sucesso (por que 90%? por que 100ms?)
- ✅ Especificar como será feita a comparação entre fases

### 10. **Apêndices - Conteúdo**

**Problema Identificado**:
- Apêndices estão vazios (apenas placeholders)
- Falta especificar o que será incluído em cada apêndice

**Recomendações**:
- ✅ Expandir descrição dos apêndices:
  - **Apêndice A**: Termo de aceite (OK)
  - **Apêndice B**: Especificações técnicas, diagramas de conexão, esquemáticos
  - **Apêndice C**: Código-fonte completo ou principais funções
  - **Apêndice D**: Tabelas detalhadas, gráficos, dados brutos
  - **Apêndice E**: Fotos dos experimentos (setup, campo, resultados)
  - **Apêndice F**: Calibração do espelho convexo (modelo matemático)

---

## 🟢 MELHORIAS COMPLEMENTARES (Baixa Prioridade)

### 11. **Título do Trabalho**

**Problema Identificado**:
- Título é "provisório" mas poderia ser mais específico
- Não menciona "baixo custo" ou "tempo real" que são diferenciais

**Sugestões de Títulos**:
- "Sistema de Visão Computacional Embarcado de Baixo Custo para Detecção e Localização de Objetos em Robôs Autônomos Utilizando Câmera OV2640 e Espelho Convexo"
- "Detecção em Tempo Real de Objetos em Robótica Autônoma: Sistema Embarcado com ESP32-S3, Câmera OV2640 e Espelho Convexo"

### 12. **Estrutura do Documento**

**Problema Identificado**:
- Falta seção de "Hipóteses" (se aplicável)
- Não há seção de "Contribuições Esperadas"
- Falta "Estrutura da Monografia" (sumário previsto)

**Recomendações**:
- ✅ Adicionar seção "Contribuições Esperadas" após objetivos
- ✅ Incluir "Estrutura Prevista da Monografia" (sumário dos capítulos)
- ✅ Considerar adicionar "Hipóteses" se for pesquisa experimental

### 13. **Formatação e Apresentação**

**Problema Identificado**:
- Alguns espaçamentos inconsistentes
- Formatação de listas poderia ser padronizada
- Falta numeração de páginas (se necessário)

**Recomendações**:
- ✅ Revisar formatação segundo normas do IFBA/ABNT
- ✅ Padronizar espaçamentos e margens
- ✅ Verificar numeração de seções e subseções
- ✅ Adicionar numeração de páginas

### 14. **Recursos e Orçamento**

**Problema Identificado**:
- Não há seção de "Recursos Necessários" ou "Orçamento"
- Falta especificar custos detalhados dos componentes

**Recomendações**:
- ✅ Adicionar seção "Recursos Necessários" com:
  - Hardware detalhado com preços
  - Software (gratuito ou licenciado)
  - Infraestrutura (laboratório, espaço)
  - Recursos humanos (orientador, bolsas)
- ✅ Criar tabela de orçamento detalhada

### 15. **Riscos e Limitações**

**Problema Identificado**:
- Não há seção sobre riscos do projeto
- Falta identificar limitações conhecidas

**Recomendações**:
- ✅ Adicionar seção "Riscos e Mitigações":
  - Risco: Hardware não chegar a tempo → Mitigação: Pedir com antecedência
  - Risco: Algoritmo não funcionar → Mitigação: Testar em simulação primeiro
  - Risco: Calibração do espelho complexa → Mitigação: Estudar geometria antes
- ✅ Identificar limitações conhecidas:
  - Dependência de iluminação adequada
  - Limitações de distância de detecção
  - Restrições de cor (apenas objetos laranja)

---

## 📝 CHECKLIST DE MELHORIAS

### Prioridade Alta (Fazer Agora)
- [ ] Expandir e formatar referências bibliográficas (ABNT)
- [ ] Desenvolver seção de Trabalhos Relacionados com análise comparativa
- [ ] Esclarecer delimitação do escopo (especialmente sobre detecção de gols)
- [ ] Corrigir numeração da metodologia

### Prioridade Média (Fazer em Breve)
- [ ] Melhorar contextualização na introdução
- [ ] Adicionar dados quantitativos e comparações na justificativa
- [ ] Detalhar aspectos técnicos da metodologia
- [ ] Detalhar cronograma com semanas e dependências
- [ ] Especificar métricas e critérios de avaliação detalhadamente

### Prioridade Baixa (Melhorias Contínuas)
- [ ] Refinar título do trabalho
- [ ] Adicionar seções complementares (contribuições, estrutura)
- [ ] Revisar formatação completa
- [ ] Adicionar seção de recursos e orçamento
- [ ] Incluir seção de riscos e limitações

---

## 🎯 RECOMENDAÇÕES ESPECÍFICAS POR SEÇÃO

### Seção 1 - Introdução
1. **Adicionar parágrafo sobre estado da arte atual**
2. **Mencionar trabalhos pioneiros na área**
3. **Contextualizar problema dentro de tendências tecnológicas**

### Seção 1.1 - Justificativa
1. **Adicionar tabela comparativa de custos**
2. **Incluir dados sobre mercado de robótica educacional**
3. **Mencionar impacto social/educacional**

### Seção 1.2 - Problema
1. **Formular como questão de pesquisa mais específica**
2. **Adicionar subproblemas (se houver)**

### Seção 1.3 - Objetivos
1. **Objetivo 8**: Especificar como gols serão detectados
2. **Adicionar objetivo sobre comparação com trabalhos relacionados**

### Seção 1.4 - Metodologia
1. **Adicionar subseção técnica detalhando algoritmos**
2. **Incluir diagrama de fluxo do pipeline**
3. **Especificar valores de parâmetros (thresholds HSV)**
4. **Adicionar modelo matemático da transformação de coordenadas**

### Seção 2 - Conceitos Teóricos
1. **Expandir cada subseção com mais detalhes**
2. **Adicionar equações matemáticas (se aplicável)**
3. **Incluir figuras/diagramas explicativos**
4. **Adicionar seção sobre calibração de câmeras**

### Seção 2.5 - Trabalhos Relacionados
1. **Transformar em seção completa (2-3 páginas)**
2. **Adicionar análise de 5-8 trabalhos**
3. **Criar tabela comparativa**
4. **Identificar lacunas na literatura**

### Seção 3 - Cronograma
1. **Adicionar cronograma detalhado por semanas**
2. **Incluir marcos intermediários**
3. **Adicionar buffer de tempo**

### Seção 4 - Referências
1. **Formatar todas segundo ABNT**
2. **Expandir para 15-20 referências**
3. **Incluir papers recentes (2020-2025)**
4. **Adicionar trabalhos específicos sobre ESP32-S3**

---

## 📚 REFERÊNCIAS SUGERIDAS PARA ADICIONAR

### Papers sobre ESP32 e Visão Embarcada
- Buscar em IEEE Xplore: "ESP32 computer vision"
- Buscar em Google Scholar: "ESP32 embedded vision"
- Papers sobre ESP32-CAM e processamento de imagens

### Papers sobre Espelhos Catadióptricos
- Trabalhos sobre visão panorâmica em robótica
- Calibração de sistemas catadióptricos
- Transformação de coordenadas em espelhos convexos

### Papers sobre Segmentação por Cor HSV
- Comparação HSV vs RGB para detecção de objetos
- Thresholding adaptativo em microcontroladores
- Otimizações de processamento HSV em tempo real

### Trabalhos RoboCup
- Team Description Papers (TDPs) de times com visão embarcada
- Papers sobre sistemas de visão em RoboCup Junior
- Trabalhos sobre detecção de bola em futebol de robôs

---

## 💡 DICAS FINAIS

1. **Consistência**: Garanta que todas as informações estejam alinhadas entre seções
2. **Precisão**: Especifique valores, parâmetros e critérios sempre que possível
3. **Justificativa**: Sempre justifique escolhas técnicas e metodológicas
4. **Completude**: Preencha todos os placeholders e seções vazias
5. **Revisão**: Peça para alguém ler e identificar pontos confusos
6. **Validação**: Discuta com orientador antes de finalizar

---

## ✅ PRÓXIMOS PASSOS RECOMENDADOS

1. **Esta Semana**:
   - Expandir referências bibliográficas
   - Corrigir numeração da metodologia
   - Esclarecer delimitação do escopo

2. **Próximas 2 Semanas**:
   - Desenvolver seção de Trabalhos Relacionados
   - Adicionar detalhamento técnico na metodologia
   - Melhorar justificativa com dados quantitativos

3. **Próximo Mês**:
   - Completar todas as seções
   - Revisar formatação completa
   - Validar com orientador

---

**Última atualização**: Janeiro 2025  
**Próxima revisão recomendada**: Após implementar melhorias críticas

---

## 📞 NOTAS

Este documento identifica oportunidades de melhoria, mas o projeto já está em **bom nível**. As melhorias sugeridas visam elevar a qualidade acadêmica e técnica do trabalho para um nível **excepcional**.

**Foco principal**: Referências, Trabalhos Relacionados e Detalhamento Técnico são as áreas que mais impactarão na avaliação do TCC.

