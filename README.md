# Tic Tac Toe

# Create the game board
board = [' ' for _ in range(9)]

# Function to print the game board
def print_board():
    print("-------------")
    print("|", board[0], "|", board[1], "|", board[2], "|")
    print("-------------")
    print("|", board[3], "|", board[4], "|", board[5], "|")
    print("-------------")
    print("|", board[6], "|", board[7], "|", board[8], "|")
    print("-------------")

# Function to check if any player has won
def check_win(player):
    # Check rows
    for i in range(0, 9, 3):
        if board[i] == board[i+1] == board[i+2] == player:
            return True

    # Check columns
    for i in range(3):
        if board[i] == board[i+3] == board[i+6] == player:
            return True

    # Check diagonals
    if board[0] == board[4] == board[8] == player:
        return True
    if board[2] == board[4] == board[6] == player:
        return True

    return False

# Function to play the game
def play_game():
    print("Welcome to Tic Tac Toe!")
    print_board()

    while True:
        # Get the current player's move
        if board.count('X') == board.count('O'):
            current_player = 'X'
        else:
            current_player = 'O'
        
        move = input("Player " + current_player + ", enter your move (1-9): ")
        
        if move.isdigit():
            move = int(move)
            if move >= 1 and move <= 9 and board[move - 1] == ' ':
                board[move - 1] = current_player
                print_board()

                if check_win(current_player):
                    print("Player " + current_player + " wins!")
                    break

                if ' ' not in board:
                    print("It's a tie!")
                    break
            else:
                print("Invalid move. Try again.")
        else:
            print("Invalid input. Try again.")

# Start the game
play_game()
