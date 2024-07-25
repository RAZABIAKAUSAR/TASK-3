# TASK-3
import java.util.ArrayList;
import java.util.Scanner;

public class ContactManager {
  private ArrayList<Contact> contactList;
  private static Scanner input;

  public ContactManager() {
    contactList = new ArrayList<>();
    input = new Scanner(System.in);
  }

  public void addContact() {
    System.out.println("Enter name:");
    String name = input.nextLine();
    System.out.println("Enter phone number:");
    String phoneNumber = input.nextLine();
    System.out.println("Enter email address:");
    String email = input.nextLine();
    Contact newContact = new Contact(name, phoneNumber, email);
    contactList.add(newContact);
  }

  public void readContactList() {
    for (Contact contact : contactList) {
      System.out.println("Name: " + contact.getName());
      System.out.println("Phone Number: " + contact.getPhoneNumber());
      System.out.println("Email: " + contact.getEmail());
      System.out.println("--------------------");
    }
  }

  public void editContact() {
    System.out.println("Enter name of contact to edit:");
    String name = input.nextLine();
    for (Contact contact : contactList) {
      if (contact.getName().equals(name)) {
        System.out.println("Enter new phone number:");
        String newPhoneNumber = input.nextLine();
        System.out.println("Enter new email address:");
        String newEmail = input.nextLine();
        contact.setPhoneNumber(newPhoneNumber);
        contact.setEmail(newEmail);
        break;
      }
    }
  }

  public void deleteContact() {
    System.out.println("Enter name of contact to delete:");
    String name = input.nextLine();
    for (Contact contact : contactList) {
      if (contact.getName().equals(name)) {
        contactList.remove(contact);
        break;
      }
    }
  }

  public static void main(String[] args) {
    ContactManager manager = new ContactManager();
    while (true) {
      System.out.println("1. Add new contact");
      System.out.println("2. Read contact list");
      System.out.println("3. Edit contact");
      System.out.println("4. Delete contact");
      System.out.println("5. Exit");
      int choice = Integer.parseInt(input.nextLine());
      switch (choice) {
        case 1:
          manager.addContact();
          break;
        case 2:
          manager.readContactList();
          break;
        case 3:
          manager.editContact();
          break;
        case 4:
          manager.deleteContact();
          break;
        case 5:
          System.exit(0);
          break;
      }
    }
  }
}

class Contact {
  private String name;
  private String phoneNumber;
  private String email;

  public Contact(String name, String phoneNumber, String email) {
    this.name = name;
    this.phoneNumber = phoneNumber;
    this.email = email;
  }

  public String getName() {
    return name;
  }

  public String getPhoneNumber() {
    return phoneNumber;
  }

  public String getEmail() {
    return email;
  }

  public void setPhoneNumber(String phoneNumber) {
    this.phoneNumber = phoneNumber;
  }

  public void setEmail(String email) {
    this.email = email;
  }

}
