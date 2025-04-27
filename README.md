
# Trabalho prático - Técnicas de desenvolvimento de videojogos.

David Querido 33219

Gabriel Solinos 31487

Paulo Pinto 31474

## Análise do jogo "Bubble Trouble"
Bubble Trouble é um jogo bidimensional com inteligência artificial(Bot) na qual dois jogadores competem entre si, neste caso, o jogador e a inteligência artificial. O objetivo principal do jogo é acertar o máximo de bolas possíveis para obter uma pontuação mais alta. Ambos os jogadores têm um determinado valor para a sua saúde e também para os pontos. O jogo termina assim que um dos jogadores fica sem vida ou quando o tempo acabar e o jogador com a pontuação mais alta vence.

## Progressão no jogo
No jogo, existem bolas de 4 cores (vermelha, azul, amarela e preta). A bola vermelha pertence a nós, enquanto que a bola azul pertence ao adversário. A bola amarela pertence a ambos os jogadores e tem como objetivo adicionar alguma ação. A bola preta é uma bola rolante que surge a cada meio minuto e que não pode ser rebatida, sendo o seu objetivo atingir as pernas dos jogadores e reduzir a saúde dos mesmos.
Um tiro só pode ser disparado quando não houver balas no ar. Um jogador só pode disparar uma flecha enquanto estiver parado no chão e imóvel. Acertar em qualquer uma das bolas (vermelha, azul ou amarela) fará com que a bola expluda em duas bolas menores. Se um dos jogadores acertar na bola do adversário, não fará com que ela expluda.
Durante o jogo, caixas irão cair do céu. Existem 5 tipos de caixas: mais saúde, menos saúde, mais pontuação, menos pontuação, mais tiros e uma para congelar o jogador. Ao apanhar uma caixa "mais tiros", pode disparar vários tiros ao mesmo tempo (até 3 tiros). As caixas "menos/mais pontuação/saúde" diminuem ou aumentam 50 pontos/saúde, respetivamente. A caixa que congela o jogador impede os seus movimentos durante alguns segundos.
O jogo tem uma duração de 120 segundos e cada jogador começa com 1000 pontos de saúde. Um tiro normal dá ao jogador 50 pontos, mas se a bola o atingir, perde 50 pontos de saúde. A bola amarela é especial, pois a saúde que tira e os pontos que oferece são números aleatórios entre 0 e 100. Já a bola preta reduz a saúde em 20 pontos.
O jogo termina se o tempo acabar ou se um dos jogadores ficar sem saúde.

## Comandos para o jogo
### Movimentos:
Movimentar para a direita - Pressionar a seta direita.

Movimentar para a esquerda - Pressionar a seta esquerda.

Saltar - Pressionar a seta para cima.

Atirar - Pressionar a tecla "Espaço".

## Pasta Content - Pasta que contém ficheiros .png, .mgcontent e .xnb
Na pasta "Content", encontramos as pastas "Goblin", "Man", "Naruto" (personagens jogáveis) e "SurpriseBox" (itens do jogo) que contém PNGs dos diversos backgrounds do jogo, telas inicial e de resultados (vitória, empate ou derrota), spritesheets para as animações das ações do jogador (idle, walk e fire) e os botões (exit e play). Ainda na pasta "Content", encontramos as pastas "bin" e "obj", que ambas possuem os mesmos conteúdos das quatro pastas mecionadas anteriormente, agora em formatos .xnb e .mgcontent, respetivamente. Estas duas pastas são geradas automáticamente durante a compilação do projeto e servem para converter os ficheiros .png em formato binário, otimizando-os para serem carregados o mais rapidamente possível durante a execução do jogo. Por fim, temos três ficheiros:

-.DS_Store é um ficheiro gerado automáticamente pelo macOS para armazenar informações de visualização de pastas;

-Content.mgcb diz ao MonoGame quais recursos precisam ser convertidos em .xnb;

-SpriteFont1.spritefont é um template XML que define uma fonte de texto que o jogo pode usar.

## ProjectStates - Pasta que guarda os diferentes estados do jogo
EndState.cs - Ficheiro que produz a tela do fim do jogo;

GameState.cs - Ficheiro que produz o estado principal do jogo, responsável pela lógica e física do mesmo;

MenuState.cs - Ficheiro que produz a tela do menu principal;

State.cs - Ficheiro que serve como base para os outros estados.

## Classes:
### Animation.cs:
A classe Animation representa as animações no contexto de um jogo. É responsável pela gestão dos frames, pelo controlo e pelas transições das animações. A classe possui vários construtores que inicializam as animações com diferentes parâmetros, tais como o personagem, estado, posição, cor, rotação, escala e profundidade.Além disso, a classe atualiza as texturas, as regiões de recorte (SourceRectangle) e gere a transição entre os frames com base no ritmo (pace) da animação. Em cada atualização, ajusta as propriedades visuais e desenha o frame atual no ecrã. Assim, a classe Animation é utilizada para criar e gerir as animações no jogo.

### Ball.cs:
A classe Ball representa a lógica das bolas que interagem com o ambiente. Contém os atributos principais, como velocity (velocidade da bola nos eixos X e Y), gravitation (gravidade aplicada à bola), points e health (pontuação e vida da bola), uniqueColor (cor única da bola) e countHitsWall (contador de colisões com as paredes). Esta classe atualiza a posição da bola com base na sua velocidade, verifica as colisões com as bordas do ecrã e com o chão, invertendo a direção da velocidade quando necessário, e incrementa o contador de colisões. Trata também das colisões com outros objetos do jogo, ajustando a direção da bola de acordo com a posição da colisão e atualizando os atributos do objeto atingido, como a cor e a vida restante. Em resumo, a classe gere o comportamento das bolas no jogo, incluindo movimentação e colisões, e implementa um sistema de física simplificado com eventos de colisão.

### BotKeyboard:
A classe BotKeyboard implementa o controlo automatizado para a inteligência artificial (bot). Esta classe associa as entradas (teclas pressionadas ou soltas) ao controlo da personagem, permitindo simular interações de teclado para um robô (bot). Dessa forma, o bot consegue movimentar-se, saltar, disparar e reagir a eventos do jogo. A classe apresenta variáveis que gerem o comportamento do bot, como a capacidade de disparar, procurar alvos e movimentar-se. Além disso, atualiza o estado do bot a cada frame, incluindo reações às bolas pretas (blackBall), como saltar para evitar colisões, encontrar a bola mais próxima, decidir os movimentos e determinar quando disparar com base na posição e direção do alvo.
Esta classe também permite ao bot ajustar a sua direção com base na posição do alvo e no movimento deste. O bot decide disparar quando a distância em relação ao alvo é suficientemente curta. Em resumo, a classe BotKeyboard é responsável por implementar comportamentos autónomos no bot, como movimentação, saltos e disparos, utilizando a lógica programada.

### Button.cs:
A classe Button representa os botões interativos na interface do jogo, permitindo que os jogadores interajam com eles através do "rato". A classe é responsável por desenhar um botão no ecrã utilizando uma textura (Texture2D) e, opcionalmente, um texto adicional (string Text) que pode ser exibido sobre os botões. Ela deteta interações do "rato", como passar o cursor sobre o botão ou clicar nele, e gere essas interações utilizando o estado atual e anterior do "rato" (MouseState). A lógica da classe verifica se o cursor do "rato" está dentro da área do botão (Rectangle) e ajusta a sua cor para cinzento, indicando que o botão está em foco, disparando o evento Click quando este é clicado. Em resumo, a classe Button é uma componente essencial para a criação de interfaces do utilizador no jogo, permitindo interações através dos cliques do "rato" e oferecendo personalização e feedback visual ao jogador.

### Camera.cs:
A classe Camera é responsável por gerir a lógica de transformação e a escala da visão da câmara em relação ao mundo do jogo. A matriz Mat é utilizada para calcular a posição e a escala da câmara no mundo 2D do jogo, transformando a posição dos objetos no mundo para a perspetiva da câmara. A câmara foi projetada para seguir um objeto específico no jogo, definido pela interface IFocus, e a sua posição é interpolada suavemente para garantir movimentos fluídos ao acompanhar o objeto. Existe uma lógica que restringe a posição da câmara dentro de limites específicos, evitando que esta mostre áreas fora do mapa do jogo. Além disso, a câmara responde às interações com o "rato" para ajustar o zoom. Esta classe é essencial para proporcionar uma experiência fluída ao jogador, ajustando dinamicamente a visualização do mundo do jogo com base no foco e nas interações do jogador.

### Drawable.cs:
A classe Drawable serve como uma base para representar elementos visuais no jogo. Contém propriedades essenciais para desenhar sprites, como Texture (textura do sprite), Position (posição do objeto no ecrã), color (cor aplicada ao sprite), rotation (rotação do sprite), scale (tamanho do sprite), layerDepth (profundidade da camada para renderização) e SourceRectangle e destinationRectangle (que gerem cortes ou escalas na textura).
Esta classe é responsável por renderizar o objeto no ecrã, desde que a propriedade isDraw esteja ativa. Permite criar objetos com diferentes conjuntos de parâmetros, facilitando a flexibilidade e a reutilização em diversos contextos. A classe é utilizada para simplificar a manipulação de elementos visuais no jogo, centralizando as propriedades e os métodos de renderização.

### Fire.cs:
A classe Fire no jogo representa o ato de disparar, interagindo com outros elementos do jogo. Esta classe implementa mecanismos para verificar colisões e atualizar o seu estado. Possui a propriedade BallColor, que define a cor da bola associada ao objeto para verificar colisões específicas, e a propriedade shooter, que é uma referência ao objeto que dispara o fogo, gerindo interações como a contagem de tiros (fireCount).
A classe verifica se o fogo colide com uma bola utilizando retângulos de interseção, realizando ações dependendo da cor da bola, como removê-las do jogo, dividir bolas maiores em bolas menores e atualizar a pontuação do jogador. Além disso, desativa a exibição do objeto após a colisão ou caso atinja o limite superior do ecrã. Assim, a classe desempenha um papel essencial na mecânica de disparo do jogo, interagindo com as bolas para aplicar efeitos como remoção ou divisão, além de gerir a lógica visual e de colisão do fogo.

### GameObject.cs:
A classe GameObject no jogo representa a nossa personagem e as funcionalidades relacionadas ao controlo, movimentação, interações físicas e ações, bem como a gestão das animações da personagem. Define atributos como a posição (Position), cor (ballColor), movimentação (velocityX, velocityY), aceleração (accelerationY) e o estado da personagem (animações e disparos). Gere o número de disparos (fireCount, maxFireCount) e interações como o tempo de congelamento (freezeTime) e atrasos no disparo (shootDelay). A classe gere a entrada do jogador através do teclado e define a movimentação e as ações, como disparar (SpacePressed). Além disso, atualiza a animação e a direção da personagem com base nas teclas pressionadas, calculando o movimento horizontal e vertical da personagem, aplicando os efeitos da gravidade e garantindo que a personagem não ultrapasse as bordas do ecrã ou o limite do chão. Existe também a gestão de colisões entre a personagem e outros objetos, ajustando a posição da personagem conforme necessário. Esta classe é responsável por implementar a lógica principal de movimentação e interação da personagem.

### MyKeyBoard.cs:
A classe MyKeyBoard define duas classes relacionadas ao controlo das entradas do teclado no jogo: BaseKeys e UserKeys. A classe BaseKeys é responsável pela manipulação das entradas do teclado que representam as ações básicas do jogador, como pressionar ou soltar teclas direcionais, correr e disparar, funcionando como uma interface para implementar controlos personalizados. Por outro lado, a classe UserKeys fornece uma implementação concreta para as ações do teclado, utilizando o estado atual do teclado. Permite mapear teclas específicas para ações no jogo, como mover para a direita/esquerda, correr ou disparar. Estas duas classes, em conjunto, são responsáveis por gerir as entradas do teclado no jogo.

### Page.cs:
A classe Page é projetada para gerir os dados visuais e as animações da personagem em diferentes estados, realizando o carregamento de texturas e dividindo a imagem em retângulos que representam os frames da animação. Define o ritmo (Tempo) da animação com base no estado da personagem, sendo que, neste caso, todos os estados partilham o mesmo ritmo (Tempo.Slow). Esta classe consegue tornar transparentes as áreas da textura que correspondem à cor de fundo, garantindo que apenas os elementos visuais relevantes sejam exibidos. A classe Page é essencial para gerir a animação da personagem no jogo, separando e organizando os frames da animação a partir de uma única textura e ajustando as propriedades de renderização para uma apresentação adequada no jogo.

### S.cs:
A classe S centraliza os dados e os métodos partilhados utilizados em várias partes do jogo. Aqui estão as suas principais características e propósitos: a classe armazena dados globais através de propriedades estáticas que contêm objetos e valores amplamente utilizados, como SpriteBatch (sb) para desenhar sprites, ContentManager (cm) para carregar recursos, e as dimensões do ecrã (screenWidth, screenHeight). Define enumerações para categorizar ou controlar comportamentos no jogo. Além disso, a classe manipula recursos e o estado do jogo, como, por exemplo, criar uma linha no solo baseada numa textura carregada, que é utilizada para calcular colisões ou interações com o chão no jogo. A classe serve como um ponto de acesso global para variáveis necessárias em diferentes partes do jogo. Em resumo, a classe S atua como um repositório central para variáveis e recursos essenciais ao funcionamento do jogo, facilitando a organização e o acesso a dados partilhados.

### SurpriseBox.cs:
A classe SurpriseBox representa as caixas surpresa no jogo. O seu principal objetivo é interagir com o jogador e aplicar efeitos dependendo do tipo de surpresa contida na caixa. A classe possui atributos como gravitation, que controla o efeito da gravidade sobre a caixa, drc, que define a direção de movimento da caixa, timeDisappearBox, que representa o tempo restante para a caixa desaparecer, e numOfBox, que identifica o tipo de surpresa associada à caixa. Esta classe atualiza a posição da caixa considerando a gravidade, aplicando-a caso a caixa esteja ativa (isDraw). Verifica também se a caixa atingiu o chão e, caso o tempo para desaparecer seja atingido, desativa a caixa. Existe ainda uma função para detetar colisões entre a caixa e outros objetos do jogo. Quando uma colisão é detetada, a caixa é desativada e um efeito é aplicado com base no valor de numOfBox. Além disso, a cor do objeto que colidiu é alterada para amarelo. Em resumo, a classe SurpriseBox adiciona elementos de interação e surpresa ao jogo, simulando o comportamento físico da caixa (gravidade e movimento), detetando colisões e aplicando efeitos dinâmicos que enriquecem a jogabilidade.

### TheDic.cs:
A classe TheDic serve como um repositório para armazenar e gerir as informações relacionadas com as personagens e os seus estados (States). Esta classe utiliza um dicionário para organizar as páginas associadas a cada combinação de personagem e estado, iterando sobre todos os heróis e estados definidos nas enumerações Heros e States. Para cada combinação de personagem e estado, verifica-se se existe um ficheiro correspondente no diretório /Content/<hero>/<state>.xnb. Caso o ficheiro exista, é criado um objeto Page para essa combinação, que é então adicionado ao dicionário. Isto permite gerir facilmente os recursos associados às personagens e aos estados no jogo, como animações ou texturas. Em resumo, a classe TheDic organiza e gere os dados das personagens e dos seus estados, carregando os recursos de forma dinâmica e armazenando-os numa estrutura que facilita a gestão eficiente de recursos no jogo.

## Análise a partes do código
### SurpriseBox.cs
Ficheiro responsável pela criação de, como o nome indica, uma "caixa surpresa" que interage com o jogador e aplica efeitos diferentes quando 		ocorre uma colisão.
	
- Variáveis
  
	![image_2025-04-25_170421579](https://github.com/user-attachments/assets/40f0d96f-e9c5-4b3d-8dce-9ee12e15dbcd)

	gravitation: Simula a gravidade;
    
	drc: Direção do movimento;

	timeDisappearBox: Tempo até a caixa desaparecer;

	numOfBox: Tipo da caixa surpresa (cada número corresponde a uma caixa com um efeito differente).

- Construtor
  
	![image_2025-04-25_183746741](https://github.com/user-attachments/assets/1ef078ba-d53c-4272-b16e-6c996e979810)

  	O construtor permite inicializar as variáveis e, para além disso, regista o método Collision no evento GameState.BoxCollision_Event.

- UpdateBox
  
  	![image_2025-04-25_184321135](https://github.com/user-attachments/assets/30506162-a536-4fb3-8fcf-f63419d58ab9)
  
  	Este método chama a função Move e faz um reset à posição da caixa.

- Move
  
  	![image](https://github.com/user-attachments/assets/97c9e6c9-c42e-490b-a7a9-ac2612375a4f)
    
  	Este método chama o procedimento Gravity e mexe na posição do objeto em questão.

- Gravity

   	![image](https://github.com/user-attachments/assets/a29a8672-0194-452d-aa5a-bbfc976bf48a)

   	Gravity, como o próprio nome indica, aumenta a gravidade ao longo do tempo, fazendo uma verificação de se a caixa já atingiu o chão e se o tempo de 	jogo estiver a acabar, desativa o desenho da caixa.

- Collision

   	![image](https://github.com/user-attachments/assets/23d8f7bb-938d-478b-b2d7-48e7cab1af84)

  	Verifica se a caixa colide com um objeto. Se houver, aplica differentes efeitos dependendo do número da caixa (por exemplo, se a o número for o 2, 	adiciona pontos mas se for o 4, congela o tempo de 	jogo). Por fim, muda a cor do objeto para amarelo.

### Fire.cs
Ficheiro responsável pelo projétil disparado pelo jogador / AI.

- Variáveis
  
  	![image](https://github.com/user-attachments/assets/4ec9a567-a5b6-4087-beda-5320bda59e8e)

  	BallColor: Muda a cor da bola;

  	shooter: Variável usada para armazenar quem disparou o projétil;
  
  	ccc: Controla o crescimento vertical do tiro;

- Construtor
  
	![image](https://github.com/user-attachments/assets/35e1afec-ba64-4b6c-b15d-d7b93994be9c)

	O construtor é usado para inicializar as variáveis, e regista os métodos Update e CheckCollision em métodos globais (Update_event e FireCollision_Event, respetivamente)

- CheckCollision
  
	![image](https://github.com/user-attachments/assets/5e76ae91-67a4-4815-97c4-b58e74994296)

 	Cria uma "hitbox" para o projétil e verifica se este tocou no topo da tela ou se colidiu com uma bola. No caso de colidir com algo, o projétil é desativado (isDraw = false) e o nº de tiros do atirador 	diminui (fireCount). Para além disso, se colidir com uma bola, remove-a, adiciona pontos e divide-a em duas bolas menores (se for grande o suficiente para ser dividida).

- Update

  	![image](https://github.com/user-attachments/assets/121ff543-be00-410e-9f99-560fba53255b)

  	No caso do projétil estar ativo, aumenta o tamanho vertical do mesmo por 10 unidades a cada atualização. Se não estiver, dá reset à ccc.

### BotKeyboard.cs
Ficheiro responsável pela criação da lógica de movimento e ação de um bot.

- Variáveis

	![Variáveis](https://github.com/user-attachments/assets/18947661-6fb5-4403-af60-f33432094a42)

	bot: Representa o bot;

	direction: Direção do movimento (esquerda/direita):

	target: Bola alvo que o bot vai tentar atingir;

	targetDist: Distância até ao alvo;

	isShot: Indica se o bot deve disparar;

	shootDelay: Intervalo mínimo entre disparos;

	shootTime: Marca o momento do último disparo;

	findTargetTime: Marca o momento da última procura do alvo;

	findDelay: Intervalo de tempo para procurar novo alvo;

	isJump: Indica se o bot deve saltar.

- Construtor
  
  	![Construtor](https://github.com/user-attachments/assets/ce93a2f0-b8d2-45fa-a423-a5076751908c)

  	Aqui apenas é chamado o construtor da classe base, pelo que não são iniciadas variáveis diretamente.

- InitBot

  	![InitBot](https://github.com/user-attachments/assets/e9e07b54-1798-4005-bf6c-a1d64bc642fa)

  	Inicializa o bot com os seus valores iniciais e chama a função Update assim que estes forem atualizados.

- Input (Override)

  	![InputOverride](https://github.com/user-attachments/assets/3c2e42ac-e6ae-4d27-abcf-4ba7ee84d54a)

  	Servem para simular os botões que o bot pressiona.

- Update

  	![Update](https://github.com/user-attachments/assets/208148e8-2220-45c7-a79c-27c6b90c3143)

  	Esta função atualiza o estado do bot a cada frame permitindo-lhe escolher uma ação com base nas circumstâncias do jogo (saltar, andar, disparar).

- FindClosestBall

  	![findClosestBall](https://github.com/user-attachments/assets/d29e22d4-8252-4a66-94dc-158010a2a0be)

  	Esta função faz o bot procurar pela bola mais próxima. A variável target é atualizada para indicar esta bola como o alvo.

## Defeitos a apontar sobre o jogo
-> No ínicio do jogo, os jogadores não tem uma posição inicial junto ao chão, pelo que "caem do céu";

-> Só se consegue fazer uma ação de cada vez;

-> Não há como escolher personagens e backgrounds diferentes apesar de o jogo possuir os pngs dos mesmos;

-> Não há botão de replay ou exit ao terminar um jogo.

## Gameplay
![Captura de ecrã 2025-04-26 113323](https://github.com/user-attachments/assets/0a0c4eac-1345-4ad5-b093-6cfb51b1c620)

![Captura de ecrã 2025-04-26 113405](https://github.com/user-attachments/assets/529cf994-c7ff-4c3f-b854-63a24574f67a)

![Captura de ecrã 2025-04-26 113510](https://github.com/user-attachments/assets/6038c29c-3442-457a-8947-bc206f681d4a)

## Link do repositório do jogo
https://github.com/YuvalBakirov/bubble-trouble
