#include <iostream>
using namespace std;
int main()
{

    int pin = 1234;
    int enteredPin;
    double balance = 1000.00;
    int attempts = 0;
    bool isLocked = false;

    while (attempts < 3)
	{
        cout << "Enter PIN: ";
        cin >> enteredPin;

        if (enteredPin == pin)
		{
            cout << "PIN correct! Welcome to the ATM.\n";
            break;
        }
			else
		{
            attempts++;
            cout << "Incorrect PIN. You have " << 3 - attempts << " attempt(s) left.\n";
        }
	        if (attempts == 3)
		{
            cout << "ATM is locked due to 3 failed attempts.\n";
            isLocked = true;
        }
    }

    // If ATM is locked, exit the program
    	if (isLocked)
	{
        return 0;
    }

    // Main menu after successful login
    int choice;
    while (true)
	{
        cout << "\nATM Menu:\n";
        cout << "1. Check Balance\n";
        cout << "2. Withdraw Money\n";
        cout << "3. Deposit Money\n";
        cout << "4. Change PIN\n";
        cout << "5. Exit\n";
        cout << "Enter your choice: ";
        cin >> choice;

        	switch (choice)
		{
            case 1: // Check Balance
                cout << "Your balance is: $" << balance << "\n";
                break;
            case 2:
			{ // Withdraw Money
                double withdrawAmount;
                cout << "Enter amount to withdraw: $";
                cin >> withdrawAmount;
                if (withdrawAmount <= balance)
				{
                    balance -= withdrawAmount;
                    cout << "You have withdrawn $" << withdrawAmount << "\n";
                    cout << "Remaining balance: $" << balance << "\n";
                }
					else
				{
                    cout << "Insufficient funds.\n";
                }
                break;
            }
            case 3:
			{ // Deposit Money
                double depositAmount;
                cout << "Enter amount to deposit: $";
                cin >> depositAmount;
                balance += depositAmount;
                cout << "You have deposited $" << depositAmount << "\n";
                cout << "New balance: $" << balance << "\n";
                break;
            }
            case 4:
			{ // Change PIN
                int newPin;
                cout << "Enter new PIN: ";
                cin >> newPin;
                pin = newPin;
                cout << "Your PIN has been changed successfully.\n";
                break;
            }
            case 5: // Exit
                cout << "Exiting... Thank you for using the ATM!\n";
                return 0;
            default:
                cout << "Invalid option. Please try again.\n";
        }
    }
    return 0;
}
