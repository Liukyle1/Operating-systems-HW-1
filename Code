#include <iostream>
#include <cstdlib>
#include <string>

using namespace std;

void displayMenu() { 
    cout << "Please select from the menu" << endl;
    cout << "1. List directory contents" << endl;
    cout << "2. Print working directory" << endl;
    cout << "3. Create a new directory" << endl;
    cout << "4. Display a message" << endl;
    cout << "5. Concatenate and display content of file" << endl;
    cout << "6. EXIT" << endl;
}

int main() {
    string input; // set a string just in the case of the user inputing anything that isnt numbers 1-6

    do {
        displayMenu();
        cout << "Please choose an option: ";
        cin >> input;

        try {
            int choice = stoi(input); // uses the "stoi" function to convert string to integer, in the case of an string not being able to convert into an integer "stoi" will throw out an invalid arguement

            switch (choice) {
                case 1:
                cout << "Listing directory contents:" << endl;
                    system("dir"); // uses the shell command "dir" to list directory contents
                     break;
                case 2:
                cout << "Printing working directory:" << endl;
                    system("cd"); // uses the shell command "cd" to print working directory
                    break;
                case 3: { 
                    int mkdirResult = system("mkdir new_folder"); // uses the shell command "mkdir" to create a new directory
                    if (mkdirResult == 0) {
                        cout << "Created new directory" << endl;
                    } else {
                        cout << "Failed to create new folder" << endl; // failed message and returns 1 if failed e.g in the case of there already being the directory mentioned
                        return 1;
                    }
                    int delResult = system("rmdir /s /q old_folder"); // delets an existing directory and its content recursvely
                    if (delResult != 0) {
                        cout << "Unable to delete existing directory" << endl; // failed message and returns 1
                        return 1;
                    }
                    break;
                }
                case 4: {
                    int returnCode = system("echo Hello welcome to Operating systems, Hope you're ready!"); // uses the shell command "echo" to display the message
                    if (returnCode == 0) {
                        cout << "Command executed successfully" << endl;
                    } else {
                        cout << "Command execution failed or returned non-zero: " << returnCode << endl; // failed message
                    }
                    break;
                }
                case 5: {
                    string filename; // creates a string filename
                    cout << "Enter the name of the file to display: ";
                    cin >> filename; // lets the user search for the designated filename
                    int typeResult = system(("type \"" + filename + "\"").c_str()); // using the system "type" to concatenate and display the contents of the file, uses c_str() to pass the string to an arguement
                    if (typeResult != 0) {
                        cout << "Error: Failed to display file content." << endl; // failed message
                    }
                    break;
                }
                case 6:
                    cout << "Exiting the program. Goodbye!" << endl; // exit option for the user
                    break;
                default:
                    cout << "Invalid choice. Please enter a number between 1 and 6." << endl;
                    break;
            }
        } catch (const invalid_argument& e) { // here this catches the invalid arguement when the funtion used earlier "stoi" throws out an invalid arguemnt from the try block
            cout << "Invalid input. Please enter a number between 1 and 6." << endl;
        }
    } while (input != "6");

    return 0;
}
