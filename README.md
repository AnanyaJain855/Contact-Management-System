# 📋 Contact Management System

## 📘 Overview

A lightweight yet powerful address book application written in C that simplifies contact management. This console-based application allows users to efficiently store, access, and modify contact information with an intuitive menu-driven interface.

## ✨ Features

- **📝 Add Contact** - Create new entries with name and either phone number or email address
- **🗑️ Delete Contact** - Remove unwanted contacts from your address book
- **✏️ Update Contact** - Modify information for existing contacts
- **👁️ View Contacts** - Display all stored contacts in an organized format
- **🔍 Search Contact** - Find specific contacts by name

## 🚀 Usage

When you run the application, you'll be presented with a simple menu interface:

```
*** Address Book Menu ***
1. Add Contact
2. Delete Contact
3. Update Contact
4. View Contacts
5. Search Contact
6. Exit
Enter your choice: 
```

Simply enter the number corresponding to the action you want to perform and follow the prompts.

## 🏗️ Code Structure

### Contact Structure

The application uses a custom structure to store contact information:

```c
struct Contact {
    char name[NAME_LENGTH];          // Stores contact name
    union {
        char phone[PHONE_LENGTH];    // Stores phone number
        char email[EMAIL_LENGTH];    // Stores email address
    } contactInfo;
    int isPhone;                     // Flag: 1 for phone, 0 for email
};
```

### Main Function

The main function manages the menu system and directs the program flow:

```c
int main() {
    struct Contact addressBook[MAX_CONTACTS];  // Array of contacts
    int numContacts = 0;                       // Contact counter
    int choice;                               // User menu selection
    
    do {
        // Display menu options
        printf("\n*** Address Book Menu ***\n");
        printf("1. Add Contact\n");
        printf("2. Delete Contact\n");
        printf("3. Update Contact\n");
        printf("4. View Contacts\n");
        printf("5. Search Contact\n");
        printf("6. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);
        
        // Process user choice
        switch (choice) {
            case 1:
                addContact(addressBook, &numContacts);
                break;
            case 2:
                deleteContact(addressBook, &numContacts);
                break;
            case 3:
                updateContact(addressBook, numContacts);
                break;
            case 4:
                viewContacts(addressBook, numContacts);
                break;
            case 5:
                searchContact(addressBook, numContacts);
                break;
            case 6:
                printf("Exiting...\n");
                break;
            default:
                printf("Invalid choice. Please try again.\n");
        }
    } while (choice != 6);
    
    return 0;
}
```

## 📋 Requirements

- C compiler (gcc recommended)
- Standard C libraries

## 🔧 Installation

1. Clone this repository
2. Compile the source code:
   ```
   gcc -o contact_manager main.c
   ```
3. Run the application:
   ```
   ./contact_manager
   ```
