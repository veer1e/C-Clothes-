#include <iostream>
#include <unistd.h>
#include <stdlib.h>
#include <conio.h>
using namespace std;

const int maxinvsize = 30; // Maximum number of inventory size (adjustable)
const int lowStockThreshold = 10; // Threshold for low stock alert
// Function Login system
bool performLogin(string correctUsername, string correctPassword) 
{

    int maxAttempts = 5;
    int loginAttempts = 0;

    while (loginAttempts < maxAttempts)
    {
        string userName, userPassword;
        cout << "              Clothes++              \n";
        cout << "-------------------------------------\n";
        cout << "Please enter your username: ";
        cin >> userName;
        cout << "Please enter your user password: ";
        cin >> userPassword;

        if (userName == correctUsername && userPassword == correctPassword)
        {
            system("cls"); // Clearing the terminal
            cout << "Login successful!\n";
            return true;
        }
        else
        {
            system("cls");
            cout << "Access Denied!\tPlease try again.\n";
            sleep(1); // Delay
            system("cls");
            loginAttempts++;

            if (loginAttempts == maxAttempts)
            {
                cout << "Maximum number of tries has been reached!\n";
                cout << "Please try again in 1 minute\n";
                sleep(60); // Timeout
                system("cls");
                loginAttempts = 0; // Reset login attempts after timeout
            }
        }
    }
}
// Function to display
void displayInventory(string itemName[], string gender[], string clothingType[], string size[], string design[], int itemQuantity[], int itemCount) 
{
    system("cls"); // Clear screen function
    cout << "                             Inventory                           " << endl;
    cout << "-----------------------------------------------------------------" << endl;
    cout << "Name\t\tGender\tType\tSize\tColor\tQuantity" << endl;
    cout << "-----------------------------------------------------------------" << endl;

    for (int i = 0; i < itemCount; ++i) 
    {
        cout << itemName[i] << "\t"
             << gender[i] << "\t"
             << clothingType[i] << "\t"
             << size[i] << "\t"
             << design[i] << "\t"
             << itemQuantity[i] << endl;
    }
    cout << "-----------------------------------------------------------------" << endl;
}
// Function to add
void addItemToInventory(string itemName[], string gender[], string clothingType[], string size[], string design[], int itemQuantity[], int& itemCount) 
{
    cin.ignore(); // Ignore newline character from previous input
    cout << "Enter item name: ";
    getline(cin, itemName[itemCount]);

    cout << "Enter Gender: ";
    cin >> gender[itemCount];
    
    while (true)
    {
        string Upperwear = "UPW"; 
        string Bottomwear = "BTW"; 
        string userinputCT;

        cout << "Enter Type ([UPW] Upperwear, [BTW] Bottomwear): ";
        cin >> userinputCT;

        if (userinputCT == Upperwear || userinputCT == Bottomwear)
        {
            clothingType[itemCount] = userinputCT;
            break;
        }
        else
        {
            cout << "Invalid input. Please try again." << endl;
            sleep(1);
        }
    }

    while (true)
    {
        string userinputSZ;

        cout << "Enter size (XS-XL): ";
        cin >> userinputSZ;
        if (userinputSZ == "XS" || userinputSZ == "S" || userinputSZ == "M" || userinputSZ == "L" || userinputSZ == "XL")
            {
                size[itemCount] = userinputSZ;
                break;
            }
        else
            {
                cout << "Invalid input. Please try again." << endl;
                sleep(1);
            }
    }

    cin.ignore(); // Ignore newline character from previous input
    cout << "Enter Color: ";
    getline(cin, design[itemCount]);

    cout << "Enter Quantity: ";
    cin >> itemQuantity[itemCount];

    itemCount++;
    system("cls"); // clear screen from terminal

    cout << "Item added to inventory!\n\n";
}

// Function to remove
void removeItemFromInventory(string itemName[], int itemQuantity[], int& itemCount)
{
    cin.ignore(); // Ignore newline character from previous input
    string itemNameToRemove; 

    cout << "Enter the name of the item to remove: ";
    getline(cin, itemNameToRemove); 

    int indexToRemove = -1;

    for (int i = 0; i < itemCount; ++i) // Loop to find the position of the item in the array by comparing the inputted "name" by the user
    {
        if (itemName[i] == itemNameToRemove) 
        {
            indexToRemove = i; // Chaning the item's position to "-1" which removes it from the inventory
            break;
        }
    }

    if (indexToRemove != -1) 
    {
        //  For filling the blanks when an item is removed.
        for (int i = indexToRemove; i < itemCount - 1; ++i) 
        {
            itemName[i] = itemName[i + 1];
            itemQuantity[i] = itemQuantity[i + 1];
        }

        itemCount--;
        system("cls");
        cout << "Item removed from inventory!\n\n";
    } 
    else 
    {
        system("cls");
        cout << "Item not found in inventory.\n\n";
    }
}

// Function to modify the quantity of an item in the inventory
void modifyItemQuantity(string itemName[], int itemQuantity[], int itemCount)
{
    cin.ignore(); // Ignore newline character from previous input
    string itemNameToModify; 

    cout << "Enter the name of the item to modify: ";
    getline(cin, itemNameToModify);

    int indexToModify = -1;
    for (int i = 0; i < itemCount; ++i) //  Loop to find the position of the item in the array by comparing the inputted "name" by the user
    {
        if (itemName[i] == itemNameToModify) {
            indexToModify = i;
            break;
        }
    }

    if (indexToModify != -1) // For changing the found item's quantity 
    {
        cout << "Enter the new quantity: ";
        cin >> itemQuantity[indexToModify];
        system("cls");
        cout << "Quantity modified successfully!\n\n";
    } 
    else 
    {
        system("cls");
        cout << "Item not found in inventory.\n\n";
    }
}
// Function Crtcl Cndtns
void checkCriticalConditions(string itemName[], int itemQuantity[], int itemCount)
{
    cout << "       Inventory Stock Conditions       " << endl;
    cout << "----------------------------------------" << endl;
    cout << "Name\t\tStatus" << endl;
    cout << "----------------------------------------" << endl;

    for (int i = 0; i < itemCount; ++i) // Loop to find if an item's quantity is too much or too low in stock 
    {
        if (itemQuantity[i] <= lowStockThreshold)
        {
            cout << itemName[i] << "\tLow in Stock!" << endl;
        }
        else if (itemQuantity[i] >= maxinvsize) 
        {
            cout << itemName[i] << "\tToo Much Stock!" << endl;
        }
    }

    cout << "----------------------------------------" << endl;
}

int main() 
{
    // Login credentials
    string correctUsername = "admin";
    string correctPassword = "123";
    // Inventory variables
    string itemName[maxinvsize];
    string gender[maxinvsize];
    string clothingType[maxinvsize];
    string size[maxinvsize];
    string design[maxinvsize];
    int itemQuantity[maxinvsize];
    int itemCount = 0;

    // Perform login
    if (!performLogin(correctUsername, correctPassword)) 
    {
        return 0;
    }
    // Inventory system
    while (true) 
    {
        cout << "          Clothes++          \n";
        cout << "-----------------------------\n";
        cout << "1. Display Inventory\n";
        cout << "2. Add Item to Inventory\n";
        cout << "3. Remove Item from Inventory\n";
        cout << "4. Modify Item Quantity\n";
        cout << "5. Business Analytics\n";
        cout << "6. Exit\n";
        cout << "-----------------------------\n";
        int choice;
        cout << "Enter your choice: ";
        cin >> choice;
        
        int anykey;

        switch (choice) {
            case 1:
                system("cls"); // Clear screen function
                displayInventory(itemName, gender, clothingType, size, design, itemQuantity, itemCount); // Calls the displayInventory function
                cout << "Press any number to continue: ";
                cin >> anykey;
                system("cls");
                break;
            case 2:
                system("cls");
                addItemToInventory(itemName, gender, clothingType, size, design, itemQuantity, itemCount); // Calls the addItemToInventory function
                cout << "Press any number to continue: ";
                cin >> anykey;
                system("cls");
                break;
            case 3:
                system("cls");
                displayInventory(itemName, gender, clothingType, size, design, itemQuantity, itemCount); // Calls the displayInventory and removeItemFromInventory function
                removeItemFromInventory(itemName, itemQuantity, itemCount);
                cout << "Press any number to continue: ";
                cin >> anykey;
                system("cls");
                break;
            case 4:
                system("cls");
                displayInventory(itemName, gender, clothingType, size, design, itemQuantity, itemCount); // Calls the displayInventory and modifyItemQuantity function
                modifyItemQuantity(itemName, itemQuantity, itemCount);
                cout << "Press any number to continue: ";
                cin >> anykey;
                system("cls");
                break;
            case 5:
                system("cls");
                checkCriticalConditions(itemName, itemQuantity, itemCount); // Calls the checkCriticalConditions function
                cout << "Press any number to continue: ";
                cin >> anykey;
                system("cls");
                break;
            case 6:
                system("cls");
                cout << "Exiting program...\n";
                sleep(1); 
                return 0; // Kills the code
            default:
                cout << "Invalid choice. Please try again.\n";
        }
    }

