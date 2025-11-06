
2

Automatic Zoom
BACHARELADO EM SISTEMAS DE INFORMAÇÃO
REGULAMENTO DE TRABALHO DE CONCLUSÃO DE CURSO
ANEXO II
SÚMULA DE PROJETO DE PESQUISA
BRENDON SOUSA LIMA
Sistema de Visão Computacional Embarcado para
Robótica Autônoma de Baixo Custo
Pré-projeto de pesquisa desenvolvido na linha
de pesquisa de desenvolvimento de sistemas
embarcados, sob orientação do(a) Prof(ª).
Andrique Figueirêdo Amorim, como requisito
de inscrição no componente curricular de
Trabalho de Conclusão de Curso I, do Curso de
Bacharelado em Sistemas de Informação, do
Instituto Federal de Educação, Ciência e
Tecnologia da Bahia, Campus Vitória da
Conquista
Vitória da Conquista, 2025
BACHARELADO EM SISTEMAS DE INFORMAÇÃO
REGULAMENTO DE TRABALHO DE CONCLUSÃO DE CURSO
ANEXO II
SÚMULA DE PROJETO DE PESQUISA
1. Introdução e Contextualização do Problema de Pesquisa
1.1 A Ascensão da Inteligência Artificial na Borda (Edge AI) e o Paradigma da TinyML
A inteligência artificial tem se expandido para além dos servidores de alta potência e
ambientes de nuvem, atingindo a fronteira dos dispositivos. Esse movimento é conhecido
como Edge AI e tem sido impulsionado pela necessidade de processamento local de
dados para aplicações que exigem baixa latência, alta privacidade e eficiência
energética.1 Nesse contexto, a disciplina do
Tiny Machine Learning (TinyML) surge como uma nova fronteira, focada em "espremer"
modelos de aprendizado de máquina para que operem em dispositivos diminutos, como
microcontroladores (MCUs), que possuem apenas algumas centenas de kilobytes de
memória.1
A ascensão do TinyML não é apenas um avanço tecnológico, mas uma resposta a um
imperativo de processamento de dados. Com bilhões de dispositivos IoT gerando volumes
massivos de dados, a dependência de servidores na nuvem para a inferência se torna um
gargalo de desempenho, latência e segurança.1 O processamento na borda permite a
tomada de decisões em tempo real sem a necessidade de comunicação de rede, o que é
vital para aplicações como veículos autônomos e robótica.1 O projeto aqui proposto se
insere diretamente nessa tendência, posicionando a robótica autônoma no centro da
evolução da Edge AI.
Contudo, a implementação de modelos de aprendizado profundo em dispositivos
embarcados de recursos limitados não é trivial. A pesquisa no campo do TinyML indica
que a principal restrição não é o número de parâmetros do modelo, mas sim a memória
de ativação.1 Isso significa que modelos originalmente projetados para plataformas
móveis ou de nuvem, como os MobileNets ou ResNets, não se adequam de forma
eficiente aos dispositivos minúsculos.1 Dessa forma, o sucesso de uma aplicação de
TinyML depende de um "co-design" — um design conjunto e otimizado do algoritmo e da
arquitetura do sistema.1 A presente proposta, ao focar na otimização de um modelo de
visão computacional especificamente para as restrições e capacidades do ESP32-S3,
adere a essa abordagem de pesquisa de ponta.
BACHARELADO EM SISTEMAS DE INFORMAÇÃO
REGULAMENTO DE TRABALHO DE CONCLUSÃO DE CURSO
ANEXO II
SÚMULA DE PROJETO DE PESQUISA
1.2 A Robótica Autônoma em Ambientes Dinâmicos: O Caso do Futebol de Robôs
A robótica autônoma, especialmente em ambientes dinâmicos e imprevisíveis, como um
campo de futebol, representa um desafio complexo e relevante no avanço da inteligência
artificial e da mecatrônica.4 A capacidade de um robô de detectar, rastrear e interagir com
objetos em movimento, como uma bola, é central para o desenvolvimento de sistemas de
percepção visual e controle de movimento. Competições como a
RoboCup Small Size League servem como um domínio de pesquisa crucial,
impulsionando a inovação em coordenação multi-agentes e controle em tempo real.6
Uma distinção fundamental na pesquisa em robótica de futebol é a arquitetura do sistema
de visão. Ligas tradicionais como a RoboCup SSL utilizam frequentemente um sistema de
visão centralizado, externo ao campo, que processa a imagem de várias câmeras e
transmite os dados de posição dos objetos aos robôs.6 Essa abordagem oferece uma
visão global e completa do ambiente de jogo.7
Em contraste, a presente proposta explora uma arquitetura de visão embarcada e
on-board, onde o próprio robô é responsável por sua percepção. Essa abordagem
enfrenta um desafio mais significativo e, de certa forma, mais realista.8 A visão embarcada
limita o campo de visão do robô, e o sistema de percepção deve lidar com movimentos
bruscos, tremores e iluminação variável do ambiente.8 A pesquisa proposta não apenas
desenvolve um sistema de visão, mas aprofunda a autonomia de percepção a um nível
mais complexo. Nesse cenário, a baixa latência proporcionada pelo TinyML e pelo
processamento on-chip se torna não apenas uma vantagem, mas um requisito
fundamental para a viabilidade do projeto, permitindo que o robô reaja a eventos em
tempo real, sem o atraso da comunicação externa.
