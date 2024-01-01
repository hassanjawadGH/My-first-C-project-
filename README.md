# My-first-Cpp-project-
The basic version of Grocery Store Management system.


#include <iostream>
#include <iomanip>
#include <string>

using namespace std;

int shelves = 0; //Global variable for total shelves 
int positions = 0; //Global variable fot total postions in a shelve 

void insertAnItem (string items [][100]); // Prototype of a function for inserting an item into a selected shelf
void displayAllItems (string items [][100]); // Prototype of a function for Displaying all items of total shelves
void removeAnItem (string items [][100]); // Prototype of a function for removing a single item from a shelf
void removeAllItems (string items [][100]); // Prototype of a function for removing all items 
void totalItems (string items [][100]); // Prototype of a function for finding total number of items in shelf 
void findAnItem (string items [][100]); // Prototype of a function for finding an item from a shelf
void updateAnItem (string items [][100]); // Prototype of a function for updating an item on the shlef 
void emptyShelfCheck (string items [][100]); // Prototype of a function for checking the shelves if they are empty or not 
void fullShelfCheck (string items [][100]); // Prototype of a function for checing empty space in shlef, if any

int main()
{
    int choice = 10;
    
    cout <<"\n\t "<< setw(56) << setfill('$') << "\n";
    cout << "\t Welcome to Departmental Store Management System-DSMS :)"; 
	cout <<"\n\t "<< setw(56) << setfill('$') << "\n\n";
	cout << "\t pov'This system is only for 100 items in a shelf!'\n\n\n\n"; 
	
	string items [100][100]; 
	
	
	do {
		cout << "\t Please! \n";
        cout << "\t Enter the no. of shelves : ";
        cin >> shelves;
        cout << "\t Enter the no. of positions on each shelf : ";
        cin >> positions;

        if (shelves <= 0 || positions <= 0) {
            cout << "\t !!! Shelves and positions should be greater than zero :(\n\t Please enter the values again :)" << endl;
        } else {
            for (int i = 0; i < shelves; i++) {
                for (int j = 0; j < positions; j++) {
                    items[i][j] = ""; //for alloting index number to a given position
                }
            }
        }
    } while (shelves <= 0 || positions <= 0); // whill repeat the code in case if the input data is wrong (means 0 or less then 0)
    

    cout << "\n\t........................ MENU .......................\n\n";
    cout << "\t Press a number from 0-9 for specific task:\n";
    cout << "\t\t 1: Insert an item\n";
    cout << "\t\t 2: Display all items\n";
    cout << "\t\t 3: Remove an item\n";
    cout << "\t\t 4: Remove all items\n";
    cout << "\t\t 5: Return the total no. of items\n";
    cout << "\t\t 6: Find an item\n";
    cout << "\t\t 7: Update an item\n";
    cout << "\t\t 8: Check if the shelf is empty\n";
    cout << "\t\t 9: Check if the shelf is full\n";
    cout << "\t\t 0: Quit";
    cout << "\n\t....................End of MENU ....................\n\n";

   

   
   while (choice != 0)// this loop will prevent the user from pressing wrong option 
    { 
			cout << "\n\t Choice : ";
        	cin >> choice;
        	while (choice > 9 || choice < 0)
        	{
            	cout << "\t!!! Invalid choice entered. Try again : ";
            	cin >> choice;
        	}

        switch (choice) // used to call funtions according to manu
        {
            case 1:
            {
                insertAnItem (items);
                break;
            }

            case 2:
            {
                displayAllItems (items);
                break;
            }

            case 3:
            {
                removeAnItem (items);
                break;
            }

            case 4:
            {
                removeAllItems (items);
                break;
            }

            case 5:
            {
                totalItems (items);
                break;
            }

            case 6:
            {
                findAnItem (items);
                break;
            }

            case 7:
            {
                updateAnItem (items);
                break;
            }

            case 8:
            {
                emptyShelfCheck (items);
                break;
            }

            case 9:
            {
                fullShelfCheck (items);
                break;
            }

            case 0:
            {
                cout << "\n\n\t Thank you :) \n";
                break;
            }
        }
    }
    return 0;
}

void removeAnItem (string items [][100])
{	cout <<"\t" << setw(55) << setfill('*') << " \n";
    int shelf, position;

    cout << "\n\n\t Enter the shelf no: ";
    cin >> shelf;

    if (shelf > shelves || shelf < 1)
    {
        cout << "\t !!! Invalid shelf no. entered :( \n\n";
    }

    else
    {
        cout << "\t Enter the position no. : ";
        cin >> position;

        if (position > positions || position < 1)
        {
            cout << "\t !!! Invalid position no. entered :( \n\n";
        }

        else
        {
            if (items [shelf - 1][position - 1] == "")//this will check if the shelf is empty or not; as shelf and position is >=1,1-1=0, if item[i][j] is empty then,
            {
                cout << "\n\t !!! No item to remove on this position :( \n\n";
            }

            else
            {
                items [shelf - 1][position - 1] = "";
                cout << "\n\t Item removed successfully :) \n\n";
            }
        }
    }
    cout <<"\t" << setw(55) << setfill('*') << " " ;
}
void removeAllItems (string items [][100])
{
	cout <<"\t" << setw(55) << setfill('*') << " \n";
    for (int i = 0; i < shelves; i++)
    {
        for (int j = 0; j < positions; j++)
        {
            items [i][j] = ""; // asigning the empty string to all vaues of arry / deleting itesm 
        }
    }

    cout << "\n\t All items removed from every shelf successfully :) \n\n";
    cout <<"\t" << setw(55) << setfill('*') << " ";
}

void totalItems (string items [][100])
{
    int countOfItems = 0;
	cout <<"\t" << setw(55) << setfill('*') << " \n";
    for (int i = 0; i < shelves; i++)
    {
        for (int j = 0; j < positions; j++)
        {
            if (items [i][j] != "")// counting all non emoty strings/
            {
                countOfItems++;
            }
        }
    }

    cout << "\n\t Total no. of items is: " << countOfItems << endl << endl;
    cout <<"\t" << setw(55) << setfill('*') <<" " ;
}

void displayAllItems (string items [][100])
{
    cout << endl;
	cout <<"\t" << setw(55) << setfill('*') << " \n";
    for (int i = 0; i < shelves; i++)
    {
        cout << "\n\t Shelf no. : " << (i + 1) << endl;

        for (int j = 0; j < positions; j++)
        {
            cout << "\n\t Position no. : " << (j + 1) << endl;

            if (items [i][j] == "")
            {
                cout << "\t No item here!";
            }

            else
            {
                cout << "\t " << items [i][j];
            }
        }
    cout << endl << endl;
    }
    cout << "\t" <<setw(55) << setfill('*') <<" ";
}

void insertAnItem (string items [][100]) // User function for inserting an item in slescted shelf  // Opt1
{	
	cout <<"\t" << setw(55) << setfill('*') << " \n";
    int shelf, position;  
    cout <<"\t" << setw(55) << setfill('*') << " \n";

    cout << "\n\n\t Enter the no. of shelf : ";
    cin >> shelf;

    if (shelf > shelves || shelf < 1)
    {
        cout << "\t Invalid no. of shelf entered :( \n\n";
    }

    else
    {
        cout << "\t Enter the position : ";
        cin >> position;

        if (position > positions || position < 1)
        {
            cout << "\t Invalid position entered :( \n\n";
        }

        else
        {
            cin.ignore();// in order to remove next line identifier in buffer 

            cout << "\t Enter the item's name: ";
            getline (cin, items [shelf - 1][position - 1]);

            cout << "\t Item added successfully :) \n";
        }
    }
    cout <<"\t" << setw(55) << setfill('*') << " \n";
}

void findAnItem (string items [][100])
{	
	cout <<"\t" << setw(55) << setfill('*') << " \n";
    string item;
    bool check = false;

    cout << "\n\n\t Enter the item's name to find : ";
    cin >> item;

    for (int i = 0; i < shelves; i++)
    {
        for (int j = 0; j < positions; j++)
        {
            if (items [i][j] == item)
            {
                cout << "\t Item found in shelf no. " << (i + 1) << ", position no. " << (j + 1) << endl << endl;
                check = true; 
            }
        }
    }

    if (check == false)
    {
        cout << "\t This item doesn't found :( \n\n";
    }
    cout <<"\t" << setw(55) << setfill('*') << " \n";
}


void updateAnItem (string items [][100])
{	
	cout <<"\t" << setw(55) << setfill('*') << " \n";
    int shelf, position;

    cout << "\n\n\t Enter the shelf no. : ";
    cin >> shelf;

    if (shelf > shelves || shelf < 1)
    {
        cout << "\t Invalid shelf no. entered :( \n\n";
    }

    else
    {
        cout << "\t Enter the position no. : ";
        cin >> position;

        if (position > positions || position < 1)
        {
            cout << "\t Invalid position no. entered :( \n\n";
        }

        else
        {
            cin.ignore();

            cout << "\t Enter the item's name to update with : ";
            getline(cin, items [shelf - 1][position - 1]);

            cout << "\t Shelf updated successfully\n";
        }
    }
    cout <<"\t" << setw(55) << setfill('*') << " ";
}


void emptyShelfCheck (string items [][100])
{
	cout <<"\t" << setw(55) << setfill('*') << " \n";
    int shelf;
    bool emptyCheck = true;

    cout << "\n\n\t Enter the shelf no. : ";
    cin >> shelf;

    if (shelf > shelves || shelf < 1)
    {
        cout << "\t Invalid shelf no. entered :( \n\n";
    }

    else
    {
        for (int i = 0; i < shelves; i++)
        {
            if (i == shelf - 1)
            {
                for (int j = 0; j < positions; j++)
                {
                    if (items [i][j] != "")
                    {
                        emptyCheck = false;
                    }
                }
            }
        }

        if (emptyCheck == true)
        {
            cout << "\t Shelf no. " << shelf << " is empty\n\n";
        }

        else
        {
            cout << "\t Shelf no. " << shelf << " is not empty\n\n";
        }
    }
    cout <<"\t" << setw(55) << setfill('*') << " ";
}


void fullShelfCheck (string items [][100])
{
	cout <<"\t" << setw(55) << setfill('*') << " \n";
    int shelf;
    bool fullCheck = true;

    cout << "\n\n\t Enter the shelf no. : ";
    cin >> shelf;

    if (shelf > shelves || shelf < 1)
    {
        cout << "\t Invalid shelf no. entered :( \n\n";
    }

    else
    {
        for (int i = 0; i < shelves; i++)
        {
            if (i == shelf - 1)
            {
                for (int j = 0; j < positions; j++)
                {
                    if (items [i][j] == "")
                    {
                        fullCheck = false;
                    }
                }
            }
        }

        if (fullCheck == true)
        {
            cout << "\t Shelf no. " << shelf << " is full\n\n";
        }

        else
        {
            cout << "\t Shelf no. " << shelf << " is not full\n\n";
        }
    }
    cout <<"\t" << setw(55) << setfill('*') << " ";
  
}
// code ended finaly :))))))
