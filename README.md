# Rock-Paper-Scissors-Game

#include <iostream>
#include <cstdlib>  // For rand() and srand()
#include <ctime>    // For time()
#include <string>

using namespace std;

// Function to get the computer's choice
string getComputerChoice() {
    int choice = rand() % 3; // 0 = rock, 1 = paper, 2 = scissors
    if (choice == 0) return "rock";
    else if (choice == 1) return "paper";
    else return "scissors";
}

// Function to determine the winner
string determineWinner(string user, string computer) {
    if (user == computer)
        return "It's a tie!";
    else if ((user == "rock" && computer == "scissors") ||
             (user == "scissors" && computer == "paper") ||
             (user == "paper" && computer == "rock"))
        return "You win!";
    else
        return "You lose!";
}

int main() {
    srand(time(0)); // Seed the random number generator

    string userChoice;
    cout << "Enter rock, paper, or scissors: ";
    cin >> userChoice;

    // Convert to lowercase (optional, but recommended)
    for (auto &c : userChoice) c = tolower(c);

    if (userChoice != "rock" && userChoice != "paper" && userChoice != "scissors") {
        cout << "Invalid choice!" << endl;
        return 1;
    }

    string computerChoice = getComputerChoice();

    cout << "Computer chose: " << computerChoice << endl;
    cout << determineWinner(userChoice, computerChoice) << endl;

    return 0;
}