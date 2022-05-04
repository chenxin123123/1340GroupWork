#include <iostream>
#include <cstdlib>      // for calling srand(), rand()
#include <ctime>

using namespace std;

#define SPADE   "\xE2\x99\xA0"
#define CLUB    "\xE2\x99\xA3"
#define HEART   "\xE2\x99\xA5"
#define DIAMOND "\xE2\x99\xA6"

void Initial()
{
  cout << "******Welcome to the game of Black Jack******" << endl;
  cout << "*****Tips: 'y' means yes, 'n' means 'no'*****" << endl;
  cout << endl;
  cout << "Start the game ? (y/n): ";
}

void ShuffleCards(int pokecards[])
{
  for (int i = 0; i < 52; i++)
  {
    pokecards[i] = i;
  }

  srand((unsigned)time(NULL));
  for (int i = 0; i < 52; i++)
  {
    int swap = rand() % 52;
    int temp = pokecards[i];
    pokecards[i] = pokecards[swap];
    pokecards[swap] = temp;
  }
}

void ShowCards(int cards[], int num)
{
  string a[13] = {"A", "2", "3", "4", "5", "6", "7", "8", "9", "10", "J", "Q", "K"};
  for (int i = 0; i < num; i++)
  {
    int value = cards[i] % 13;
    int type = cards[i] / 13;
    if (type == 0)
    {
      cout << a[value] << SPADE << " ";
    }
    else if (type == 1)
    {
      cout << a[value] << CLUB << " ";
    }
    else if (type == 2)
    {
      cout << a[value] << HEART << " ";
    }
    else if (type == 3)
    {
      cout << a[value] << DIAMOND << " ";
    }
  }
  cout << endl;
}

void ShowCards_HIDD(int cards[], int num)
{
  string a[13] = {"A", "2", "3", "4", "5", "6", "7", "8", "9", "10", "J", "Q", "K"};
  for (int i = 0; i < num; i++)
  {
    if (i == 0)
    {
      cout << "?" << " ";
    }
    else
    {
      int value = cards[i] % 13;
      int type = cards[i] / 13;
      if (type == 0)
      {
        cout << a[value] << SPADE << " ";
      }
      else if (type == 1)
      {
        cout << a[value] << CLUB << " ";
      }
      else if (type == 2)
      {
        cout << a[value] << HEART << " ";
      }
      else if (type == 3)
      {
        cout << a[value] << DIAMOND << " ";
      }
    }
  }
  cout << endl;
}

int calculator(int cards[], int num)
{
  int b[13] = {11, 2, 3, 4, 5, 6, 7, 8, 9, 10, 10, 10, 10};
  int sum = 0;
  int position;
  for (int i = 0; i < num; i++) //take A as 11 first
  {
    position = cards[i] % 13;
    sum = sum + b[position];
  }

  if (sum > 21)
  {
    for (int i = 0; i < num; i++) // if sum > 21 and A exiist
    {
      position = cards[i] % 13;
      if (position == 0 and sum > 21)
      {
        sum = sum - 10;
      }
    }
  }
  return sum;
}

int calculator_MAX(int cards[], int num)
{
  int b[13] = {11, 2, 3, 4, 5, 6, 7, 8, 9, 10, 10, 10, 10};
  int sum = 0;
  int position;
  for (int i = 0; i < num; i++) //take A as 11 first
  {
    position = cards[i] % 13;
    sum = sum + b[position];
  }
  return sum;
}

int calculator_MIN(int cards[], int num)
{
  int b[13] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 10, 10, 10};
  int sum = 0;
  int position;
  for (int i = 0; i < num; i++) //take A as 1
  {
    position = cards[i] % 13;
    sum = sum + b[position];
  }
}

bool Is_A(int cards[], int n)
{
  if (cards[1] % 13 == 0)
  {
    return true;
  }
  else
  {
    return false;
  }
}

int main()
{
  int pokecards[52];//poke cards
  int banker[10];//use to store the cards for the banker for the game
  int player[10];//use to store the cards for the player for the game
  int capital;


  Initial();
  char Game_Flag;
  cin >> Game_Flag;

  // cin for capital
  cout << "Houw much capacity you will push for this game? (At least 1000 & an integer): ";
  cin >> capital;
  while (capital < 1000)
  {
    cout << "Capital not meet requirement !" << endl;
    cout << "Houw much capacity you will push for this game? (At least 10000 & an integer): ";
    cin >> capital;
  }
  cout << endl;

  while (Game_Flag == 'y')
  {
    int wager;

    ShuffleCards(pokecards);

    cout << "Houw much wager you will push for this game? (an integer): ";
    cin >> wager;
    while (capital - wager < 0)
    {
      cout << "Wager can not larger than Capital!"  << endl;
      cout << "Houw much wager you will push for this game? (an integer): ";
      cin >> wager;
    }
    cout << endl;

    int CardNUM_Player = 0; //record number of cards for Player
    int CardNUM_Banker = 0; //record number of cards for Banker
    int CardNUM_Poke = 0; //record number of pokecards

    for (int i = 0; i < 4; i++) //give two cards to player and two to banker
    {
      if (i % 2 == 0)//give cards to player
      {
        player[CardNUM_Player] = pokecards[CardNUM_Poke];
        CardNUM_Player += 1;
        CardNUM_Poke += 1;
      }
      else //give cards to banker
      {
        banker[CardNUM_Banker] = pokecards[CardNUM_Poke];
        CardNUM_Banker += 1;
        CardNUM_Poke += 1;
      }
    }

    //print the inital condition
    cout << "Game started: " << endl;
    cout << "Banker: ";
    ShowCards_HIDD(banker, CardNUM_Banker);
    cout << "Player: ";
    ShowCards(player, CardNUM_Player);
    cout << endl;

    //Condition for Insurance and Natural Black Jack
    char flag_INSURANCE = 'n';
    char flag_Natural_BJ = 'n';
    int Points_P = calculator(player, CardNUM_Player);
    int Points_B = calculator(banker, CardNUM_Banker);
    if (Points_P == 21)
    {
      flag_Natural_BJ = 'y';
    }
    else
    {
      if (Is_A(banker, CardNUM_Banker))
      {
        char flag_Buy;
        cout << "Do player need an insurance?(y/n) : ";
        cin >> flag_Buy;
        cout << endl;
        if (flag_Buy == 'y') //Player buy insurance
        {
          flag_INSURANCE = 'y';
        }
      }
    }


    //Player's turn
    char Round_P = 'Y';
    char Boom_A = 'N';
    if (flag_INSURANCE == 'n' and flag_Natural_BJ == 'n')
    {
      while (Round_P == 'Y')
      {
        if (Points_P < 21)
        {
          char Get_Cards_P;
          cout << "Get one more cards(Player)? (y/n): ";
          cin >> Get_Cards_P;
          if (Get_Cards_P == 'y')//player gets one more card
          {
            player[CardNUM_Player] = pokecards[CardNUM_Poke];
            CardNUM_Player += 1;
            CardNUM_Poke += 1;
            cout << "Player gets one more cards" << endl;
            cout << "Banker: ";
            ShowCards_HIDD(banker, CardNUM_Banker);
            cout << "Player: ";
            ShowCards(player, CardNUM_Player);
            cout << endl;
            Points_P = calculator(player, CardNUM_Player);
          }
          else if (Get_Cards_P == 'n')//do not need more cards break the loop
          {
            cout << "Player do not want more cards" << endl;
            cout << "End of Player's round" << endl;
            cout << endl;
            Round_P = 'N';
          }
        }
        else//condition for a non-natural BlackJack or points > 21 break the loop
        {
          if (Points_P > 21)
          {
            Boom_A = 'Y';
            cout << "BOOM" << endl;
          }
          else if (Points_P = 21)
          {
            cout << "BlackJack" << endl;
          }
          cout << "End of Player's round" << endl;
          cout << endl;
          Round_P = 'N';
        }
      }
    }

    //banker's turn
    cout << "show the first cards of banker" << endl;
    cout << "Banker: ";
    ShowCards(banker, CardNUM_Banker);
    cout << "Player: ";
    ShowCards(player, CardNUM_Player);
    cout << endl;

    int Points_B_MAX = calculator_MAX(banker, CardNUM_Banker);
    int Points_B_MIN = calculator_MIN(banker, CardNUM_Banker);
    char Round_B = 'Y';
    if (flag_INSURANCE == 'n' and flag_Natural_BJ == 'n')
    {
      if (Boom_A == 'Y')
      {
        cout << "Skip Banker's round" << endl;
      }
      while (Round_B == 'Y' and Boom_A == 'N')
      {
        if (Points_B_MAX < 17)//condition for must get cards
        {
          banker[CardNUM_Banker] = pokecards[CardNUM_Poke];
          CardNUM_Banker += 1;
          CardNUM_Poke += 1;
          cout << "Banker must get one more pokecard" << endl;
          cout << "Banker: ";
          ShowCards(banker, CardNUM_Banker);
          cout << "Player: ";
          ShowCards(player, CardNUM_Player);
          cout << endl;
          Points_B_MAX = calculator_MAX(player, CardNUM_Player);
          Points_B_MIN = calculator_MIN(player, CardNUM_Player);
        }
        else if (Points_B_MIN >= 17)//condition for must stop
        {
          cout << "Banker cannot get more cards" << endl;
          cout << "End of Banker's turn" << endl;
          Points_B = calculator(banker, CardNUM_Banker);
          Round_B = 'N';
        }
        else if (Points_B_MIN < 17 and Points_B_MAX >= 17) //decision about get more cards or not
        {
          Points_B = calculator(banker, CardNUM_Banker);
          if (Points_B < Points_P)
          {
            banker[CardNUM_Banker] = pokecards[CardNUM_Poke];
            CardNUM_Banker += 1;
            CardNUM_Poke += 1;
            cout << "Banker get one more pokecard." << endl;
            cout << "Banker: ";
            ShowCards(banker, CardNUM_Banker);
            cout << "Player: ";
            ShowCards(player, CardNUM_Player);
            cout << endl;
            Points_B_MAX = calculator_MAX(player, CardNUM_Player);
            Points_B_MIN = calculator_MIN(player, CardNUM_Player);
          }
          else if (Points_B >= Points_P)
          {
            cout << "Banker do not want more cards" << endl;
            cout << "End of Banker's turn" << endl;
            Round_B = 'N';
          }
        }
      }
    }


    cout << endl;

    //process result
    if (flag_Natural_BJ == 'y')
    {
      cout << "Player gets Natural BlackJack" << endl;
      if (Points_B == 21)
      {
        cout << "Banker also have Natural Black Jack" << endl;
        cout << "Tie" << endl;
        cout << "You do not earn or lose money" << endl;
        cout << "The capital you have: " << capital << endl;
      }
      else
      {
        cout << "Banker donot have Natural Black Jack" << endl;
        cout << "Player Win" << endl;
        cout << "You earn " << wager*1.5 << " HKD for this round." << endl;
        capital = capital + wager * 1.5;
        cout << "The capital you have: " << capital << endl;
      }
      cout << endl;
    }
    else if (flag_INSURANCE == 'y')
    {
      cout << "Player buy the insurance" << endl;
      if (Points_B == 21)
      {
        cout << "Banker gets Natural BlackJack and Player has insurance" << endl;
        cout << "Player Win" << endl;
        cout << "You earn " << wager/2 << " HKD for this round" << endl;
        capital = capital + wager/2;
        cout << "The capital you have: " << capital << endl;
      }
      else
      {
        cout << "Banker does not have Natural BlackJack and Player has insurance" << endl;
        cout << "Banker Win" << endl;
        cout << "You lose " << wager/2 << " HKD for this round" << endl;
        capital = capital - wager/2;
        cout << "The capital you have: " << capital << endl;
      }
      cout << endl;
    }
    else if (flag_Natural_BJ == 'n' and flag_INSURANCE == 'n')
    {
      if (Boom_A == 'Y')
      {
        cout << "Player's points is greater than 21, Boom!" << endl;
        cout << "Banker Win" << endl;
        cout << "You lose " << wager << " HKD for this round" << endl;
        capital = capital - wager;
        cout << "The capital you have: " << capital << endl;
      }
      else if (Boom_A == 'N')
      {
        if (Points_B > 21)
        {
          cout << "Banker's points is greater than 21, Boom!" << endl;
          cout << "Player Win" << endl;
          cout << "You win " << wager << " HKD for this round" << endl;
          capital = capital + wager;
          cout << "The capital you have: " << capital << endl;
        }
        else if (Points_B <= 21)
        {
          if (Points_P == Points_B)
          {
            cout << "Banker and Player have same points" << endl;
            cout << "Tie" << endl;
            cout << "You do not earn or lose money" << endl;
            cout << "The capital you have: " << capital << endl;
          }
          else if (Points_P > Points_B)
          {
            cout << "Player has larger points" << endl;
            cout << "Player Win" << endl;
            cout << "You win " << wager << " HKD for this round" << endl;
            capital = capital + wager;
            cout << "The capital you have: " << capital << endl;
          }
          else if (Points_P < Points_B)
          {
            cout << "Banker has larger points" << endl;
            cout << "Banker Win" << endl;
            cout << "You lose " << wager << " HKD for this round" << endl;
            capital = capital - wager;
            cout << "The capital you have: " << capital << " HKD" << endl;
          }
        }
      }
      cout << endl;
    }

    if (capital > 0)
    {
      cout << "Start a new game? (y/n): ";
      cin >> Game_Flag;
    }
    else if (capital < 0)
    {
      cout << "You lose all your money" << endl;
      cout << "Game Over !" << endl;
      Game_Flag = 'n';
    }
  }
}
