#include<iostream>
#include<cstdlib>
#include<cstring>
#include<windows.h>
#include<limits>
using namespace std;
int call();
void display();
int main()
{
    char a;
    cout<<"\t***********************************************Word Gussing Game*********************************************************\n\n"<<endl;
    
	 char n;
     string Name;
     cout<<"Enter name  :       ";
     getline(cin,Name);
     cout<<endl;
     int score=0;
     do
     {
     	system("cls");
     	display(); 	
        score=score+call();
        cout<<"Do you want to play again y/n   :   ";
        cin>>n;
        cout<<endl;
     }while(n!='n');
     cout<<Name<<"  ";
     cout<<"your score is   :   "<<score<<endl;
     cout<<"\n\n\t***************************************************************************************************************\n\n"<<endl;
}

   int call() {
    string words[] = {"cat","dog","lion",
					"tiger","elephant","girraf","monkey","duck"
							,"wolf","cow"};
    const int numWords = 10;

    char arr[10][10];
    for (int i = 0; i < 10; i++) {
        for (int j = 0; j < 10; j++) {
            arr[i][j] = 'a' + rand() % 26;
        }
    }

    int index = rand() % numWords;
    string output = words[index];

    int row, col;
    if (output.length() % 2 == 0) {
        row = rand() % 10;
        col = rand() % (10 - output.length() + 1);
        for (int i = 0; i < output.length(); i++) {
            arr[row][col + i] = output[i];
        }
    } else {
        row = rand() % (10 - output.length() + 1);
        col = rand() % 10;
        for (int i = 0; i < output.length(); i++) {
            arr[row + i][col] = output[i];
        }
    }

    for (int i = 0; i < 10; i++) {
        for (int j = 0; j < 10; j++) {
            cout << " " << arr[i][j];
            Sleep(90);// Correct usage
        }
        cout << endl;
    }

    int hint;
    string guess;
    while (true) {
        cout << "Press 1 to Guess the word" << endl;
        cout << "Press 2 to see a hint and then guess the word" << endl;
        cout << "Enter input: ";

        // Validate input
        while (!(cin >> hint) || (hint != 1 && hint != 2)) {
            cout << "Invalid input. Please enter 1 or 2: ";
            cin.clear(); // Clear the error flag
            cin.ignore(numeric_limits<streamsize>::max(),'\n'); // Discard invalid input
        }

        cout << endl;

        if (hint == 2) {
            cout << "The length of the word is: " << output.size() << endl;
        }

        cout << "Enter the word you guessed: ";
        cin >> guess;
        cout << endl;

        if (guess == output) {
            cout << "Congratulations! You guessed the correct word." << endl;
            return 1;
        } else {
            cout << "Sorry! Your guessed word is incorrect. Try again." << endl;
            return 0;
        }
    }
}



void display()
{
	    cout<<"\t***********************************************Word Gussing Game*********************************************************\n\n"<<endl;
    cout<<"You have to guess the word in this puzzle"<<endl;
    cout<<"For example word in this puzzle can be (Dangerous Animals or Pet Animals)"<<endl;
    cout<<"You can also take help for hint from the system"<<endl<<endl;
    
}

