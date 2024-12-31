#include <iostream>
using namespace std;

class ATM
{
private:
    int pin = 1234;
    int balance = 1000;
    int attempts = 0;

public:
    void login()
	{
        int enteredPin;
        while (attempts < 3)
		{
            cout << "Enter PIN: ";
            cin >> enteredPin;

            if (enteredPin == pin)
			{
                cout << "Login successful!" << endl;
                showMenu();
                return;
            }
				else
			{
                cout << "Incorrect PIN. You have " << 3 - (attempts + 1) << " attempts left." << endl;
                attempts++;
            }
        }
        cout << "ATM locked. Too many incorrect attempts." << endl;
    }

    void showMenu()
	{
        int choice;
        do
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
                case 1:
                    checkBalance();
                    break;
                case 2:
                    withdrawMoney();
                    break;
                case 3:
                    depositMoney();
                    break;
                case 4:
                    changePin();
                    break;
                case 5:
                    cout << "Thank you for using the ATM. Goodbye!" << endl;
                    exit(0);
                    break;
                default:
                    cout << "Invalid option. Please try again." << endl;
            }
        }
		while (true);
    }

    void checkBalance()
	{
        cout << "Your current balance is: $" << balance << endl;
    }

    void withdrawMoney()
	{
        int amount;
        cout << "Enter amount to withdraw: $";
        cin >> amount;

        if (amount > balance)
		{
            cout << "Insufficient balance!" << endl;
        }
			else
		{
            balance -= amount;
            cout << "You have successfully withdrawn $" << amount << ". Your new balance is: $" << balance << endl;
        }
    }

    void depositMoney()
	{
        int amount;
        cout << "Enter amount to deposit: $";
        cin >> amount;

        balance += amount;
        cout << "You have successfully deposited $" << amount << ". Your new balance is: $" << balance << endl;
    }

    void changePin()
	{
        int newPin;
        cout << "Enter your new PIN: ";
        cin >> newPin;
        pin = newPin;
        cout << "Your PIN has been successfully changed." << endl;
    }
};

int main()
{
    ATM atm;
    atm.login();
    return 0;
}
