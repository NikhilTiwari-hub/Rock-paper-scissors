# Rock-paper-scissors
"Rock Paper Scissors game challenge"
# RPS.py
import random

# Define the possible moves
MOVES = ['R', 'P', 'S']

def player(prev_play, opponent_history=[]):
    """Return the next move based on the opponent's previous move."""
    if prev_play == "":
        # For the first game, pick randomly
        return random.choice(MOVES)
    
    # Track the opponent's history to develop a strategy
    opponent_history.append(prev_play)
    
    # Simple strategy: Predict that the opponent will repeat their last move
    if len(opponent_history) > 1 and opponent_history[-2] == opponent_history[-1]:
        return random.choice(MOVES)  # Pick randomly if opponent repeats moves
    
    # Default strategy: pick the move that beats the opponent's last move
    if prev_play == 'R':
        return 'P'  # Paper beats Rock
    elif prev_play == 'P':
        return 'S'  # Scissors beats Paper
    else:
        return 'R'  # Rock beats Scissors
