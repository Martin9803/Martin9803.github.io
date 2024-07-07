# Expense Tracker
## By Martin Sattam
def add_transaction(transactions, type):
    description = input(f"Enter the {type} description: ")
    amount = float(input(f'Enter the {type} amount: '))

    transaction = {
        "description": description, "amount": amount, "type": type
    }
    transactions.append(transaction)
    print("Successfully added transaction.")

def view_transactions(transactions, income):
    if len(transactions) == 0:
        print("No transactions in list.")
        return
    
    expenses = 0.00

    for i, transaction in enumerate(transactions, 1):
        type = transaction['type']
        amount = transaction['amount']
        print(f"{i}. Description: {transaction['description']}, Amount: ${amount}, Type: {type}")

        if type == "expense":
                expenses += amount
        elif type == "income":
                income += amount
    Balance = income - expenses
    print(f"\n Total Expenses: ${expenses:.2f}")
    print(f"\n Total Income: ${income:.2f}")
    print(f"\n Net Balance: ${Balance:.2f}")

def remove_transaction(transactions, income):
    view_transactions(transactions, income)
    if len(transactions) == 0:
         return
    index = int(input("Enter the number of the transaction to remove: ")) - 1
    if 0 <= index < len(transactions):
        transaction_remove = transactions.pop(index)
        print(f"Index {index} has been removed from tracker.")
    else:
         print("Index is invalid. Try again.")

def main():
    print("Welcome to the Expense Planner!")
    print("This program is designed to help you organize where you spend your money.\nAlong with making sure you don't go over your provided income.")
    transactions = []
    income = float(input("Enter your starting amount of money: "))
    while True:
        print()
        print("Select an option below")
        print("1. Add Expense")
        print("2. Add Extra Income")
        print("3. View Transactions")
        print("4. Remove Transaction")
        print("5. Exit")

        x = int(input("Choose a command: "))
        if x == 1:
            add_transaction(transactions, "expense")
        elif x == 2:
            add_transaction(transactions, "income")
        elif x == 3:
            view_transactions(transactions, income)
        elif x == 4:
            remove_transaction(transactions, income)
        elif x == 5:
            print("Exiting program...")
            break
        else:
            print("Not a valid choice. Please try again.")

if __name__ == "__main__":
    main()
