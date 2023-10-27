# Tic-tac-toe-game
#include <iostream>
#include <vector>

using namespace std;

// Function to print the tic-tac-toe board
void printBoard(const vector<vector<char>>& board) {
    for (int i = 0; i < 3; ++i) {
        for (int j = 0; j < 3; ++j) {
            cout << board[i][j] << " ";
        }
        cout << endl;
    }
}

// Function to check if there is a winner
bool checkWinner(const vector<vector<char>>& board, char player) {
    // Check rows and columns
    for (int i = 0; i < 3; ++i) {
        if (board[i][0] == player && board[i][1] == player && board[i][2] == player)
            return true;
        if (board[0][i] == player && board[1][i] == player && board[2][i] == player)
            return true;
    }
  
    // Check diagonals
    if (board[0][0] == player && board[1][1] == player && board[2][2] == player)
        return true;
    if (board[0][2] == player && board[1][1] == player && board[2][0] == player)
        return true;
  
    return false;
}

// Function to play the game
void playGame() {
    vector<vector<char>> board(3, vector<char>(3, ' '));
    char currentPlayer = 'X';
    int moves = 0;
  
    while (moves < 9) {
        // Print the current board
        printBoard(board);
      
        // Get the move from the current player
        int row, col;
        cout << "Player " << currentPlayer << ", enter your move (row column): ";
        cin >> row >> col;
      
        // Check if the move is valid
        if (row < 0 || row >= 3 || col < 0 || col >= 3 || board[row][col] != ' ') {
            cout << "Invalid move. Try again." << endl;
            continue;
        }
      
        // Make the move
        board[row][col] = currentPlayer;
        moves++;
      
        // Check if the current player wins
        if (checkWinner(board, currentPlayer)) {
            cout << "Player " << currentPlayer << " wins!" << endl;
            return;
        }
      
        // Switch to the next player
        currentPlayer = (currentPlayer == 'X') ? 'O' : 'X';
    }
  
    // If no player wins, it's a tie
    cout << "It's a tie!" << endl;
}

int main() {
    // Start the game
    playGame();
  
    return 0;
}
