# Pipeline de Extração de Respostas em Folhas de Gabarito

#### Aluno: [Gustavo Teixeira](https://github.com/gustavoteixeirah)
#### Orientador: [Vitor](https://github.com/link_do_github).

---

Trabalho apresentado ao curso [VC MASTER](https://ica.puc-rio.ai/vc-master) como pré-requisito para conclusão de curso e obtenção de crédito na disciplina "Projetos de Sistemas Inteligentes de Apoio à Decisão".

<!-- para os links a seguir, caso os arquivos estejam no mesmo repositório que este README, não há necessidade de incluir o link completo: basta incluir o nome do arquivo, com extensão, que o GitHub completa o link corretamente -->


- Trabalhos relacionados: <!-- caso não aplicável, remover estas linhas -->
    - [Nome do Trabalho 1](https://link_do_trabalho.com).
    - [Nome do Trabalho 2](https://link_do_trabalho.com).

---
### Resumo

Este trabalho apresenta o desenvolvimento de uma pipeline de visão computacional para a extração automática de respostas marcadas em folhas de gabarito (answer sheets) de provas de múltipla escolha. O sistema recebe como entrada uma fotografia da folha de respostas preenchida pelo aluno, capturada por dispositivo móvel ou digitalizada, e retorna a relação de alternativas marcadas para cada questão (letras de A a E). A saída contempla diferentes cenários: uma única alternativa marcada, múltiplas alternativas marcadas na mesma questão, nenhuma alternativa marcada, ou falha na detecção. A solução combina técnicas clássicas de processamento de imagens, como transformação de perspectiva, detecção de bordas (Canny) e Transformada Circular de Hough, com modelos modernos de deep learning baseados na arquitetura YOLO (You Only Look Once) para detecção de objetos. O pipeline inclui etapas de alinhamento da imagem, detecção e decodificação de QR Code para identificação do modelo de gabarito, localização de grupos de questões, detecção de círculos marcados e não marcados, e reconhecimento óptico dos números das questões. O sistema foi projetado visando baixo custo computacional, baixa latência e alta confiabilidade, sendo aplicável como componente de sistemas educacionais que necessitam extrair respostas de provas objetivas em larga escala.

### Abstract

This work presents the development of a computer vision pipeline for automatic extraction of marked answers from multiple-choice answer sheets. The system receives as input a photograph of a filled answer sheet, captured by a mobile device or scanned, and returns the list of marked alternatives for each question (letters A through E). The output covers different scenarios: a single marked alternative, multiple alternatives marked for the same question, no marked alternative, or detection failure. The solution combines classical image processing techniques, such as perspective transformation, edge detection (Canny), and Hough Circle Transform, with modern deep learning models based on the YOLO (You Only Look Once) architecture for object detection. The processing pipeline includes image alignment stages, QR Code detection and decoding to identify the answer sheet template, localization of question groups, detection of marked and unmarked circles, and optical character recognition of question numbers. The system was designed with a focus on low computational cost, low latency, and high reliability, making it applicable as a component in educational systems that require large-scale answer extraction from objective tests.

### 1. Introdução

A leitura manual de respostas em folhas de gabarito é uma tarefa repetitiva, demorada e propensa a erros humanos, especialmente quando realizada em larga escala. Em instituições de ensino, vestibulares e concursos públicos, milhares de folhas de respostas precisam ser processadas em curto período de tempo, demandando soluções automatizadas eficientes para extração das marcações. O reconhecimento óptico de marcas (OMR - Optical Mark Recognition) surge como uma solução tecnológica para este problema, permitindo a leitura automática de formulários preenchidos.

Tradicionalmente, sistemas OMR requerem leitoras ópticas dedicadas e formulários específicos impressos em papel especial, o que encarece significativamente a implementação. Com o avanço das técnicas de visão computacional e a popularização de dispositivos móveis com câmeras de alta resolução, tornou-se viável desenvolver soluções baseadas em software que processam imagens capturadas por smartphones ou scanners convencionais.

O presente trabalho propõe o desenvolvimento de uma pipeline de extração de respostas marcadas em folhas de gabarito, utilizando apenas uma imagem de entrada sem necessidade de hardware especializado. O sistema emprega uma combinação de técnicas clássicas de processamento de imagens para pré-processamento e alinhamento, modelos YOLO treinados para detecção de círculos e grupos de questões, e algoritmos de inferência para determinação das alternativas marcadas. A saída do sistema é uma estrutura de dados contendo, para cada questão, as letras marcadas (de A a E), podendo incluir: uma única marcação, múltiplas marcações, nenhuma marcação, ou indicação de falha na detecção.

Os principais objetivos do sistema são: (1) robustez a variações de iluminação e ângulo de captura da imagem; (2) baixo tempo de processamento para viabilizar uso em tempo real; (3) alta precisão na identificação das marcações; e (4) flexibilidade para diferentes formatos de gabarito através do uso de QR Codes identificadores.

### 2. Modelagem

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin pulvinar nisl vestibulum tortor fringilla, eget imperdiet neque condimentum. Proin vitae augue in nulla vehicula porttitor sit amet quis sapien. Nam rutrum mollis ligula, et semper justo maximus accumsan. Integer scelerisque egestas arcu, ac laoreet odio aliquet at. Sed sed bibendum dolor. Vestibulum commodo sodales erat, ut placerat nulla vulputate eu. In hac habitasse platea dictumst. Cras interdum bibendum sapien a vehicula.

Proin feugiat nulla sem. Phasellus consequat tellus a ex aliquet, quis convallis turpis blandit. Quisque auctor condimentum justo vitae pulvinar. Donec in dictum purus. Vivamus vitae aliquam ligula, at suscipit ipsum. Quisque in dolor auctor tortor facilisis maximus. Donec dapibus leo sed tincidunt aliquam.

### 3. Resultados

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin pulvinar nisl vestibulum tortor fringilla, eget imperdiet neque condimentum. Proin vitae augue in nulla vehicula porttitor sit amet quis sapien. Nam rutrum mollis ligula, et semper justo maximus accumsan. Integer scelerisque egestas arcu, ac laoreet odio aliquet at. Sed sed bibendum dolor. Vestibulum commodo sodales erat, ut placerat nulla vulputate eu. In hac habitasse platea dictumst. Cras interdum bibendum sapien a vehicula.

Proin feugiat nulla sem. Phasellus consequat tellus a ex aliquet, quis convallis turpis blandit. Quisque auctor condimentum justo vitae pulvinar. Donec in dictum purus. Vivamus vitae aliquam ligula, at suscipit ipsum. Quisque in dolor auctor tortor facilisis maximus. Donec dapibus leo sed tincidunt aliquam.

### 4. Conclusões

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin pulvinar nisl vestibulum tortor fringilla, eget imperdiet neque condimentum. Proin vitae augue in nulla vehicula porttitor sit amet quis sapien. Nam rutrum mollis ligula, et semper justo maximus accumsan. Integer scelerisque egestas arcu, ac laoreet odio aliquet at. Sed sed bibendum dolor. Vestibulum commodo sodales erat, ut placerat nulla vulputate eu. In hac habitasse platea dictumst. Cras interdum bibendum sapien a vehicula.

Proin feugiat nulla sem. Phasellus consequat tellus a ex aliquet, quis convallis turpis blandit. Quisque auctor condimentum justo vitae pulvinar. Donec in dictum purus. Vivamus vitae aliquam ligula, at suscipit ipsum. Quisque in dolor auctor tortor facilisis maximus. Donec dapibus leo sed tincidunt aliquam.

---

Matrícula: 123.456.789

Pontifícia Universidade Católica do Rio de Janeiro

Curso de Pós Graduação *Visão Computacional Master*
