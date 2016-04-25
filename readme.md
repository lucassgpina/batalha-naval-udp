Batalha Naval
=============

Objetivo
--------
Este projeto tem como objetivo exemplificar o uso de comunicação UDP para jogos utilizando-se exclusivamente de C/C++ e bibliotecas standart de cada plataforma. Espera-se que sirva de referência para novos estudantes que buscam entender de forma prática a utilização dos sockets para jogos.

O Código
--------
Infelizmente é muito comum não ser respeitado os padrões de código de projetos open-source. A regra é simples, siga o padrão
já adotado, mesmo que você considere o seu mais adequado. Um padrão tosco é melhor que vários padrões misturados.

Para facilitar o processo vamos listar aqui quais serão eles:

1. Variáveis:
	* Todas as variáveis locais devem começar com letra minúscula e suas palavras separadas por underscore.
	* Variáveis globais devem ser iniciadas com a letra g.		
```c++
	sockaddr_in g_addr_host;
    
    void foo(void)
    {
        int ships_pos[10];
		char player_name[20];
		
        //...
    }
```


2. Métodos:
	* Todos devem começar com letra minúscula e a primeira letra da palavra seguinte maiúscula, sem separação por underscore.
	* Caso o retorno seja um booleano, o ideal é que o nome seja uma pergunta começando por "is". É apenas uma recomendação, não se prenda muito a isso
```c++
	void printBoard (char *board)
    {
		//...
	}
    
    bool isGameOver ()
    {
		//...
	}
```
3. Classes:
	* Todas as classes devem ter sua primeira letra maiúscula e o inicio de cada palavra também.
	
```c++
	class SocketManager {
		//...
	}
```
4. Definição de tipos:
	* Todo tipo definido deve ter todas letras minúsculas e palavras separadas com underscore, contendo _type no final para diferenciar de uma variável.
```c++
	typedef struct{
    	int x;
        int y;
    }ship_pos_type;
```
5. Definições:
	* As definições (#defines) devem ter todas letras maiúsculas e palavras separadas por underscore.
```c++
	#define BOARD_SIZE 10
```
6. Sequencias:
	* Quando houver uma sequencia de dados a ser definida, o separador deve ir antes do item na lista. Isso facilita a identação, também ajuda a controlar os separadores, evitando esquecimentos e coisas do tipo.
```c++
    typedef enum{
    	 AIRCRAFT_CARRIER
        ,WAR_SHIP
        ,CRUZADER
        ,SUBMARINE
        ,DESTROYER
        ,SHIP_NUM
    }ship_type;
    
    if((current_ship == DESTROYER)
    || (current_ship == CRUZADER)
    || (current_ship == WAR_SHIP)){
    	//...
    }
```


O Jogo
------
É o clássico Batalha Naval que todos conhecemos 

* Tabuleiro

	O tabuleiro quadriculado com suas coordenadas que variam de A à J na horizontal e de 1 à 10 na vertical:
	|##| A | B | C | D | E | F | G | H | I | J |
	|--|---|---|---|---|---|---|---|---|---|---|
	|1 |   |   |   |   |   |   |   |   |   |   |
	|2 |   |   |   |   |   |   |   |   |   |   |
	|3 |   |   |   |   |   |   |   |   |   |   |
	|4 |   |   |   |   |   |   |   |   |   |   |
	|5 |   |   |   |   |   |   |   |   |   |   |
	|6 |   |   |   |   |   |   |   |   |   |   |
	|7 |   |   |   |   |   |   |   |   |   |   |
	|8 |   |   |   |   |   |   |   |   |   |   |
	|9 |   |   |   |   |   |   |   |   |   |   |
	|10|   |   |   |   |   |   |   |   |   |   |

As regras são:

1. O Objetivo é afundar todas as embarcações do outro player passando as coordendas, quem afundar todas as embarcações primeiro vence.

2. Após o jogador escolher as coordenadas, se ele errar é a vez do próximo, caso acerte é a vez dele de novo.

3. Ao acertar o jogador só sabe que acertou e não recebe o feedback de qual embarcação ele acertou.

4. Ao afundar uma embarcação ele é informado de qual embarcação acabou de afundar.


O jogo é dividido em duas fases:

1. Fase de Planejamento
	
    Cada jogador deve posicionar seus navios na horizontal ou vertical no tabuleiro Esses navios são:
	* 1x [P] Porta-aviões (5 posições)
	* 1x [E] Encouraçados (4 posições)
	* 2x [C] Cruzadores (3 posições)
	* 1x [S] Submarinos (1 posição)
	
	Para posicionar cada navio basta indicar de onde à onde você quer que ele fique. Exemplo:
     |coordenada|             descrição                                 |
     |----------|-------------------------------------------------------|
	 |D3,F3     | posiciona um Cruzador ocupando as posições D3,E3 e F3 |
	 |A5        | posiciona um submarino em A5                          |
	 |G2,G6     | posiciona um Porta-aviões de G2 a G6                  |
		
2. Fase de Batalha	
	
    Para disparar basta digitar uma cooerdenada válida, exemplo:
	
	A10, J1, B6, (...)
		
To do
-------
    - [ ] Lógica do Jogo
    - [ ] API UDP
      - [ ] Windows
      - [ ] Linux
		
		
Autores
-------
Iniciaram esse projeto o @whateverton , @wiiro e @lucassgpina . Mas esperamos que muitos outros contribuam :wink: