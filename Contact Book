import os
import json

CONTACTS_FILE = "contacts.json"
contacts = []

def load_contacts():
    if os.path.exists(CONTACTS_FILE):
        with open(CONTACTS_FILE, "r") as file:
            return json.load(file)
    else:
        return []

def save_contacts():
    with open(CONTACTS_FILE, "w") as file:
        json.dump(contacts, file)

def add_contact():
    name = input("Enter the contact's name: ")
    phone = input("Enter the contact's phone number: ")
    email = input("Enter the contact's email: ")
    address = input("Enter the contact's address: ")
    contacts.append({"name": name, "phone": phone, "email": email, "address": address})
    save_contacts()
    print("Contact added successfully!")

def view_contacts():
    if not contacts:
        print("No contacts found.")
    else:
        print("Contact List:")
        for i, contact in enumerate(contacts, 1):
            print(f"{i}. Name: {contact['name']}, Phone: {contact['phone']}")

def search_contact():
    search_term = input("Enter the name or phone number to search for: ")
    found_contacts = []
    for contact in contacts:
        if search_term.lower() in contact['name'].lower() or search_term in contact['phone']:
            found_contacts.append(contact)
    if found_contacts:
        print("Search Results:")
        for i, contact in enumerate(found_contacts, 1):
            print(f"{i}. Name: {contact['name']}, Phone: {contact['phone']}")
    else:
        print("No matching contacts found.")

def update_contact():
    view_contacts()
    if not contacts:
        return
    try:
        index = int(input("Enter the index of the contact to update: ")) - 1
        if 0 <= index < len(contacts):
            contact = contacts[index]
            print(f"Updating contact: {contact['name']}")
            contact['name'] = input("Enter the new name (press Enter to keep the same): ") or contact['name']
            contact['phone'] = input("Enter the new phone number (press Enter to keep the same): ") or contact['phone']
            contact['email'] = input("Enter the new email (press Enter to keep the same): ") or contact['email']
            contact['address'] = input("Enter the new address (press Enter to keep the same): ") or contact['address']
            save_contacts()
            print("Contact updated successfully!")
        else:
            print("Invalid index.")
    except ValueError:
        print("Invalid input. Please enter a valid index.")

def delete_contact():
    view_contacts()
    if not contacts:
        return
    try:
        index = int(input("Enter the index of the contact to delete: ")) - 1
        if 0 <= index < len(contacts):
            deleted_contact = contacts.pop(index)
            save_contacts()
            print(f"Contact deleted: {deleted_contact['name']}")
        else:
            print("Invalid index.")
    except ValueError:
        print("Invalid input. Please enter a valid index.")

def generate_report():
    if not contacts:
        print("No contacts found to generate a report.")
    else:
        print("Contact Report:")
        for i, contact in enumerate(contacts, 1):
            print(f"{i}. Name: {contact['name']}, Phone: {contact['phone']}, Email: {contact['email']}, Address: {contact['address']}")

contacts = load_contacts()

while True:
    print("\nContact Management System")
    print("1. Add Contact")
    print("2. View Contacts")
    print("3. Search Contact")
    print("4. Update Contact")
    print("5. Delete Contact")
    print("6. Generate Report")
    print("7. Exit")
    
    choice = input("Enter your choice: ")
    
    if choice == '1':
        add_contact()
    elif choice == '2':
        view_contacts()
    elif choice == '3':
        search_contact()
    elif choice == '4':
        update_contact()
    elif choice == '5':
        delete_contact()
    elif choice == '6':
        generate_report()
    elif choice == '7':
        print("Exiting program. Goodbye!")
        break
    else:
        print("Invalid choice. Please try again.")

