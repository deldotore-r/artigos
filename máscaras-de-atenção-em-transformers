---
title: "As máscaras de atenção em transformers: funções e funcionament"
date: 2025-04-22
tags: [IA, Saúde, Transformação Digital]
---


As máscaras de atenção em transformers: funções e funcionamento
Reinaldo Del Dotore

Oficial Dentista Militar (Reformado) | Em transição para Inteligência Artificial Aplicada à Saúde

22 de abril de 2025

A arquitetura Transformer revolucionou o processamento de linguagem natural, graças, principalmente, à inovadora utilização do Mecanismo de Atenção, como expliquei neste artigo.

Nesse mecanismo, há um elemento fundamental, ainda que muito menos discutido: a máscara de atenção. Vamos explorar o que é, como funciona e por que é tão importante.



O que é uma Máscara de Atenção?

Uma máscara de atenção é, em poucas palavras, uma matriz de valores que determina quais palavras podem "olhar" para quais outras palavras durante o processamento em uma cabeça de atenção. Funciona como um filtro, que controla o fluxo de informação entre tokens (palavras ou pedaços de palavras) em um modelo Transformer.



Para que ela serve?

A máscara de atenção tem duas funções principais:



1) Ignorar padding: Como as sequências de entrada geralmente têm tamanhos variados, adicionamos "padding" (tokens vazios) para criar lotes uniformes (para que as matrizes de entrada não tenham vetores de comprimentos diferentes, o que inviabilizaria os cálculos). 

A máscara permite que o modelo ignore esses tokens artificiais: a matriz da máscara utiliza valores específicos para multiplicar os paddings, de forma que os valores resultantes sejam zero ou praticamente zero.



2) Impedir "vazamento de informação": Em tarefas como geração de texto, impede que o modelo enxergue palavras futuras (que ainda não foram geradas) durante a fase de treinamento. O objetivo, ao treinar o modelo, é "forçar o aprendizado", e não "entregar o prato feito". 



Como funciona tecnicamente?

No cerne do mecanismo de atenção, calculamos pontuações que indicam quanto cada palavra deve "prestar atenção" em todas as outras palavras. A fórmula básica é:

Attention(Q, K, V) = softmax(QK^T / √dk) × V



A máscara de atenção entra em jogo logo antes da função softmax:

Attention(Q, K, V) = softmax((QK^T / √dk) + Mask) × V

Onde: Q (Query), K (Key) e V (Value) são matrizes derivadas da entrada.



Conteúdo do artigo
A máscara no mecanismo de atenção. Imagem adaptada de Data Science Academy Brasil


Tipos de máscaras de atenção

Explorando um pouco mais os dois tipos de máscaras de atenção descritos anteriormente:



1) Máscara de padding: Substitui os valores correspondentes aos tokens de padding por valores muito negativos (como -10000), fazendo com que após o softmax, esses valores se aproximem de zero, sendo efetivamente ignorados. É utilizada nos codificadores e nos codificadores-decodificadores (camada do decodificador que, além dos tokens de entrada, recebe também o output do codificador).



2) Máscara causal (ou auto-regressiva): Usada principalmente em decodificadores, impede que uma posição acesse informações de posições futuras. É uma matriz triangular inferior, onde cada token só pode ver a si mesmo e os tokens anteriores.



Um exemplo simples

Imagine que estamos processando a frase: "O gato comeu o rato".

Vamos explicitar os índices desse array: [ 0:"O", 1:"gato", 2:"comeu", 3:"o", 4:"rato" ]



Máscara de padding:

Se adicionarmos padding para atingir comprimento 7 (lembrando que o primeiro índice do array é 0, logo, o sétimo índice é 6):

[ 0:"O", 1:"gato", 2:"comeu", 3:"o", 4:"rato", 5, 6]



Nossa máscara de padding seria:

[ 0, 0, 0, 0, 0, -∞, -∞]



Onde 0 significa "permitido olhar" e -∞ (na prática, um número muito negativo) significa "ignorar".



Máscara causal:

Se estivéssemos gerando esta frase token por token, a máscara causal seria a matriz triangular inferior :



[[ 0, -∞, -∞, -∞, -∞],

 [ 0, 0, -∞, -∞, -∞],

 [ 0, 0, 0, -∞, -∞],

 [ 0, 0, 0, 0, -∞],

 [ 0, 0, 0, 0, 0]]



Isso significa que:

Ao processar "O", o modelo não vê nenhuma palavra futura;

Ao processar "gato", o modelo vê "O" e "gato";

Ao processar "comeu", o modelo vê "O", "gato" e "comeu";

E assim por diante.

Conteúdo do artigo
Crédito da imagem: krypticmouse.hashnode.dev
A máscara de atenção é mesmo tão importante?

A máscara de atenção é fundamental para:



✔️ Eficiência computacional: Direciona o modelo a focar apenas em tokens relevantes.

✔️ Capacidade generativa: Permite que modelos como GPT gerem texto coerente sem "trapacear".

✔️ Processamento de lotes: Viabiliza treinamento eficiente com sequências de diferentes comprimentos.



Compreender esse componente aparentemente simples nos ajuda a entender uma parte fundamental da eficácia que caracteriza os modelos de linguagem que revolucionaram a IA.



#InteligênciaArtificial #MachineLearning #Transformers #DeepLearning #IA #AI
