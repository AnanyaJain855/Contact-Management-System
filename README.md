# Contact-Management-System

##Description
This is a simple Address Book application written in C. It allows users to manage their contacts by adding, deleting, updating, viewing, and searching for contacts. Each contact can have either a phone number or an email address associated with it.

##Features
**Add Contact:** Add a new contact to the address book.
**Delete Contact:** Remove an existing contact from the address book.
**Update Contact:** Update the information of an existing contact.
**View Contacts:** View all contacts in the address book.
**Search Contact:** Search for a specific contact by name.

##Usage
**1)Upon Running the Application:**
*** Address Book Menu ***
1. Add Contact
2. Delete Contact
3. Update Contact
4. View Contacts
5. Search Contact
6. Exit
Enter your choice:

**2)Enter the Option: Type the corresponding number to perform an action (e.g., 1 to add a contact).**

##Code Structure
**Contact Structure**
**The Contact structure holds the contact information:**
struct Contact {
    char name[NAME_LENGTH]; // Holds the name of the contact
    union {
        char phone[PHONE_LENGTH]; // Union to hold phone number
        char email[EMAIL_LENGTH]; // Union to hold email address
    } contactInfo;
    int isPhone; // Flag to indicate whether phone number is present (1) or email (0)
};

**Main Function
The main function handles the menu and user inputs:**
int main() {
    struct Contact addressBook[MAX_CONTACTS]; // Array to store contacts
    int numContacts = 0; // Variable to track the number of contacts
    int choice; // Variable to store user's menu choice
    do {
        printf("\n*** Address Book Menu ***\n");
        printf("1. Add Contact\n");
        printf("2. Delete Contact\n");
        printf("3. Update Contact\n");
        printf("4. View Contacts\n");
        printf("5. Search Contact\n");
        printf("6. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);
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

