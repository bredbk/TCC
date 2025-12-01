
INSTITUTO FEDERAL DE EDUCAÇÃO, CIÊNCIA E TECNOLOGIA DA BAHIA - IFBA






BRENDON SOUSA LIMA




MÓDULO DE VISÃO COMPUTACIONAL EMBARCADO PARA ROBÓTICA AUTÔNOMA





Vitória da Conquista
2025BRENDON SOUSA LIMA







MÓDULO DE VISÃO COMPUTACIONAL EMBARCADO PARA ROBÓTICA AUTÔNOMA: ANÁLISE COMPARATIVA DE PLATAFORMAS E DESENVOLVIMENTO DE PROTÓTIPO DE BAIXO CUSTO




Projeto de Pesquisa apresentado como requisito parcial de avaliação da disciplina Trabalho de Conclusão de Curso I, do curso de Bacharelado em Sistemas de Informação do Instituto Federal de Educação, Ciência e Tecnologia da Bahia – IFBA, sob orientação do Prof. Andrique Figueirêdo Amorim.


Vitória da Conquista
2025
ABSTRACT
This work proposes the development of a low-cost embedded computer vision module for autonomous robotics based on Tiny Machine Learning (TinyML). The research addresses the challenge of implementing real-time object detection systems in resource-constrained microcontrollers, focusing on the ESP32-S3 platform as a cost-effective alternative to high-end embedded systems. The proposed module will capture images through a camera, process them locally using optimized TinyML models, and provide object coordinates (x, y) for integration with autonomous robot control systems. The application context is autonomous robot soccer, where the system must detect and track objects such as balls and goals in real-time. The methodology includes a comparative analysis of different hardware platforms, development and optimization of machine learning models for microcontrollers, and incremental validation through three phases: initial tests with top-view images (isolated ball, then ball and goals), followed by tests with a convex mirror simulating the robot's field perspective. Performance metrics such as detection accuracy, latency, frames per second (FPS), and energy consumption will be evaluated, with the goal of achieving a balance between performance and accuracy. The expected contribution is to democratize access to autonomous robotics technology by providing a solution with a total cost of less than R$ 200, representing a 80-90% cost reduction compared to traditional solutions, while maintaining acceptable performance for educational and research applications in autonomous robotics.

Keywords: Computer Vision, TinyML, Embedded Systems, Autonomous Robotics, ESP32-S3, Edge AI, RoboCup







Sumário
1.	INTRODUÇÃO	4
1.1	Justificativa	4
1.2	Problema	4
1.3	Objetivos	4
1.3.1	Geral	4
1.3.2	Específicos	4
1.4	Metodologia	4
2	CONCEITOS TEÓRICOS (Quantas seções forem necessárias)/ TRABALHOS RELACIONADOS	5
3	CRONOGRAMA	6
4	REFERÊNCIAS	7
APÊNDICES	8





INTRODUÇÃO
	A robótica autônoma móvel tem desempenhado um papel crucial na evolução da indústria 4.0 e na automação de tarefas complexas. Em ambientes dinâmicos e competitivos, como o futebol de robôs (RoboCup), a capacidade de perceber o ambiente, identificar objetos de interesse e tomar decisões em tempo real é um requisito fundamental (KITANO et al., 1997).
	Tradicionalmente, a percepção visual em robótica móvel depende de duas abordagens: processamento centralizado (câmeras externas ao campo enviando dados via rádio) ou processamento embarcado em hardware de alto custo (como placas com GPUs dedicadas). Ambas as soluções apresentam barreiras significativas para a massificação da robótica educacional e amadora, seja pelo custo de infraestrutura ou pelo consumo energético elevado.
	Nesse cenário, o paradigma do Edge AI e do TinyML (Tiny Machine Learning) surge como uma alternativa promissora, permitindo a execução de algoritmos de visão computacional diretamente em microcontroladores de baixo custo (WARDEN; SITUNAYAKE, 2019). Este projeto propõe o desenvolvimento de um módulo de visão embarcada utilizando o microcontrolador ESP32-S3 e uma câmera OV2640.
	O diferencial inovador desta proposta reside na integração de um sistema óptico catadióptrico (uso de espelho convexo), que visa ampliar o campo de visão do robô para 360 graus (omnidirecional) com um único sensor, eliminando partes móveis e mantendo o custo do sistema reduzido.

Justificativa
A relevância deste trabalho é sustentada por três pilares:
Tecnológica: A validação do ESP32-S3 (custo ~R$ 60,00) como plataforma de visão computacional desafia os limites do hardware atual. A aplicação de técnicas de TinyML e segmentação de cores (HSV) em dispositivos com memória restrita (SRAM < 512KB) contribui para o estado da arte em sistemas embarcados (LIN et al., 2020).
Econômica e Social: Ao propor uma solução com custo total inferior a R$ 200,00, o projeto democratiza o acesso a tecnologias avançadas de percepção robótica, permitindo que instituições de ensino com orçamentos limitados participem de competições de robótica de nível superior.

Inovação em Design: A utilização de um espelho convexo (catadióptrico) para obter visão panorâmica em um sistema de baixo custo é uma alternativa criativa aos caros sensores LIDAR ou arranjos de múltiplas câmeras, reduzindo a complexidade mecânica e eletrônica do robô.

Problema
A implementação de visão computacional em robôs móveis de pequeno porte enfrenta um dilema de trade-off (compromisso) entre desempenho e recursos. Plataformas robustas como NVIDIA Jetson ou Raspberry Pi 4 custam entre R$ 500,00 e R$ 2.000,00 e demandam baterias volumosas. Por outro lado, microcontroladores baratos frequentemente carecem de memória para processar imagens.
Além disso, câmeras convencionais possuem campo de visão limitado (aprox. 60°), obrigando o robô a girar constantemente para encontrar a bola, o que reduz sua eficiência em jogo. Diante disso, formula-se a seguinte questão de pesquisa:
Qual a viabilidade técnica e o desempenho de um módulo de visão computacional embarcado de baixo custo (baseado em ESP32-S3 e óptica catadióptrica) para a detecção de objetos em tempo real em robôs móveis autônomos?

Objetivos
Geral
Desenvolver um protótipo funcional de módulo de visão computacional embarcado utilizando o microcontrolador ESP32-S3 e óptica catadióptrica, capaz de detectar uma bola laranja em tempo real e fornecer suas coordenadas relativas para o controle de navegação de um robô autônomo.
Específicos
Realizar levantamento bibliográfico sobre TinyML, segmentação de imagens em microcontroladores e sistemas de visão omnidirecional.
Implementar e comparar algoritmos de detecção de objetos baseados em cor (Espaço HSV) e Machine Learning (TensorFlow Lite Micro) quanto à latência e acurácia.
Desenvolver o suporte físico para acoplamento da câmera OV2640 e do espelho convexo.
Criar algoritmo de mapeamento para converter a imagem distorcida do espelho em coordenadas cartesianas (X, Y) úteis para o robô.
Validar o sistema em etapas incrementais: visão estática superior e visão embarcada omnidirecional.

Metodologia
A pesquisa classifica-se como aplicada e experimental, com abordagem quantitativa. O desenvolvimento seguirá um processo incremental para isolar variáveis e garantir a robustez do sistema.
Procedimentos Metodológicos
O projeto será executado em três fases principais:
Fase 1: Configuração e Algoritmo Base (Ambiente Controlado) Inicialmente, será configurado o firmware no ESP32-S3 para captura de imagens em resolução reduzida (QVGA ou QQVGA) para otimizar o FPS (Frames Per Second). Serão implementados filtros de segmentação no espaço de cor HSV (Hue, Saturation, Value), que é mais robusto a variações de luz que o RGB, para isolar a cor laranja da bola.
Fase 2: Validação Incremental Para garantir a confiabilidade dos dados, os testes seguirão uma ordem de complexidade:
Visão Superior (Bird’s Eye View): O módulo será testado com a câmera apontada diretamente para baixo (sem espelho), capturando a bola em fundo contrastante. O objetivo é validar o algoritmo de detecção e medir o tempo de resposta (latência) sem a distorção óptica.
Visão Catadióptrica (Com Espelho): A câmera será acoplada ao espelho convexo. O algoritmo será adaptado para identificar o "blob" (mancha) laranja na imagem refletida e calcular seu ângulo e distância relativos ao centro da imagem (posição do robô).
Fase 3: Coleta de Métricas e Otimização Serão realizados experimentos práticos medindo:
Latência (ms): Tempo entre captura e saída da coordenada.
Taxa de Acerto (%): Eficácia da detecção em diferentes distâncias (0.5m a 2.0m).
FPS: Fluidez do processamento de vídeo. O objetivo é encontrar o equilíbrio ideal entre resolução da imagem e velocidade de processamento.

CONCEITOS TEÓRICOS / TRABALHOS RELACIONADOS
Visão Computacional Embarcada e TinyML
	A visão computacional embarcada difere da tradicional por processar os dados na "borda" (Edge), sem envio para a nuvem. Isso elimina a latência de rede, crucial para robôs que precisam reagir em milissegundos. O TinyML viabiliza esse processamento em hardware restrito através da quantização de modelos (redução da precisão numérica para economizar memória), conforme descrito por Warden e Situnayake (2019).
Segmentação por Cor no Espaço HSV
	Para aplicações de alta velocidade como o futebol de robôs, redes neurais profundas podem ser lentas em microcontroladores. A segmentação por cor no espaço HSV é uma técnica eficiente que separa a cromaticidade (cor) da luminosidade (brilho). Como a bola oficial de competições possui uma cor laranja padronizada, esta técnica permite uma detecção rápida e robusta com baixo custo computacional.
Sistemas de Visão Omnidirecional (Catadióptricos)
	Sistemas catadióptricos combinam lentes (dióptricos) e espelhos (catóptricos). O uso de um espelho convexo alinhado ao eixo óptico da câmera permite capturar uma imagem de 360 graus em um único frame. Embora a imagem resultante sofra distorções radiais, ela contém informações de todo o entorno do robô, permitindo que ele "veja" o gol adversário e a bola simultaneamente sem precisar girar o chassi.
CRONOGRAMA
Tabela 1 – Cronograma de Atividades
Períodos
Atividades
AGO 20xx
SET 20xx
OUT 20xx
NOV 20xx
DEZ 20xx
JAN 20xx
1
2
1
2
1
2
1
2
1
2
1
2
Levantar literatura 
X
X
X
X
X














Elaborar Projeto
X
X
X


















Coletar os dados


X
X
X
X
X












Tratar os dados






X
X
X
X
X
X






Elaborar a monografia












X
X
X
X
X


Revisar o texto
















X
X
X


Entregar o trabalho






















X
























X
Desenvolvimento
Fase 1




















X
X





Períodos
Atividades
FEV 2026
MAR 2026
ABR 2026
MAIO 2026
JUN 2026
JUL 2026
1
2
1
2
1
2
1
2
1
2
1
2
Desenvolvimento
Fase 1
X
X




















Desenvolvimento
Fase 2


X
X
X
















Desenvolvimento
Fase 3




X
X
















Teste prático com equipe da RoboCup








X
X






































Revisar o texto
























Entregar o trabalho
























Defesa da monografia





















































REFERÊNCIAS
BANBURY, C. R. et al. MicroNets: Neural Network Architectures for Deploying TinyML Applications on Commodity Microcontrollers. In: Proceedings of Machine Learning and Systems (MLSys), v. 3, p. 517-532, 2021. Disponível em: https://arxiv.org/pdf/2010.11267. Acesso em: 15 nov. 2025.
BONARDI, F. et al. Embedded Vision System for Real-Time Object Tracking Using an Asynchronous Transient Vision Sensor. In: International Conference on Computer Vision Systems (ICVS), p. 125-135, 2015. Disponível em: http://www.belbachir.info/PDF/dsp2006.pdf. Acesso em: 15 nov. 2025.
BROWNING, B. et al. RoboCup Small Size League: Past, Present and Future. In: RoboCup 2019: Robot World Cup XXIII. Springer, Cham, p. 611-623, 2019.
CHEN, J.; RAN, X. Deep Learning with Edge Computing: A Review. Proceedings of the IEEE, v. 107, n. 8, p. 1655-1674, ago. 2019. Disponível em: https://ieeexplore.ieee.org/document/8763885. Acesso em: 15 nov. 2025.
ESPRESSIF SYSTEMS. ESP32-S3 Series Datasheet. Version 1.0. Shanghai: Espressif Systems, 2021. Disponível em: https://documentation.espressif.com/esp32-s3_datasheet_en.pdf. Acesso em: 15 nov. 2025.
KITANO, H. et al. RoboCup: The Robot World Cup Initiative. In: Proceedings of the First International Conference on Autonomous Agents (AGENTS'97), p. 340-347, Marina del Rey, CA, USA, 1997. ACM Press.
LIN, J. et al. MCUNet: Tiny Deep Learning on IoT Devices. In: Advances in Neural Information Processing Systems (NeurIPS), v. 33, p. 11711-11722, 2020.
MÜHLENBROCK, D. et al. Detecting and Tracking Robots in Real-Time Using RGB-D Data. In: RoboCup 2018: Robot World Cup XXII. Springer, Cham, p. 147-158, 2018.
WARDEN, P.; SITUNAYAKE, D. TinyML: Machine Learning with TensorFlow Lite on Arduino and Ultra-Low-Power Microcontrollers. Sebastopol, CA: O'Reilly Media, 2019.


APÊNDICES

QUESTIONÁRIOS E/OU ENTREVISTAS
