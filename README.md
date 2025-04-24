Trabalho prático - Técnicas de desenvolvimento de videojogos.

David Querido 33219;
Gabriel Solinos 31487; 
Paulo Pinto 31474;

Análise do jogo "Bubble Trouble"

Bubble Trouble é um jogo bidimensional com inteligência artificial(Bot) na qual dois jogadores competem entre si, neste caso, o jogador e a inteligência artificial. O objetivo principal do jogo é acertar o máximo de bolas possíveis para obter uma pontuação mais alta. Ambos os jogadores têm um determinado valor para a sua saúde e também para os pontos. O jogo termina assim que um dos jogadores fica sem vida ou quando o tempo acabar e o jogador com a pontuação mais alta vence.

Progressão no jogo:

No jogo, existe bolas de 4 cores(vermelha, azul, amarela e preta). A bola vermelha pertence a nós enquanto que a bola azul pertence ao adversário. A bola amarela pertence a ambos os jogaodores e o seu objetivo é adicionar alguma ação. A bola preta é uma bola rolante que aparece a cada meio minuto e que não pode ser rebatida cujo seu objetivo é atingir as pernas dos jogadores e diminuir a saúde dos jogaodres.
Um tiro só pode ser disparado quando não houver balas no ar. Um jogador só pode atirar uma flecha enquanto estiver parado no chão e imóvel. Acertar qualquer uma das bolas(vermelha, azul e amarela) fará com que a bola exploda em duas bolas menores. Se algum dos jogadorores acertar a bola do adversário não explodirá a bola dele. Durante o jogo, caixas irão cair do céu. Existem 5 tipos de caixas: mais saúde, menos saúde, mais pontuação, menos pontuação, mais tiros e para congelar o jogador. Ao apanhar uma caixa "mais tiros" , pode disparar vários tiros ao mesmo tempo(até 3 tiros). A caixa "menos/mais pontuação/saúde" diminui ou aumenta 50 pontos/saúde. A caixa que congela o jogador por alguns segunods. O jogo tem a duração de 120 segundos e cada jogador tem 1000 pontos de saúde. Um tiro normal lhe dará 50 pontos, mas se a bola o atingir perderá 50 pontos de saúde. Uma bola
amarela é uma bola cuja saúde e o número de pontos que ela lhe dá são números aleatórios entre 0 e 100. Uma bola preta reduzirá a sua saúde em 20 pontos.O jogo termina se o tempo acabar ou se um dos jogadores ficar sem saúde.

Comandos para o jogo:

Movimentos:
Movimentar para a direita- Pressionar a seta direita.
Movimentar para a esquerda- Pressionar a seta esquerda.
Saltar- Pressionar a seta para cima.

Atirar:
Atirar- Pressionar a tecla "Espaço".

Pasta Content:
-> ProjectStates - Pasta que guarda os diferentes estados do jogo
	  EndState.cs - Ficheiro que produz a tela do fim do jogo;
	  GameState.cs - Ficheiro que produz o estado principal do jogo, responsável pela lógica e física do mesmo;
	  MenuState.cs -	Ficheiro que produz a tela do menu principal;
	  State.cs - Ficheiro que serve como base para os outros estados.

Classes:

Animation.cs:
Esta classe serve para gerir as animações no jogo.
Ela controla qual frame da animação deve ser exibido, a posição do desenho, a rotação, a escala e outros efeitos visuais. Além disso, ela atualiza a animação com base no estado do herói (hero) e no estado do jogo (state), mudando o frame atual no ritmo apropriado.

Ball.cs:
A classe Ball representa uma bola no jogo. Ela gerencia a posição, movimentação, colisões e a aparência da bola, incluindo sua interação com paredes e outros objetos (como jogadores), além de atualizar a física da bola, como gravidade e velocidade.

BotKeyboard:
A classe BotKeyboard é responsável por controlar o comportamento de um bot no jogo. Ela define a lógica de movimentação, salto e disparo do bot, além de calcular a direção com base na posição e velocidade dos alvos (bolas) mais próximos.

Button.cs:
A classe Button representa um botão interativo no jogo. Ela detecta cliques e alterações no estado do mouse, muda a cor ao passar o cursor sobre ela, e executa ações configuradas em eventos de clique.

Camera.cs:
A classe Camera gerencia a visualização do jogo, ajustando a posição e o zoom para focar em objetos ou áreas específicas da cena. Ela utiliza matrizes de transformação para aplicar escala, translação e rotação, garantindo que a câmera acompanhe o objeto de foco (implementado pela interface IFocus), enquanto respeita limites como bordas da tela e ajuste de zoom com o mouse.

Drawable.cs:
A classe Drawable representa objetos desenháveis no jogo. Ela gerencia propriedades como textura, posição, cor, escala e rotação, permitindo que os objetos sejam renderizados na tela com o método Draw.

Fire.cs:
A classe Fire representa um disparo feito pelo jogador no jogo. Ela controla a lógica de colisão com bolas, gerencia o crescimento vertical do disparo, e atualiza o estado visual (ex.: quando deve ser desenhado ou removido).

GameObject.cs:
A classe GameObject representa objetos no jogo "Bubble Trouble" que podem se mover, interagir com o ambiente, reagir a comandos do jogador (como andar, pular e disparar), detectar colisões e exibir animações. É usada principalmente para gerenciar o comportamento e as ações de personagens jogáveis ou elementos dinâmicos no jogo.

MyKeyBoard.cs:
A classe MyKeyBoard define controles de teclado para o jogo "Bubble Trouble". Ela tem uma classe base abstrata, BaseKeys, que especifica métodos para verificar ações como pressionar ou soltar teclas (direcionais, espaço, shift). A classe concreta UserKeys implementa esses métodos, associando teclas específicas a essas ações e detectando o estado do teclado em tempo real.

Page.cs:
A classe Page gerencia texturas e animações para diferentes estados de um herói no jogo "Bubble Trouble". Ela carrega texturas, identifica regiões específicas (retângulos) e pontos de origem para animações, define o ritmo (Tempo) baseado no estado do herói e torna o fundo transparente para exibição correta.

S.cs:
A classe estática S serve como um espaço global para armazenar e gerenciar dados e recursos compartilhados no jogo "Bubble Trouble". Ela contém referências a elementos essenciais, como dispositivos gráficos, gerenciadores de conteúdo, objetos do jogo (como bolas e caixas surpresa), configurações de tela, estados do jogo, e funções utilitárias, como a criação do chão no cenário.

SurpriseBox.cs:
A classe SurpriseBox representa caixas surpresa no jogo "Bubble Trouble". Essas caixas interagem com o jogador através de colisões, aplicando efeitos como adicionar pontos, aumentar o tempo do jogo, congelar o personagem, ou até penalidades. Elas também possuem comportamento de gravidade e desaparecem após um tempo ou interação.

TheDic.cs:
A classe estática TheDic serve para inicializar e armazenar um dicionário global que organiza as páginas (Page) de animações por heróis (Heros) e seus estados (States) no jogo "Bubble Trouble". Ela verifica os arquivos de conteúdo e mapeia os estados e heróis para suas respectivas animações.

Análise a partes do código:

Defeitos a apontar sobre o jogo:
-> Só se consegue fazer uma ação de cada vez






















https://github.com/YuvalBakirov/bubble-trouble
