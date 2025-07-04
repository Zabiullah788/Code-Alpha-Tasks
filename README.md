# Task 1:
import random

# Predefined list of words
words = ["python", "hangman", "computer", "program", "keyboard"]
word = random.choice(words)

guessed = []
tries = 6

print("Welcome to Hangman by ZB!")
print("_ " * len(word))

while tries > 0:
    guess = input("Guess a letter: ").lower()

    if guess in guessed:
        print("You already guessed that letter.")
        continue

    guessed.append(guess)

    if guess in word:
        print("Correct guess!")
    else:
        tries -= 1
        print(f"Wrong guess! {tries} Tries left:")

    # Display current progress
    display_word = ""
    for letter in word:
        if letter in guessed:
            display_word += letter + " "
        else:
            display_word += "_ "
    print(display_word.strip())

    if all(letter in guessed for letter in word):
        print("Congratulations! You guessed the word correctly.")
        break
else:
    print(f"Game over! The word was '{word}'.")



**Task 2**
stock_prices = {
    "AAPL": 180,
    "TSLA": 250,
    "GOOG": 135,
    "MSFT": 310,
    "AMZN": 125
}

portfolio = {}
total_value = 0

print("Welcome to Stock Portfolio Tracker by ZB")

while True:
    stock = input("Enter stock symbol (or type 'done' to finish): ").upper()
    if stock == 'DONE':
        break
    if stock not in stock_prices:
        print("Stock not found in our list. Try again.")
        continue

    try:
        qty = int(input(f"Enter quantity for {stock}: "))
    except ValueError:
        print("Invalid quantity. Please enter a number.")
        continue

    portfolio[stock] = qty
    total_value += stock_prices[stock] * qty

# Display portfolio
print("\nYour Portfolio Summary:")
for stock, qty in portfolio.items():
    print(f"{stock}: {qty} shares @ ${stock_prices[stock]} = ${stock_prices[stock] * qty}")

print(f"\nTotal Investment Value: ${total_value}")

# Optional: Save to file
save = input("Do you want to save this to a file? (y/n): ").lower()
if save == 'y':
    with open("portfolio_summary.txt", "w") as f:
        f.write("Your Portfolio Summary:\n")
        for stock, qty in portfolio.items():
            f.write(f"{stock}: {qty} shares @ ${stock_prices[stock]} = ${stock_prices[stock] * qty}\n")
        f.write(f"\nTotal Investment Value: ${total_value}")
    print("Saved to portfolio_summary.txt")
