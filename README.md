# CODSOFT_2
import tkinter as tk
from tkinter import messagebox
import random

# Game choices
choices = ["Rock", "Paper", "Scissors"]

# Initialize scores
user_score = 0
computer_score = 0

# Function to determine the result of a round
def determine_winner(user_choice):
    global user_score, computer_score
    
    # Computer makes a random choice
    computer_choice = random.choice(choices)
    
    # Update the computer choice label
    computer_choice_label.config(text=f"Computer chose: {computer_choice}")
    
    # Determine the winner
    if user_choice == computer_choice:
        result = "It's a tie!"
    elif (user_choice == "Rock" and computer_choice == "Scissors") or \
         (user_choice == "Scissors" and computer_choice == "Paper") or \
         (user_choice == "Paper" and computer_choice == "Rock"):
        result = "You win!"
        user_score += 1
    else:
        result = "Computer wins!"
        computer_score += 1

    # Update the result and score labels
    result_label.config(text=result)
    user_score_label.config(text=f"Your Score: {user_score}")
    computer_score_label.config(text=f"Computer Score: {computer_score}")

# Function to reset the game
def reset_game():
    global user_score, computer_score
    user_score = 0
    computer_score = 0
    result_label.config(text="Let's Play!")
    user_score_label.config(text="Your Score: 0")
    computer_score_label.config(text="Computer Score: 0")
    computer_choice_label.config(text="")

# Initialize the Tkinter window
root = tk.Tk()
root.title("Rock-Paper-Scissors Game")
root.geometry("400x400")
root.config(bg="#f0f8ff")

# Heading label
title_label = tk.Label(root, text="Rock-Paper-Scissors", font=("Helvetica", 20, "bold"), bg="#f0f8ff", fg="#333")
title_label.pack(pady=20)

# Label for computer's choice
computer_choice_label = tk.Label(root, text="", font=("Arial", 12), bg="#f0f8ff")
computer_choice_label.pack(pady=10)

# Result label
result_label = tk.Label(root, text="Let's Play!", font=("Arial", 15, "bold"), bg="#f0f8ff", fg="#333")
result_label.pack(pady=10)

# User's choice buttons
button_frame = tk.Frame(root, bg="#f0f8ff")
button_frame.pack(pady=20)

rock_button = tk.Button(button_frame, text="Rock", font=("Arial", 12), width=10, bg="#add8e6", command=lambda: determine_winner("Rock"))
rock_button.grid(row=0, column=0, padx=10)

paper_button = tk.Button(button_frame, text="Paper", font=("Arial", 12), width=10, bg="#add8e6", command=lambda: determine_winner("Paper"))
paper_button.grid(row=0, column=1, padx=10)

scissors_button = tk.Button(button_frame, text="Scissors", font=("Arial", 12), width=10, bg="#add8e6", command=lambda: determine_winner("Scissors"))
scissors_button.grid(row=0, column=2, padx=10)

# Score labels
score_frame = tk.Frame(root, bg="#f0f8ff")
score_frame.pack(pady=10)

user_score_label = tk.Label(score_frame, text="Your Score: 0", font=("Arial", 12), bg="#f0f8ff")
user_score_label.grid(row=0, column=0, padx=20)

computer_score_label = tk.Label(score_frame, text="Computer Score: 0", font=("Arial", 12), bg="#f0f8ff")
computer_score_label.grid(row=0, column=1, padx=20)

# Reset button
reset_button = tk.Button(root, text="Reset", font=("Arial", 12), bg="#4682b4", fg="white", command=reset_game)
reset_button.pack(pady=20)

# Start the main loop
root.mainloop()
