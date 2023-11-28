import random

class RockPaperScissorsGame:
    def __init__(self):
        self.user_score = 0
        self.computer_score = 0

    def get_user_choice(self):
        user_choice = input("Choose rock, paper, or scissors: ").lower()
        while user_choice not in ["rock", "paper", "scissors"]:
            print("Invalid choice. Please choose rock, paper, or scissors.")
            user_choice = input("Choose rock, paper, or scissors: ").lower()
        return user_choice

    def get_computer_choice(self):
        return random.choice(["rock", "paper", "scissors"])

    def determine_winner(self, user_choice, computer_choice):
        if user_choice == computer_choice:
            return "It's a tie!"
        elif (
            (user_choice == "rock" and computer_choice == "scissors") or
            (user_choice == "scissors" and computer_choice == "paper") or
            (user_choice == "paper" and computer_choice == "rock")
        ):
            self.user_score += 1
            return "You win!"
        else:
            self.computer_score += 1
            return "You lose!"

    def display_result(self, user_choice, computer_choice, result):
        print(f"\nYour choice: {user_choice}")
        print(f"Computer's choice: {computer_choice}")
        print(f"Result: {result}")
        print(f"Your Score: {self.user_score} | Computer Score: {self.computer_score}")

    def play_again(self):
        return input("Do you want to play again? (yes/no): ").lower() == "yes"


def main():
    rps_game = RockPaperScissorsGame()

    while True:
        user_choice = rps_game.get_user_choice()
        computer_choice = rps_game.get_computer_choice()
        result = rps_game.determine_winner(user_choice, computer_choice)
        rps_game.display_result(user_choice, computer_choice, result)

        if not rps_game.play_again():
            print("Thanks for playing! Goodbye!")
            break


if __name__ == "__main__":
    main()
