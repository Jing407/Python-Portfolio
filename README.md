# Python-Portfolio
Python projects from International Passports Class
#class 9
#while  loop
#lab 5:  combining while loop with input 
# function and f strings
# real life gaming scenario (homework not needed for the real life use case skip to lake 6)
print("Pablo escobar escaped in part 1! Are you ready to kill him in part 2?!")
print("Let's Rumble!")
name = input("If you about that shooter life, enter your name to begin the game: ")
while name == "":
    print("Player one did not enter his name")
    name = input ("Enter your name to begin the game: ") 
print(f"Welcome {name} to ready to rumble in colombia!")
age = int(input("Enter your age to begin the game: "))
while age < 0:
    print("Age can't be negative!")
    age = int(input("enter your age to begin the game: ")) 
print(f"Thanks for confirming that you are a {age} year old shooter go murk escobar") 

#class 10
#for  loop
#lab 13: python password project 
import random
capital_let = "QwertyUIOPASDFGHJKLZXCVBNM"
small_let = "qwertyuiopasdfghjklzxcvbnm"
numbers = "1234567890"
special_char = "?,.<>!%$]{+*})#@"
upper,lower,digits,odd = True,True,True,True
finalpass = ""
if upper:
    finalpass += capital_let
if lower:
    finalpass += small_let
if digits: 
    finalpass += numbers
if odd:
    finalpass += special_char
length = 20
howmuch = 10
for x in range(howmuch):
    password = "".join(random.sample(finalpass,length))
    print(password)

#lab 10 real life use case program - applying try except
def passport_bros_bank_product():
    ronald_mcdonald = {"balance": 100000, "authenticated": False}
    
    def opening_message_user_sees():
        print("\nHey! Welcome to Passport Bros Bank! ")
        print("1. Check your cash balance")
        print("2. Deposit cash into your account")
        print("3. Withdrawal cash from your bank account")
        print("4. Terminate your current bank session")
        
    def check_your_cash_balnce():
        print(f"\nYour current balnce is: ${ronald_mcdonald['balance']}")
        
    def deposit_cash_into_your_account():
        while True:
            try:
                amount = float(input("\nEnter amount to deposit your cash"))
                if amount > 0:
                    ronald_mcdonald["balance"] += amount
                    print(f"Deposit successful! Your new cash balnce is ${ronald_mcdonald["balance"]}")
                    break
                else:
                    print("Please enter a valid positive number. Numbers less than zero are invalid! ")
            except ValueError:
                print("Invalid input. I don't think you entered an actual number. Please enter a number Ronald.")
    def withdrawal_cash_from_your_bank_account():
        while True:
            try:
                amount = float(input("\nEnter amount to withdrawal cash: $"))
                if amount > 0:
                    if amount <= ronald_mcdonald["balance"]:
                        ronald_mcdonald["balance"] -= amount
                        print(f"Withdrawal successful! Your new balance is ${ronald_mcdonald["balance"]}")
                        break
                    else:
                        print("Request declined! Ronald you have insufficients funds.")
                else:
                    print("Please enter a valid positive number. Numbers less than zero are invalid!")
            except ValueError:
                print("Invalid input. I don't think you entered an actual number. Please enter a number Ronald")
                
    def authenticate_bank_user():
        while ronald_mcdonald["authenticated"] == False:
            password = input("Enter your bank password: ")
            if password == "blasion":
                print("Authentication successful!")
                ronald_mcdonald["authenticated"] = True
            else:
                print("Incorrect password. Try again.")
     
                
    authenticate_bank_user()
    while True:
        opening_message_user_sees
        try:
            selection = int(input("\nHi Ronald! Please select an option from [1-4]: "))
        except ValueError:
            print("Invalid input. Plewase enter a number between 1 and 4. ")
            continue
        
        if selection == 1:
            check_your_cash_balnce()
        elif selection == 2:
            deposit_cash_into_your_account()
        elif selection == 3:
            withdrawal_cash_from_your_bank_account()
        elif selection == 4:
            print("\nThank you for using Passport Bros Bank. See you later and enjoy your next trip!")
            break
        else:
            print("Invalid choice, Please enter a number between 1 and 4. ")
            
passport_bros_bank_product()
