# 1340GroupWork
Group Assignment for ENGG 1340.

Group member: Chen Xin (3035952733), Zhang Zhen Yu (3033101768)

Game and Game Rules;

This is a traditional called Black Jack or points 21

Rules:

1.There is a set of pokecards includes 52 cards (all cards except the 2 jokers). 

2.All cards will have value that equals to its cards number, except A, J, Q and K.

2."A" can be 1 or 11, "J", "Q" and "K" euqual to 10.

3.Black jack: The initial 2 cards contain both an "A" and a tenner (cards that equal to 10).

4.There are two characters, a banker and a player. The banker will be the robot.

5.Press "y" to start the game, "n" to stop the game.

6.Input a number no less then 1000 as your total amount of chips.

7.Input a second number to decide how much to put in this round of game (no more then your last input).

8.Both the banker and the player will recieve 2 cards, and 1 of the banker's card is hidden from the player.

9.If the public card of the banker is an "A", player can choose to input "y" or "n" to choose whether or not to buy an insurance with 50% of their chips.

10.If the hidden card of the banker is a tenner and the player has insurance, the player earns 100% of their initial chips.
   If the player doen't have insurance, he lose all of his chips.
   
11.If the player has black jack, player gets 150% of their initial chips.

12.If both player and banker are black jack(or not), the game continues.

13.Player can choose to insert "y" to get 1 more card or "n" to give up.

14.If the player choose "y" and the sum of cards in the players hands exceeds 21, then he loses the chip he betted.

15.If the player choose "n", the hidden card of the banker is revealed, and the one with the biggest sum wins the game.

16.Once the player loses or wins a game, he can insert "y" or "n" to decide whether or not to start a new round.

17.If the total capacity in the player's hand is 0, the game is over.

Function of the codes:

1. void Initial: Print out the initial condition.
2. void ShuffleCards: Make sure the cards are in different order.
3. void ShowCards: Print out the cards in the player's hand and the cards in banker's hand.
4. void ShowCards_HIDD: Hide the first card of the banker with a "?" before the plyer's round ends.
5. int Calculator: Calculate the sum of the points carrried by the player and the banker.
6. int Calculator_MAX: Control the movements of the banker.
7. int Calculator_MIN: Control the movements of the banker.
8. bool_Is_A: Determine if the player can buy the insurance or not.
9. int main: Main function.

Compilation instructions:

1. Use a linux server
2. $ vi blackjack.cpp
3. press "i" to enter insert mode, copy and paste the code.
4. press "esc" to quit insert mode, and insert ":wq" to save and quit.
5. $ chmod u+x blackjack.cpp
6. $ g++ -pedantic-errors -std=c++11 blackjack.cpp -o blackjack
7. $ ./blackjack
8. follow the rules
9. Have Fun :D
