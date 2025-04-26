
# Trabalho prático - Técnicas de desenvolvimento de videojogos.

David Querido 33219

Gabriel Solinos 31487

Paulo Pinto 31474

## Análise do jogo "Bubble Trouble"
Bubble Trouble é um jogo bidimensional com inteligência artificial(Bot) na qual dois jogadores competem entre si, neste caso, o jogador e a inteligência artificial. O objetivo principal do jogo é acertar o máximo de bolas possíveis para obter uma pontuação mais alta. Ambos os jogadores têm um determinado valor para a sua saúde e também para os pontos. O jogo termina assim que um dos jogadores fica sem vida ou quando o tempo acabar e o jogador com a pontuação mais alta vence.

## Progressão no jogo:
No jogo, existe bolas de 4 cores(vermelha, azul, amarela e preta). A bola vermelha pertence a nós enquanto que a bola azul pertence ao adversário. A bola amarela pertence a ambos os jogaodores e o seu objetivo é adicionar alguma ação. A bola preta é uma bola rolante que aparece a cada meio minuto e que não pode ser rebatida cujo seu objetivo é atingir as pernas dos jogadores e diminuir a saúde dos jogaodres. Um tiro só pode ser disparado quando não houver balas no ar. Um jogador só pode atirar uma flecha enquanto estiver parado no chão e imóvel. Acertar qualquer uma das bolas(vermelha, azul e amarela) fará com que a bola exploda em duas bolas menores. Se algum dos jogadorores acertar a bola do adversário não explodirá a bola dele. Durante o jogo, caixas irão cair do céu. Existem 5 tipos de caixas: mais saúde, menos saúde, mais pontuação, menos pontuação, mais tiros e para congelar o jogador. Ao apanhar uma caixa "mais tiros" , pode disparar vários tiros ao mesmo tempo(até 3 tiros). A caixa "menos/mais pontuação/saúde" diminui ou aumenta 50 pontos/saúde. A caixa que congela o jogador por alguns segunods. O jogo tem a duração de 120 segundos e cada jogador tem 1000 pontos de saúde. Um tiro normal lhe dará 50 pontos, mas se a bola o atingir perderá 50 pontos de saúde. Uma bola amarela é uma bola cuja saúde e o número de pontos que ela lhe dá são números aleatórios entre 0 e 100. Uma bola preta reduzirá a sua saúde em 20 pontos.O jogo termina se o tempo acabar ou se um dos jogadores ficar sem saúde.

## Comandos para o jogo:
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

## ProjectStates - Pasta que guarda os diferentes estados do jogo;
EndState.cs - Ficheiro que produz a tela do fim do jogo;

GameState.cs - Ficheiro que produz o estado principal do jogo, responsável pela lógica e física do mesmo;

MenuState.cs - Ficheiro que produz a tela do menu principal;

State.cs - Ficheiro que serve como base para os outros estados.

## Classes:
### Animation.cs:
A classe Animation representa uma animação no contexto de um jogo, utilizando a biblioteca Microsoft.Xna.Framework. Ela gerencia quadros (frames), controle e transição de animações. Possui propriedades como Anime (representa a animação atual, armazenando informações como texturas e 	recortes), CurrentIndex (índice atual do quadro) e CurrentFrame (controla o avanço dos quadros). A classe tem múltiplos construtores que inicializam animações com diferentes parâmetros, como herói, estado, posição, cor, rotação, escala e profundidade. O método Update atualiza texturas, regiões de recorte (SourceRectangle) e gerencia a transição entre quadros com base no ritmo (pace) da animação, reiniciando o ciclo quando necessário. A cada 	atualização, ele ajusta propriedades visuais e desenha o quadro atual na tela. Assim, a classe Animation é usada para criar e gerenciar animações fluidas no jogo.

### Ball.cs:
A classe Ball faz parte de um jogo e representa a lógica de uma bola que interage com o ambiente. Ela contém atributos principais como velocity (velocidade da bola em X e Y), gravitaion (gravidade aplicada à bola), points e health (pontuação e vida da bola), uniqueColor (cor única da bola) e countHitsWall (contador de colisões com as paredes). Existem dois construtores que inicializam os dados da bola, como sua posição, cor, escala, profundidade de camada, textura e velocidade inicial. O método Update atualiza a posição da bola com base em sua velocidade, verifica colisões com as bordas da tela e o chão, invertendo a direção da velocidade quando necessário, e incrementa o contador de colisões. O método Collision trata colisões com outros objetos do jogo, ajustando a direção da bola com base na posição da colisão e atualizando atributos do objeto colidido, como cor e vida restante. Por fim, o método Draw renderiza a bola na tela caso ela esteja marcada para ser desenhada. Em resumo, a classe lida com o comportamento da bola no jogo, incluindo movimentação, colisões e renderização na tela, além de implementar um sistema de física simplificado com eventos de colisão.

### BotKeyboard:
A classe BotKeyboard é uma implementação de um controle automatizado para um personagem no jogo. Aqui está um resumo detalhado de suas funcionalidades: A classe herda de BaseKeys, o que significa que implementa métodos relacionados a entradas (teclas pressionadas ou liberadas) para controlar o personagem. Esta classe é usada para simular entradas de teclado para um robô (bot), permitindo que ele se mova, pule, atire, e reaja a eventos do jogo. A propriedade bot representa o objeto do jogo controlado pelo bot. A propriedade direction é um vetor que indica a direção do movimento. A propriedade target representa o alvo atual do bot (uma bola, por exemplo). Variáveis como tagetDist, isShot, shootDelay, findTargetTime, findDelay controlam o comportamento do bot, como atirar, procurar alvos e movimentação. O método InitBot(GameObject bot) inicializa o bot com suas configurações iniciais e define o evento de atualização. O método Update() atualiza o estado do bot a cada quadro, incluindo reações às bolas pretas (blackBall), como pular para evitar colisões, encontrar a bola mais próxima (chamando findClosestBall()), decidir movimentos e quando atirar com base na posição e direção do alvo. O método findClosestBall() determina qual bola é a mais próxima do bot, considerando diferentes listas de bolas (balls1 e pointBalls). Métodos sobrescritos como RightPressed, LeftPressed, UpPressed, etc., simulam entradas do teclado dependendo do estado atual do bot. O método Update() é vinculado ao evento GameState.Update_event, garantindo que o bot seja atualizado continuamente durante o jogo. O bot ajusta sua direção com base na posição do alvo e na direção do movimento do alvo. Ele decide atirar quando a distância em relação ao alvo é suficientemente curta (tagetDist <= 300f). Em resumo, a classe BotKeyboard atua como um controlador de IA para um personagem do jogo, permitindo que ele tenha comportamentos autônomos, como mover-se, pular e atirar, com base na lógica implementada.

### Button.cs:
A classe Button representa um botão interativo na interface do jogo, permitindo que os jogadores interajam com ele através do mouse. A classe é responsável por desenhar um botão na tela utilizando uma textura (Texture2D) e, opcionalmente, um texto adicional (string Text) que pode ser exibido sobre o botão. Ela detecta interações do mouse, como passar o cursor sobre o botão ou clicar nele, e gerencia essas interações utilizando os estados atual e anterior do mouse (MouseState). A classe possui um evento chamado Click, que é disparado sempre que o botão é clicado (quando o botão esquerdo do mouse é liberado após estar pressionado sobre o botão). Propriedades como Position, Scale, PenColor (cor do texto) e color (cor do botão) permitem personalizar a aparência e o posicionamento do botão. A classe tem três construtores: um que inicializa o botão com uma textura, outro que inicializa o botão com uma textura e uma fonte (SpriteFont) para texto, e um terceiro que cria uma cópia de outro botão. Propriedades como Rectangle calculam e retornam a área retangular do botão com base em sua posição, textura e escala. O método Draw(GameTime gameTime, SpriteBatch spriteBatch) desenha o botão na tela com sua textura e cor, enquanto o método Update(GameTime gameTime) atualiza o estado do botão verificando se o mouse está sobre ele (hover) ou se foi clicado. A lógica da classe verifica se o cursor do mouse está dentro da área do botão (Rectangle) e ajusta sua cor para Gray para indicar que o botão está em foco, disparando o evento Click quando ele é clicado. Em resumo, a classe Button é um componente essencial para a criação de interfaces de usuário no jogo, permitindo interações através de cliques do mouse e oferecendo personalização e feedback visual ao jogador.

### Camera.cs:
A classe Camera, implementada em C#, é responsável por gerenciar a lógica de transformação e escala da visão da câmera em relação ao mundo do jogo. A matriz Mat (de transformação) é usada para calcular a posição e a escala da câmera no mundo 2D do jogo, transformando a posição de objetos no mundo para a perspectiva da câmera. A propriedade ScaleMatrix controla a escala da câmera, e o zoom é ajustado de acordo com o movimento do scroll do mouse, permitindo aumentar ou diminuir a visão. A câmera é projetada para seguir um objeto específico no jogo, definido pela interface IFocus, e a posição da câmera é interpolada suavemente (lerp) para garantir movimentos fluidos ao seguir o objeto. Há uma lógica para restringir a posição da câmera dentro de limites específicos, evitando que ela exiba áreas fora do mapa do jogo. Além disso, a câmera responde às entradas do mouse, como o scroll, para alterar o zoom. Esta classe é fundamental para proporcionar uma experiência fluida e responsiva ao jogador, ajustando dinamicamente a visualização do mundo do jogo com base no foco e nas interações do jogador.

### Drawable.cs:
A classe Drawable serve como uma classe base para representar elementos visuais no jogo "BubbleTrouble". Ela encapsula propriedades e métodos relacionados à renderização de objetos visuais usando o framework MonoGame. Contém propriedades essenciais para desenhar sprites, como Texture (textura do sprite), Position (posição do objeto na tela), color (cor aplicada ao sprite), rotation (rotação do sprite), scale (tamanho do sprite), layerDepth (profundidade da camada para renderização) e SourceRectangle e destinationRectangle (que gerenciam cortes ou escalas na textura). O método Draw é responsável por renderizar o objeto na tela, desde que a propriedade isDraw esteja habilitada. A classe possui construtores variados que permitem criar objetos Drawable com diferentes conjuntos de parâmetros, facilitando a flexibilidade e 	reutilização em diferentes contextos. Além disso, inclui suporte para texto (text) e fontes (font), sugerindo que também pode ser usado para renderizar texto, não apenas sprites. Essa classe é utilizada para simplificar a manipulação de elementos visuais no jogo, centralizando as propriedades e métodos de renderização.

### Fire.cs:
A classe Fire no jogo "BubbleTrouble" representa um objeto do tipo "fogo" que interage com outros elementos do jogo, como as bolas. Ela 		herda da classe Drawable, o que significa que possui propriedades e métodos para renderização visual. Além disso, ela implementa mecanismos para verificar colisões e atualizar seu estado. A classe possui a propriedade BallColor, que define a cor da bola associada ao objeto para verificar colisões específicas, e a propriedade shooter, que é uma referência ao objeto que dispara o fogo, gerenciando interações como a contagem de tiros (fireCount). O construtor inicializa a classe com informações como textura, posição, cor, escala e o objeto atirador, além de associar os eventos Update_event e FireCollision_Event da classe GameState, permitindo atualizações de estado e verificação de colisões. O método CheckCollision verifica se o fogo colide com uma bola usando retângulos de interseção, realizando ações dependendo da cor da bola, como removê-las do jogo, dividir bolas maiores em menores e atualizar a pontuação do jogador. Ele também desativa a exibição do objeto Fire após a colisão ou caso atinja o limite superior da tela. O método Update atualiza o estado do fogo, aumentando seu tamanho (scale) enquanto está ativo. Essa classe desempenha um papel essencial na mecânica de disparo do jogo, interagindo com as bolas para aplicar efeitos como remoção ou divisão, além de gerenciar a lógica visual e de colisão do fogo.

### GameObject.cs:
A classe GameObject no jogo "BubbleTrouble" representa um personagem jogável e encapsula funcionalidades relacionadas ao controle, 			movimentação, interações físicas e ações, como disparos e colisões. Ela herda da classe Animation, o que permite gerenciar animações associadas ao personagem. Define atributos como posição (Position), cor (ballColor), movimentação (velocityX, velocityY), aceleração (accelerationY) e estados do personagem (e.g., animações e disparos). Gerencia o número de disparos (fireCount, maxFireCount) e interações como o tempo de congelamento (freezeTime) e atrasos de disparo (shootDelay). O construtor inicializa o personagem com seu herói (Heros), teclas de controle (BaseKeys), posição inicial e configurações de movimento e gravidade, cria uma lista de disparos (playerShots) para armazenar os objetos de fogo (Fire) do personagem e associa eventos como colisões de jogador (PlayerCollision_Event). O método UpdateState atualiza o estado do personagem, verificando ações de entrada (teclas pressionadas) e executando movimentos, controlando a renderização de disparos ativos e atualizações gerais do personagem. O método Input gerencia a entrada do jogador por meio do teclado, definindo a movimentação (e.g., esquerda, direita, pulo) e ações como disparar (SpacePressed), além de atualizar a animação e direção do personagem com base nas teclas pressionadas. O método Move e o método Gravity calculam o movimento horizontal e vertical do personagem, aplicando os efeitos da gravidade e garantindo que o personagem não ultrapasse as bordas da tela ou o limite do chão. O método AddFire adiciona novos objetos de fogo (Fire) à lista de disparos, permitindo que o personagem aumente seu número máximo de disparos disponíveis. O método PlayerCollision gerencia colisões entre o personagem e outros objetos, ajustando a posição do personagem para evitar sobreposição. Esta classe é responsável por implementar a lógica principal de movimentação e interação de um personagem jogável no jogo, incluindo controle do jogador, física básica e gerenciamento de disparos.

### MyKeyBoard.cs:
A classe MyKeyBoard no arquivo fornecido não existe diretamente, mas o arquivo define duas classes relacionadas ao controle de entrada do teclado no jogo: BaseKeys e UserKeys. A classe BaseKeys define uma classe base abstrata para manipulação de entradas do teclado, contendo métodos abstratos que representam as ações básicas do jogador, como pressionar ou soltar teclas direcionais (RightPressed, LeftReleased, etc.), correr (ShiftPressed) e disparar (SpacePressed) e serve como uma interface para implementar controles personalizados. Já a classe UserKeys herda de BaseKeys e fornece uma implementação concreta para as ações do teclado utilizando o estado atual do teclado via Keyboard.GetState(), permitindo mapear teclas específicas (como Keys.Right, Keys.Left, etc.) para ações no jogo, como mover para a direita/esquerda, correr ou disparar. Ela implementa os métodos definidos em BaseKeys para verificar se uma tecla está pressionada (IsKeyDown) ou solta (IsKeyUp). Essas classes juntas são responsáveis por gerenciar as entradas do teclado no jogo, abstraindo e organizando as ações em métodos de fácil utilização.

### Page.cs:
A classe Page no jogo "BubbleTrouble" é projetada para gerenciar os dados visuais e animações de um herói em diferentes estados. Ela carrega texturas e divide a imagem em retângulos que representam quadros de animação, além de calcular origens para renderização. A propriedade Tex representa a textura associada ao herói e estado específico, a propriedade Recs é uma lista de retângulos que delimitam os quadros de animação extraídos da textura, a propriedade Orgs é uma lista de vetores que indicam os pontos de origem para renderização de cada quadro, e a propriedade Pace determina o ritmo (Tempo) da animação com base no estado do herói. O construtor recebe como parâmetros o herói (Heros) e seu estado (States), carrega a textura correspondente ao herói e estado, processa a textura para identificar quadros de animação usando a linha inferior da imagem como referência para separação, calcula os pontos de origem para renderização e define o ritmo da animação (Pace) com base no estado. O método FindTempo determina o ritmo da animação (Tempo) com base no estado atual do herói, e atualmente todos os estados compartilham o mesmo ritmo lento (Tempo.Slow). O método MakeTransparent torna transparente as áreas da textura que correspondem à cor de fundo, garantindo que apenas os elementos visuais relevantes sejam renderizados. A classe Page é essencial para gerenciar a animação e renderização do herói no jogo, separando e organizando os quadros de animação a partir de uma única textura e ajustando as propriedades de renderização para uma exibição adequada no jogo.

### S.cs:
A classe estática S no código fornecido parece ser uma classe utilitária que centraliza dados e métodos compartilhados usados em várias partes do jogo "Bubble Trouble". Aqui estão suas principais características e propósitos: A classe armazena dados globais por meio de propriedades estáticas que contêm objetos e valores usados amplamente, como SpriteBatch (sb) para desenhar sprites, GraphicsDeviceManager (gp) para gerenciar configurações gráficas, ContentManager (cm) para carregar recursos, dimensões da tela (screenWidth, screenHeight), um gerador de números aleatórios (rnd), listas de objetos do jogo como bolas (balls, balls1, pointBalls) e caixas surpresa (supBox). Ela também define enumerações, como tipos de heróis (Heros), estados (States) e tempos (Tempo), para categorizar ou controlar comportamentos no jogo. Além disso, a classe manipula recursos e o estado do jogo, incluindo métodos como Create_Ground_Line, que cria uma linha de solo baseada em uma textura carregada, útil para configurar o ambiente do jogo. A classe serve como um ponto de acesso global para variáveis necessárias em diferentes partes do jogo, como o estado do jogo (gameState), temporizadores (gameCDTimer) e o vencedor (winner). Também define delegados para gerenciar eventos de colisão e atualizações no jogo, como HandleCollision, HandleCollisionball e HandlePlayerCollision. O método Create_Ground_Line(float scale) é notável, pois processa uma textura de chão para determinar a altura do solo em diferentes posições horizontais, armazenando os dados na matriz ground, o que provavelmente é usado para calcular colisões ou interações com o chão no jogo. Em 	resumo, a classe S atua como um repositório central para variáveis, recursos e métodos estáticos essenciais para o funcionamento do jogo, facilitando a organização e o acesso a dados compartilhados.

### SurpriseBox.cs:
A classe SurpriseBox representa uma caixa surpresa no jogo "Bubble Trouble". Ela herda de uma classe base chamada Drawable, o que indica que a caixa pode ser desenhada na tela. Seu propósito principal é interagir com o jogador e aplicar efeitos dependendo do tipo de surpresa contida na caixa. A classe possui atributos como gravitaion para controlar o efeito de gravidade sobre a caixa, drc que define a direção de movimento da caixa, timeDisappearBox que representa o tempo restante para a caixa desaparecer e numOfBox que identifica o tipo de surpresa associada à caixa. O construtor inicializa a posição, cor, escala e textura da caixa, configura a gravidade inicial e registra o método Collision no evento GameState.BoxCollision_Event, permitindo que a classe reaja às colisões. A classe possui métodos como UpdateBox, que atualiza o movimento da caixa chamando o método Move e reseta a direção; Move, que atualiza a posição da caixa considerando a gravidade e aplica a gravidade se a caixa estiver ativa (isDraw); e Gravity, que aplica o efeito da gravidade aumentando o deslocamento vertical (drc.Y), verifica se a caixa atingiu o chão e, se o tempo para desaparecer for atingido, desativa a caixa. O método Collision detecta colisões entre a caixa e outros objetos do jogo. Quando uma colisão é detectada, a caixa é desativada, e um efeito é aplicado com base no valor de numOfBox: 0 adiciona um poder de fogo ao objeto, 1 incrementa pontos (count1) em 50, 2 incrementa a pontuação geral (countPts) em 50, 3 aumenta o tempo restante do jogo em 20 segundos, 4 congela o tempo do objeto por 5 segundos, 5 reduz count1 em 50 e 6 reduz countPts em 50. Além disso, a cor do objeto que colidiu é alterada para amarelo. Em resumo, a classe SurpriseBox adiciona elementos de interação e surpresa ao jogo, simulando o comportamento físico da caixa (gravidade e movimento), detectando colisões e aplicando efeitos dinâmicos que enriquecem a jogabilidade.

### TheDic.cs:
A classe estática TheDic serve como um repositório centralizado para armazenar e gerenciar informações relacionadas aos heróis (Heros) e seus estados (States) no jogo "Bubble Trouble". Ela utiliza um dicionário aninhado para organizar páginas (Page) associadas a cada combinação de herói e estado. A propriedade estática Big é um dicionário que mapeia heróis para outro dicionário, onde cada estado do herói está associado a um objeto Page, organizando os dados de maneira clara e eficiente para acesso rápido. O método estático Init inicializa o dicionário Big, iterando sobre todos os heróis e estados definidos nas enumerações Heros e States. Para cada combinação de herói e estado, o método verifica se existe um arquivo correspondente no diretório /Content/<hero>/<state>.xnb. Caso o arquivo exista, ele cria um objeto Page para essa combinação e o adiciona ao dicionário. A classe carrega dinamicamente os dados necessários durante a inicialização, garantindo que apenas os estados e heróis com arquivos válidos sejam adicionados ao dicionário. Isso permite gerenciar facilmente os recursos associados aos heróis e estados no jogo, como animações ou texturas. Em resumo, a classe TheDic organiza e gerencia dados de heróis e seus estados, carregando recursos de forma dinâmica e armazenando-os em uma estrutura de dicionário aninhado, o que facilita o gerenciamento eficiente de recursos no jogo.

## Análise a partes do código:
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

## Defeitos a apontar sobre o jogo:
-> No ínicio do jogo, os jogadores não tem uma posição inicial junto ao chão, pelo que "caem do céu";

-> Só se consegue fazer uma ação de cada vez;

-> Não há como escolher personagens e backgrounds diferentes apesar de o jogo possuir os pngs dos mesmos;

-> Não há botão de replay ou exit ao terminar um jogo;

## Gameplay
![Captura de ecrã 2025-04-26 113510](https://github.com/user-attachments/assets/6038c29c-3442-457a-8947-bc206f681d4a)

![Captura de ecrã 2025-04-26 113405](https://github.com/user-attachments/assets/529cf994-c7ff-4c3f-b854-63a24574f67a)

![Captura de ecrã 2025-04-26 113323](https://github.com/user-attachments/assets/0a0c4eac-1345-4ad5-b093-6cfb51b1c620)

## Link do repositório do jogo
https://github.com/YuvalBakirov/bubble-trouble
