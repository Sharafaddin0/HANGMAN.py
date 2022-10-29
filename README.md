# HANGMAN.py
This program contains codes of hangman game
# Greetings to the hangman game
print("Welcome to the HANGMAN!")
from replit import clear

import random
end_of_game = False

# Computer chooses the random word from words.py
import words
chosen_word = random.choice(words.word_list)

# Bring the logo of game from art.py
from art import logo
print(logo)

# Create a variable called 'lives' to keep track of the number of lives left.
lives = len(chosen_word) - 1

# Create blanks
display = []
for letter in range(len(chosen_word)):
  display += "_"


while not end_of_game:
    guess = input("Guess the random letter: ").lower()

    clear()
  
    if guess in display:
      print(f'You have guessed the letter {guess}')
      
    # Check guessed letter
    for position in range(len(chosen_word)):
      letter = chosen_word[position]
      if letter == guess:
        display[position] = letter
        
    #Join all the elements in the list and turn it into a String.
    print(f"{' '.join(display)}")  
      
    # If guessed letter is False, reduce lives by 1. When lives reached 0, game finished  
    if guess not in chosen_word:
      print("You guessed wrong letter and you lost a life")
      lives -= 1
      if lives == 0:
        end_of_game = True
        print("You lost!")
  
    # If player guessed all letters correctly, he/she is winning
    if "_" not in display:
      end_of_game = True
      print("You win!")
  
    # Bring the arts in stages list to our game from art.py
    from art import stages
    print(stages[lives])
