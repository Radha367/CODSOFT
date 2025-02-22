# CODSOFT
#include <iostream>
#include <cstdlib>
#include <ctime>

using namespace std;

int score = 0;

void playGame() {
    srand(time(0));
    int randomNum = rand() % 100 + 1; 
    int number;
    int i = 10;
    bool guessedCorrectly = false;

    cout << "Welcome to the Number Guessing Game!" << endl;
    cout << "You have 10 attempts to guess a number between 1 and 100." << endl;

    while (i > 0) {
        cout << "\nAttempts left: " << i << endl;
        cout << "Enter your guess: ";

        while (!(cin >> number)) {
            cout << "Invalid input! Please enter a valid number." << endl;
            cin.clear();
            cin.ignore(numeric_limits<streamsize>::max(), '\n'); 
        }

        if (number == randomNum) {
            cout << "Correct! You guessed it!" << endl;
            score++;
            cout << "Your current score: " << score << endl;
            guessedCorrectly = true;
            break;
        } else if (number > randomNum) {
            cout << "Too high! Try again." << endl;
        } else {
            cout << "Too low! Try again." << endl;
        }

        i--;
    }

    if (!guessedCorrectly) {
        cout << "\nYou've run out of attempts! " << endl;
    }
}

int main() {
    char playAgain;
    
    do {
        playGame();
        cout << "\nDo you want to play again? (yes/no): ";
        cin >> playAgain;
        
    } while (tolower(playAgain) == 'y');

    cout << "\nThank you for playing! Your final score: " << score << endl;
    return 0;
}
