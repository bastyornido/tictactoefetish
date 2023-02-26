# tictactoefetish
import random

# Define the game board
board = [' ' for i in range(9)]

# Define the winning combinations
winning_combinations = [(0, 1, 2), (3, 4, 5), (6, 7, 8), (0, 3, 6), (1, 4, 7), (2, 5, 8), (0, 4, 8), (2, 4, 6)]

# Define the function to display the game board
def display_board():
    print('   |   |   ')
    print(' ' + board[0] + ' | ' + board[1] + ' | ' + board[2] + ' ')
    print('   |   |   ')
    print('-----------')
    print('   |   |   ')
    print(' ' + board[3] + ' | ' + board[4] + ' | ' + board[5] + ' ')
    print('   |   |   ')
    print('-----------')
    print('   |   |   ')
    print(' ' + board[6] + ' | ' + board[7] + ' | ' + board[8] + ' ')
    print('   |   |   ')

# Define the function to make a move
def make_move(player, position):
    board[position] = player

# Define the function to check for a win
def check_win(player):
    for combination in winning_combinations:
        if board[combination[0]] == player and board[combination[1]] == player and board[combination[2]] == player:
            return True
    return False

# Define the main function
def main():
    # Display the game board
    display_board()

    # Define the players
    players = ['X', 'O']

    # Set the current player to player 1
    current_player = players[0]

    # Set the game status to ongoing
    game_status = True

    # Loop until the game is over
    while game_status:
        # Get the current player's move
        position = int(input('Player ' + current_player + ', make your move (1-9): ')) - 1

        # Check if the move is valid
        if board[position] == ' ':
            # Make the move
            make_move(current_player, position)

            # Display the game board
            display_board()

            # Check for a win
            if check_win(current_player):
                print('Player ' + current_player + ' wins!')
                game_status = False
            else:
                # Check for a tie
                if ' ' not in board:
                    print('Tie game!')
                    game_status = False
                else:
                    # Switch players
                    current_player = players[1] if current_player == players[0] else players[0]

# Call the main function
if __name__ == '__main__':
    main()
