# User and Admin accounts
users = {
    "user1": {"password": "pass1", "balance": 1000},
    "user2": {"password": "pass2", "balance": 1000},
    "user3": {"password": "pass3", "balance": 1000},
    "user4": {"password": "pass4", "balance": 1000},
    "user5": {"password": "pass5", "balance": 1000},
}

admin = {"password": "adminpass", "balance": 75000}

# Function to lock the account if login fails three times
def lock_account(account_type):
    print(f"Account locked due to multiple failed login attempts. Contact the {account_type}.")
    exit()

# User login
def user_login():
    attempts = 0
    while attempts < 3:
        username = input("Enter User ID: ")
        password = input("Enter Password: ")
        if username in users and users[username]["password"] == password:
            return username
        else:
            print("Invalid User ID or Password. Try again.")
            attempts += 1
    lock_account("user")

# Admin login
def admin_login():
    attempts = 0
    while attempts < 3:
        password = input("Enter Admin Password: ")
        if admin["password"] == password:
            return True
        else:
            print("Invalid Admin Password. Try again.")
            attempts += 1
    lock_account("admin")

# Create new user account
def create_user_account():
    new_username = input("Enter a new username: ")
    new_password = input("Enter a password for the new account: ")
    users[new_username] = {"password": new_password, "balance": 0}
    print("Account created successfully!")

# Cash deposit function
def cash_deposit(username):
    max_deposit = 100000  # Maximum deposit limit (1L)
    denomination = [100, 200, 500, 2000]
    total_deposit = 0

    while True:
        amount = int(input("Enter the deposit amount: "))
        if amount <= max_deposit - total_deposit:
            total_deposit += amount
            for denom in denomination:
                count = amount // denom
                if count > 0:
                    print(f"[{denom}*{count}] = {denom * count}")
                amount %= denom
            users[username]["balance"] += total_deposit
            print(f"Total deposit = {total_deposit}")
            break
        else:
            print("Exceeded maximum deposit limit. Try again.")

# Cash withdraw function
def cash_withdraw(username):
    max_withdraw = 50000  # Maximum withdraw limit (50k)
    denomination = [100, 200, 500, 2000]

    while True:
        amount = int(input("Enter the withdraw amount: "))
        if amount <= max_withdraw and amount <= users[username]["balance"]:
            withdrawn_amount = 0
            for denom in denomination:
                count = amount // denom
                if count > 0:
                    print(f"[{denom}*{count}] = {denom * count}")
                    withdrawn_amount += denom * count
                amount %= denom
            users[username]["balance"] -= withdrawn_amount
            print(f"Total withdraw = {withdrawn_amount}")
            break
        else:
            print("Invalid amount or exceeded maximum withdraw limit. Try again.")

# Check balance function
def check_balance(username):
    balance = users[username]["balance"]
    print(f"Account balance: {balance}")

# Change password function
def change_password(username):
    current_password = input("Enter current password: ")
    if current_password == users[username]["password"]:
        new_password = input("Enter new password: ")
        users[username]["password"] = new_password
        print("Password changed successfully.")
    else:
        print("Invalid password. Password change failed.")

# Admin functions
def admin_total_balance():
    total_balance = admin["balance"]
    print(f"Admin's total balance: {total_balance}")

def admin_cash_deposit():
    max_deposit = 300000  # Maximum cash deposit limit (3L)
    denomination = [100, 200, 500, 2000]
    total_deposit = 0

    while True:
        amount = int(input("Enter the deposit amount: "))
        if amount <= max_deposit - total_deposit:
            total_deposit += amount
            for denom in denomination:
                count = amount // denom
                if count > 0:
                    print(f"[{denom}*{count}] = {denom * count}")
                amount %= denom
            admin["balance"] += total_deposit
            print(f"Total deposit = {total_deposit}")
            break
        else:
            print("Exceeded maximum deposit limit. Try again.")

# Main program
while True:
    print("* Welcome to the ATM *")
    account_type = input("Are you a User or an Admin? (user/admin/exit): ").lower()

    if account_type == "exit":
        print("Thank you. Goodbye!")
        break
    elif account_type == "user":
        username = user_login()
        while True:
            print("\nUser Options:")
            print("1. Cash Deposit")
            print("2. Cash Withdraw")
            print("3. Check Balance")
            print("4. Change Password")
            print("5. Create an Account")
            print("6. Switch to Admin")
            print("7. Exit")
            option = input("Enter option (1/2/3/4/5/6/7): ")

            if option == "1":
                cash_deposit(username)
            elif option == "2":
                cash_withdraw(username)
            elif option == "3":
                check_balance(username)
            elif option == "4":
                change_password(username)
            elif option == "5":
                create_user_account()
            elif option == "6":
                break  # Exit the user loop to switch to admin
            elif option == "7":
                print("Thank you for using the ATM. Goodbye!")
                exit()
            else:
                print("Invalid option. Please try again.")
    elif account_type == "admin":
        if admin_login():
            while True:
                print("\nAdmin Options:")
                print("1. Admin's Total Balance")
                print("2. Admin Cash Deposit")
                print("3. Switch to User")
                print("4. Exit")
                option = input("Enter option (1/2/3/4): ")

                if option == "1":
                    admin_total_balance()
                elif option == "2":
                    admin_cash_deposit()
                elif option == "3":
                    break  # Exit the admin loop to switch to user
                elif option == "4":
                    print("Thank you, Admin. Goodbye!")
                    exit()
                else:
                    print("Invalid option. Please try again.")
    else:
        print("Invalid account type. Please enter 'user', 'admin', or 'exit'.")
