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
Ball.cs:
BotKeyboard:
Button.cs:
Camera.cs:
Drawable.cs:
Fire.cs:
GameObject.cs:
MyKeyBoard.cs:
Page.cs:
S.cs:
SurpriseBox.cs:
TheDic.cs:

Análise a partes do código:

Defeitos a apontar sobre o jogo:






















https://github.com/YuvalBakirov/bubble-trouble
