# A Basic Guessing Game
```Python
#Have a variable with a number between 1 and 20 for the user to guess. (you can research random package if you are feeling frisky).
#Import the random packet to assign a variable a random number
import random

#Assign the variable a random int between 1 and 20
random_num = random.randint(1,20)

#Using a loop, compare the users guess, check user input against the number you have stored.When they get it correctly show a success message and end the program.
guess_counter = 0
while guess_counter <= 20:
    #Assign the number that a user guesses to an int via input. Handle error exceptions
    try:
        user_guess = int(input('Guess a number between 1 and 20:'))
    except:
        print('There was a problem, please try again.')
        exit(0)
    #Compare user input to variable with if statements
    if user_guess == random_num:
        print('Correct! Nice job.')
        exit(0)
    else:
        print('Incorrect, please try again.')
    guess_counter+=1

#If guesses have run out, print this
print('No more guesses left, try again later.')
```