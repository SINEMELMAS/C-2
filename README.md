# C++2
#include <iostream>
using namespace std;

class Node {
public:
    int data;
    Node* next;
};

class LinkedList {
private:
    Node* head;
public:
    LinkedList() {
        head = nullptr;
    }

    void add(int value) {
        Node* newNode = new Node();
        newNode->data = value;
        newNode->next = head;
        head = newNode;
        cout << "Element added successfully." << endl;
    }

    void deleteNode(int value) {
        Node* temp = head;
        Node* prev = nullptr;

        while (temp != nullptr && temp->data != value) {
            prev = temp;
            temp = temp->next;
        }

        if (temp == nullptr) {
            cout << "Element not found in the list." << endl;
            return;
        }

        if (prev != nullptr) {
            prev->next = temp->next;
        } else {
            head = temp->next;
        }

        delete temp;
        cout << "Element deleted successfully." << endl;
    }

    void search(int value) {
        Node* temp = head;
        while (temp != nullptr) {
            if (temp->data == value) {
                cout << "Element found in the list." << endl;
                return;
            }
            temp = temp->next;
        }
        cout << "Element not found in the list." << endl;
    }

    void print() {
        Node* temp = head;
        cout << "Linked List: ";
        while (temp != nullptr) {
            cout << temp->data << " ";
            temp = temp->next;
        }
        cout << endl;
    }

    ~LinkedList() {
        Node* temp = head;
        while (temp != nullptr) {
            Node* next = temp->next;
            delete temp;
            temp = next;
        }
    }
};

int main() {
    LinkedList list;
    int choice, value;

    cout << "===============By Sinem Elmas================" << endl;
    cout << "~~ WELCOME to Linked List program ~~" << endl;
    cout << "=============================================" << endl;
    cout << "Select and Enter Your Choice from the Menu __" << endl;
    cout << "=============================================" << endl;
    cout << "1. Add" << endl;
    cout << "2. Delete" << endl;
    cout << "3. Search" << endl;
    cout << "4. Print" << endl;
    cout << "5. Exit" << endl;

    while (true) {
        cout << "Enter your choice: ";
        cin >> choice;

        switch (choice) {
            case 1:
                cout << "Enter the element to add: ";
                cin >> value;
                list.add(value);
                break;
            case 2:
                cout << "Enter the element to delete: ";
                cin >> value;
                list.deleteNode(value);
                break;
            case 3:
                cout << "Enter the element to search: ";
                cin >> value;
                list.search(value);
                break;
            case 4:
                list.print();
                break;
            case 5:
                cout << "Exiting the program. Goodbye!";
                exit(0);
            default:
                cout << "Invalid choice. Please enter a valid option." << endl;
        }
    }

    return 0;
}

