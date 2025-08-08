# hangman_game
A simple hangman game in python 
import random

# List of predefined words
word_list = ['apple', 'train', 'chair', 'house', 'plant']

# Randomly choose a word from the list
secret_word = random.choice(word_list)
guessed_letters = []
tries = 6

print("Welcome to Hangman!")
print("_ " * len(secret_word))  # Display blanks for each letter

while tries > 0:
    guess = input("Guess a letter: ").lower()

    if len(guess) != 1 or not guess.isalpha():
        print("Please enter a single alphabet letter.")
        continue

    if guess in guessed_letters:
        print("You already guessed that letter.")
        continue

    guessed_letters.append(guess)

    if guess in secret_word:
        print("Good guess!")
    else:
        tries -= 1
        print(f"Wrong guess. You have {tries} tries left.")

    # Show current progress
    display_word = ''
    for letter in secret_word:
        if letter in guessed_letters:
            display_word += letter + ' '
        else:
            display_word += '_ '

    print(display_word.strip())

    # Check if player has guessed all letters
    if all(letter in guessed_letters for letter in secret_word):
        print("Congratulations! You guessed the word!")
        break
else:
    print(f"Sorry, you're out of tries. The word was '{secret_word}'.")
